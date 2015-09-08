
# Donor Contact Data Details

```Rebol
GET http://jop.betterplace.dev/de/api_v4/clients/volksfreund/client_donations/V9mxWWAeuVK9PtJw9mrZRyRk/donor_contact_data.json
```

Name and email for the donor.

This feature is based on a special checkbox that
has to be integrated in the client donation form or
on the postdonation page. Only users that give the
explicit permission to provide the data to the client
will be included.

**:lock: Only available if authenticated as a client and only if this clients has permissions to access this data.**
See [betterplace.org clients](../README.md#client-api).


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
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
  <tr>
    <th align="left">client_donation_id</th>
    <td><code>V9mxWWAeuVK9PtJw9mrZRyRk</code></td>
    <td>yes</td>
    <td>The betterplace.org donation token or given client reference.</td>
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
      <th align="left">first_name</th>
      <td>string</td>
      <td>Peter</td>
      <td>The first name of the user or donor.</td>
    </tr>
    <tr>
      <th align="left">last_name</th>
      <td>string</td>
      <td>Paul</td>
      <td>The last name of the user or donor.</td>
    </tr>
    <tr>
      <th align="left">email</th>
      <td>string</td>
      <td>peter.paul@betterplace.org</td>
      <td>The email address of the user or donor.</td>
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
  "first_name": "Peter",
  "last_name": "Paul",
  "email": "peter.paul@betterplace.org",
  "links": [

  ]
}
```

