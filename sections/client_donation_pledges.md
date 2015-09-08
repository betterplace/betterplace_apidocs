
# Client Donation Pledges

```Rebol
POST http://jop.betterplace.dev/de/api_v4/clients/volksfreund/projects/1114/donation_pledges.json
```

Submit a donation pledge into the system. This will be transformed into
a donation to the receiver. The request has to be a POST request with a
JSON body.

**:lock: Only available if authenticated as a client.**
See [betterplace.org clients](../README.md#client-api).

**Response and error codes:**

A successful request will return HTTP status 202 (accepted). The
donation pledge is now saved and queued and will be processed
by background workers. This part takes place asynchronously and might
take up to a few minutes, especially in high traffic scenarios.
Please make sure that you queue and retry your API calls until you
receive a 202 response from us. Note that we will book only one
donation per <code>client_reference</code> so there is no need to
worry about retrying the pledge-sending.

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
    <th align="left">language</th>
    <td><code>en</code></td>
    <td>yes</td>
    <td>The donation is marked with the language you use in your URL.
Project manager use this language information for their donation
thank you message, for example. To target a lang see
<a href="../README.md#addressing-the-locale-of-a-resource">api setting lang</a>.
</td>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>volksfreund</code></td>
    <td>yes</td>
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1114</code></td>
    <td>yes</td>
    <td>Project-id as an integer number ≥ 14.</td>
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
  "first_name": "Max",
  "last_name": "Mustermann",
  "email": "mm@example.com",
  "amount_in_cents": 100,
  "client_reference": "djksbf23u4sjkdn234p",
  "street": "Rheinstrasse 202",
  "city": "Wiesbaden",
  "zip": "65185",
  "country_code": "DE"
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
    <td><code>Max</code></td>
    <td>string</td>
    <td>yes</td>
    <td>First name of the donor.</td>
  </tr>
  <tr>
    <th align="left">last_name</th>
    <td><code>Mustermann</code></td>
    <td>string</td>
    <td>yes</td>
    <td>Last name of the donor.</td>
  </tr>
  <tr>
    <th align="left">email</th>
    <td><code>mm@example.com</code></td>
    <td>string</td>
    <td>yes</td>
    <td>Email address of the donor.
Only valid email addresses will be accepted.
</td>
  </tr>
  <tr>
    <th align="left">amount_in_cents</th>
    <td><code>100</code></td>
    <td>number</td>
    <td>yes</td>
    <td>The amount of cents that are donated.
Must be a positive integer between
100
and 100000.
</td>
  </tr>
  <tr>
    <th align="left">client_reference</th>
    <td><code>djksbf23u4sjkdn234p</code></td>
    <td>string</td>
    <td>yes</td>
    <td>A unique identifier for this transaction.
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
    <th align="left">street</th>
    <td><code>Rheinstrasse 202</code></td>
    <td>string</td>
    <td>yes</td>
    <td>The street of the donors address.
Used to issue a donation receipt if the donation is tax deductible.
</td>
  </tr>
  <tr>
    <th align="left">city</th>
    <td><code>Wiesbaden</code></td>
    <td>string</td>
    <td>yes</td>
    <td>The city of the donors address.
Used to issue a donation receipt if the donation is tax deductible.
</td>
  </tr>
  <tr>
    <th align="left">zip</th>
    <td><code>65185</code></td>
    <td>string</td>
    <td>yes</td>
    <td>Zip code of the city or region the donor lives at.
Used to issue a donation receipt if the donation is tax deductible.
</td>
  </tr>
  <tr>
    <th align="left">country_code</th>
    <td><code>DE</code></td>
    <td>string</td>
    <td>yes</td>
    <td>ISO2 code of the country the donor lives in. A list of valid ISO2 codes
can be found at <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements">
Wikipedia ISO_3166-1_alpha-2</a>. Used to issue a donation receipt if
the donation is tax deductible.
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
      <td>string</td>
      <td>accepted</td>
      <td>HTTP status code as a descriptive string.
For a list of codes, <a href="http://httpstatus.es/">see httpstatus.es</a>.
Example: "accepted" for code 202
</td>
    </tr>
    <tr>
      <th align="left">status_code</th>
      <td>number</td>
      <td>202</td>
      <td>HTTP status code as an integer number, e.g. 202.
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
      <th align="left">location</th>
      <td>Location where the created/updated resource can be viewed or more
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
      "href": "http://jop.betterplace.dev/de/api_v4/clients/some_client/client_donations/666-a-reference"
    }
  ]
}
```

