---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-14"

keywords: IBM Cloud, LogDNA, Activity Tracker, account settings, config

subcollection: logdnaat

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

 
# Enhancing your data by defining custom indexed fields
{: #logdna_parsing}

In {{site.data.keyword.at_full_notm}}, you can create custom fields that you can use in advanced searches, and filtering queries by using parsing rules. You define parsing templates through the LogDNA web UI to add custom fields to your records.
{:shortdesc}


## Considerations when defining a parsing template


## Using custom fields



You can define parsers that define new index fields. These fields show up at the record level and can be used for searches in Views after 15 min. To be able to use them in Boards and screens take a bit longer. For example - I have a parser that adds the field client_id

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
When I defined the template - I could not use this index field in any view, board, or screen

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
after 15 min - I can see it in records as shown in the image above

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
after Midnight UTC - I can use it in boads

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
before it is available for selecting as a field in a board, and once it shows in records in your view -> you can use it in advanced searching

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
btq - there was a bug where All lines were not showing - That is fixed now and I can also see all the fields -

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
For your other question regarding copying raw lines - there is a new setting (I am currently trying to get that topic out) that sets the ability to see the raw line for each record (it is a setting that can only be turned on by the manager of the instance now) This is a change in functionaqlity from the way it was before where a user could change it itself

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
image.png 
image.png



Marisa LOPEZ DE SILANES RUIZ  1 hour ago
Notice that the raw line does not include all fields shown as line identifiers, etc -> The only way to get these fields is by exporting or getting the log line from an archive file

Marisa LOPEZ DE SILANES RUIZ  1 hour ago
And also - there is a new feature that can stop exporting to any users  - another new thing that has just been released