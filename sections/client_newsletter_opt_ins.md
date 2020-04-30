
# Client Newsletter OptIns

```Cirru
POST https://api.betterplace.org/de/api_v4/clients/volksfreund/newsletter_opt_ins.json
```

Start the opt-in process to subscribe an email address to the
betterplace platform newsletter.

**:lock: Only available if authenticated as a client.**
See [betterplace.org clients](../README.md#client-api).

### Response and error codes:

A successful request will return HTTP status 201 (created).

If an error occurs the HTTP return code will be 422 (unprocessable
entity). [More error codes](../README.md#http-status-codes).


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
    <th align="left">language</th>
    <td><code>en</code></td>
    <td>yes</td>
<td>

The language preference of the subscriber.

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
  "email": "peter.paul@betterplace.org",
  "first_name": "Peter",
  "last_name": "Paul",
  "wording": "I want to receive newsletters from betterplace"
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
    <th align="left">email</th>
    <td><code>peter.paul@betterplace.org</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

The email of the user

</td>
  </tr>
  <tr>
    <th align="left">first_name</th>
    <td><code>Peter</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

The first name of the user

</td>
  </tr>
  <tr>
    <th align="left">last_name</th>
    <td><code>Paul</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

The last name of the user

</td>
  </tr>
  <tr>
    <th align="left">wording</th>
    <td><code>I want to receive newsletters from betterplace</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

The text that has been used to explain the subscription to the user.
E.g. if you have a checkbox to subscribe, pass its label text.

This text must be recorded due to GDPR requirements.


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
  "status": "created",
  "status_code": 201,
  "links": [

  ]
}
```

