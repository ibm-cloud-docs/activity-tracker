---

copyright:
  years:  2021
lastupdated: "2021-01-27"

keywords: LogDNA, logging, groups, access

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
{:external: target="_blank" .external}

# Using groups to control LogDNA data access
{: #group_data_access}

You can configure, control, and manage the LogDNA data that is available to users in your {{site.data.keyword.cloud}} account by configuring **groups** in the LogDNA instance. 
{:shortdesc}

A user granted permission to view and manage LogDNA instance data is a **user** in a **group**.  A **group** is comprised of **users** with authorization to specific data.

Configuration of groups is only available in the *Paris* data centers.
{: important}

## Before you begin
{: #groups_data_access_before_beginning}

Before configuring and using groups you need to understand the following requirements and limitations.

Users require specific {{site.data.keyword.iamlong}} permissions to work with groups and group members.

Role                                                               | Permissions
-------------------------------------------------------------------|------------------------------------------------
Administrator platform role                                        | Required to define group members and their roles
Manager service role                                               | Required to manage LogDNA instance groups
Platform role viewer, service role reader, or standard member      | Required to launch the LogDNA instance
{: caption="Table 1. Roles required for groups" caption-side="top"} 

User roles defining permissions and access to manage LogDNA instance data are defined in {{site.data.keyword.iamlong}}.  However, there is no mapping of {{site.data.keyword.iamshort}} access groups to LogDNA groups. Each must be managed separately.  To ease management of the groups consider defining similar access groups in LogDNA as you have defined in {{site.data.keyword.iamshort}}.

Users are assigned to a group by their email address.  If a user changes their email address, you must remove the old email address from the LogDNA group and add the new one.  

All users must have logged in to the LogDNA instance at least once before the user can be assigned to a LogDNA group.  If a user changes their email address, the new email must be logged in to the LogDNA instance before it can be added to the LogDNA group.

Users defined in the LogDNA group can see all resources defined in the LogDNA instance.  For example: views, boards, and screens.  Using the data access feature a user can open multiple LogDNA instances in different browser tabs.

## Configuring default LogDNA instance settings
{: #groups_data_access_settings}

1. Log in to your {{site.data.keyword.cloud_notm}} account.

   Click [Log in to {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login){: external} to sign in to the {{site.data.keyword.cloud_notm}}.

   After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} console opens.

2. Select your account.

3. Click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg) &gt; **Observability**. 

4. Select **Logging**.

5. For your instance, click **View LogDNA**. The LogDNA web UI will be displayed.

6. Click **Settings** &gt; **Organization** &gt; **Team** &gt; **Settings**.

7. Set the **Access Control** to your desired default setting:

   * **ON** allows all users to see the LogDNA instance data even if they are not part of a group.
   * **OFF** requires users to be a member of a group associated with the LogDNA instance to see data.

   Setting **Access Control** to **OFF** prevents users who are not defined to a group for seeing the LogDNA instance data.
   {: tip}

## Defining LogDNA groups
{: #groups_data_access_groups}

In LogDNA you can define 1 or more groups, also known as teams, defining the set of data the users in that group can view and analyze.  In LogDNA you are configuring the scope of data visible to users in the group.  However, user permissions to access LogDNA and LogDNA features are defined in {{site.data.keyword.iamlong}}.

You will configure the access scope defining the dataset available to the users in a group.  You will then configure a group of users authorized to that access scope.

1. Log in to your {{site.data.keyword.cloud_notm}} account.

   Click [Log in to {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login){: external} to sign in to the {{site.data.keyword.cloud_notm}}.

   After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} console opens.

2. Select your account.

3. Click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg) &gt; **Observability**. 

4. Select **Logging**.

5. For your instance, click **View LogDNA**. The LogDNA web UI will be displayed.

6. Click **Settings** &gt; **Organization** &gt; **Team** &gt; **Groups**.

7. Click **Add Group**.

8. Enter a name for your group.

   Consider a naming convention similar to your {{site.data.keyword.iamshort}} for ease of management.
   {: tip}
