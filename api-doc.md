---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:generic: .ph data-hd-programlang='generic'}
{:java: .ph data-hd-programlang='java'}
{:ruby: .ph data-hd-programlang='ruby'}
{:c#: .ph data-hd-programlang='c#'}
{:objectc: .ph data-hd-programlang='Objective C'}
{:python: .ph data-hd-programlang='python'}
{:node: .ph data-hd-programlang='node'}
{:php: .ph data-hd-programlang='PHP'}
{:swift: .ph data-hd-programlang='swift'}
{:curl: .ph data-hd-programlang='curl'}
{:node: .ph data-hd-programlang='node'}
{:middle: .ph data-hd-position='middle'}
{:right: .ph data-hd-position='right'}

# Creating front matter for your IBM Cloud API Docs

This template is designed to help you extend your Swagger 2.0 or OpenAPI 3.0 API documentation. Every offering onboarding into IBM Cloud must deliver API documentation, and this requirement includes adding some additional front matter to your API docs that use our extensions. The required sections are few, and you can author them in Markdown. We have a parser that transforms your .md file into an assembled JSON output and merges the output with your Swagger or OpenAPI JSON file.

## Markdown rules

The API IBM Docs app is rendered as a 3-pane GUI, and is broken into three parts:

| Left | Middle | Right |
|-----|--------|-------|
| Navigation uses H1 pre-defined titles. You never need to use attributes to define left content - only H1 titles are used. | All content is defined as `{: middle}` by default. Any element or header that does not otherwise specify a position is rendered in the middle pane. H1 headings display in the left pane as the navigation entry and as the title in the middle pane. H3 headings display under the H1 title in the left pane and within the H1 section in the middle pane. **Note**: H2 titles are *never* rendered. | The right pane is designed to show code examples.<br>&nbsp;- To render code examples in the right pane, use H2s with the `{: right}` attribute. Include the language (`{: java}`) attribute to make it language specific.<br>&nbsp;- To line up the middle and right pane, nest code examples as H2s inside the H1 middle-pane content you want to align with. |

**Tip**: Although the language tabs (for example, Curl, Node, Java, Python, Ruby) are displayed in the right-pane, switching these languages can change the display in both the middle and right panes.

---

H1:

* Titles are rendered as entries in both the left navigation and the title in the middle pane.
* H1 can include `inline code`, images, tables, links, bullets, numbered lists, and any markdown element.
* H1 is non-language specific unless otherwise modified by binding an attribute to it (which we don't recommend for most users)
* H1 retains its language value until a new H1 is introduced. When an element within the H1 (including h2, h3, etc.) is bound with a language-attribute (for example, `{: java}`), only that element becomes language-specific. The next subsequent element reverts to generic.
* H1 usually do not include H3s because H2s nested inside H1s are used to create relationships between the middle and right pane. You don't need to break that relationship by introducing an H3.
* H1 can include any conrefs from the same master yaml conref file as used with docs. For example, `{{site.data.keyword.visualrecognitionshort}}`.

---

H2:

* H2 titles are **never** rendered. The H2 is used in these extensions explicitly as a container for language or for position-specific rendering. Many examples are included to demonstrate middle-pane and right-pane H2s with language attributes and custom content that displays in middle and right panes.
* H2 can include all valid markdown.
* H2 can include H3s.
* H2 retains its language value (just like H1) until a new heading is introduced. Any time an element within the H2 (including h3s) is bound with a language-attribute like `{: java}`, only that element becomes language-specific. The next subsequent element reverts to generic.
* H2 can include conrefs.

We include some H2 examples that are associated with the `# Introduction` and `# Data collection` H1 sections. The /apidocs GUI is separated into three panes (Left nav/middle/right). To provide custom code examples in different programming languages (for example, Curl, Node, Java, and Python), add language-specific attributes to H2s within the H1 (TOC and middle) content.

Different ways to structure your H2s:

* Provide one H2 for each corresponding language and apply the language and position tags only to the H2.
    * Everything that is nested within the H2 appears under that language tab on the right pane. See the samples below associated with `# Introduction`.
    * This method supports nesting multiple content types (bullets, codeblocks, h3s, paragraphs, and so on) under the example.
* Create an H2 that is generic. Nest your codeblocks within that h2 and bind language and position attributes to each of the included examples. This technique can be useful when you have several codeblocks for each language. See the example below for `# Data collection`.
* Exclude content and examples for a language. For example, see the `# Additional headers` section below. This section illustrates how to exclude the content from Curl but render middle and right pane content for Node, Java, and Python.
      * Alternatively, deliver an entire section only for a single language. Bind an H1 with a language attribute to display the content only when that language tab is selected.

**Note**: You can also use H2s to add custom content to the middle-pane! See the `# Error handling` section.

---

H3:

* H3 sections are rendered in both the left navigation and the middle pane. The H3 is used to organize complex H1 sections.
* H3s can also include H2s to specify position.
* To make an H3 heading and its content language-specific, you have to add language attributes to both the heading and to the content blocks (for example, to each paragraph). Without the language attribute, the H3 heading or content renders in all languages.

---

H4:
* H4 sections are rendered only in the middle pane. Use H4s to further organize H3 content.


---

Code examples:

Place code examples within backticks (```) and bind the language class attribute to the codeblock. Two types of language mapping to codeblocks are used:

* Define the syntax highlighting for the language on the same line as the first backticks (```java). See http://highlightjs.readthedocs.io/en/latest/css-classes-reference.html#language-names-and-aliases for the complete list of supported languages.
* Bind the codeblock to a language tab with an attribute after the codeblock. This binding defines which language tab renders the codeblock (`{: java}`).

**Important:** These two values sometimes do not match. For example, with **Node**, use `javascript` for the highlighting and `{: node}` for the binding. See the code examples in the `# Data collection` section for more details.

## Section order

This is the required order all sections.

* **Introduction**, **Error handling**, **Authentication** are required.
* Include other sections that apply to your API.
* For your own custom sections, please ask on `#api-enablement` Slack channel about how to open a request for a new section.

1. Introduction **REQUIRED**
2. Error handling **REQUIRED**
3. Authentication **REQUIRED**
4. Versioning
5. Additional headers
6. Data labels
7. Data collection
8. Pagination
9. Sorting
10. Filtering
11. Searching
12. Rate limiting
13. Related APIs
14. Deprecated APIs

---

# Introduction

**Required**
**Purpose**: This section is all about giving your customers an overall intro to the API you are documenting. You can provide as much information as you like, and provide language specific code examples that would apply to the API as a whole. Try and be as descriptive as possible - what is the service for? Why do they care? Feel free to link off to your docs or other resources.

**Example**:

The {{site.data.keyword.visualrecognitionshort}} service uses deep learning algorithms to identify scenes, objects, and faces in images you upload to the service. You can create and train a custom classifier to identify subjects that suit your needs.

For details about using {{site.data.keyword.visualrecognitionshort}}, see the {{site.data.keyword.cloud_notm}} [docs](https://cloud.ibm.com/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial).

## Curl example (This H2 title will not be displayed)
{: curl}
{: right}

Use the correct language attribute for each H2 language example that is associated with each H1 section, (for example, `{: curl}`). Follow the attribute by a line break and the `{: right}` attribute to ensure this content displays in the right-hand pane.

### API endpoint (This H3 is displayed as the heading under the **Curl** tab associated with the Introduction section)

Add code inside code-blocks. Add text, bullets, links, and even tips like the example below:

```
https://gateway.watsonplatform.net/visual-recognition/api

```

If you have {{site.data.keyword.Bluemix_dedicated_notm}}, this might not be your endpoint. Check your `endpoint URL` on the Service credentials page for your instance of the {{site.data.keyword.visualrecognitionshort}} service.
{: tip}

## Node example
{: node}
{: right}

The code examples on this tab use the client library that is provided for Node.js.

### Installation

`npm install --save watson-developer-cloud`

### GitHub

`https://github.com/watson-developer-cloud/node-sdk`

## Java example
{: java}
{: right}

The code examples on this tab use the client library that is provided for Java.

### Maven

```xml
<dependency>
  <groupId>com.ibm.watson.developer_cloud</groupId>
  <artifactId>java-sdk</artifactId>
  <version>6.1.0</version>
</dependency>
```

### Gradle

`compile 'com.ibm.watson.developer_cloud:java-sdk:6.1.0'`

### GitHub

`https://github.com/watson-developer-cloud/java-sdk`

## Python example
{: python}
{: right}

The code examples on this tab use the client library that is provided for Python.

Installation

`pip install --upgrade "watson-developer-cloud>=1.4.0"`

### GitHub

`https://github.com/watson-developer-cloud/python-sdk`

# Error handling

**Required**
**Purpose**: Defines common response codes and the language-specific response models. For more information, see [API Handbook - Errors](https://pages.github.ibm.com/CloudEngineering/api_handbook/design/errors.html).
**Example**:

This API uses standard HTTP response codes to indicate whether a method completed successfully. A `200` response indicates success. A `400` type response indicates a failure, and a `500` type response indicates an internal system error.

| HTTP Error Code | Description           | Recovery                                                                    |
|-----------------|-----------------------|-----------------------------------------------------------------------------|
| `200`           | Success               | The request was successful.                                                 |
| `400`           | Bad Request           | The input parameters in the request body are either incomplete or in the wrong format. Be sure to include all required parameters in your request. |
| `401`           | Unauthorized          | You are not authorized to make this request. Log in to {{site.data.keyword.Bluemix_notm}} and try again. If this error persists, contact the account owner to check your permissions. |
| `403`           | Forbidden             | The supplied authentication is not authorized to access '{namespace}'.      |
| `404`           | Not Found             | The requested resource could not be found.                                  |
| `408`           | Request Timeout       | The connection to the server timed out. Wait a few minutes, then try again. |
| `409`           | Conflict              | The entity is already in the requested state.                               |
| `500`           | Internal Server Error | *offering_name* is currently unavailable. Your request could not be processed. Wait a few minutes and try again. |

## Curl middle-pane examples
{: curl}

**ErrorResponse**

| Name                    | Description                                            |
|-------------------------|--------------------------------------------------------|
| code <br><br> `integer` | HTTP error code.                                       |
| error <br><br> `string` |	Human-readable error string, like 'Invalid image file'.|

**ErrorAuthentication**

| Name                          | Description                    |
|-------------------------------|--------------------------------|
| status <br><br> `string`      | The status of error.           |
| statusInfo  <br><br> `string` |	Information about the error. |

**ErrorHTML**

| Name                          | Description                    |
|-------------------------------|--------------------------------|
| Error <br><br> `string`       | HTML description of the error. |
| statusInfo  <br><br> `string` |	Information about the error. |

**ErrorInfo**

Information about what might have caused a failure, such as an image that is too large. Not returned when there is no error.

| Name                           | Description                                                                 |
|--------------------------------|-----------------------------------------------------------------------------|
| code <br><br> `integer`        | HTTP status code.                                                           |
| description  <br><br> `string` |	Human-readable error description. For example, `File size limit exceeded`. |
| error_id  <br><br> `string`    |	Codified error string. For example, `limit_exceeded`.                      |


## Node middle-pane error tables
{: node}

When the Node SDK receives an error response from the {{site.data.keyword.visualrecognitionshort}}  service, it creates an Error object with information describing the error that occurred. This error object is passed as the first parameter to the callback function for the method. The contents of the error object are as shown in the following table:

**Errors**

| Error Field |	Description                    |
|-------------|--------------------------------|
| code        | The HTTP status code returned  |
| message     |	A message describing the error |

## Node right-pane code examples
{: node}
{: right}

```javascript
visualRecognition.method(params,
    function(err, response) {
        // The error will be the first argument of the callback
        if (err.code == 404) {
            // Handle Not Found (404) error
        } else if (err.code == 413) {
            // Handle Request Too Large (413) error
        } else {
            console.log('Unexpected error: ', err.code);
            console.log('error:', err);
        }
    });
```

## Java middle-pane error tables
{: java}

The Java SDK generates an exception for any unsuccessful method invocation. All methods that accept an argument can also throw an `IllegalArgumentException`.

| Exception                 | Description                                   |
|---------------------------|-----------------------------------------------|
| IllegalArgumentException  | An invalid argument was passed to the method. |

When the Java SDK receives an error response from the {{site.data.keyword.visualrecognitionshort}} service, it generates an exception from the `com.ibm.watson.developer_cloud.service.exception` package. All service exceptions contain the following fields:

| Field      | Description                    |
|------------|--------------------------------|
| statusCode |The HTTP status code returned   |
| message    | A message describing the error |

## Java right-pane code examples
{: java}
{: right}

Example error handling

```java
try {
    // Invoke a Visual Recognition method
} catch (NotFoundException e) {
    // Handle Not Found (404) exception
} catch (RequestTooLargeException e) {
    // Handle Request Too Large (413) exception
} catch (ServiceResponseException e) {
    // Base class for all exceptions caused by error responses from the service
    System.out.println("Service returned status code " + e.getStatusCode() + ": " + e.getMessage());
}
```

## Python middle-pane errors
{: python}

The Python SDK generates an exception for any unsuccessful method invocation. When the Python SDK receives an error response from the {{site.data.keyword.visualrecognitionshort}} service, it generates a WatsonApiException containing the following fields:

| Field   | Description                                           |
|---------|-------------------------------------------------------|
| code    |The HTTP status code returned                          |
| message | A message describing the error                        |
| info    |A dictionary of additional information about the error |

## Python right-pane code examples
{: python}
{: right}

Example error handling

```python
from watson_developer_cloud import WatsonApiException
try:
    # Invoke a Visual Recognition method
except WatsonApiException as ex:
    print "Method failed with status code " + str(ex.code) + ": " + ex.message
```

# Authentication

This API is protected with HTTP Basic authentication. The Basic authentication credentials are in the `AUTH` property in your `~/.wskprops` file, delimited by a colon. You can also retrieve these credentials by using the CLI running `ibmcloud fn property get --auth`.

In the following cURL example, authentication is passed by using the `-u` flag:
`curl -u USERNAME:PASSWORD https://openwhisk.console.test.cloud.ibm.com/api/v1/namespaces`.

You can also include authentication part of the URL:
`curl https://USERNAME:PASSWORD@openwhisk.console.test.cloud.ibm.com/api/v1/namespaces`.

For the {namespace} in the URL, the underscore character (`_`) can be used to specify the user's default namespace.

# Versioning

**Optional**
**Purpose**: If your API supports versions, provide details. For more information, see [API Handbook - Versioning overview](https://pages.github.ibm.com/CloudEngineering/api_handbook/versioning/overview.html).

This example explains the minor version parameter that {{site.data.keyword.watson}} services support.

**Example**:

API requests require a version parameter that takes a date in the format `version=YYYY-MM-DD`. When we change the API in a [backwards-incompatible](https://github.com/watson-developer-cloud/api-guidelines/#versioning) way, we release a new version date.

Send the version parameter with every API request. The service uses the API version for the date you specify, or the most recent version before that date. Don't default to the current date. Instead, specify a date that matches a version that is compatible with your app, and don't change it until your app is ready for a later version.
{: curl}

Specify the version to use on API requests with the version parameter when you create the service instance. The service uses the API version for the date you specify, or the most recent version before that date. Don't default to the current date. Instead, specify a date that matches a version that is compatible with your app, and don't change it until your app is ready for a later version.
{: java}

Specify the version to use on API requests with the version parameter when you create the service instance. The service uses the API version for the date you specify, or the most recent version before that date. Don't default to the current date. Instead, specify a date that matches a version that is compatible with your app, and don't change it until your app is ready for a later version.
{: node}

Specify the version to use on API requests with the version parameter when you create the service instance. The service uses the API version for the date you specify, or the most recent version before that date. Don't default to the current date. Instead, specify a date that matches a version that is compatible with your app, and don't change it until your app is ready for a later version.
{: python}

This documentation describes the current version of {{site.data.keyword.visualrecognitionshort}}, `2018-03-19`. In some cases, differences in earlier versions are noted in the descriptions of parameters and response models.
{: tip}

# Additional headers

**Optional**
**Purpose**: If your API accepts extra request header parameters, define the important or common uses. For more information, see [API Handbook - Headers](https://pages.github.ibm.com/CloudEngineering/api_handbook/fundamentals/headers.html).

In the example below, `curl` is excluded from the middle and right text and code examples because the content does not apply to Curl. You can set up your language-specific middle and right sections however you like.
**Example**:

## Node middle-pane text
{: node}

Some {{site.data.keyword.watson}} services accept special parameters in headers that are passed with the request. You can pass request header parameters in all requests or in a single request to the service.

To pass header parameters with every request, specify the `set_default_headers` method of the service object. See Data collection for an example use of this method.

To pass header parameters in a single request, include `headers` as a `dict` in the request.

## Java middle-pane text
{: java}

Some {{site.data.keyword.watson}} services accept special parameters in headers that are passed with the request. You can pass request header parameters in all requests or in a single request to the service.

To pass header parameters with every request, use the `setDefaultHeaders` method of the service object. See Data collection for an example use of this method.

To pass header parameters in a single request, use the `addHeader` method as a modifier on the request before you execute the request.

## Python middle-pane text
{: python}

Some {{site.data.keyword.watson}} services accept special parameters in headers that are passed with the request. You can pass request header parameters in all requests or in a single request to the service.

To pass header parameters with every request, specify the `set_default_headers` method of the service object. See Data collection for an example use of this method.

To pass header parameters in a single request, include `headers` as a `dict` in the request.

## Node right-pane code examples
{: node}
{: right}

Example header parameter in a request

```javascript
visualRecognition.methodName(
    {
        parameters,
        headers: {
            'Custom-Header': '{header_value}'
        }
    }, function(err, response) {
        if (err)
            console.log('error:', err);
        else
            console.log(response);
    }
);
```
## Java right-pane code examples
{: java}
{: right}

Example header parameter in a request

```java
ReturnType returnValue = visualRecognition.methodName(parameters)
        .addHeader("Custom-Header", "{header_value}")
        .execute();
```

## Python right-pane code examples
{: python}
{: right}

Example header parameter in a request

```python
response = visualRecognition.methodName(
    parameters,
    headers = {
        'Custom-Header': '{header_value}'
    })
```

# Data labels

**Optional**
**Purpose**: Information about labeling customer data for GDPR. (Link to the API Handbook TBD)
**Example**:

You can remove customer data if you associate the customer and the data when you send the information to a service. First, you label the data with a customer ID, and then you can delete the data by the ID.

* Use the `X-Watson-Metadata` header to associate a customer ID with the data. By adding a customer ID to a request, you indicate that it contains data that belongs to that customer. Specify a random or generic string for the customer ID. Do not include personal data, such as an email address. Pass the string `customer_id={id}` as the argument of the header.
* Use the `Delete labeled data` method to remove data that is associated with a customer ID.

Labeling data is used only by methods that accept customer data. For more information about {{site.data.keyword.visualrecognitionshort}} and labeling data, see [Information security](https://cloud.ibm.com/docs/services/visual-recognition?topic=visual-recognition-information-security).

# Data collection

**Optional**
**Purpose**: This section is about opting out of using your data for service improvements
**Example**:

By default, all {{site.data.keyword.watson}} services log requests and their results. Logging is done only to improve the services for future users. The logged data is not shared or made public.

To prevent IBM from accessing your data for general service improvements, set the `X-Watson-Learning-Opt-Out` request header to `true` for all requests. (Any value other than `false` or `0` disables request logging for that call.) You must set the header on each request that you do not want IBM to access for general service improvements.
{: curl}

You can set the header by using the `setDefaultHeaders` method of the service object.
{: java}

You can set the header by using the `headers` parameter when you create the service object.
{: node}

You can set the header by using the `set_default_headers` method of the service object.
{: python}

## Example request
{: right}

```bash
curl -H "X-Watson-Learning-Opt-Out: true" "https://gateway-a.watsonplatform.net/visual-recognition/api/{endpoint}?api_key={api_key}"
```
{: curl}

```javascript
var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');

var visualRecognition = new VisualRecognitionV3({
    version: '{version}',
    api_key: '{api_key}'
    headers: {
        'X-Watson-Learning-Opt-Out': 'true'
    }
});
```
{: node}

```java
Map<String, String> headers = new HashMap<String, String>();
headers.put("X-Watson-Learning-Opt-Out", "true");

visualRecognition.setDefaultHeaders(headers);
```
{: java}

```python
visual_recognition.set_default_headers({'x-watson-learning-opt-out': "true"})
```
{: python}

# Pagination

**Optional**
**Purpose**: Do you limit the page results returned by any of your API endpoints? If so, clarify the pagination your API supports. For more information, see [API Handbook - Pagination](https://pages.github.ibm.com/CloudEngineering/api_handbook/collections/pagination.html)
**Example**:

Some API requests might return many results. To avoid performance issues, these results are returned one page at a time, with a limited number of results on each page. GET requests for the following resources use pagination:

* /v1/workspaces
* /v1/workspaces/{workspace_id}/counterexamples
* /v1/workspaces/{workspace_id}/intents
* /v1/workspaces/{workspace_id}/intents/{intent}/examples

The default page size is 100 objects. To use a different page size, use the `page_limit` query parameter.

To change the attribute by which results are sorted, use the `sort` query parameter. If you include multiple sort parameters on the same query, the results are sorted first by the first sorting attribute, then the second, and so on.

The supported sorting attributes vary by endpoint; for more information, see the API Reference information for each request.

For any request that uses pagination, the response includes a `pagination` object that specifies pagination information. This object includes two URLs you can use to make subsequent requests:

* refresh_url: the URL for requesting the same page of results again.
* next_url: the URL for requesting the next page of results. The next_url property is omitted if there no more results.

These URLs retain the same `page_limit` and `sort` parameters that were used for the initial request.

# Sorting

**Optional**
**Purpose**: Does your API provide custom sorting? If so, provide details to clarify how sorting is handled. For more information, see: [API Handbook - Sorting](https://pages.github.ibm.com/CloudEngineering/api_handbook/collections/sorting.html)
**Example**:

TBD

# Filtering

**Optional**
**Purpose**: Does your API support filtering? For example, do you support the use of pre-defined tags? If so, provide details to clarify how your API handles filtering. For more information, see: [API Handbook - Filtering](https://pages.github.ibm.com/CloudEngineering/api_handbook/collections/filtering.html)
**Example**:

TBD

# Searching

**Optional**
**Purpose**: (Link to the API Handbook - NA)
**Example**:

TBD

# Rate limiting

**Optional**
**Purpose**: Provide details if your API supports rate limiting. In the example, we see details about a response header that shows users how close they are to the rate limit. (Link to the API Handbook TBD)
**Example**:

Rate limits for API requests are enforced on a per-service-instance basis. If the number of requests for a particular method and endpoint reaches the request limit within the specified time window, no further requests are accepted until the timer expires. After the timer expires, a new time window begins with the next accepted request.

The response to each HTTP request includes headers that you can use to determine whether you are close to the rate limit:

* X-RateLimit-Reset: the time the current timer expires (in UNIX epoch time)
* X-RateLimit-Remaining: the number of requests remaining in the current time window
* X-RateLimit-Limit: the total number of requests allowed within the time window

HTTP status code `429` indicates that the rate limit has been exceeded.

The number of allowed requests, and the length of the time window, vary by method and endpoint. The reference information for each endpoint specifies the rate limit that applies.

# Related APIs

**Optional**
**Purpose**: Are you delivering a set of grouped APIs? Or maybe your offering has three kinds of APIs but you want to define the interrelationship between them? Provide any text that explains how one or more related APIs might be useful for the user to understand.
**Example**:

Intro text...

* [Conversation](/apidocs/conversation)
* [Natural Language Classifier](/apidocs/natural-language-classifier)
* [Visual Recognition Dedicated](/apidocs/dedicated/visual-recognition-dedicated)

# Deprecated APIs

**Optional**
**Purpose**: Have you deprecated one or more APIs associated with the latest one you are documenting? Provide some information about the deprecation and link to the deprecated API.
**Example**:

Intro text...

* [V1](/apidocs/v1/visual-recognition-extension)
