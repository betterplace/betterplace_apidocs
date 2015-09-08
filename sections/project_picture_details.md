
# Project Picture Details ⇄ [List](project_pictures_list.md)

```Rebol
GET http://jop.betterplace.dev/de/api_v4/projects/1114/pictures/286505.json
```

The details of a betterplace.org project picture.
The details and list view show the same data.

*Custom picture-sizes:* [Please read more!](project_picture_list.md)

**For [betterplace.org clients](../README.md#client-api):**
If you request data for a project that is not part of the client
projects, the API will return a `404` HTTP code.


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
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>286505</code></td>
    <td>yes</td>
    <td>Picture-id as an integer number ≥ 1.</td>
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
      <td>number</td>
      <td>1</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>Yada…</td>
      <td>Description of the picture</td>
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
      <th align="left">image</th>
      <td>Link to the original image as uploaded by the user</td>
    </tr>
    <tr>
      <th align="left">self</th>
      <td>The single resource for this picture</td>
    </tr>
    <tr>
      <th align="left">parent</th>
      <td>The parent object of this picture.</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 31766,
  "created_at": "2012-07-23T13:45:15+02:00",
  "updated_at": "2014-03-13T04:10:27+01:00",
  "description": "Young Afghan Skate Instructor Fazilla sitting on her board at Mekroyan Fountain",
  "links": [
    {
      "rel": "image",
      "href": ""
    },
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures/31766.json"
    },
    {
      "rel": "parent",
      "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
    }
  ]
}
```

