
# Client Details

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/volksfreund.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

All statistic values are DEPRECATED here and will be removed after 31.5.2015.

Please find the new values in
[**Client** Project Statistics](client_project_statistics.md) and
[**Client** Fundraising Event Statistics](client_fundraising_event_statistics.md).


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>volksfreund</code></td>
    <td>yes</td>
    <td>The betterplace.org-internal client permalink</td>
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
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>10100</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

How many cents are donated already to all client projects. 
Calculation based on open_amount_in_cents and requested_amount_in_cents.

Therefore it includes the money of the client-pool-fundraising-event
that still has to be forwarded to one of the client-projects-needs.
It also includes external donations that project manager can add to projects.

Remember: This includes all donations to projects of this client even those
that are donated via betterplace.org or other channels.
</td>
    </tr>
    <tr>
      <th align="left">pool_balance_in_cents</th>
      <td>number</td>
      <td>100</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

Clients may have a client-pool-fundraising-event that receives money
from offline-donations that could not be associated with a project or
similar use cases.

The balance repesents the donated amount in cents on the pool
that has not yet been forwarded to one of the client-project-needs.

This is the number that is include in open_amount_in_cents and donated_amount_in_cents.
</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td>number</td>
      <td>9900</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

How many cents are still needed to complete all client projects.
This calculation is based on the sum of all
<a href="need_details.md">needs (open_amount_in_cents)</a>.
We also substract the money of the client-pool-fundraising-event
that still has to be forwarded to one of the client-projects-needs.
</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td>number</td>
      <td>11000</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

How many cents are still needed to complete all client projects.
This calculation is based on the sum of all
<a href="need_details.md">needs (requested_amount_in_cents)</a>.
</td>
    </tr>
    <tr>
      <th align="left">projects_count</th>
      <td>number</td>
      <td>100</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

The number of <a href="projects_list.md">projects</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">client_donated_amount_in_cents</th>
      <td>number</td>
      <td>8100</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

How many cents are donated through the clients donation page.
</td>
    </tr>
    <tr>
      <th align="left">client_matched_amount_in_cents</th>
      <td>number</td>
      <td>2500</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

How many cents are donated by matching donations by all matching funds of the client
</td>
    </tr>
    <tr>
      <th align="left">client_donations_count</th>
      <td>number</td>
      <td>200</td>
      <td>DEPRECATED and will be removed after 31.5.2015.

The number of <a href="client_donations_list.md">client donations</a> for this client
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
      <th align="left">projects</th>
      <td>Link to the <a href="projects_list.md">project list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">client_donations</th>
      <td>Link to the <a href="client_donations_list.md">client donations list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">client_project_tags</th>
      <td>Link to the <a href="client_tags_list.md">tags list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">client_fundraising_events</th>
      <td>Link to the <a href="fundraising_events_list.md">fundraising events list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">opinions</th>
      <td>Link to the <a href="opinions_list.md">opinions list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">project_mailing_subscriptions</th>
      <td>Link to the templated <a href="client_mailing_subscriptions.md">client mailing subscriptions</a>
of this client. Replace <code>{project_id}</code> with the ID of a project that is
part of you client projects list.
</td>
    </tr>
    <tr>
      <th align="left">project_statistics</th>
      <td>Link to the <a href="project_statistics_list.md">project statistics</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">fundraising_event_statistics</th>
      <td>Link to the <a href="fundraising_event_statistics_list.md">fundraising event statistics</a> of this client
</td>
    </tr>
</table>

## Response Example

```json
{
  "donated_amount_in_cents": 143535560,
  "pool_balance_in_cents": 8341137,
  "open_amount_in_cents": 22341785,
  "requested_amount_in_cents": 165877345,
  "projects_count": 0,
  "client_donated_amount_in_cents": 107270688,
  "client_matched_amount_in_cents": 0,
  "client_donations_count": 11482,
  "links": [
    {
      "rel": "projects",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/projects.json"
    },
    {
      "rel": "client_donations",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations.json"
    },
    {
      "rel": "client_project_tags",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/tags.json"
    },
    {
      "rel": "client_fundraising_events",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/fundraising-events.json"
    },
    {
      "rel": "opinions",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/opinions.json"
    },
    {
      "rel": "project_mailing_subscriptions",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/projects/%7Bproject_id%7D/mailing_subscriptions.json",
      "templated": true
    },
    {
      "rel": "project_statistics",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/project_statistics.json"
    },
    {
      "rel": "fundraising_event_statistics",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/fundraising_event_statistics.json"
    }
  ]
}
```

