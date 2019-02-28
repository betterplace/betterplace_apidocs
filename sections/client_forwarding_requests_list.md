
# Creating a Client Forwarding Request ⇄ [Status](client_forwarding_request_details.md)

```Cirru
POST https://api.betterplace.org/de/api_v4/clients/volksfreund/projects/1114/forwarding_requests.json
```

Transfer money from a client donation pool to a Project.
The request has to be a POST request with a JSON body.

**:lock: Only available if authenticated as a client.**
See [betterplace.org clients](../README.md#client-api).


### Process Flow

[This a flow chart describes the process…](https://ixwphj.axshare.com/forwarding-request-flow.html).


### What if the donation receiver is fully funded?

The donation will be booked in the receiver account even
if the receiver is fully funded. The receiver will than show a
progress percentage > 100 %. For a project that means, the project
manager has to add new money needs to pay out the additional funds.

Please note that closed projects are prohibited from receiving donations.


### What if the donation receiver is prohibited from receiving donations?

At the time when the forwarding request is received, the system does not
check the receiver status. Therefore the API will always respond with a
success message for all receivers.

Should the receiver be prohibited from receiving donations at the time
when the donation is processed, the forwarding will not be inserted into
the system. The forwarding request will then be marked as "failed" and
the "error_reason" field holds detailed information about the problem.
Learn more at [Client Forwarding Request Status](client_forwarding_request_details.md).

There are two possible next steps:

_Option 1:_ Handle those cases manually with the betterplace.org-support-team.
This option is only feasible in selected cases.

_Option 2:_ The client system reacts to the error-state of the
forwarding request automatically. For example by moving the donation
to a fallback project.


### Response and error codes:

[A list of all response and error codes](../README.md#http-status-codes).

The most likely ones are:

[HTTP Code **`202`**](http://httpstatus.es/202)
if a resource was successfully submitted for delayed processing.
A successful request will return HTTP status 202 (accepted). The
forwarding request is now saved and queued and will be processed
by background workers. This part takes place asynchronously and might
take up to a few minutes, especially in high traffic scenarios.
Please make sure that you queue and retry your API calls until you
receive clear answer (202, 422, 404, etc.) from us.
Note that we will book only one
donation per <code>client_reference</code> so there's no need to
worry about retrying the forwarding.

[HTTP Code **`422`**](http://httpstatus.es/422)
if the submitted resource could not be accepted due to erroneous parameters.
Please remember to validate all user input on your side before submitting
it to the API.

[HTTP Code **`404`**](http://httpstatus.es/404)
if a requested resource could not be found. This might happen if
the resource has been deleted in the timeframe between selection by the
user and confirmation of the forwarding request by the client. In this
case, either contact your user and change the resource (most likely a
project) or redirect the donation to the client pool (the URL is
provided by betterplace.org).


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>volksfreund</code></td>
    <td>yes</td>
<td>

The betterplace.org-internal client permalink.

</td>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1114</code></td>
    <td>yes</td>
<td>

Project id as an integer number ≥ 14.

</td>
  </tr>
</table>

## JSON Parameters

JSON parameters have to be provided in the body of the request with the
Content-Type header set to "application/json". The parameters are part of a
flat JSON document without any nesting. Some parameters are required, others
are optional.

### Example

```json
{
  "amount_in_cents": 100,
  "client_reference": "djksbf23u4sjkdn234p",
  "tracking_via": "campaign-0815"
}
```

### Supported Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Types</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">amount_in_cents</th>
    <td><code>100</code></td>
    <td><code>number</code></td>
    <td>
      yes
    </td>
<td>

The amount of cents that are forwarded.
Must be a positive integer between
1
and 100000.


</td>
  </tr>
  <tr>
    <th align="left">client_reference</th>
    <td><code>djksbf23u4sjkdn234p</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

A unique identifier for this transaction.
With this reference one can find the donation and its status later
by using the client_reference-facet on the
<a href="client_donations_list.md">donation list endpoint</a>.
<br>
Allowed characters are <code>a-zA-Z0-9_-</code>.
<br>
<em>Attention:</em> If you use a non-unique client reference,
the donation pledge endpoint will still respond with success.
However the pledge will <em>not be processed</em> into a donation but ignored.
<br>
This is to make sure that one transaction is only processed once.


</td>
  </tr>
  <tr>
    <th align="left">tracking_via</th>
    <td><code>campaign-0815</code></td>
    <td><code>string</code></td>
    <td>
      no
    </td>
<td>

A tracking identifier for the current campaign, origin or similar
information. Default is blank.
<br>
Allowed characters are <code>a-zA-Z0-9_-</code>.


</td>
  </tr>
</table>

## Response Attributes


### Root Attributes

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">status</th>
      <td><code>string</code></td>
      <td><code>accepted</code></td>
<td>

HTTP status code as a descriptive string.
For a list of codes, <a href="http://httpstatus.es/">see httpstatus.es</a>.
Example: "accepted" for code 202


</td>
    </tr>
    <tr>
      <th align="left">status_code</th>
      <td><code>number</code></td>
      <td><code>202</code></td>
<td>

HTTP status code as an integer number, e.g. 202.


</td>
    </tr>
  </table>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>
    <tr>
<th align="left">

location

</th>
<td>

Location where the created/updated resource can be viewed or more
information about it can be gathered.


</td>
    </tr>
</table>

## Response Example

```json
{
  "status": "accepted",
  "status_code": 202,
  "links": [
    {
      "rel": "location",
      "href": "https://api.betterplace.org/de/api_v4/clients/some_client/forwarding_requests/1337"
    }
  ]
}
```

