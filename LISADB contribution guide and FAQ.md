# LISADB contribution guide and FAQ

### 1. Set up the local enviroment

read the reference in admin/README.md

### 2. How to update or download new spreadsheets?

for update (if no new spreadsheet is created), just run again as README.md instructs, so the data refreshes along with the updates in Googlesheets.

If there a new seperate google spreadsheet is created, find the document in admin/src/lib/Resources.ts, inside "export const SPREADSHEETS", add a name of the new spreadsheet, along with its google ID which is the last part of the share link

### 3. How to include a new column/relationship in the database?

Find the document **src/init.sql** To update the init.sql with adding new tables by CREAT TABLE (notice the dependency of table is also important, the reference should be set up always before the foreign key or ManyToMany one, the order matters.

Test in the site: https://www.db-fiddle.com/ to debug

### 4. How to import the data of a new column?

Go to: admin/src/scripts/upsert-data.ts, create a new export const upsertTableName. Don't forget to add the following at the end

```
await upsertTableName(db, spreadsheets);
```

### 5. Tips for coding "export const upsertTableName"

#### Begin - import data

- locate the google sheet

```
const {GoogleSheetNameInResources} = Json;
isRecord {GoogleSheetNameInResources};
```

- locate a specific subsheet

```
const TableName**s**Json = GoogleSheetNameInResources["NameOfSubsheet"]
isArray(TableName**s**Json)
```

- to display the process and also for debug

```
console.log(
    `Inserting ${TableName**s**Json .length} rows into table_name...`,
  );
```

to define the type of import, such as isRecord, isArray, isString...refer to: [Typed-Assert](https://github.com/elierotenberg/typed-assert)

#### Handle the string

- recall the location of subsheet

```
for (const TableNameJson of TableName**s**Json) {
    isRecord(TableNameJson);
```

- matching the columns in Googlesheet with tables in SQL

  option 1: if the name of column in Googlesheet is exactly the same as the variable name in the sql database

  ```
    columnName, 
  ```

  option 2: if they are different

  ```
    columnName : sqlVariableName,
  ```

  option 3: if they are different and also the columnName of Googlesheet contains white space, such as "_", " ",

  ```
    ["columnName"]: sqlVariableName,
  ```

  **From now on, we should forget the column names in the google sheet, and always recall the name of SQL varaibles**

```
IsString(sqlVariableName); or isOptionofType/isSring.....;
```

#### Insert data to SQL

```
Insert to sql
      await db.query({
        name: "upsert_table_name_in_sql",
        text: `
          INSERT INTO table_name (
            varaible_name_1,
            varaible_name_2
          ) VALUES (
            $1,
            $2
          ) ON CONFLICT (varaible_name_1)DO UPDATE SET
        varaible_name_2 = $2;
      `,
        values: [varaible_name_1, varaible_name_2],});
```

**Becareful of the different usage "," ";"** There are more specific codings to deal with null and complex/empty strings, check details in codes.

### 6. Coding for debug

use the following code to debug

```
try{}
catch (error) {
      console.error(TableNameJson);
      throw error;
    }
```

### 7. Common errors and theirs solution

- syntax error
  check the usage of "," ";"
- is expcted to be a string
  high chance there is null value, use isOptionofType and treat the value in the db.query
- paramaters number is uncorrect
  check the code inside db.query, to count the numbers of variables and to check whether there is extra "," in value
- conflict Foreign Key
  either the refered table is not imported yet (change the order of table)
  or errors in sql schema (remember to run docker after update schema)