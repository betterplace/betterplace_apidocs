
# Client Donation Details ⇄ [List](client_donations_list.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/V9mxWWAeuVK9PtJw9mrZRyRk.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

The details of a betterplace.org client donation.
The details and list view show the same data.


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
    <th align="left">id</th>
    <td><code>V9mxWWAeuVK9PtJw9mrZRyRk</code></td>
    <td>yes</td>
    <td>          The donation token that the client donation form passed to the
          callback url or the client_reference that was provided by the client.
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
      <th align="left">amount_in_cents</th>
      <td>number</td>
      <td>10100</td>
      <td>Donated amount in cents</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td>string</td>
      <td>"confirmed"</td>
      <td>At the moment, all donations that are returned by the API are "confirmed".
Unconfirmed donations do not show up at all or disappear after they where revoked.
Revocations usually take place during the first 14 days – but there are no guarantees.

Please make sure to check for the "confirmed" state in your application explicitly since
we might add a "revoked" state in the future.
</td>
    </tr>
    <tr>
      <th align="left">token</th>
      <td>string</td>
      <td>ofMmTgfiPL-n1dDlNmFWqTQN</td>
      <td>A token uniquely identifies a donation on the platform.
</td>
    </tr>
    <tr>
      <th align="left">client_reference</th>
      <td>string</td>
      <td>922ec9b-etc</td>
      <td>Client Donations can be identified via a custom client reference token.

This <code>donation_client_reference</code> can be provided by users of our
<a href="../donation_form/third_party_app_donation_form.md">
ThirdPartyApp custom donation form for organisations</a>, for example.
</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">receiver_type</th>
      <td>string</td>
      <td>"Project"</td>
      <td>Client donations may go to <code>Project</code>,
Project <code>Element</code>, <code>FundraisingEvent</code>.
</td>
    </tr>
    <tr>
      <th align="left">receiver_id</th>
      <td>number</td>
      <td>1114</td>
      <td>The id of the project, project element or fundraising event.</td>
    </tr>
    <tr>
      <th align="left">receiver_title</th>
      <td>string</td>
      <td>"Skateistan Afghanistan"</td>
      <td>The title of the project, project element or fundraising event.</td>
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
      <th align="left">receiver</th>
      <td>Link to the <a href="project_details.md">project details</a>
or <a href="need_details.md">project need details</a>
that is associated with this donation.
</td>
    </tr>
    <tr>
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="client_donation_details.md">client donation details</a>)
</td>
    </tr>
    <tr>
      <th align="left">donor_contact_data</th>
      <td>Link to the donor contact data
(<a href="donor_contact_data_details.md">donor contact data details</a>)
</td>
    </tr>
</table>

## Response Example

```json
{
  "amount_in_cents": 500,
  "state": "confirmed",
  "token": "V9mxWWAeuVK9PtJw9mrZRyRk",
  "client_reference": "",
  "created_at": "2014-04-15T10:26:20+02:00",
  "receiver_type": "Project",
  "receiver_id": 18417,
  "receiver_title": "Mobiler Kinder- und Jugendtreff",
  "links": [
    {
      "rel": "receiver",
      "href": "https://api.betterplace.org/de/api_v4/projects/18417.json"
    },
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/V9mxWWAeuVK9PtJw9mrZRyRk.json"
    },
    {
      "rel": "donor_contact_data",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/V9mxWWAeuVK9PtJw9mrZRyRk/donor_contact_data.json"
    }
  ]
}
```

