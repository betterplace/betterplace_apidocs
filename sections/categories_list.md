
# Project Categories List

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1/categories.json
```

A list of betterplace.org project categories.
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
    <th align="left">project_id</th>
    <td><code>1</code></td>
    <td>yes</td>
<td>

Project id as an integer number.

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
      <th align="left">id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">name</th>
      <td><code>string</code></td>
      <td><code>The category</code></td>
<td>

Name to be displayed for this category

</td>
    </tr>
    <tr>
      <th align="left">slug</th>
      <td><code>string</code></td>
      <td><code>category</code></td>
<td>

Slug for this category

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

platform

</th>
<td>

Permalink to betterplace.org discover category

</td>
    </tr>
</table>

## Response Example

```json
{
  "current_page": 1,
  "offset": 0,
  "per_page": 3,
  "total_entries": 1,
  "total_pages": 1,
  "data": [
    {
      "id": 1,
      "created_at": "2023-07-24T14:20:19+02:00",
      "updated_at": "2023-07-24T14:20:19+02:00",
      "name": "Highly interesting",
      "slug": null,
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/discover/1"
        }
      ]
    }
  ]
}
```

