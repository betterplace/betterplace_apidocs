
# Client-project tags list

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/projects/4425/tags.json?order=projects_count%3ADESC
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all tags assigned by this client for this project.
Client project tags are a custom client feature and andministered
as a service of [betterplace solutions](http://www.betterplace-solutions.de/#buergerzeitung).

Results are contained in a *data* attribute.

To guarantee stable search results, all clients are required to specify an order with each
request as explained below.


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

The betterplace.org-internal client permalink

</td>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>4425</code></td>
    <td>yes</td>
<td>

Project id as an integer number ≥ 14.

</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>projects_count:DESC</code></td>
    <td>no</td>
<td>

Order the result set.
<br>
It is strongly recommended to <strong>specify an order</strong> with each request.
The default order might change at any time without notice.
A recommended order is
<code>projects_count:asc| slug:asc</code> (without the spaces).
<br>
<em>Supported orders are:</em>
<ul>
<li><code>slug:ASC/DESC</code> – tag name
<li><code>projects_count:ASC/DESC</code> - how many projects are using that client?
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


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
  "total_entries": 5,
  "offset": 0,
  "total_pages": 2,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "tag": "Trier",
      "slug": "Trier",
      "projects_count": 31,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/tags/Trier/projects.json"
        }
      ]
    },
    {
      "tag": "KinderJugendliche",
      "slug": "KinderJugendliche",
      "projects_count": 33,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/tags/KinderJugendliche/projects.json"
        }
      ]
    },
    {
      "tag": "Familien",
      "slug": "Familien",
      "projects_count": 10,
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

