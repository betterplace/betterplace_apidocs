
# Creating a Client Donation Pledge ⇄ [Status](client_donation_pledge_status.md)

```Cirru
POST https://api.betterplace.org/de/api_v4/clients/volksfreund/projects/1114/donation_pledges.json
```

Submit a donation pledge into the system. This will be transformed into
a donation to the receiver. The request has to be a POST request with a
JSON body.

**:lock: Only available if authenticated as a client.**
See [betterplace.org clients](../README.md#client-api).


### Process Flow

[This flow chart describes the process…](https://ixwphj.axshare.com/donation-pledge-flow.html).


### What if the donation receiver is fully funded?

The donation will be booked in the receiver account even
if the receiver is fully funded. The receiver will than show a
progress percentage > 100 %. For a project that means, the project
manager has to add new money needs to pay out the additional funds.

Please note that a closed project is prohibited from receiving donations.


### What if the donation receiver is prohibited from receiving donations?

At the time when the pledge is received the system does not check the receiver
status. Therefore the API will always respond with a success message for all
receivers. Should the receiver be prohibited from receiving donations at the
time when the donation is processed, the donation will be redirected to a
specific client donation pool. Clients can later forward this money to
projects they choose.


### Reconciliation of donation pledges

Part of the contract for the usage of this donation pledge API will
be the time period in which the pledges need to be reconciled. Ususally
every two weeks or once a month. At the end of this time, the client
will sum all pledges in the client system, wire us the donations and
also send us a CSV file which allows betterplace.org to check the amounts.

The fields for the CSV files are:
- receiver_type, eg. `Project`
- receiver_id, eg. `1114`
- amount_in_cents, eg. `12000`
- client_reference, eg. `123123123123`
- datetime (ISO8601 with Timezone), eg `2007-11-01T13:15:30Z`

Please use these names as column titles, use utf-8, use ","
as a separator and force double quotes around all values.

Here is [a flow chart describing the process](https://ixwphj.axshare.com/money-transfer-flow.html).


### Sending donation pledges to the client-pool

It is possible to send donation pledges directly to the client-pool, by
submitting to this endpoint instead of the project specific one:

`POST https://api.betterplace.org/de/api_v4/clients/{CLIENT}/pool/donation_pledges.json`

This endpoint will respond and behave like described above, but the
money will be stored on the pool. Clients can later forward this money to
projects they choose.


### Response and error codes:

[A list of all response and error codes](../README.md#http-status-codes).

The most likely ones are:

[HTTP Code **`202`**](http://httpstatus.es/202)
if a resource was successfully submitted for delayed processing.
A successful request will return HTTP status 202 (accepted). The
donation pledge is now saved and queued and will be processed
by background workers. This part takes place asynchronously and might
take up to a few minutes, especially in high traffic scenarios.
Please make sure that you queue and retry your API calls until you
receive clear answer (202, 422, 404, etc.) from us.
Note that we will book only one
donation per <code>client_reference</code> so there's no need to
worry about retrying the pledge-sending.

[HTTP Code **`422`**](http://httpstatus.es/422)
if the submitted resource could not be accepted due to erroneous parameters.
Please remember to validate all user input on your side before submitting
it to the API.

[HTTP Code **`404`**](http://httpstatus.es/404)
if a requested resource could not be found. This might happen if
the resource has been deleted in the timeframe between selection by the
user and confirmation of the pledge by the client. In this case, either
contact your user and change the resource (most likely a project) or
redirect the donation to the client pool (the URL is provided by
betterplace.org).


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

Project id as an integer number.

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
  "first_name": "Max",
  "last_name": "Mustermann",
  "email": "mm@example.com",
  "amount_in_cents": 100,
  "client_reference": "djksbf23u4sjkdn234p",
  "tracking_via": "campaign-0815",
  "earmark": 123,
  "street": "Rheinstrasse 202",
  "city": "Wiesbaden",
  "zip": "65185",
  "country_code": "DE",
  "validate_address": false
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
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

First name of the donor.

This field is required by default, but optional with
validate_address=false.


</td>
  </tr>
  <tr>
    <th align="left">last_name</th>
    <td><code>Mustermann</code></td>
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

Last name of the donor.

This field is required by default, but optional with
validate_address=false.


</td>
  </tr>
  <tr>
    <th align="left">email</th>
    <td><code>mm@example.com</code></td>
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

Email address of the donor.
Only valid email addresses will be accepted.

This field is required by default, but optional with
validate_address=false.


</td>
  </tr>
  <tr>
    <th align="left">amount_in_cents</th>
    <td><code>100</code></td>
    <td><code>number</code></td>
    <td>
      yes
    </td>
<td>

The amount of cents that are donated.
Must be a positive integer between
1
and 1000000.


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
  <tr>
    <th align="left">earmark</th>
    <td><code>123</code></td>
    <td><code>number</code></td>
    <td>
      no
    </td>
<td>

An "earmark" indicating which need this donation should go to.
<em>Attention:</em> this parameter may be completely ignored by the API
at any time. There is no guarantee that the earmark will have an effect
on the donation, and support for the feature may be pulled in the
future.


</td>
  </tr>
  <tr>
    <th align="left">street</th>
    <td><code>Rheinstrasse 202</code></td>
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

The street of the donors address.
Used to issue a donation receipt if the donation is tax deductible.

This field is required by default, but optional with validate_address=false.


</td>
  </tr>
  <tr>
    <th align="left">city</th>
    <td><code>Wiesbaden</code></td>
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

The city of the donors address.
Used to issue a donation receipt if the donation is tax deductible.

This field is required by default, but optional with validate_address=false.


</td>
  </tr>
  <tr>
    <th align="left">zip</th>
    <td><code>65185</code></td>
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

Zip code of the city or region the donor lives in.
Used to issue a donation receipt if the donation is tax deductible.

This field is required by default, but optional with validate_address=false.


</td>
  </tr>
  <tr>
    <th align="left">country_code</th>
    <td><code>DE</code></td>
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

ISO2 code of the country the donor lives in. A list of valid ISO2 codes
can be found at <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements">
Wikipedia ISO_3166-1_alpha-2</a>. Used to issue a donation receipt if
the donation is tax deductible.

This field is required by default, but optional with validate_address=false.


</td>
  </tr>
  <tr>
    <th align="left">validate_address</th>
    <td><code>false</code></td>
    <td><code>boolean</code></td>
    <td>
      no
    </td>
<td>

Pass <code>false</code> to allow donations without a donor address.
<br>
<em>Attention:</em> Donation receipts can only be issued to donors who
provide their full address details. Therefore a warning might be
in order when using this option: Let donors know that they won't get a
donation receipt, or that they will only get a receipt if they do enter
their address.
<br>
True by default.


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
      "href": "https://api.betterplace.dev/de/api_v4/clients/some_client/client_donations/666-a-reference"
    }
  ]
}
```

