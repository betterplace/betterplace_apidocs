
# Client Donations List ⇄ [Details](client_donation_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations.json?facets=client_reference%3A922ec9b-etc
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all donations to all client projects that where made using
the client donation form (but none of the other donation-sources).

Results are contained in a *data* attribute.


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
    <th align="left">facets</th>
    <td><code>client_reference:922ec9b-etc</code></td>
    <td>no</td>
<td>

You can search for a specific client_reference: <code>?facets=client_reference:54</code>

<br>
Example:
<a href="https://api.betterplace.org/en/api_v4/clients/karmic_minion/client_donations?facets=client_reference:54">
  <code>https://api.betterplace.org/en/api_v4/ clients/karmic_minion/ client_donations?facets=client_reference:54</code>
</a>

<br>
This feature is only used in some cases that relate to the
<a href="../donation_form/third_party_app_donation_form.md">ThirdPartyApp custom donation form for organisations</a>
and the <a href="client_donation_pledges.md">Client donation pledge endpoint</a>.


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
  "total_entries": 19040,
  "offset": 0,
  "total_pages": 6347,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "amount_in_cents": 200,
      "state": "confirmed",
      "token": "6766b8f76ada1c988521",
      "client_reference": null,
      "created_at": "2011-12-13T13:48:15+01:00",
      "receiver_type": "FundraisingEvent",
      "receiver_id": 8821,
      "receiver_title": "Stark fürs Leben - für die Zukunft unserer Kinder",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/8821.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/6766b8f76ada1c988521.json"
        },
        {
          "rel": "donor_contact_data",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/6766b8f76ada1c988521/donor_contact_data.json"
        }
      ]
    },
    {
      "amount_in_cents": 100,
      "state": "confirmed",
      "token": "706d6d8ac3dba9760e83",
      "client_reference": null,
      "created_at": "2012-05-23T16:41:06+02:00",
      "receiver_type": "FundraisingEvent",
      "receiver_id": 9866,
      "receiver_title": "Fab&amp;Vivien Nr. 3 | The third fundraising bet",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/9866.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/706d6d8ac3dba9760e83.json"
        },
        {
          "rel": "donor_contact_data",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/706d6d8ac3dba9760e83/donor_contact_data.json"
        }
      ]
    },
    {
      "amount_in_cents": 1000,
      "state": "confirmed",
      "token": "f8f85a0fe885bd0b8612",
      "client_reference": null,
      "created_at": "2012-06-12T16:53:03+02:00",
      "receiver_type": "FundraisingEvent",
      "receiver_id": 10987,
      "receiver_title": "Touchrugbyturnier",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/10987.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/f8f85a0fe885bd0b8612.json"
        },
        {
          "rel": "donor_contact_data",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/f8f85a0fe885bd0b8612/donor_contact_data.json"
        }
      ]
    }
  ]
}
```

