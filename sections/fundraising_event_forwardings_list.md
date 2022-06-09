
# Fundraising Event Forwardings List

```Cirru
GET https://api.betterplace.org/de/api_v4/fundraising_events/19267/forwardings.json
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
<td>

Fundraising Event id as an integer number ≥ 1.

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
      <th align="left">forwarded_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the fundraising event has forwarded to this project.


</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code>Rescue the turtles</code></td>
<td>

The name of the receiving project

</td>
    </tr>
    <tr>
      <th align="left">project_id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

The ID of the receiving project

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

project

</th>
<td>

Link to the <a href="project_details.md">project</a> to which the money was forwarded.


</td>
    </tr>
    <tr>
<th align="left">

platform

</th>
<td>

Link to the project on betterplace.org. Can be blank if project is hidden.

</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 2,
  "offset": null,
  "total_pages": 1,
  "current_page": 1,
  "per_page": null,
  "data": [
    {
      "forwarded_amount_in_cents": 76900,
      "title": "Pro-A-kids e.V.-Hilfe für die Kinder Kongonis",
      "project_id": 358,
      "links": [
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/358.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/358-pro-a-kids-e-v-hilfe-fuer-die-kinder-kongonis"
        }
      ]
    },
    {
      "forwarded_amount_in_cents": 15702,
      "title": "Die Arche: Mittagstisch für bedürftige Kinder",
      "project_id": 7910,
      "links": [
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/7910.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/7910-die-arche-mittagstisch-fuer-beduerftige-kinder"
        }
      ]
    }
  ]
}
```

