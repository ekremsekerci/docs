---
title: "Delete External Object"
url: /refguide9/delete-external-object/
---
{{% alert color="warning" %}}
These activities can only be used in **Microflows**.
{{% /alert %}}

## Introduction

The **Delete external object** activity can be used to delete an external object. It sends a DELETE request to the publishing app.

{{% alert type="info" %}}
This activity was introduced in Studio Pro [9.12.0](/releasenotes/studio-pro/9.12/).
{{% /alert %}}

### Entity Access

When the microflow has **Apply entity access** set to **Yes**, only users with *delete* entity access can execute this activity. Users without *delete* entity access will see an error message.

## Activity Properties

To manage the properties of the activity, double-click the **Delete external object** activity, or right-click the activity and select **Properties**. 

Single-clicking on the activity displays the properties in the **Properties** pane.

### Object

Choose a variable that contains a single deletable external object.

### Refresh in Client

This setting defines how changes are reflected in the pages presented to the end-user. The default for this setting is *No*.

## After the Activity

After this activity, the `$latestHttpResponse` variable (of the [HttpResponse](/refguide9/http-request-and-response-entities/#http-response) type) is available to inspect the response returned by the service.

{{% alert color="info" %}}
The feature to set `$latestHttpResponse` was introduced in Studio Pro [9.15.0](/releasenotes/studio-pro/9.15/).
{{% /alert %}}
