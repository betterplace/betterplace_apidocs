
# Project Categories List

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1114/categories.json
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
    <td><code>1114</code></td>
    <td>yes</td>
<td>

Project id as an integer number ≥ 14.

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
  "total_entries": 3,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 3,
      "created_at": "2016-12-13T16:18:14+01:00",
      "updated_at": "2018-12-03T17:26:13+01:00",
      "name": "Bildung",
      "slug": "bildung",
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/discover-projects/3-bildung"
        }
      ]
    },
    {
      "id": 15,
      "created_at": "2016-12-13T17:07:22+01:00",
      "updated_at": "2018-03-02T12:21:51+01:00",
      "name": "Sport",
      "slug": "sport",
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/discover-projects/15-sport"
        }
      ]
    },
    {
      "id": 2,
      "created_at": "2016-12-13T16:17:58+01:00",
      "updated_at": "2019-08-23T15:43:38+02:00",
      "name": "Kinder und Jugend",
      "slug": "kinder",
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/discover-projects/2-kinder"
        }
      ]
    }
  ]
}
```

