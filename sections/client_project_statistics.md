
# Client Project Statistics

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/ww-testclient/project_statistics.json
```

**For [betterplace.org clients](../README.md#client-api) only:**
Some client statistics for a betterplace.org client. All results are cached for 20 minutes.


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
    <td><code>ww-testclient</code></td>
    <td>yes</td>
<td>

The betterplace.org-internal client permalink

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
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>10100</code></td>
<td>

How many cents are donated already through user donations or forwardings
to all client projects.

Remember: This includes all donations to projects of this client even those
that are donated via betterplace.org or other channels.


</td>
    </tr>
    <tr>
      <th align="left">external_donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>10100</code></td>
<td>

⚠️ DEPRECATED!
This value will be removed in the future.

How many cents are external donations, that means they were given directly
to the project on other, non-betterplace channels.


</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>11000</code></td>
<td>

How many cents were requested by all client projects in total.
This calculation is based on the sum of all
<a href="need_details.md">needs (requested_amount_in_cents)</a>.

Calculate the amount of cents that is still missing until all projects
are completed like this:
  `requested_amount_in_cents - donated_amount_in_cents - external_donated_amount_in_cents`


</td>
    </tr>
    <tr>
      <th align="left">projects_count</th>
      <td><code>number</code></td>
      <td><code>100</code></td>
<td>

The number of <a href="projects_list.md">projects</a> of this client.


</td>
    </tr>
    <tr>
      <th align="left">client_donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>8100</code></td>
<td>

How many cents are donated through the client's donation page and forwarded
from the clients donation pool or matching funds of this client.


</td>
    </tr>
    <tr>
      <th align="left">client_donations_count</th>
      <td><code>number</code></td>
      <td><code>200</code></td>
<td>

The number of <a href="client_donations_list.md">client donations</a> for this client.


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
  "external_donated_amount_in_cents": 0,
  "requested_amount_in_cents": 0,
  "projects_count": 0,
  "client_donated_amount_in_cents": 0,
  "client_donations_count": 0,
  "links": [

  ]
}
```

