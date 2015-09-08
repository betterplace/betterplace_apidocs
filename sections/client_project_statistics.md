
# Client Project Statistics

```Rebol
GET http://jop.betterplace.dev/de/api_v4/clients/volksfreund/project_statistics.json
```

**For [betterplace.org clients](../README.md#client-api) only:**
Some client-statistics for a betterplace.org client. All results are cached for 20 minutes.


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
      <td>How many cents are donated already to all client projects.
Calculation based on <code>open_amount_in_cents</code> and
<code>requested_amount_in_cents</code>.

It also includes external donations that project managers can add to projects.

Remember: This includes all donations to projects of this client even those
that are donated via betterplace.org or other channels.
</td>
    </tr>
    <tr>
      <th align="left">pool_balance_in_cents</th>
      <td>number</td>
      <td>100</td>
      <td>Clients may have a client-pool-fundraising-event that receives money
from offline-donations, or <a href="client_donation_pledges.md">api-donation-pledges</>
that could not be associated with a project.

The balance represents the donated amount in cents on the client-pool
that has not yet been forwarded to one of the client-projects.
</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td>number</td>
      <td>9900</td>
      <td>How many cents are still needed to complete all client projects.
This calculation is based on the sum of all
<a href="need_details.md">needs (open_amount_in_cents)</a>.
</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td>number</td>
      <td>11000</td>
      <td>How many cents are still needed to complete all client projects.
This calculation is based on the sum of all
<a href="need_details.md">needs (requested_amount_in_cents)</a>.
</td>
    </tr>
    <tr>
      <th align="left">projects_count</th>
      <td>number</td>
      <td>100</td>
      <td>The number of <a href="projects_list.md">projects</a> of this client.
</td>
    </tr>
    <tr>
      <th align="left">client_donated_amount_in_cents</th>
      <td>number</td>
      <td>8100</td>
      <td>How many cents are donated through the clients donation page.
</td>
    </tr>
    <tr>
      <th align="left">client_matched_amount_in_cents</th>
      <td>number</td>
      <td>2500</td>
      <td>How many cents are donated by matching donations by all matching funds of the client.
</td>
    </tr>
    <tr>
      <th align="left">client_donations_count</th>
      <td>number</td>
      <td>200</td>
      <td>The number of <a href="client_donations_list.md">client donations</a> for this client.
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
  "donated_amount_in_cents": 0,
  "pool_balance_in_cents": 0,
  "open_amount_in_cents": 0,
  "requested_amount_in_cents": 0,
  "projects_count": 0,
  "client_donated_amount_in_cents": 0,
  "client_matched_amount_in_cents": 0,
  "client_donations_count": 0,
  "links": [

  ]
}
```

