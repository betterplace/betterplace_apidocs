
# Client Fundraising Event Statistics

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/fundraising_event_statistics.json
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
      <td>How many cents are donated already to all fundraising events of this client.

It does not include the money of the client-pool-fundraising-event.

Remember: This includes all donations to fundraising events of this client even those
that are donated via betterplace.org or other channels.
</td>
    </tr>
    <tr>
      <th align="left">fundraising_events_count</th>
      <td>number</td>
      <td>100</td>
      <td>The number of <a href="fundraising_events_list.md">fundraising events</a> of this client.

Blocked fundraising events are excluded from this count and from the API in general.
</td>
    </tr>
    <tr>
      <th align="left">client_donated_amount_in_cents</th>
      <td>number</td>
      <td>8100</td>
      <td>How many cents are donated through the clients donation page to
all fundraising events (those that are active, closed, blocked and so on).

The client-pool-fundraising-event is ignored.
</td>
    </tr>
    <tr>
      <th align="left">client_donations_count</th>
      <td>number</td>
      <td>200</td>
      <td>The number of <a href="client_donations_list.md">client donations</a> for this client to
all fundraising events (those that are active, closed, blocked and so on).

The client-pool-fundraising-event is ignored.
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
  "fundraising_events_count": 0,
  "client_donated_amount_in_cents": 0,
  "client_donations_count": 0,
  "links": [

  ]
}
```

