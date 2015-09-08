
# Client-project tags list

```Rebol
GET http://jop.betterplace.dev/de/api_v4/clients/volksfreund/projects/4425/tags.json?order=projects_count%3ADESC
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all tags assigned by this client for this project.
Client project tags are a custom client feature and andministered
as a service of [betterplace solutions](http://www.betterplace-solutions.de/#buergerzeitung).

Results are contains in a *data* attribute.


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
  <tr>
    <th align="left">project_id</th>
    <td><code>4425</code></td>
    <td>yes</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>projects_count:DESC</code></td>
    <td>no</td>
    <td>Order the result by
<code>slug</code> (tag name) or <code>projects_count</code>.
Use the optional <code>ASC</code> (default) or <code>DESC</code> to
change the order of the results. <a
href="../README.md#request-parameter-format">Learn how to format the
parameter</a>.
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
  "total_entries": 5,
  "offset": 0,
  "total_pages": 2,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "tag": "Trier",
      "projects_count": 209,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/tags/Trier/projects.json"
        }
      ]
    },
    {
      "tag": "KinderJugendliche",
      "projects_count": 216,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/tags/KinderJugendliche/projects.json"
        }
      ]
    },
    {
      "tag": "Familien",
      "projects_count": 108,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/tags/Familien/projects.json"
        }
      ]
    }
  ]
}
```

