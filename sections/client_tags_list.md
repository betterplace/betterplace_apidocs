
# Client tags list

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/ww-testclient/tags.json
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
    <td><code>ww-testclient</code></td>
    <td>yes</td>
<td>

The betterplace.org-internal client id

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
      <td><code>string</code></td>
      <td><code>"Education"</code></td>
<td>

The name of the tag. It is unique per client.


</td>
    </tr>
    <tr>
      <th align="left">slug</th>
      <td><code>string</code></td>
      <td><code>"education"</code></td>
<td>

The slug of the tag. It is unique per client and used to build urls.
It must not contain any non url-safe characters.


</td>
    </tr>
    <tr>
      <th align="left">projects_count</th>
      <td><code>number</code></td>
      <td><code>23</code></td>
<td>

The number of <a href="projects_list.md">projects</a>
that were tagged with this tag.


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

projects

</th>
<td>

Link to the <a href="client_tag_projects_list.md">client-tag projects list</a> – all projects that are tagged with given client-tag.


</td>
    </tr>
</table>

## Response Example

```json
{
  "current_page": 1,
  "offset": 0,
  "per_page": 2,
  "total_entries": 1,
  "total_pages": 1,
  "data": [
    {
      "tag": "client-tag-1",
      "slug": "client-tag-1",
      "projects_count": 0,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/ww-testclient/tags/client-tag-1/projects.json"
        }
      ]
    }
  ]
}
```

