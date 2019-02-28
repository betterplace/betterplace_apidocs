
# Volunteering Inquiries

```Cirru
POST https://api.betterplace.org/de/api_v4/clients/volksfreund/volunteering/37443/inquiries.json
```

Submit a volunteering inquiry into the system. It will be sent as
email to the manager of the volunteering. A copy of the inquiry will
be sent to the inquiring user. The request has to be a POST request
with a JSON body.


**:lock: Only available if authenticated as a client and only
if this client has permissions to use this feature.**
See [betterplace.org clients](../README.md#client-api).


**Response and error codes:**

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
    <th align="left">volunteering_id</th>
    <td><code>37443</code></td>
    <td>yes</td>
<td>

volunteering/job description id as an integer number.

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
  "first_name": "Peter",
  "last_name": "Paul",
  "email": "peter.paul@betterplace.org",
  "phone": "+49 (0)30 / 123456",
  "availability": "I can help every Sunday evening.",
  "profile": "I have taken care of kittens many times before.",
  "questions": "Will I work in a team or on my own?",
  "terms_of_use": true
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
    <th align="left">phone</th>
    <td><code>+49 (0)30 / 123456</code></td>
    <td><code>string</code></td>
    <td>
      no
    </td>
<td>

The phone number of the user

</td>
  </tr>
  <tr>
    <th align="left">availability</th>
    <td><code>I can help every Sunday evening.</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

Information about the user’s availability.
How much time would he like to spend, what are his preferred dates,
would he prefer a short-term or a long-term involvement, etc.


</td>
  </tr>
  <tr>
    <th align="left">profile</th>
    <td><code>I have taken care of kittens many times before.</code></td>
    <td><code>string</code></td>
    <td>
      no
    </td>
<td>

Information about the user himself, his skills, etc.

</td>
  </tr>
  <tr>
    <th align="left">questions</th>
    <td><code>Will I work in a team or on my own?</code></td>
    <td><code>string</code></td>
    <td>
      no
    </td>
<td>

Any questions the user might have about the offer

</td>
  </tr>
  <tr>
    <th align="left">terms_of_use</th>
    <td><code>true</code></td>
    <td><code>boolean</code></td>
    <td>
      yes
    </td>
<td>

Confirmation that the user has accepted the privacy terms,
e.g. via a checkbox.


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

