---

copyright:
  years: 2019, 2023
lastupdated: "2021-08-09"

keywords: IBM Cloud, Activity Tracker, cidr

subcollection: activity-tracker

---

{{site.data.keyword.attribute-definition-list}}

# Setting up Terraform for {{site.data.keyword.at_full_notm}}
{: #terraform-setup}

This information applies only to {{site.data.keyword.at_full}} event viewing.
{: important}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent provisioning of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multitier cloud environments that follow Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API and SDKs, you can automate the provisioning, update, and deletion of your {{site.data.keyword.registrylong}} instances by using HashiCorp Configuration Language (HCL).
{: shortdesc}

Looking for a managed Terraform on {{site.data.keyword.cloud_notm}} solution? Try out [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started). With {{site.data.keyword.bpshort}}, you can use the Terraform scripting language that you are familiar with, but you don't need to worry about setting up and maintaining the Terraform command line and the {{site.data.keyword.cloud_notm}} Provider plug-in. {{site.data.keyword.bpshort}} also provides pre-defined Terraform templates that you can install from the {{site.data.keyword.cloud_notm}} catalog.
{: tip}

## Installing Terraform
{: #terraform-install}

Before you begin, ensure that you have the [required access](/docs/Registry?topic=Registry-iam) to create and work with {{site.data.keyword.registrylong_notm}} resources.

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud}} Provider plug-in for Terraform, follow the [Terraform on {{site.data.keyword.cloud}} getting started tutorial](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started). The plug-in abstracts the {{site.data.keyword.cloud_notm}} APIs that are used to provision, update, or delete {{site.data.keyword.registryshort}} resources.

    1. Create a terraform folder on your local machine, and navigate to your terraform folder.

        ```text
        mkdir terraform && cd terraform
        ```
        {: pre}

    2. Download the Terraform version that you want. The IBM Cloud Provider plug-in for Terraform currently supports Terraform version 0.12.x, 0.13.x, and 0.14.x only. Make sure to select a supported Terraform version.

    3. Extract the Terraform zip file and copy the files to your terraform directory.

    4. Set the environment PATH variable to your Terraform files.

        ```text
        export PATH=$PATH:<terraform-directory>/terraform
        ```
        {: codeblock}

    5. Verify that the installation is successful by using a terraform command.

        ```text
        terraform
        ```
        {: pre}

2. Create a Terraform configuration file that is named `main.tf`. In this file, you add the configuration to create a {{site.data.keyword.registryshort}} namespace and to assign a user an access policy in Identity and Access Management (IAM) for that namespace by using HashiCorp Configuration Language (HCL). For more information, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

   The following example creates a namespace in the default resource group with a name of your choice and attaches an image retention policy to that namespace that retains 10 images. To retrieve the ID of the default resource group, the `ibm_resource_group` data source is used. Then, the user `user@ibm.com` is assigned the Manager role in the IAM access policy for the namespace for a particular region. The region is retrieved from the `terraform.tfvars` file that you created in step 1.

   ```terraform
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_cr_namespace" "cr_namespace" {
     name = "<namespace_name>"
     resource_group_id = data.ibm_resource_group.group.id
   }

   resource "ibm_cr_retention_policy" "cr_retention_policy" {
     namespace = ibm_cr_namespace.cr_namespace.id
     images_per_repo = 10
   }

   resource "ibm_iam_user_policy" "policy" {
     ibm_id = "user@ibm.com"
     roles  = ["Manager"]

     resources {
       service              = "container-registry"
       resource = ibm_cr_namespace.cr_namespace.id
       resource_type = "namespace"
       region = var.region
     }
   }
   ```
   {: codeblock}

   Updating a namespace by using Terraform is not supported. You can use Terraform to create and remove namespaces only.
   {: note}

3. Initialize the Terraform CLI.

   ```text
   terraform init
   ```
   {: pre}

4. Create a Terraform execution plan. The Terraform execution plan summarizes all the actions that need to be run to create the {{site.data.keyword.registryshort}} namespace and IAM access policy in your account.

   ```text
   terraform plan
   ```
   {: pre}

5. Create the {{site.data.keyword.registryshort}} namespace and IAM access policy in {{site.data.keyword.cloud_notm}}.

   ```text
   terraform apply
   ```
   {: pre}

6. From the [{{site.data.keyword.registryshort}} namespace overview page](https://cloud.ibm.com/registry/namespaces){: external}, verify that your namespace is created successfully.

7. Verify that the access policy is successfully assigned. For more information, see [Reviewing assigned access in the console](/docs/account?topic=account-assign-access-resources#review-your-access-console).

## What's next?
{: #registry_terraform_setup_next}

Now that you successfully created your first {{site.data.keyword.registryshort}} namespace with Terraform on {{site.data.keyword.cloud_notm}}, you can choose between the following tasks:

- Learn how to [add images to your namespace](/docs/Registry?topic=Registry-registry_images_).
- Explore other supported arguments and attributes for the [{{site.data.keyword.registryshort}} Terraform resources and data sources](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cr_namespace){: external} that were used in this example.






Error: No deployment found for service plan 30-day at location toronto.
Valid location(s) are: ["ca-tor" "eu-de" "eu-gb" "in-che" "us-south" "au-syd" "jp-osa" "jp-tok" "kr-seo" "us-east"].
Use 'ibm_service_instance' if the service is a Cloud Foundry service.


```text
Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

ibm_resource_instance.at_instance: Creating...
ibm_resource_instance.at_instance: Still creating... [10s elapsed]
ibm_resource_instance.at_instance: Still creating... [20s elapsed]
ibm_resource_instance.at_instance: Creation complete after 20s [id=crn:v1:bluemix:public:logdnaat:ca-tor:a/81de6380e6232019c6567c9c8de6dece:279d5d5d-fe0d-4806-8f98-1510d2ad8fe1::]
ibm_resource_key.resourceKey: Creating...
ibm_resource_key.resourceKey: Creation complete after 4s [id=crn:v1:bluemix:public:logdnaat:ca-tor:a/81de6380e6232019c6567c9c8de6dece:279d5d5d-fe0d-4806-8f98-1510d2ad8fe1:resource-key:938ee790-ff3c-4f4d-ade6-a709747d984d]

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
MacBook-Pro:myproject luisalopezdesicanes$
````
