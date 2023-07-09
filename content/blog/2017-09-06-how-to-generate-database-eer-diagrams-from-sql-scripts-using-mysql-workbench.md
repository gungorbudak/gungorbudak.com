---
author: Güngör Budak
date: '2017-09-06T16:42:00+03:00'
slug: how-to-generate-database-eer-diagrams-from-sql-scripts-using-mysql-workbench
tags:
- mysql
- database
- mysql workbench
- database diagram
- eer diagram
- sql
title: How to Generate Database EER Diagrams from SQL Scripts using MySQL Workbench
year: '2017'
---

MySQL Workbench makes it really easy to generate EER diagrams from SQL scripts. Follow below steps to make one for yourself.

[Download](https://dev.mysql.com/downloads/workbench/) and install MySQL Workbench for your system.

See below simple SQL commands, later I'll use them to generate a sample diagram.

```sql
create table country (
    id integer primary key,
    name CHAR(55));

create table city (
    id integer primary key,
    country_id integer,
    name CHAR(55),
    foreign key (country_id) references country(id));
```


Open MySQL Workbench and create a new model (**File -> New Model**).

[![MySQL Workbench New Model](/public/images/eer-diagrams-sql-script-1.png)](/public/images/eer-diagrams-sql-script-1.png)

Then import your SQL script (**File -> Import -> Reverse Engineer MySQL Create Script**). Note that you should select MySQL Model tab prior to this to be able to import the SQL script.

[![MySQL Workbench Reverse Engineer MySQL Create Script](/public/images/eer-diagrams-sql-script-2.png)](/public/images/eer-diagrams-sql-script-2.png)

The above operation will open a window where you should be selecting your SQL file and make sure that you checked **Place imported objects on a diagram**. This will automatically generate the diagram for you.

[![MySQL Workbench Reverse Engineer MySQL Create Script Window](/public/images/eer-diagrams-sql-script-3.png)](/public/images/eer-diagrams-sql-script-3.png)

After you **Execute**, and complete, click **Continue** and then **Close** to finish up. You should be able to see the diagram as shown below.

[![MySQL Workbench EER Diagrams](/public/images/eer-diagrams-sql-script-4.png)](/public/images/eer-diagrams-sql-script-4.png)

Finally, use **File -> Export -> Export as Single Page PDF...** to export the diagram to a PDF file.

[![MySQL Workbench EER Diagrams Export as PDF](/public/images/eer-diagrams-sql-script-5.png)](/public/images/eer-diagrams-sql-script-5.png)

This applies to MySQL Workbench 6.3.9 on macOS Sierra 10.12.6.
