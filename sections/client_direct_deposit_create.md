
# Creating a Direct Deposit Donation ⇄ [Status](direct_deposit_details.md)

```Cirru
POST https://api.betterplace.org/de/api_v4/clients/bergluft/projects/1114/direct_deposits.json
```

Create an unconfirmed direct deposit donation to a project.
The donation is confirmed when the money arrives on the betterplace
bank account.

**:lock: Only available if authenticated as a client.**
See [betterplace.org clients](../README.md#client-api).

**:lock: This is an experimental feature and needs additional privileges.**

### Response and error codes:

[A list of all response and error codes](../README.md#http-status-codes).

The most likely ones are:

[HTTP Code **`202`**](http://httpstatus.es/202)
if the donation was created. The response data
will include an IBAN and the reference number to submit the actual
bank transfer.

[HTTP Code **`422`**](http://httpstatus.es/422)
if the submitted resource could not be accepted due to erroneous parameters
or missing data.


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
    <td><code>bergluft</code></td>
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
  "first_name": "Max",
  "last_name": "Mustermann",
  "company_name": "Mustermann Inc.",
  "email": "mm@example.com",
  "message": "Great Project!",
  "amount_cents": 100,
  "client_reference": "djksbf23u4sjkdn234p",
  "street": "Rheinstrasse 202",
  "city": "Wiesbaden",
  "zip": "65185",
  "country_alpha2": "DE",
  "validate_address": true
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
      yes
    </td>
<td>

First name of the donor.


</td>
  </tr>
  <tr>
    <th align="left">last_name</th>
    <td><code>Mustermann</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

Last name of the donor.


</td>
  </tr>
  <tr>
    <th align="left">company_name</th>
    <td><code>Mustermann Inc.</code></td>
    <td><code>string</code></td>
    <td>
      no
    </td>
<td>

Company name of the donor.


</td>
  </tr>
  <tr>
    <th align="left">email</th>
    <td><code>mm@example.com</code></td>
    <td><code>string</code></td>
    <td>
      yes
    </td>
<td>

Email address of the donor.
Only valid email addresses will be accepted.


</td>
  </tr>
  <tr>
    <th align="left">message</th>
    <td><code>Great Project!</code></td>
    <td><code>string</code></td>
    <td>
      no
    </td>
<td>

A message from the donor to be shown on the project profile page.


</td>
  </tr>
  <tr>
    <th align="left">amount_cents</th>
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
    <th align="left">street</th>
    <td><code>Rheinstrasse 202</code></td>
    <td><code>string</code></td>
    <td>
      see description
    </td>
<td>

The street of the donors address.
Used to issue a donation receipt if the donation is tax deductible.

This field is required by default, but optional with
validate_address=false.


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

This field is required default, but optional with validate_address=false.


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
    <th align="left">country_alpha2</th>
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
    <td><code>true</code></td>
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
      <th align="left">reference_id</th>
      <td><code>number</code></td>
      <td><code>123456</code></td>
<td>

The reference for the pending debit donation. Use it within
the transaction to ensure it gets matched with the donation.


</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">iban</th>
      <td><code>string</code></td>
      <td><code>DE123</code></td>
<td>

The IBAN for the SEPA transaction.


</td>
    </tr>
    <tr>
      <th align="left">holder_name</th>
      <td><code>string</code></td>
      <td><code>betterplace</code></td>
<td>

The holder name for the SEPA transaction.


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
  <th colspan="2">No response example defined</th>
</table>

## Response Example

```json
{
  "id": 1563628,
  "created_at": "2018-08-21T16:52:43+02:00",
  "updated_at": "2018-09-01T09:00:29+02:00",
  "reference_id": 1563628,
  "iban": "DE14672700030088880032",
  "holder_name": "gut.org",
  "links": [

  ]
}
```

