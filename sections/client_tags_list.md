
# Client tags list

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/tags.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all tags defined for a client.

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
    <td>The betterplace.org-internal client id</td>
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
      <th align="left">tag</th>
      <td>string</td>
      <td>"Education"</td>
      <td>The name of the tag, that is unique per client.
</td>
    </tr>
    <tr>
      <th align="left">projects_count</th>
      <td>number</td>
      <td>23</td>
      <td>The number of <a href="projects_list.md">projects</a>
that where tagged with this tag.
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
      <td>Link to the <a href="projects_list.md">project list</a> of all projects that are tagged with this tag for the current client.
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 13,
  "offset": 0,
  "total_pages": 7,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "tag": "Bedürftige",
      "projects_count": 17,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/heidenheim/tags/Bed%C3%BCrftige/projects.json"
        }
      ]
    },
    {
      "tag": "Behinderte",
      "projects_count": 20,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/heidenheim/tags/Behinderte/projects.json"
        }
      ]
    }
  ]
}
```

