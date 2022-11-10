---

copyright:
  years: 2019, 2022
lastupdated: "2022-11-10"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Managing access with IAM
{: #iam}

{{site.data.keyword.iamlong}} (IAM) enables you to securely authenticate users and control access to all cloud resources consistently in the {{site.data.keyword.cloud_notm}}. Access to {{site.data.keyword.at_full_notm}} service instances for users in your account is controlled by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).
{: shortdesc}

The access policy that you assign users in your account determines what actions a user can perform within the context of the service or specific instance that you select. The allowable actions are customized and defined by {{site.data.keyword.at_short}} as operations that are allowed to be performed on the service. An action is mapped to an IAM platform or service role that you can assign to a user.

For more information about the steps to assign IAM access, see [Managing access to resources](/docs/account?topic=account-assign-access-resources).
- When you assign policies to users, use `atracker` for the service name in the CLI command or API call for {{site.data.keyword.atracker_short}}. Use `logdnaat` for {{site.data.keyword.at_short}} hosted event search offerings.
- When you assign policies to users, use `Activity Tracking` for {{site.data.keyword.atracker_short}}. When you assign policies to users, use `IBM Cloud {{site.data.keyword.atracker_short}}` for the service name in the UI for {{site.data.keyword.at_short}} hosted event search offerings.

**To organize a set of users and service IDs into a single entity that makes it easy for you to manage IAM permissions, use *access groups*.** You can assign a single policy to the group instead of assigning the same access multiple times per individual user or service ID.
{: tip}


## Managing access by using access groups
{: #groups}

To manage access or assign new access for users by using access groups, you must be the account owner, administrator, or editor on all Identity and Access enabled services in the account, or the assigned administrator or editor for the IAM Access Groups Service.

Choose any of the following actions to manage access groups in the {{site.data.keyword.cloud_notm}}:

* [Creating an access group](/docs/account?topic=account-groups#create_ag).
* [Assigning access to a group](/docs/account?topic=account-groups#access_ag).


## Managing access by assigning policies directly to users
{: #users}

To manage access or assign new access for users by using IAM policies, you must be the account owner, administrator on all services in the account, or an administrator for the particular service or service instance.

Choose any of the following actions to manage IAM policies in the {{site.data.keyword.cloud_notm}}:

* To grant permissions to a user, see [Assigning access](/docs/account?topic=account-assign-access-resources#assign_new_access).
* To revoke permissions, see [Removing access](/docs/account?topic=account-assign-access-resources#removing_access).
* To review a user's permissions, see [Reviewing your assigned access](/docs/account?topic=account-assign-access-resources#review_your_access).

## Managing access through trusted profiles
{: #iam-profiles}

[Trusted profiles](/docs/account?topic=account-identity-overview#trustedprofiles-bestpract) are supported.

## {{site.data.keyword.cloud_notm}} platform roles
{: #platform}

The following tables detail actions that are mapped to platform roles.

Platform roles enable users to perform tasks on service resources at the platform level, for example, assign user access for the service, create or delete instances, and bind instances to applications.

Review the following tables that outline what types of tasks each role allows for when you're configuring {{site.data.keyword.atracker_short}} in your account.

### {{site.data.keyword.atracker_short}}
{: #iam_ater}

Use the following table to identify the **Account management** **{{site.data.keyword.atracker_short}}** platform role that you can grant a user in the {{site.data.keyword.cloud_notm}} to run any of the following platform actions:

| Platform role            | Description of actions |
|--------------------------|------------------------|
| Viewer                   | As a viewer, you can view {{site.data.keyword.atracker_short}} configuration resources such as routes and targets. |
| Operator                 | As an operator, you can view {{site.data.keyword.atracker_short}} configuration resources such as routes and targets. |
| Editor                   | As an editor, you can view, create, update, and delete {{site.data.keyword.atracker_short}} resources. |
| Administrator            | As an administrator, you can view, create, update, and delete {{site.data.keyword.atracker_short}} resources. You can also assign access policies to manage {{site.data.keyword.atracker_short}} resources to other users in the account. |
{: caption="Table 1. IAM platform roles for {{site.data.keyword.atracker_short}}" caption-side="top"}
{: summary="Descriptions of the actions in the service that are permitted for the listed platform management role."}

Review the available platform roles that are available, and the actions that are mapped to each to help you assign access.

For {{site.data.keyword.atracker_short}} the IAM actions and Activity Tracker actions are the same.
{: note}

| Action | IAM and Activity Tracker action | Administrator | Editor | Operator | Viewer |
|--------|------------|---------------|--------|-----------|--------|
| Grant other account members access to configure {{site.data.keyword.atracker_short}} | `iam-am.policy.create` |![Checkmark icon](images/checkmark-icon.svg) | | | |
| Revoke member access to configure {{site.data.keyword.atracker_short}} | `iam-am.policy.delete` | ![Checkmark icon](images/checkmark-icon.svg) | | | |
| Modify member access to configure {{site.data.keyword.atracker_short}}  | `iam-am.policy.update` | ![Checkmark icon](images/checkmark-icon.svg) | | | |
{: caption="Table 2. IAM platform roles for {{site.data.keyword.atracker_short}}" caption-side="top"}


| Action | IAM and Activity Tracker action | Administrator | Editor | Operator | Viewer |
|--------|------------|---------------|--------|-----------|--------|
| View a target      | `atracker.target.read` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |
| Create a target    | `atracker.target.create` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | | |
| Update a target    | `atracker.target.update` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | | |
| Delete a target    | `atracker.target.delete` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | | |
| List all targets   | `atracker.target.list` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 3. IAM platform roles for {{site.data.keyword.atracker_short}}" caption-side="top"}

| Action | IAM and Activity Tracker | Administrator | Editor | Operator | Viewer |
|--------|------------|---------------|--------|-----------|--------|
| View a route | `atracker.route.read` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |
| Create a route | `atracker.route.create` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | | |
| Update a route | `atracker.route.update` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | | |
| Delete a route | `atracker.route.delete` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) | | |
| List all routes | `atracker.route.list` |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 4. IAM platform roles for {{site.data.keyword.atracker_short}}" caption-side="top"}


| Action | IAM and Activity Tracker action | Administrator | Editor | Operator | Viewer |
|--------|------------|---------------|--------|-----------|--------|
| Set endpoint properties `[V1]` | `atracker.endpoint.set` | ![Checkmark icon](images/checkmark-icon.svg) | | |  |
| View endpoint properties `[V1]` | `atracker.endpoint.get` | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 5. IAM platform roles for {{site.data.keyword.atracker_short}}" caption-side="top"}


| Action | IAM and Activity Tracker action | Administrator | Editor | Operator | Viewer |
|--------|------------|---------------|--------|-----------|--------|
| View configuration settings `[V2]` | `atracker.setting.get` | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
| Update configuration settings `[V2]` | `atracker.setting.update` | ![Checkmark icon](images/checkmark-icon.svg) | | | |
{: caption="Table 6. IAM platform roles for {{site.data.keyword.atracker_short}}" caption-side="top"}

| Action | IAM and Activity Tracker action | Administrator | Editor | Operator | Viewer |
|--------|------------|---------------|--------|-----------|--------|
| Start migration `[V2]` | `atracker.migration.post` | ![Checkmark icon](images/checkmark-icon.svg) | | | |
| View migration status `[V2]` | `atracker.migration.get` | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) | ![Checkmark icon](images/checkmark-icon.svg) |
{: caption="Table 7. IAM platform roles for {{site.data.keyword.atracker_short}}" caption-side="top"}

`[V2]` is only applicable once you have [migrated to the V2 configuration.](/docs/activity-tracker?topic=activity-tracker-migration)  `[V1]` is only applicable to the V1 configuration and is unavailable after you migrate to the V2 configuration. All others are applicable to both configurations.
{: note}

### {{site.data.keyword.atracker_short}} actions by role
{: #iam_ater_byrole}

The following tables show the {{site.data.keyword.atracker_short}} actions by role.

| Platform role | Activity Tracker action | Action |
|---------------|-------------------------|-------------|
| Operator | `atracker.target.read` | View a target |
| Operator | `atracker.target.list` | List all targets |
| Operator | `atracker.route.read` | View a route |
| Operator | `atracker.route.list` | List all routes |
| Operator | `atracker.endpoint.get` | View endpoint properties `[V1]` |
| Operator | `atracker.setting.get` | View configuration settings `[V2]` |
| Operator | `atracker.migration.get` | View migration status `[V2]` |
{: caption="Table 8. {{site.data.keyword.atracker_short}} actions for the operator role" caption-side="top"}

| Platform role | Activity Tracker action | Action |
|---------------|-------------------------|-------------|
| Viewer | `atracker.target.read` | View a target |
| Viewer | `atracker.target.list` | List all targets |
| Viewer | `atracker.route.read` | View a route |
| Viewer | `atracker.route.list` | List all routes |
| Viewer | `atracker.endpoint.get` | View endpoint properties `[V1]` |
| Viewer | `atracker.setting.get` | View configuration settings `[V2]` |
| Viewer | `atracker.migration.get` | View migration status `[V2]` |
{: caption="Table 9. {{site.data.keyword.atracker_short}} actions for the viewer role" caption-side="top"}

| Platform role | Activity Tracker action | Action |
|---------------|-------------------------|-------------|
| Editor | `atracker.target.read` | View a target |
| Editor | `atracker.target.create` | Create a target |
| Editor | `atracker.target.update` | Update a target |
| Editor | `atracker.target.delete` | Delete a target |
| Editor | `atracker.target.list` | List all targets |
| Editor | `atracker.route.read` | View a route |
| Editor | `atracker.route.create` | Create a route |
| Editor | `atracker.route.update` | Update a route |
| Editor | `atracker.route.delete` | Delete a route |
| Editor | `atracker.route.list` | List all routes |
| Editor | `atracker.endpoint.get` | View endpoint properties `[V1]` |
| Editor | `atracker.setting.get` | View configuration settings `[V2]` |
| Editor | `atracker.migration.get` | View migration status `[V2]` |
{: caption="Table 10. {{site.data.keyword.atracker_short}} actions for the editor role" caption-side="top"}

| Platform role | Activity Tracker action | Action |
|---------------|-------------------------|-------------|
| Administrator | `atracker.target.read` | View a target |
| Administrator | `atracker.target.create` | Create a target |
| Administrator | `atracker.target.update` | Update a target |
| Administrator | `atracker.target.delete` | Delete a target |
| Administrator | `atracker.target.list` | List all targets |
| Administrator | `atracker.route.read` | View a route |
| Administrator | `atracker.route.create` | Create a route |
| Administrator | `atracker.route.update` | Update a route |
| Administrator | `atracker.route.delete` | Delete a route |
| Administrator | `atracker.route.list` | List all routes |
| Administrator | `atracker.endpoint.set` | Set endpoint properties `[V1]` |
| Administrator | `atracker.endpoint.get` | View endpoint properties `[V1]` |
| Administrator | `atracker.setting.get` | View configuration settings `[V2]` |
| Administrator | `atracker.setting.update` | Update configuration settings `[V2]` |
| Administrator | `atracker.migration.post` | Start migration `[V2]` |
| Administrator | `atracker.migration.get` | View migration status `[V2]` |
{: caption="Table 11. {{site.data.keyword.atracker_short}} actions for the administrator role" caption-side="top"}

`[V2]` is only applicable once you have [migrated to the V2 configuration.](/docs/activity-tracker?topic=activity-tracker-migration)  `[V1]` is only applicable to the V1 configuration and is unavailable after you migrate to the V2 configuration. All others are applicable to both configurations.
{: note}

### {{site.data.keyword.atracker_short}} hosted event search
{: #iam_athes}

Use the following table to identify the platform role for the {{site.data.keyword.at_short}} hosted event search offerings that you can grant a user in the {{site.data.keyword.cloud_notm}} to run any of the following platform actions:

| Platform actions                                                          | Administrator                                     | Editor | Operator | Viewer  |
|---------------------------------------------------------------------------|:-------------------------------------------------:|:-------:|:--------:|:------:|
| `Grant other account members access to work with the service`             | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |         |          |        |
| `View the ingestion key in the {{site.data.keyword.cloud_notm}} console`  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |         |          |        |
| `Provision a service instance`                                            | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |      |      |
| `Delete a service instance`                                               | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |        |      |
| `Update a service instance`                                               | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |        |      |
| `Create a service ID`                                                     | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |        |      |
| `View details of a service instance`                                      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |
| `View service instances in the Observability Activity Tracker dashboard`  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |
{: caption="Table 12. IAM user platform roles and actions for {{site.data.keyword.at_short}} hosted event search offerings" caption-side="top"}


## {{site.data.keyword.cloud_notm}} service roles
{: #service}

Use the following table to identify the service roles that you can grant a user to run any of the following service actions when you use {{site.data.keyword.at_short}} hosted event search offerings:

| Actions   | Manager  | Standard-Member  | Reader |
|-----------|----------|------------------|------|
| `Create and delete ingestion keys` | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |  | |
| `Create and delete service keys` | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |  | |
| `Configure account settings` | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |  |  |
| `Manage groups`   | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |  |  |
| `Configure archiving`   | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | |  |
| `Define exclusion rules` | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |    |        |
| `Create and delete categories`    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |  |        |
| `Manage how views and dashboards are grouped in categories`    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") |   |   |
| `Export data`  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | |
| `View ingestion keys`  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | | |
| `View service keys`  | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | | |
| `Configure alerts`                                                      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | |
| `View usage`                                                            | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | |
| `Create views`                                                          | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | |
| `Create dashboards`                                                     | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | |
| `Create screens`                                                        | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | |
| `Configure user preferences in the UI`                       | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage") | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")                    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |
| `Filter and search data`                                                | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")                    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |
| `Use views to monitor events`                                           | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")                    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |
| `Use dashboards to monitor events`                                      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")                    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |
| `Use screens to monitor events`                                         | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")      | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")                    | ![Check mark icon](images/checkmark-icon.svg "Check mark icon indicating correct usage")    |
{: caption="Table 13. IAM service roles and actions for {{site.data.keyword.at_short}} hosted event search offerings" caption-side="top"}


The **manager** service role maps directly to the service admin role.
{: note}



## How do I know which access policies are set for me?
{: #iam_accesspolicy}

You can see which access policies are set for you in the [{{site.data.keyword.cloud_notm}} UI](https://cloud.ibm.com/){: external} console.

1. Go to [Access IAM users](https://cloud.ibm.com/iam/users){: external}.
2. Click your name in the user table.
3. Click the **Access policies** tab to see your access policies.
4. Click the **Access groups** tab to see the access groups where you are a member. Check the policies for each group.
