
# Project Pictures List ⇄ [Details](project_picture_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/projects/1114/pictures.json
```

A list of pictures of a betterplace.org project (donate money).
Results are contained in a *data* attribute.

*Custom picture-sizes:* This API will only deliver the orginal image.
That is the largest image betterplace.org can provide.
Please use an image-transformation-service of your choice to resize this
image to your liking. Note howevers that some have non-url-save characters
that might break services like Sencha Source.

We are working on a better solution. Please contact us for more information.

In the meantime, the following links might help:

* [Sencha Source](http://docs.sencha.io/current/index.html#!/guide/src) provides a easy URL-based solution
* [adaptive-images.com](http://adaptive-images.com/) is a self-hosted solution
* [Google mod_pagespeed "image resizing"](https://developers.google.com/speed/docs/mod_pagespeed/filter-image-optimize)
  should also help – and give you more performance-goodies as well

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
  "total_entries": 35,
  "offset": 3,
  "total_pages": 12,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "id": 68085,
      "created_at": "2012-07-23T14:25:15+02:00",
      "updated_at": "2014-03-26T22:13:34+01:00",
      "description": "Kids practice to jump at Mekroyan Fountain, Kabul",
      "links": [
        {
          "rel": "image",
          "href": ""
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures/68085.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 68086,
      "created_at": "2012-07-23T14:30:13+02:00",
      "updated_at": "2014-03-26T22:13:36+01:00",
      "description": "Afghan Skate Instructor Merza showing his skills at an old Soviet swimming pool on Bibi Maru Hill, Kabul",
      "links": [
        {
          "rel": "image",
          "href": ""
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures/68086.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 31767,
      "created_at": "2012-07-23T14:45:29+02:00",
      "updated_at": "2014-03-13T04:10:36+01:00",
      "description": null,
      "links": [
        {
          "rel": "image",
          "href": ""
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures/31767.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    }
  ]
}
```

