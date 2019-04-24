---

copyright:
  years: 2019
lastupdated: "2019-04-15"

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


# Introduction


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

