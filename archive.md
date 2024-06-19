---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-24"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Configuring archiving through the UI
{: #archiving}

You can archive events from an {{site.data.keyword.at_full_notm}} instance into a bucket in an {{site.data.keyword.cos_full_notm}} (COS) instance.
{: shortdesc}


{{../log-analysis/_include-segments/deprecation_notice.md}}

For more information about archiving, see [Archiving events to {{site.data.keyword.cos_full_notm}}](/docs/activity-tracker?topic=activity-tracker-archiving-ov).


Complete the following steps to archive an {{site.data.keyword.at_full_notm}} instance into a bucket in an {{site.data.keyword.cos_full_notm}} instance:


## Prerequisites on the {{site.data.keyword.at_full_notm}} service
{: #archiving_prereqs}

* **You must have a paid service plan** for the {{site.data.keyword.at_full_notm}} service. [Learn more](/docs/services/activity-tracker?topic=activity-tracker-service_plan#service_plan).

* Check that your user ID has permissions to launch the web UI and configure archiving. The following table lists the minimum roles that a user must have to be able to launch the {{site.data.keyword.at_full_notm}} web UI, and configure archiving through the UI or by using the API:

| Role                      | Permission granted            |
|---------------------------|-------------------------------|
| Platform role: `Viewer`     | Allows the user to view the list of service instances in the Observability dashboard. |
| Service role: `Manager`      | Allows the user to launch the web UI and configure archiving through the web UI or by using the API.  |
{: caption="Table 1. IAM roles" caption-side="top"}

For more information on how to configure policies for a user, see [Granting user permissions to a user or service ID](/docs/services/activity-tracker?topic=activity-tracker-iam_view_events#iam_view_events).



## Step 1. Grant IAM policies to a user to work with {{site.data.keyword.cos_full_notm}}
{: #archiving_step1}

**Note:** This step must be completed by the account owner or an administrator of the {{site.data.keyword.cos_full_notm}} service on the {{site.data.keyword.cloud_notm}}.

As an administrator of the {{site.data.keyword.cos_full_notm}} service, you must be able to provision instances of the service, grant other users permissions to work with these instances, and create service IDs.

There are different ways in which you can grant a user permission to become an editor of the {{site.data.keyword.cos_full_notm}} service:

* As administrator of the service in the account, the user must have an IAM policy for the {{site.data.keyword.cos_full_notm}} service with the platform role *Administrator*. You must assign this user access to an individual resource in the account.

* As administrator of the service within the context of a resource group, the user must have an IAM policy for the {{site.data.keyword.cos_full_notm}} service with the platform role *Administrator* within the context of the resource group.


The following table lists the roles that a user can have to complete the actions listed for the {{site.data.keyword.cos_full_notm}} service:

| Service                    | Platform roles    | Action                                                                                        |
|----------------------------|-------------------|-----------------------------------------------------------------------------------------------|
| `Cloud Object Storage`     | Administrator     | Allows the user to assign policies to users in the account to work with the {{site.data.keyword.cos_full_notm}} service. |
| `Cloud Object Storage`     | Administrator   \n Editor | Allows the user to provision an instance of the {{site.data.keyword.cos_full_notm}} service.    |
| `Cloud Object Storage`     | Administrator   \n Editor   \n Operator | Allows the user to create a service ID.    |
{: caption="Table 2. Roles and actions" caption-side="top"}


Complete the following steps to assign a user administrator role to the {{site.data.keyword.cos_full_notm}} service within the context of a resource group:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.
2. From the menu bar, click **Manage** &gt; **Access (IAM)**, and then select **Users**.
3. From the row for the user that you want to assign access, select the **Actions** menu, and then click **Assign access**.
4. Select **Assign access within a resource group**.
5. Select a resource group.
6. If the user does not have a role already granted for the selected resource group, choose a role for the **Assign access to a resource group** field.

    Depending on the role that you select, the user can view the resource group on their dashboard, edit the resource group name, or manage user access to the group.

    You can select **No access**, if you want the user to only have access to the {{site.data.keyword.at_full_notm}} service in the resource group.

7. Select **Cloud Object Storage**.
8. Select the platform role **Administrator**.
9. Click **Assign**.



## Step 2. Provision an instance of {{site.data.keyword.cos_full_notm}}
{: #archiving_step2}

**Note:** This step must be completed by an editor, or administrator of the {{site.data.keyword.cos_full_notm}} service on the {{site.data.keyword.cloud_notm}}.
Complete the following steps to provision an {{site.data.keyword.cos_full_notm}} instance:

1. From the menu bar, click **Catalog**. The list of the services that are available in {{site.data.keyword.cloud_notm}} opens.

2. To filter the list of services that is displayed, select the **Storage** category.

3. Click the **Object Storage** tile.

4. Enter a name for the service instance.

5. Select a resource group.

    By default, the **Default** resource group is set.

6. Select a service plan.

    By default, the **Lite** plan is set.

7. Click **Create**.



## Step 3. Create a bucket
{: #archiving_step3}

Buckets are a way to organize your data in an {{site.data.keyword.cos_full_notm}} instance.

To manage buckets, your user must be granted permissions to work with buckets on the {{site.data.keyword.cos_full_notm}} instance. For more information about roles, see [Identity and Access Management roles](/docs/cloud-object-storage?topic=cloud-object-storage-iam).

To create a bucket, your user must have manager or writer permissions for the {{site.data.keyword.cos_full_notm}} instance.
{: note}

Complete the following steps to create a bucket:

1. From the Navigation menu, select **Resource List**.

2. Select the {{site.data.keyword.cos_full_notm}} instance where you plan to create the bucket.

3. Select **Buckets**. Then, click **Create Bucket**.

    If you are configuring **archiving in an EU-managed location**, you must configure a bucket that complies with the EU-managed and GDPR regulations.

4. Enter a bucket name for the *Unique bucket name* field.

    **Note:** All buckets in all regions across the globe share a single namespace.

    You can use as part of the bucket name your {{site.data.keyword.at_full_notm}} instance name. For example, for an instance with name *logging-1*, you can use *accountN-logging-1* as your bucket name.

    You will need this name to configure archiving through the {{site.data.keyword.at_full_notm}} web UI.

5. Choose the type of resiliency and a location where you would like your data to be physically stored.

    Resiliency refers to the scope and scale of the geographic area across which your data is distributed.

    Cross Region resiliency will spread your data across several metropolitan areas.

    Regional resiliency will spread data across a single metropolitan area.

    A Single Data Center will only distribute data across devices within a single site.

    For more information, see [Select regions and endpoints](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints).

6. Choose the type of *Storage class*.

    You can create buckets with different storage classes. Choose the storage class for your bucket based on your requirements to retrieve data. For more information, see [Use storage classes](/docs/services/cloud-object-storage?topic=cloud-object-storage-classes).

    **Note:** It is not possible to change the storage class of a bucket once the bucket is created. If objects need to be reclassified, it is necessary to move the data to another bucket with the wanted storage class.

7. Optionally, add a Key Protect Key to encrypt data at rest.

    All objects are encrypted by default using randomly generated keys and an all-or-nothing-transform. While this default encryption model provides at-rest security, some workloads need to be in possession of the encryption keys used. For more information, see [Manage encryption](/docs/services/cloud-object-storage?topic=cloud-object-storage-encryption).




## Step 4. Create a service ID for the {{site.data.keyword.cos_full_notm}} instance
{: #archiving_step4}

A service ID identifies a service similar to how a user ID identifies a user. Service IDs are not tied to a specific user. If the user that creates the service ID leaves your organization and is deleted from the account, the service ID remains.

You must create a service ID for your {{site.data.keyword.cos_full_notm}} instance. This service ID is used by the {{site.data.keyword.at_full_notm}} instance to authenticate with your {{site.data.keyword.cos_full_notm}} instance.

You must assign specific access policies to the service ID that restrict permissions for using specific services, or even combine permissions for accessing different services.


Complete the following steps to create a service ID with writing permissions for the {{site.data.keyword.cos_full_notm}} instance:

1. From the Dashboard, select the {{site.data.keyword.cos_full_notm}} instance where you plan to create the bucket.

2. Select **Service credentials**. Then, select **New credential**.

3. Enter a name that it is easy to recognize. For example, you can name the service ID `activity-tracker-cos-serviceID`.

4. Select the **Reader** role.

5. Click **Add**.

    A new service ID is created and added to the list.

    **Note:** The service ID that is created in the {{site.data.keyword.cloud_notm}} and listed through the IAM UI has a generic name. The name of the service ID in the IAM UI maps to the value of the field **iam_apikey_name** that you created in this step through the COS service ID UI.

6. [Optional] To lock the service ID to prevent deletion, from the menu bar, click **Manage** &gt; **Access (IAM)**. Search for the service ID. Then, select the action **Lock**.


For the service ID that you just created, click **View credentials**. You can see information that is related to the service ID.

* Copy the API key. This is the value set for the field **apikey**.

   When the service credential is rotated, make sure the [API Key is updated with the new API Key.](#archiving_step8)  Archiving will stop if the API Key is not updated.
   {: important}

* Copy the resource instance ID. This is the value set for the field **resource_instance_id**.
* Copy the value of the **iam_apikey_name** field.


## Step 5. Restrict the service ID to only have writing permissions for the bucket
{: #archiving_step5}

If you want to restrict the service ID to only have writing permissions for a bucket, complete the following steps:

1. From the COS UI, select the bucket.

2. From the bucket menu, select **Policies**. The *Bucket access policies* page opens.

3. Select **Service IDs**.

4. In the field **Select a service ID**, look for a service ID that has the following name: `auto-generated-serviceId-<ID that is part of the iam_apikey_name value>`.

5. Select the service ID. Then, in **Access policies**, select **Writer**.

6. Click **Create access policy**.



## Step 6. Select the endpoint
{: #archiving_step6}

An endpoint defines where to look for a bucket. There are different endpoints depending on the region and type of resiliency. For more information, see [Select regions and endpoints](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints).

Complete the following steps to obtain the endpoint for your bucket:

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.

	After you log in, the {{site.data.keyword.cloud_notm}} Dashboard opens.

2. From the Dashboard, select the {{site.data.keyword.cos_full_notm}} instance where you plan to create the bucket.

3. Select **Buckets**. Then, select the bucket that you created where you want to archive events.

4. Select **Configuration**.

5. Copy one of the private endpoints.



## Step 7. Grant IAM policies to a user to archive events
{: #archiving_step7}

The following table lists the policies that a user must have to configure archiving of events from the {{site.data.keyword.at_full_notm}} web UI into a bucket in an {{site.data.keyword.cos_full_notm}} instance:

| Service                              | Role                      | Permission granted                  |
|--------------------------------------|---------------------------|-------------------------------------|
| `{{site.data.keyword.at_full_notm}}` | Platform role: Viewer     | Allows the user to view the list of service instances in the Observability Logging dashboard. |
| `{{site.data.keyword.at_full_notm}}` | Service role: Manager     | Allows the user to launch the web UI and view events in the web UI.                             |
{: caption="Table 3. IAM policies" caption-side="top"}

[Learn more](/docs/services/activity-tracker?topic=activity-tracker-iam#iam).

Complete the following steps to assign a user permission to archive events:

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and then select **Users**.
2. From the row for the user that you want to assign access, select the **Actions** menu, and then click **Assign access**.
3. Select **Assign access within a resource group**.
4. Select a resource group.
5. If the user does not have a role already granted for the selected resource group, choose a role for the **Assign access to a resource group** field.

    Depending on the role that you select, the user can view the resource group on their dashboard, edit the resource group name, or manage user access to the group.

    You can select **No access**, if you want the user to only have access to the {{site.data.keyword.at_full_notm}} service in the resource group.

6. Select **{{site.data.keyword.at_full_notm}}**.
7. Select the platform role **Viewer**.
8. Select the service role **Manager**.
9. Click **Assign**.



## Step 8. Configure archiving for your {{site.data.keyword.at_full_notm}} instance
{: #archiving_step8}


Complete the following steps to configure archiving of your {{site.data.keyword.at_full_notm}} instance into a COS bucket:

1. [Launch the {{site.data.keyword.at_full_notm}} web UI](/docs/services/activity-tracker?topic=activity-tracker-launch).

2. Select the **Configuration** icon. Then select **Archiving**.

3. Select **IBM Cloud Object Storage**.

4. Set the bucket, endpoint, API key, and instance ID where you want events to be archived.

    | Field       | Value                                                |
    |-------------|------------------------------------------------------|
    | Bucket      | Set to the COS bucket name.                          |
    | Endpoint    | Set to the COS bucket private endpoint.              |
    | API Key     | Set to the API key associated to the COS service ID. |
    | Instance ID | Set to the COS instance ID.                          |
    {: caption="Table 4. COS fields" caption-side="top"}

5. Click **Save**.


Notice that when you save the configuration, you can get a message that informs you that the configuration has been saved successfully. When you get this message, the integration between the auditing instance and the bucket is verified. A test to upload and delete an object from the bucket is completed successfully.

If you get an error when you save the configuration, the verification process fails. Check your configuration and retry again.

When the service credential is rotated, make sure the API Key is updated with the new API Key.  Archiving will stop if the API Key is not updated.
{: important}
