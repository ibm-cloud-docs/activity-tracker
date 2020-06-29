---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-26"

keywords: IBM Cloud, LogDNA, Activity Tracker, use cases

subcollection: Activity-Tracker-with-LogDNA

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


# Aligning IAM and Activity Tracker (COS prototype)
{: #at_iam}


{:shortdesc}

API for configuring IBM Cloud Object Storage buckets: [COS Resource Configuration API](https://cloud.ibm.com/apidocs/cos/cos-configuration#introduction)
*  Endpoint URL: `https://config.cloud-object-storage.cloud.ibm.com/v1`

| Action                                    | Method        |
|-------------------------------------------|---------------|
| Returns metadata for the specified bucket | `GET {endpoint}/{version}/{bucket}` |
| Make changes to a bucket's configuration  | `PATCH {endpoint}/{version}/{bucket}` | 



API for reading and writing objects: [COS Compatibility S3 API](https://cloud.ibm.com/apidocs/cos/cos-compatibility#introduction)

| Action                                    | Method |
|-------------------------------------------|-------------------|
| List buckets                              | `GET {endpoint}/{bucket}` |
| Create a bucket | `PUT {endpoint}/{Bucket}?{LocationConstraint}` |
| List objects    | `GET {endpoint}/{Bucket}?` |
| Check a bucket's headers | `HEAD {endpoint}/{Bucket}?`|
| Delete a bucket | `DELETE {endpoint}/{Bucket}?` |
| Upload an object | `PUT {endpoint}/{Bucket}/{Key}` |
| Download an object | `GET {endpoint}/{Bucket}/{Key}` |
| Check an object''s headers | `HEAD {endpoint}/{Bucket}/{Key}`|
| Delete an object | `DELETE {endpoint}/{Bucket}/{Key}` | 


## Bucket actions

Bucket actions:

`cloud-object-storage.bucket.read`  ????

| Action                                   | Method             | IAM Action                                            | Permission Keyword    | AT action       |
|------------------------------------------|--------------------|-------------------------------------------------------|-----------------------|-----------------|
| List the buckets in the service instance | GET Capabilities   | `cloud-object-storage.account.get_account_buckets`	| s3:ListAllMyBuckets   | `cloud-object-storage.instance.list` |
| Create a bucket in the service instance  | POST Bucket	    | `cloud-object-storage.bucket.post_bucket`             | s3:CreateBucket       | `cloud-object-storage.bucket.create` |
| Delete a bucket in the service instance  | DELETE Bucket      | `cloud-object-storage.bucket.delete_bucket`           | s3:DeleteBucket       | `cloud-object-storage.bucket.delete` |
| | | | | |
| List the objects in the bucket           | GET Bucket         | `cloud-object-storage.bucket.get`                     | s3:ListBucket         | `cloud-object-storage.bucket.list`   |
| | | | | |
| Get the CORS configuration               | GET Bucket cors    | `cloud-object-storage.bucket.get_cors`                | s3:GetBucketcors     | `cloud-object-storage.bucket-cors.read`|
| Create the CORS configuration            | PUT Bucket cors    | `cloud-object-storage.bucket.put_cors`                | s3:PutBucketcors     | `cloud-object-storage.bucket-cors.create` |
| Delete the CORS configuration            | DELETE Bucket cors | `cloud-object-storage.bucket.delete_cors`             | s3:DeleteBucketcors  | `cloud-object-storage.bucket-cors.delete` |
| | | | | |
| Get the bucket ACL                        | GET Bucket acl     | `cloud-object-storage.bucket.get_acl`                 | s3:GetBucketAcl       | `cloud-object-storage.bucket-acl.read` |
| Create the bucket ACL                     | PUT Bucket acl     | `cloud-object-storage.bucket.put_acl`                 | s3:PutBucketAcl       | `cloud-object-storage.bucket-acl.create` |
| | | | | |
| Get the bucket CRN                        | Get Bucket CRN     | `cloud-object-storage.bucket.list_bucket_crn`         | s3:GetBucketCrn | `cloud-object-storage.bucket-crn.read` |
| | | | | |
| Get the bucket location                   | GET Bucket Location | `cloud-object-storage.bucket.get_location`       | s3:GetBucketLocation  | `cloud-object-storage.bucket-location.read` |


| Action                                   | Method             | IAM Action                                            | Permission Keyword    | AT action       |
|------------------------------------------|--------------------|-------------------------------------------------------|-----------------------|-----------------|
| Delete a Key Protect root encryption key |  |  |  | `cloud-object-storage.bucket-key-state.update`|


| Action                                   | Method             | IAM Action                                            | Permission Keyword    | AT action       |
|------------------------------------------|--------------------|-------------------------------------------------------|-----------------------|-----------------|
| Get the metadata for the bucket          | GET Bucket Basic   | `cloud-object-storage.bucket.get_basic`               | ibm:GetBucketBasic    | `cloud-object-storage.bucket-lifecycle.read`   |
| Check a bucket's headers                 | HEAD Bucket        | `cloud-object-storage.bucket.head`                    | s3:ListBucket         |  `cloud-object-storage.bucket-lifecycle.read` (outcome failure) |
| | | | | |
| Get the bucket lifecycle configuration    | GET Bucket Lifecycle | `cloud-object-storage.bucket.get_lifecycle` | s3:GetLifecycleConfiguration | `cloud-object-storage.bucket-lifecycle.read ` |
| Create the bucket lifecycle configuration | PUT Bucket Lifecycle | `cloud-object-storage.bucket.put_lifecycle` | s3:PutLifecycleConfiguration | `cloud-object-storage.bucket-lifecycle.create` |
| Delete the bucket lifecycle configuration |                   |                                                       |                       | `cloud-object-storage.bucket-lifecycle.delete` |
| | | | | |
| Read the retention policy of a bucket | GET Bucket Policy | `cloud-object-storage.bucket.get_policy` | s3:GetBucketPolicy  | ``|
| Set the retention policy of a bucket | PUT Bucket Policy | `cloud-object-storage.bucket.put_policy` | s3:PutBucketPolicy  | ``|
| Modify the retention policy of a bucket |   |   |   |  |
| Delete the retention policy     | DELETE Bucket Policy | cloud-object-storage.buket.delete_policy | s3:DeleteBucketPolicy   | `` |
| | | | | |
| Enable Activity Tracker    | PUT Bucket Activity Tracking | `cloud-object-storage.bucket.put_activity_tracking` | ibm:PutBucketActivityTracking | `cloud-object-storage.resource-configuration.update` |
| Read AT tracking configuration | GET Bucket Activity Tracking | `cloud-object-storage.bucket.get_activity_tracking` | ibm:GetBucketActivityTracking | `cloud-object-storage.bucket-lifecycle.read`|
| | | | | |
| Enable montioring with Sysdig    | PUT Bucket Metrics Monitoring | `cloud-object-storage.bucket.put_metrics_monitoring` | ibm:PutBucketMetricsMonitoring | `cloud-object-storage.resource-configuration.update` |
| Read monitoring configuration | GET Bucket Metrics Monitoring | `cloud-object-storage.bucket.get_metrics_monitoring` | ibm:GetBucketMetricsMonitoring | `cloud-object-storage.resource-configuration.read` |
| | | | | |
| Configure Firewall IPs      | PUT Bucket Firewall | `cloud-object-storage.bucket.put_firewall` | ibm:PutBucketFirewall | `cloud-object-storage.resource-configuration.update` |
| Read configured firewall IPs | GET Bucket Firewall | `cloud-object-storage.bucket.get_firewall` | ibm:GetBucketFirewall | `cloud-object-storage.resource-configuration.read` |
| | | | | |
| Add an expriration rule | PUT Bucket Policy | `cloud-object-storage.bucket.put_policy` | s3:PutBucketPolicy | `cloud-object-storage.bucket-lifecycle.create` |






ListCrkId	Manager, Writer	cloud-object-storage.bucket.list_crk_id	s3:ListBucket


GET Bucket Object versions	Manager, Writer, Reader, ContentReader	cloud-object-storage.bucket.get_versions	s3:ListBucketVersions

List Multipart Uploads	Manager, Writer, Reader	cloud-object-storage.bucket.get_uploads	s3:ListBucketMultipartUploads



GET Bucket Versioning	Manager, Writer, Reader	cloud-object-storage.bucket.get_versioning	s3:GetBucketVersioning
PUT Bucket Versioning	Manager, Writer	cloud-object-storage.bucket.put_versioning	s3:PutBucketVersioning
GET Bucket FASP Connection Info	Manager, Writer, Reader	cloud-object-storage.bucket.get_fasp_connection_info	ibm:GetFaspConnectionInfo
DELETE Bucket FASP Connection Info	Manager, Writer	cloud-object-storage.account.delete_fasp_connection_info	ibm:DeleteFaspConnectionInfo

GET Bucket Notifications	NotificationsManager	cloud-object-storage.bucket.get_notifications	ibm:GetBucketNotifications
PUT Bucket Notifications	NotificationsManager	cloud-object-storage.bucket.put_notifications	ibm:PutBucketNotifications

GET Bucket Logging	Manager, Writer, Reader	cloud-object-storage.bucket.get_logging	s3:GetBucketLogging
PUT Bucket Logging	Manager, Writer	cloud-object-storage.bucket.put_logging	s3:PutBucketLogging

GET Bucket Tagging	Manager, Writer, Reader	cloud-object-storage.bucket.get_tagging	s3:GetBucketTagging
PUT Bucket Tagging	Manager, Writer	cloud-object-storage.bucket.put_tagging	s3:PutBucketTagging
DELETE Bucket Tagging	Manager, Writer	cloud-object-storage.bucket.delete_tagging	s3:DeleteBucketTagging

GET Bucket Website	Manager, Writer, Reader	cloud-object-storage.bucket.get_website	s3:GetBucketWebsite
PUT Bucket Website	Manager, Writer	cloud-object-storage.bucket.put_website	s3:PutBucketWebsite
DELETE Bucket Website	Manager, Writer	cloud-object-storage.bucket.delete_website	s3:DeleteBucketWebsite

GET Bucket Replication	Manager, Writer, Reader	cloud-object-storage.bucket.get_replication	s3:GetReplicationConfiguration
PUT Bucket Replication	Manager, Writer	cloud-object-storage.bucket.put_replication	s3:PutReplicationConfiguration
DELETE Bucket Replication	Manager, Writer	cloud-object-storage.bucket.delete_replication	s3:DeleteReplicationConfiguration

PUT Bucket protection	Manager	cloud-object-storage.bucket.put_protection	s3:PutBucketProtection
GET Bucket protection	Manager, Writer, Reader	cloud-object-storage.bucket.get_protection	s3:GetBucketProtection


GET Bucket Accelerate	Manager, Writer, Reader	cloud-object-storage.bucket.get_accelerate	s3:GetAccelerateConfiguration
PUT Bucket Accelerate	Manager, Writer	cloud-object-storage.bucket.put_accelerate	s3:PutAccelerateConfiguration



Object actions:

| Action                                   | API                | IAM Action                                            | Permission Keyword    | AT action       |
|------------------------------------------|--------------------|-------------------------------------------------------|-----------------------|-----------------|


GET Object	Manager, Writer, Reader, ContentReader,ObjectReader	cloud-object-storage.object.get	s3:GetObject
HEAD Object	Manager, Writer, Reader, ContentReader,ObjectReader	cloud-object-storage.object.head	s3:GetObject
GET Object Torrent	Manager, Writer, Reader	cloud-object-storage.object.get_torrent	s3:GetObject
GET Object (Version)	Manager, Writer, Reader, ContentReader,ObjectReader	cloud-object-storage.object.get_version	s3:GetObjectVersion
HEAD Object (Version)	Manager, Writer, Reader, ContentReader,ObjectReader	cloud-object-storage.object.head_version	s3:GetObjectVersion
GET Object Torrent (Version)	Manager, Writer, Reader	cloud-object-storage.object.get_torrent_version	s3:GetObjectVersion
PUT Object	Manager, Writer,ObjectWriter	cloud-object-storage.object.put	s3:PutObject
POST Object (Forms)	Manager, Writer,ObjectWriter	cloud-object-storage.object.post	s3:PutObject
POST Object (Metadata Update)	Manager, Writer,ObjectWriter	cloud-object-storage.object.post_md	s3:PutObject
Initiate Multipart Upload	Manager, Writer,ObjectWriter	cloud-object-storage.object.post_initiate_upload	s3:PutObject
Upload Part	Manager, Writer,ObjectWriter	cloud-object-storage.object.put_part	s3:PutObject
Upload Part (Copy)	Manager, Writer	cloud-object-storage.object.copy_part	s3:PutObject
Upload Part (Copy)	Manager, Writer, Reader	cloud-object-storage.object.copy_part_get	s3:PutObject
Complete Multipart Upload	Manager, Writer,ObjectWriter	cloud-object-storage.object.post_complete_upload	s3:PutObject
PUT Object - Copy	Manager, Writer	cloud-object-storage.object.copy	s3:PutObject
PUT Object - Copy	Manager, Writer, Reader	cloud-object-storage.object.copy_get	s3:PutObject
GET Object acl	Manager	cloud-object-storage.object.get_acl	s3:GetObjectAcl
GET Object acl (Version)	Manager	cloud-object-storage.object.get_acl_version	s3:GetObjectVersionAcl
PUT Object acl	Manager	cloud-object-storage.object.put_acl	s3:PutObjectAcl
PUT Object acl (Version)	Manager	cloud-object-storage.object.put_acl_version	s3:PutObjectVersionAcl
DELETE Object	Manager, Writer	cloud-object-storage.object.delete	s3:DeleteObject
DELETE Object (Version)	Manager, Writer	cloud-object-storage.object.delete_version	s3:DeleteObjectVersion
List Parts	Manager, Writer, Reader,ObjectWriter	cloud-object-storage.object.get_uploads	s3:ListMultipartUploadParts
Abort Multipart Upload	Manager, Writer,ObjectWriter	cloud-object-storage.object.delete_upload	s3:AbortMultipartUpload
GET Object Torrent	Manager, Writer, Reader	cloud-object-storage.object.get_torrent	s3:GetObjectTorrent
Get Object Torrent (Version)	Manager, Writer, Reader	cloud-object-storage.object.get_torrent_version_id	s3:GetObjectVersionTorrent
POST Object restore	Manager, Writer	cloud-object-storage.object.restore	s3:RestoreObject
DELETE Multiple Objects	Manager, Writer	cloud-object-storage.object.post_multi_delete	s3:PostObjectMultiDelete
GET Object Tagging	Manager, Writer, Reader	cloud-object-storage.object.get_tagging	s3:GetObjectTagging
PUT Object Tagging	Manager, Writer	cloud-object-storage.object.put_tagging	s3:PutObjectTagging
DELETE Object Tagging	Manager, Writer	cloud-object-storage.object.delete_tagging	s3:deleteObjectTagging
POST Object legalHold	Manager, Writer	cloud-object-storage.object.post_legal_hold	s3:PostObjectLegalHold
GET Object legalHold	Manager, Writer, Reader	cloud-object-storage.object.get_legal_hold	s3:GetObjectLegalHold
POST Object extendRetention	Manager, Writer	cloud-object-storage.object.post_extend_retention	s3:PostObjectExtendRetention

{: caption="Register- success" caption-side="top"}


