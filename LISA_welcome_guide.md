# LISA Welcome Guide

This is a guide to help contributors of LISA to get onboard, and mainly focus on the tech and database part. For Learner Porile(assessment and visualization), approach Anirudh or Kseniia for an updated orientation.

## Background

### Architecture

![Architecture](https://github.com/xuanqiz/lisa-db/blob/directus-www/Architecture.png)

### Recommended reading

[1] [About LISA DB and the database of support resources](https://docs.google.com/document/d/1mUFWPNduuATLscxms1EsisRDfyfZNWFaslUIIp2L1X0/edit)

[2] [Learner Individualized Support Assistant](https://docs.google.com/document/d/1Zjh2kauiyZQVP8hehJIxbsRkcL53YD19WbssjI3-2Gk/edit)

In short, Learner Individualized Support Assistant (LISA) is a novel digital tool that aiming to help every kid according to their needs. 

## About Us

### IFEA

The project LISA is incubated in the school [IFEA](https://ifea.education/en/), an innovative school located at Clichy near Paris.

### Team Members

Elie Rotenberg, PhD, 

Ariel B. Lindner, PhD, 

Arno Klein, PhD

Anirudh Krishnakumar, PhD,

Kseniia Konishcheva, MSc

### Partnership:

[Chile Mind Institute (CMI)](https://childmind.org/)

[The Center for Research and Interdisciplinarity (CRI)](https://cri-paris.org/en)

## Tech

### Check list of tech installation/registration:

1. [VSCode](https://code.visualstudio.com) (the project pre-configured with this editor, but it's also possible to use others)

2. [Node JS](https://nodejs.org/en/download/)

3. [Docker](https://docs.docker.com/get-docker/)

4. [Github account](https://github.com)

5. (Optional) [LISA DB Admin App]( https://admin.lisa-db.ifea.education/admin/)

   The account is created by Elie, if you work on database, contact him for access

### Prepare your working repository:

1. find Elie's Github (Ofcourse follow him and star the project)

   - [LISA Prototype](https://github.com/elierotenberg/lisa-prototype)

   - [LISA Dashboard](https://github.com/elierotenberg/lisa-db)

     confirm with the team of the choice

2. Fork the repository (right top of the page, don't clone befoer fork)

   [Github instructions here](https://docs.github.com/en/get-started/quickstart/fork-a-repo)

3. You will be redirected to a new page like YourUserName/lisa-db, now [clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository) it locally to create your work branch (example with LISA Dashboard)

   **Method1: HTTPS**

   `https://github.com/YOUR_USERNAME/lisa-db.git
   https://github.com/elierotenberg/lisa-db.git`

   **Method2: SSHkey** (Pre-requirement: [Connecting to GitHub with SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh))

   `git clone git@github.com:YOUR_USERNAME/lisa-db.git
   git checkout -b @content/add-my-custom-guide`

4. You might need to switch branch to do your tasks by using [git checkout](https://git-scm.com/docs/git-checkout), discuss with the team to identify your desired one.

5. Usually, there are specific guides under each branch, check the one you needed. 

   **Tips:** 

   - search within the repository: Readme/CONTRIBUTING.md
   - instructions might vary under admin/www

### Tech Enviroments

If you already know some of these will be helpful, but if you don't know them before, you will have the chance to learn them in your contribution.

- [TypeScript](https://www.typescriptlang.org/docs/) (coding)
- [React.js](https://reactjs.org/docs/getting-started.html), [next.js](https://nextjs.org/docs/getting-started), [node. js](https://nodejs.org/en/docs/guides/) (full-stack)
- [PostgreSQL](https://www.postgresql.org/about/) (database)
  - [Diagrams.net](https://www.diagrams.net) (skema construction)
  - [Db-fiddle](https://www.db-fiddle.com) (script bug detecter)
- [Directus](https://directus.io/) (Database management)
- [Figma](https://www.figma.com/) (wireframe)
- [Chakra UI](https://chakra-ui.com/) (front-end)
- [Swagger](https://swagger.io/) (API development)

### Suggestions

When there are bugs or questions, try with the following:

- Google it
- Official documentation of website

- [StackOverFlow](https://stackoverflow.com)

  no matter how simple the question is, believe that someone has asked in the past

- [Youtube](https://www.youtube.com)

  try with the keyword of the tech to find some video tutorials

- Your friends, classmates, work partners

- Your final life saver: Elie

## Database

### Architecture

![LISAMHdb-Architecture](https://github.com/xuanqiz/lisa-db/blob/directus-www/LISAMHdb3.0-Architecture.png)

### GoogleSheet Review

The work of database starts from a series of GoogleSheets that our researchers made in the past years. Our research team members then made a [prority list]( https://docs.google.com/document/d/1Ktd97V5AQaNOkfzYKq-5WyLM-hwcqnFr5FwigC55wio/edit) to for the primary version.

Thus, the first step to get familiar with the database, it's to go through the priority list, to open the Google sheets, and to browse the subsheets and columns.

Note: this step refers to 4 Google Sheets ([Disorders](https://docs.google.com/spreadsheets/d/13a0w3ouXq5sFCa0fBsg9xhWx67RGJJJqLjD_Oy1c3b0/edit#gid=1688172512), [Resources](https://docs.google.com/spreadsheets/d/1LeLlrsvBWMYTTIXTVtkynmBzzb0Uzi1OwpRLfyRAwzM/edit#gid=2061888024), [Assessments](https://docs.google.com/spreadsheets/d/1VUf3XnieYThY8OA6JWtpNP4zI2xa9xak9LXuyH_PaoE/edit#gid=2140512446), [States](https://docs.google.com/spreadsheets/d/11OkIWLwZYi9xkpuFODAKXQZHEFeMvYCQ8BTfIBKm0Z8/edit#gid=1401217933)) and the [MHDB priority sheets](https://docs.google.com/document/d/1Ktd97V5AQaNOkfzYKq-5WyLM-hwcqnFr5FwigC55wio/edit) (MHDB stands for Mental Health Dashboard, it's a bigger picture than LISA DB)

### PostgreSQL Schema Construction

After a overview of Google Sheet, the next step is to construct a data model to represent the information. The schema construction is done in the [diagrams.net](https://app.diagrams.net/#G1TzjiQH8p-sOGwXyafGgUvI-NhmrkOfUU), each table represents a subsheet and each entry represents a column in a sheet. To understand this schema, it is necessary to get familiar with the [SQL Language](https://www.postgresql.org/docs/13/index.html), for example, some key terms:

0. Relationships: One-To-One, One-To-Many, Many-To-Many

1. Constraints: primary key, foreign key, NOT NULL, unique etc.
2. Data Type: text, uuid, timestamp with time zone
3. etc. etc.

Thus, in this step, every colomn that is taken from Google Sheet has been assigned some attributes.	

In the bottom of the schema, you might find a part that all tables start with name LISA_XX, it's the schema made to display the database in front-end.  The domain and domain category correspond to SRQ(Strength and Resilience Questionnaire), Guide corresponds to EDUCARE guides. Details refer to Assessment part.

**Conventions**:

1. Assign NOT NULL to every "column" and use comments to explain when a NOT NULL is taken out
2. the name of each "column" should be name_of_column this format, little case joined by "_"
3. Avoid use abbrevations in the names unless it is over limit
4. Avoid the composite key for Directus reason, generate a uuid for composite keys (this could change when later we leave Directus), it also means only one Primary key per table
5. We prefer to explicitly present ManyToMany relationship in our schema

Notes: each row should have only one attribute, but in the schema, if you see FK1,FK2 in the same row, because it has been changed from a composite key to seperated single foreign keys.

### PostgreSQL Script Writing

After having valided the schema, the next step is to use PostgreSQL language to code it. 

The code start with CREATE TABLE. Notice that after a merge, when adding/deleting/modifying tables, don't edit direcly on the same file, rather we prefer to create a new 000X.sql in sequence. In the new 000X.sql, we use ALTER TABLE to modify already existed table, for example to add an attribute(column); for non-existed table, it's the same as CREATE TABLE in the beginning. On top of this, we still need a scratch.sql document which the code is all in CREATE TABLE fomat but corresponds to the combination of a series of 000X.sql. It's coder's responsibility to make sure the two different scripts match.

**Tips**:

1. Always run [Db-fiddle](https://www.db-fiddle.com/) to test before any commit (make sure you choose PostgreSQL v13)
2. dependent table always come first than others
3. Add "ON UPDATE CASCADE ON DELETE CASCADE" for all foreign keys
4. check the " , ; ()" spellings 
5. learn the keyboard shortcut of VS code can help improve the productivity

### Data Upsert to Directus

Now we have a data schema to hold all the information we have in Google sheet, so now we need to transform the data to from Google sheet to our database, autonomaically, with the help of coding. To do this step, we start to set up the local enviroment and also write code by TYPESCRIPT. Here are two technical guides corresponding to this procedure:

- Step 1: [Installation and progress overview](https://github.com/elierotenberg/lisa-db/tree/directus-www/admin) 

- Step 2: [Upserting FAQ](https://github.com/xuanqiz/lisa-db/blob/sql-schema/admin/Readme(contributing).md)  (Common errors and solutions are included)

### Directus CMS 

Following the last step to upser data to Directus (including installation and also upserting data), now log in to [LISA DB Admin App]( https://admin.lisa-db.ifea.education/admin/) with your given account, you should see plenty of data. [Directus official documentation](https://docs.directus.io/getting-started/introduction/) could be helpful, at least to understand the field/items such Directus terms. 

In the Directus maintainence part, there are two parts, one is to be able to modify "rows/items" manually, such as add or delete; the other is to be able to do configuration in the Data Model of Settings. 

**Manual modification Tips:** (Collections)

​	If you recall your memory, we prefer to use "name_of_the_column" to name a variable or a table in SQL script writing, but here, the name of the new items are like rows, and we prefer the form "name-of-the-row''. Try not to mix the naming principle. for your reference, here is a summary:

| Place                   | Writing Convention            |
| ----------------------- | ----------------------------- |
| SQL Tables & Columns    | underscore name_of_the_column |
| Url & item in Directus  | hyphens name-of-the-row       |
| Javascript / Typescript | camelCase or PascalCase       |

**Cofiguration Tips:** (Settings-DataModel)

	1. "generate and save UUID" for all uuids and disable to edit the value
 	2. "save current data/time" On Create
 	3. check the interface for all many-to-one relationships and choose a good display template
 	4. markdown field for content writing columns

### API

under construction

recommend tool: [Swagger](https://swagger.io/)
