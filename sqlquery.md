---

copyright:
  years:  2018, 2019
lastupdated: "2019-08-15"

keywords: IBM Cloud, LogDNA, {{site.data.keyword.at_short}}, EU-supported

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

# Using SQL Query to monitor events in archived files
{: #sqlquery}

You can use the {{site.data.keyword.sqlquery_short}} service to query {{site.data.keyword.at_full_notm}} (AT) archive files that are stored in a {{site.data.keyword.cos_short}} (COS) bucket in your account. You can run queries from the {{site.data.keyword.cloud_notm}} UI, or programmatically.
{:shortdesc}

![{{site.data.keyword.cloud_notm}} services integration scenario](images/sqlquery.png "{{site.data.keyword.cloud_notm}} services integration scenario")

Each {{site.data.keyword.at_full_notm}} instance has a service plan associated that indicates the number of days that you can query data through the web UI. To have access to the events after this period, you must enable archiving in the {{site.data.keyword.at_full_notm}} instance. When you enable archiving, you get an archive file daily. This file contains information for the previous day. Notice that UTC timestamps are used to determine which records are included in each file. The file name includes the ID of your {{site.data.keyword.at_full_notm}} instance and the date of the records that are included in the file.

To query the archive data in a file, you can use the {{site.data.keyword.sqlquery_short}} service. The service offers an SQL editor through the UI, and also programmatic options such as a REST API.

Use the {{site.data.keyword.sqlquery_short}} user interface (UI) to develop and test your queries, and the [SQL Query REST API](#restapi) to automate them. 
{: tip}

The {{site.data.keyword.sqlquery_short}} service provides a serverless, no-ETL solution to easily query data stored in {{site.data.keyword.cos_short}}. Underneath, SQL Query uses Apache Spark SQL as its underlying query engine. 

You can use the {{site.data.keyword.sqlquery_short}} to run SQL queries (that is, `SELECT` statements) to analyze, transform structured and semi-structured data, or clean up rectangular data. You cannot run actions such as `CREATE`, `DELETE`, `INSERT`, and `UPDATE`.

The {{site.data.keyword.sqlquery_short}} service can process input data that is read from CSV, JSON, ORC, Parquet, or AVRO files. **Notice that the archive files from an {{site.data.keyword.at_full_notm}} instance contain data in JSON format.**

Each query result can be written to a `CSV`, `JSON`, `ORC`, `PARQUET`, or `AVRO` file in a {{site.data.keyword.cos_short}} instance of your choice. **When you query an {{site.data.keyword.at_full_notm}} archive file, you must convert the JSON formatted file into `PARQUET` format to be able to query the contents successfully.**





## Prerequisites
{: #sqlquery_prereq}

To be able to use the {{site.data.keyword.sqlquery_short}} service to query archived event files, check the following prerequites: 

* You have access to a COS instance in your account. 

    You must have access to a bucket that contains the {{site.data.keyword.at_full_notm}} archive files and a bucket to use to store results from your queries. 

* You have an {{site.data.keyword.at_full_notm}} instance provisioned in your account that has [archiving configured to a bucket in the COS instance in your account](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving). 

    Events are archived daily to a file in a COS bucket. 

    Notice that if archiving is not configured, you must wait at least 24 hours before an archive file is available after archiving is configured.

* You have 1 or more archive files uploaded in the bucket.

* You have a policy on the COS service with at least platform role **reader** so that you can view data in the COS bucket where the archive files are uploaded.

* You have a policy on the COS instance with at least **Writer** access to at least one COS bucket so that result files (files containing output data) can be written there.



## Provisioning an {{site.data.keyword.sqlquery_short}} instance
{: #sqlquery_step1}

To query archive files hosted in a COS bucket, you can use the {{site.data.keyword.sqlquery_short}} service.

Notice that you must provision an instance of the {{site.data.keyword.sqlquery_short}} service in the same account where the COS instance that manages the bucket with the files that you want to query is available.
{: important}

To provision an instance, see [Create your {{site.data.keyword.sqlquery_short}} service instance](/docs/services/sql-query?topic=sql-query-gettingstarted#sql_query).

When you provision the instance with the **Lite** plan, you can only run 1 query at a time.
{: note}

Once you have {{site.data.keyword.sqlquery_short}} running on {{site.data.keyword.cloud_notm}}, you can immediately start querying your data by using the {{site.data.keyword.sqlquery_short}} UI, or programmatically by using either [the {{site.data.keyword.sqlquery_short}} REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/apidocs/sql-query){:new_window}, or the Python `ibmcloudsql` library. 


## Granting user permissions to run a query
{: #sqlquery_step2}

To run queries with the SQL query service, a user needs a platform role and a service role. The following tables show the roles that are enabled to run an action:


| Platform actions                        | Administrator                                     | Editor | Operator | Viewer  |
|---------------------------------------------------------------------------|:-------------------------------------------------:|:-------:|:--------:|:------:|
| `View details of a service instance`    | ![Checkmark icon](../../icons/checkmark-icon.svg)  | ![Checkmark icon](../../icons/checkmark-icon.svg)    | ![Checkmark icon](../../icons/checkmark-icon.svg)      | ![Checkmark icon](../../icons/checkmark-icon.svg)    |
{: caption="Table 1. Platform roles" caption-side="top"}


| Service actions                 | Manager                                           | Writer                                            | Reader           |
|:-------------------------------:|:-------------------------------------------------:|:-------------------------------------------------:|:----------------:|
| `Run a query`                   | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |                  |
{: caption="Table 2. Service roles" caption-side="top"}

Notice that users with **reader** role, get an access error when they launch the SQL Query UI.

To manage access or assign new access for users by using IAM policies, you must be the account owner, administrator on all services in the account, or an administrator for the particular service or service instance. 

Choose any of the following actions to manage IAM policies in the {{site.data.keyword.cloud_notm}}:

* To modify the permissions of a user, see [Editing existing access](/docs/iam?topic=iam-iammanidaccser#edit_existing).
* To grant permissions to a user, see [Assign new access](/docs/iam?topic=iam-iammanidaccser#assign_new_access).
* To revoke permissions, see [Removing access](/docs/iam?topic=iam-iammanidaccser#removing_access).
* To review a user's permissions, see [Reviewing your assigned access](/docs/iam?topic=iam-iammanidaccser#review_your_access).


## Running a query through the {{site.data.keyword.sqlquery_short}} UI
{: #sqlquery_step3}

In SQL, the term *query* is just another way of saying *SELECT statement*. 

To run a query, complete the following steps:

### Step 1. Launching the {{site.data.keyword.sqlquery_short}} query UI
{: #sqlquery_step3-1}

1. [Log in to your {{site.data.keyword.cloud_notm}} account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.

	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} dashboard opens.

2. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Resource list** &gt; **Services**.

3. Select an {{site.data.keyword.sqlquery_short}} instance.

4. From the *Manage* tab, select **Launch {{site.data.keyword.sqlquery_short}} UI**.

When the {{site.data.keyword.sqlquery_short}} query UI opens, a COS bucket is automatically generated. This bucket is used by default by the {{site.data.keyword.sqlquery_short}} service to store the results from your SQL queries. 

Wen you run queries, you can specify a custom bucket to store results in. If your query does not specify one, the default one is used.
{: note}

### Step 2. Getting information on the file that you want to query in COS
{: #sqlquery_step3-2}

Complete the following steps:

1. In the {{site.data.keyword.cloud_notm}} dashboard, click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) &gt; **Resource list** &gt; **Storage**.

2. Select the {{site.data.keyword.sqlquery_short}} instance that has the bucket with the archive files.

    Contact your {{site.data.keyword.at_full_notm}} administrator to get the COS information.

3. Select **Buckets**. 

4. Select the bucket name. You can see the list of archive files in the bucket.

5. Identify the file that you want to query.

    Notice that the file name has the name of your {{site.data.keyword.at_full_notm}} instance and the date, in UTC format, of the events that are included.

    If you get a file of `20 bytes`, that file does not have any data.

6. For that file, select **SQL URL**.

    A window opens that shows the URL.

7. Copy the URL.

### Step 3. Getting information on the COS bucket that is used to store results from queries
{: #sqlquery_step3-3}

Complete the following steps:

1. Select **Buckets**. 

2. Select the bucket name that you plan to use to store the results from queries.

3. For that bucket, select **SQL URL**.

    A window opens that shows the URL.

4. Copy the URL.


### Step 4. Transforming an archive file to PARQUET format
{: #sqlquery_step3-4}

When you query an archive file, the format of the data is JSON. You must transform the format to **PARQUET** to query successfully the data. 
{: important}

Parquet is an open source file format that stores nested data structures into a flat columnar format, and preserves the schema of the original data. 

The {{site.data.keyword.sqlquery_short}} UI is an editor that lets you immediately start composing SQL queries. Since SQL Query uses Spark SQL, you can use Spark SQL functions and ANSI SQL to compose both simple and complex queries that involve large amounts of data.

In the {{site.data.keyword.sqlquery_short}} UI, you must run the following query to transform content from JSON into **PARQUET** format:

```
SELECT * FROM SQL_URL STORED AS JSON 
INTO RESULTS_BUCKET STORED AS PARQUET
```
{: codeblock}

Where

* **SQL_URL** is the sql URL of the archive file in COS
* **RESULTS_BUCKET** is the sql URL of the custom COS bucket that you plan to use to upload the query results

For example, the following query is used to transform an archive file:

```
SELECT * FROM cos://ams03/at-logdna-eu-de/999999d8f1f.2019-06-03.62.json.gz STORED AS JSON 
INTO cos://eu-de/results-at STORED AS PARQUET
```
{: screen}

Complete the following steps to run the query:
1. In the SQL editor field of the {{site.data.keyword.sqlquery_short}} UI, enter a SELECT statement.
2. Click **Run**.

    You can see the query result in the *Result* area of the UI. 

    You can see the target COS URL in the *Result location* area of the UI. This URL points to the object storage bucket used by {{site.data.keyword.sqlquery_short}} to store the results.
    
    With the lite plan, you can run only 1 query. You can run up to 5 queries simultaneously with a paid plan.

3. Copy the **Result location URL**. You need it to run other queries to analyze the events that are included in that archive file.

After you run the query, three objects are written as a result set in your COS results bucket:

1. `jobid=<job_id>`
2. `jobid=<job_id>/_SUCCESS`
3. `jobid=<job_id>/<part-number>`

Only one object contains the result set (`jobid=<job_id>/<part-number>`), and the other two are empty and don't contain any data. 

It is important not to delete any of the files if you want to use the result set.
{: important}

Each result is stored with an own job ID prefix that allows you to use the result directly in a query.

When you want to specify a result as input in your SQL query, specify the first (`jobid=<job_id>`) or the third one (`jobid=<job_id>/<part-number>`).

[Learn more about the result set created per query](/docs/services/sql-query?topic=sql-query-overview#result).

After you have the file converted to 'PARQUET` format, you can run queries to analyze its content.
{: note}


### Step 5. Running a query to determine the number of events in the archive file
{: #sqlquery_step3-5}

To report on the total number of events that are included in the archive file, run the following query:

```
SELECT COUNT(*) AS NUMBER_EVENTS FROM PARQUET_FILE STORED AS PARQUET
INTO RESULTS_BUCKET STORED AS CSV
```
{: codeblock}

Where

* **NUMBER_EVENTS** is the name of the field that you want to use to report the numerical value
* **PARQUET_FILE** is the **Result location URL** that you get when you transform the archive file from JSON to PARQUET
* **RESULTS_BUCKET** is the sql URL of the custom COS bucket that you plan to use to upload the query results

For example, to get the total number of events in a file, you can run the following query:
```
SELECT COUNT(*) AS logLines FROM cos://eu-de/results-at/jobid=f178778e-7707-46a9-982d-1e89261b63a5 STORED AS PARQUET
INTO cos://eu-de/results-marisa STORED AS CSV
```
{: screen }






    - If required, you can use JOIN constructs to join data from several input files, even if those files are located in different instances.








SELECT _source.action AS component, COUNT(*) AS logLines FROM cos://us-south/sql.query.at.demo/transformed_logs_3a941d8f1f.2019-06-03.62 STORED AS PARQUET GROUP BY _source.action
-- INTO clause was automatically added based on the default target
INTO cos://us-south/sql-e1b292f2-0796-4b8f-98a0-06c390db916d/result/ STORED AS CSV


SELECT COUNT(*) AS logLines FROM cos://us-south/sql.query.at.demo/transformed_logs_3a941d8f1f.2019-06-03.62 STORED AS PARQUET
-- INTO clause was automatically added based on the default target
INTO cos://us-south/sql-e1b292f2-0796-4b8f-98a0-06c390db916d/result/ STORED AS CSV

SELECT _source.action AS component, _source.eventTime AS eventtime FROM cos://us-south/sql.query.at.demo/transformed_logs_3a941d8f1f.2019-06-03.62 STORED AS PARQUET
-- INTO clause was automatically added based on the default target
INTO cos://us-south/sql-e1b292f2-0796-4b8f-98a0-06c390db916d/result/ STORED AS CSV


SELECT _source.action AS component, _source.eventTime AS eventtime FROM cos://us-south/sql.query.at.demo/transformed_logs_3a941d8f1f.2019-06-03.62 STORED AS PARQUET ORDER BY _source.eventTime
-- INTO clause was automatically added based on the default target
INTO cos://us-south/sql-e1b292f2-0796-4b8f-98a0-06c390db916d/result/ STORED AS CSV

SELECT _source.action AS component, _source.eventTime AS eventtime FROM cos://us-south/sql.query.at.demo/transformed_logs_3a941d8f1f.2019-06-03.62 STORED AS PARQUET
-- INTO clause was automatically added based on the default target
INTO cos://us-south/sql-e1b292f2-0796-4b8f-98a0-06c390db916d/result/ STORED AS CSV

SELECT * FROM CLEANCOLS(cos://us-south/logdna-dallas-test/2efeb87512.2019-07-09.70.json.gz STORED AS JSON)
INTO cos://us-south/sql.query.at.demo/transformed_logs_2efeb87512.2019-07-09.70 STORED AS PARQUET


SELECT _index AS index, _source._app AS app, _source._ts AS timestamp FROM cos://us-south/sql.query.at.demo/transformed_logs_2efeb87512.2019-07-09.70 STORED AS PARQUET

INTO cos://us-south/sql-e1b292f2-0796-4b8f-98a0-06c390db916d/result/ STORED AS CSV







## Limitations
{: #limitations}

- If a JSON, ORC, or Parquet object contains a nested or arrayed structure, using a wildcard (for example, `select * from cos://...`) returns an error such as 
"Invalid CSV data type used: `struct<nested JSON object>`."
Use one of the following workarounds:
  - For a nested structure, specify the fully nested column name instead of the wildcard, for example, `select address.city from cos://...`.
  - For an array, use the Spark SQL explode() function, for example, `select explode(address.city) from cos://...`.
- If you receive a corrupted result, verify that the source file is correct and that the correct input file format is specified using 'STORED AS' in the SQL statement.
- If you receive an error message stating that some columns are not found in the input columns,
but the columns do exist in the input file, check if the input file format being specified using 'STORED AS'
in the SQL statement is the actual file format of your current file.
- In order to further process CSV output with {{site.data.keyword.sqlquery_short}}, all values have to be contained within one line. The multi-line option is not supported and therefore must be manually changed. 
To remove new lines from multi-line column values, use the SQL function `regexp_replace`. For example, a CSV object `data` has an attribute `multi_line` containing values spanning multiple lines. To select a subset of rows based on a `condition` and store it on COS for further processing, a skeleton SQL statement looks like the following:

	`SELECT regexp_replace(multi_line, '[\\r\\n]', ' ') as multi_line FROM data STORED AS CSV WHERE condition`
	
- Ensure that each SQL query updating the composite object uses the same column select list, meaning that names of columns and sequence 
of columns have to be identical. Otherwise, composed objects become unreadable due to incompatible headers stored in different parts of the object.
- Ensure that for growing composite objects, all SQL statements that update the object and introduce new columns to a column selection list, add these columns to the end of the column list. If this is not the case, the structure of the object gets corrupted, causing unreadable objects, corrupted data, or unreliable results.
