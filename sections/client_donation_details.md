
# Client Donation Details ⇄ [List](client_donations_list.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/d0d35e347873169aec71.json
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
<td>

The betterplace.org-internal client permalink.

</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>d0d35e347873169aec71</code></td>
    <td>yes</td>
<td>

          The donation token that the client donation form passed to the
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
      <td><code>number</code></td>
      <td><code>10100</code></td>
<td>

Donated amount in cents

</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td><code>string</code></td>
      <td><code>"confirmed"</code></td>
<td>

At the moment, all donations that are returned by the API are "confirmed".
Unconfirmed donations do not show up at all or disappear after they were revoked.
Revocations usually take place during the first 14 days – but there are no guarantees.

Please make sure to check for the "confirmed" state in your application explicitly since
we might add a "revoked" state in the future.


</td>
    </tr>
    <tr>
      <th align="left">token</th>
      <td><code>string</code></td>
      <td><code>ofMmTgfiPL-n1dDlNmFWqTQN</code></td>
<td>

A token uniquely identifies a donation on the platform.


</td>
    </tr>
    <tr>
      <th align="left">client_reference</th>
      <td><code>string</code></td>
      <td><code>922ec9b-etc</code></td>
<td>

Client Donations can be identified via a custom client reference token.

This <code>donation_client_reference</code> can be provided by users of our
<a href="../donation_form/third_party_app_donation_form.md">
ThirdPartyApp custom donation form for organisations</a>, for example.


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
      <th align="left">receiver_type</th>
      <td><code>string</code></td>
      <td><code>"Project"</code></td>
<td>

Client donations may go to a <code>Project</code>,
a Project's <code>Element</code>, a <code>FundraisingEvent</code>,
a <code>Pool</code>.


</td>
    </tr>
    <tr>
      <th align="left">receiver_id</th>
      <td><code>number</code></td>
      <td><code>1114</code></td>
<td>

The id of the project, project element or fundraising event.

</td>
    </tr>
    <tr>
      <th align="left">receiver_title</th>
      <td><code>string</code></td>
      <td><code>"Skateistan Afghanistan"</code></td>
<td>

The title of the project, project element or fundraising event.

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

receiver

</th>
<td>

Link to the <a href="project_details.md">project details</a>,
<a href="need_details.md">project need details</a>,
<a href="fundraising_event_details.md">fundraising event details</a>,
that is associated with this donation.<br>
Right now, there is no api end point for donations that are
redirect or donated to the client pool.


</td>
    </tr>
    <tr>
<th align="left">

self

</th>
<td>

Link to this resource itself
(<a href="client_donation_details.md">client donation details</a>)


</td>
    </tr>
    <tr>
<th align="left">

donor_contact_data

</th>
<td>

Link to the donor contact data
(<a href="donor_contact_data_details.md">donor contact data details</a>)


</td>
    </tr>
</table>

## Response Example

```json
{
  "amount_in_cents": 1000,
  "state": "confirmed",
  "token": "25463e68bb714c6f07ec",
  "client_reference": null,
  "created_at": "2010-10-28T14:44:49+02:00",
  "receiver_type": "Project",
  "receiver_id": 4807,
  "receiver_title": "Kleinbus für den Palais e.V. Trier",
  "links": [
    {
      "rel": "receiver",
      "href": "https://api.betterplace.org/de/api_v4/projects/4807.json"
    },
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/25463e68bb714c6f07ec.json"
    },
    {
      "rel": "donor_contact_data",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/25463e68bb714c6f07ec/donor_contact_data.json"
    }
  ]
}
```

