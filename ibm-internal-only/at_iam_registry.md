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
{: #at_iam_registry}


{:shortdesc}


[Registry API](https://test.cloud.ibm.com/apidocs/container-registry)

## Auth

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| Get authorization options for the targeted account | `GET /api/v1/auth` |   |   |
| Update authorization options for the targeted account | `PATCH /api/v1/auth` |    |   |

## Builds

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| Build a container image | `POST /api/v1/builds` | `container-registry.image.build` | `container-registry.image.build` |



## Images

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| List all images in namespaces in a targeted IBM Cloud account | `GET /api/v1/images` | `container-registry.image.list` | `container-registry.image.list` |
| Remove multiple container images from the registry | `POST /api/v1/images/bulkdelete` |  | `container-registry.image.bulkdelete` |
| List all images by digest in namespaces in a targeted IBM Cloud account | `POST /api/v1/images/digests` |  |  |
| In the region that you're logged into, create a new tag in a private registry that refers to an existing image in the same region | `POST /api/v1/images/tags` |  |  |
| Remove a container image from the registry | `DELETE /api/v1/images/{image}` | `container-registry.image.delete` | `container-registry.image.delete` |
| Inspect a container image in the private registry | `GET /api/v1/images/{image}/json` | `container-registry.image.inspect` | `container-registry.image.inspect` |
| Get the manifest for a container image in the private registry | `GET /api/v1/images/{image}/manifest` |  | `container-registry.manifest.inspect` |


AT actions - no IAM actions:

container-registry.image.rm
container-registry.image.tag
container-registry.image.untag

AT Actions with matching IAM actions: 
container-registry.image.push
container-registry.image.pull

## Messages

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| Return any published system messages | `GET /api/v1/messages` |

## Namespaces

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| List authorized namespaces in the targeted IBM Cloud account | `GET /api/v1/namespaces` | `container-registry.namespace.list` | `container-registry.namespace.list` |
| Add a namespace to the targeted IBM Cloud account | `PUT /api/v1/namespaces/{namespace}` | `container-registry.namespace.create` | `container-registry.namespace.create` |
| Delete the IBM Cloud Container Registry namespace from the targeted IBM Cloud account, and removes all images that were in that namespace | `DELETE /api/v1/namespaces/{namespace}` | `container-registry.namespace.delete` | `container-registry.namespace.delete` |

## Plans

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| Get plans for the targeted account | `GET /api/v1/plans` | `container-registry.plan.get` | `container-registry.plan.get` |
| Update plans for the targeted account | `PATCH /api/v1/plans` | `container-registry.plan.set` | `container-registry.plan.set` |


## Quotas

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| Get quotas for the targeted account | `GET /api/v1/quotas` | `container-registry.quota.get` | `container-registry.quota.get` |
| Update quotas for the targeted account | `PATCH /api/v1/quotas` | `container-registry.quota.set` | `container-registry.quota.set` |


## Retentions

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| List retention policies for all namespaces in the targeted IBM Cloud account | `GET /api/v1/retentions | `container-registry.retention.list` | `container-registry.retention.list` |
| Set the retention policy for the specified namespace | `POST /api/v1/retentions` | `container-registry.retention.set` | `container-registry.retention.set` |
| Analyze a retention policy, and get a list of what would be deleted by it | `POST /api/v1/retentions/analyze` | `container-registry.retention.analyze`  | `container-registry.retention.analyze`  |
| Get the retention policy for the specified namespace | `GET /api/v1/retentions/{namespace}` | `container-registry.retention.get` |   |

## Tags

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| Untag a container image in the registry | `DELETE /api/v1/tags/{image}` |  |  |

## Tokens

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| List all valid registry access tokens for an owner| `GET /api/v1/tokens` | `container-registry.registrytoken.list` | `container-registry.registrytoken.list` |
| Issue a registry access token for the targeted IBM Cloud account | `POST /api/v1/tokens` |  |   |
| Revoke all registry access tokens that match a query | `DELETE /api/v1/tokens` | `container-registry.registrytoken.bulkdelete` | `container-registry.registrytokens.delete` |
| Retrieve the registry token with the given UUID | `GET /api/v1/tokens/{uuid}` | `container-registry.registrytoken.get` | `container-registry.registrytoken.get` |
| Revoke the specified registry access token | `DELETE /api/v1/tokens/{uuid}` | `container-registry.registrytoken.delete` | `container-registry.registrytoken.delete` |


## Trash

| Action                                    | Method | IAM ACTION   |  AT ACTION |
|-------------------------------------------|-------------------|----|-------|
| List all images that are in the trash can | `GET /api/v1/trash` |    | `container-registry.trash.list` |
| In the region that you're logged into, restore a digest and all its tags in the same repository from the trash can | `POST /api/v1/trash/{digest}/restoretags` |  |   | 
| In the region that you're logged into, restore an image from the trash can | `POST /api/v1/trash/{image}/restore` |  | `container-registry.trash.restore` |


## Vulnerability

AT actions - no IAM action:

container-registry.exemption.create
container-registry.exemption.delete

IAM action - no AT action:
container-registry.exemption.manager