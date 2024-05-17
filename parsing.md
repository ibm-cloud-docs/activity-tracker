---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-17"

keywords:

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}


# Enhancing your data by defining custom indexed fields
{: #parsing}

In {{site.data.keyword.at_full_notm}}, you can create custom fields that you can use in advanced searches and in filtering queries by using parsing rules. You define parsing templates through the UI to add custom fields to your records.
{: shortdesc}

<!-- Common deprecation statement -->
{{../log-analysis/_include-segments/deprecation_notice.md}}

## Create a parsing rule
{: #AT-create-parsing rule}
{: step}

There are occasions when you might want to reference information that is available in log records. Parsing rules maps information from a log line to a field that can be used in other configuration settings.

1. [Make sure you are logged in to the {{site.data.keyword.cloud_notm}} and have accessed the {{site.data.keyword.at_full_notm}} web UI](/docs/activity-tracker?topic=activity-tracker-launch#launch_cloud_ui).

2. Select the view with the fields you want to use.  Your view will be listed under the category where it was created, or under **UNCATEGORIZED** if you didn't specify a category when the view was created. For example, the following shows a view named "My View" that was created without an assigned category.

   ![Navigation example](/images/uncategorized_myview.png "An uncategorized view named My View in the navigation")

3. Click the selected view name.  The following example shows the view named "My View".

   ![My View view](/images/myview.png "Heading showing the My View view")

4. Click the view name.  The menu is displayed.  Click **Edit view properties**.

   ![Edit view properties](/images/editviewproperties.png "Edit view properties")

5. In the **Custom Template** you can find the fields you can use for parsing.

   * To determine the possible fields, click the down arrow on a log line in the view.

      ![Open log entry](/images/loglinedropdown.png "Open log entry twistie")

   * Click **Extract Fields** ![Extract Fields](/images/extractfields.png "Extract Fields")

      The log fields that can be used are displayed in the **Reference line** along with the specific values from the selected log entry.  For example:

      ```text
      {"logSourceCRN":"crn:v1:bluemix:public:containers-kubernetes:us-south:a/xxxxx:yyyyy::","saveServiceCopy":true,"message":"Cluster yyyyy health status set to All Workers Normal"}
      ```
      {: codeblock}

      In this case, the following fields can be used for parsing: `logSourceCRN` and `message`.

      The `saveServiceCopy` field value cannot be used because it is a boolean value.
      {: important}

6. Click the **Settings** icon ![Settings icon](/images/config.png "Settings icon").

7. Click **PARSING**.

8. Click **Create Template**. The template wizard opens.

9. For this example, for **Choose a sample log line to begin building your template** select *Find an existing log line*. Enter a search term that will match a field you extracted from you log view.

10. Scroll to the end of the page and click **Build Parsing Template**. A **Reference Line** for your log records is displayed.

11. Click the the **Pencil** icon ![Pencil icon](/images/pencil.png "Pencil icon") and enter a name for your parsing rule.

    If you name a template before you click **Build Parsing Template**, the name is not changed.
    {: note}

12. Choose the **Extract values by delimiter** extractor.

13. For **Delimiter** specify a `,` (comma). A preview of the output delimited by a comma is presented for your review.

14. Choose one of the entries.  For example, if your log contains a field called `message` you might select that line.

15.  For **Choose an Operator** select **Extract Values by Delimiter**.

16. For **Delimiter** specify a delimiter that makes sense for your selected entry. For example, a reasonable delimiter might be a `:` (colon).  A preview of the delimited output is presented for your review.

17. Select an entry containing a date value.

18. For **Choose an Operator** select **Trim Value**. Using the index range specify a starting and ending character position so only the date is retained in the displayed output.

19. For **Choose an Operator** select **Capture in Field** to set the name of the field that will capture this information.

20. For **Field Name** specify a name that you will use to reference this type of information.

21. At the end of the page click **Proceed to Validation**.

22. For **Set a query and verify parsed output with different sample lines** enter a search that will return multiple records.  For example, `message`.

23. If all log lines returned match the rule you specified, click **Mark as Valid** for each and then click **Activate** at the end of the page.

    Until you validate all results, the **Activate** option will be disabled.
    {: note}

The rule will take affect for views in approximately 15 minutes.  Dashboards and screen updates can take a bit longer.
