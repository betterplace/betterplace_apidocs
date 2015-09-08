
# Fundraising Event Forwardings List

```Rebol
GET http://jop.betterplace.dev/de/api_v4/fundraising_events/19267/forwardings.json
```

A list of forwarings from the fundraising event to its projects.

**This is an experimental feature and is still under heavy development. Please use it with caution.**


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">fundraising_event_id</th>
    <td><code>19267</code></td>
    <td>yes</td>
    <td>Fundraising-Event-id as an integer number ≥ 1.</td>
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
      <th align="left">forwarded_amount_in_cents</th>
      <td>number</td>
      <td>12300</td>
      <td>The amount in cents the fundraising event has forwarded to this project.
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
      <th align="left">project</th>
      <td>Link to the <a href="project_details.md">project</a> to which the money was forwarded.
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 1,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 30,
  "data": [
    {
      "forwarded_amount_in_cents": 123,
      "links": [
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    }
  ]
}
```

