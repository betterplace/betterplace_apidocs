Organisations
===================================


Organisation Details
-------------------

```nginx
GET http://betterplace.dev/en/api_v4/organisations/care.json
```

Retrieve the details for one organisation as a single JSON object.

### Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>slug</th>
    <td><code>volksfreund</code></td>
    <td>required</td>
    <td>Organisation-slug based on the internal betterplace.org client-table.</td>
  </tr>
</table>

### Output Paramter

<table>
  <tr>
    <th>Parameter</th>
    <th>Always/Sometimes</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>id</th>
    <td>Always</td>
    <td>Integer number of the organisation ≥ 14.</td>
  </tr>
  <tr>
    <th>slug</th>
    <td>Always</td>
    <td>Identifier for the API v4, fixed permalink on betterplace.org.</td>
  </tr>
  <tr>
    <th>name</th>
    <td>Always</td>
    <td>Name of the organisation, max ?? character.</td>
  </tr>
  <tr>
    <th>description</th>
    <td>Always</td>
    <td>Name of the organisation, max ?? character.</td>
  </tr>
  <tr>
    <th>created_at</th>
    <td>Always</td>
    <td>DateTime</td>
  </tr>
  <tr>
    <th>updated_at</th>
    <td>Always</td>
    <td>DateTime</td>
  </tr>
  <tr>
    <th>latitude</th>
    <td>Always</td>
    <td>Float</td>
  </tr>
  <tr>
    <th>longitude</th>
    <td>Always</td>
    <td>Float</td>
  </tr>
  <tr>
    <th>etc</th>
    <td>Always</td>
    <td>etc</td>
  </tr>
</table>

### Example response

```json
{
  "format": "json",
  "id": 1,
  "slug": "care",
  "name": "CARE Deutschland-Luxemburg e.V.",
  "description": "Supi klasse tolle Schueler quaelen, muhahar",
  "created_at": "2013-01-03T14:21:01Z",
  "updated_at": "2013-01-03T14:21:01Z",
  "latitude": 52.5094,
  "longitude": 13.4588,
  "city": "Berlin",
  "street": "Wühlischstr 27",
  "country": "Germany",
  "zip": "10245",
  "website_url": "http://www.lorem.com",
  "primary_language": "en",
  "tax_deductible": true,
  "image": {
    "description": "",
    "links": [
      {
        "rel": "thumb",
        "href": "http://www.betterplace.dev/uploads/organisations/…/….jpg"
      },
      {
        "rel": "medium",
        "href": "http://www.betterplace.dev/uploads/organisations/…/….jpg"
      }
    ]
  },
  "contact": {
    "name": "F. Meyn",
    "picture": {
      "links": [
        {
          "rel": "profile",
          "href": "http://www.betterplace.org/paperclip/000/269/654/profile_IMG_0381.jpg"
        },
        {
          "rel": "thumb",
          "href": "http://www.betterplace.org/paperclip/000/269/654/thumb_IMG_0381.png"
        }
      ]
    },
    "links": [
      {
        "rel": "profile",
        "href": "http://www.betterplace.dev/en/users/frauke_m3"
      }
    ]
  },
  "links": [
    {
      "rel": "projects",
      "active_count": 4,
      "completed_count": 2,
      "href": "http://www.betterplace.dev/en/api_v4/organisations/care/projects.json"
    },
    {
      "rel": "volunteering",
      "count": 19,
      "href": "http://www.betterplace.dev/en/api_v4/organisations/care/volunteering.json"
    },
    {
      "rel": "fundraising_events",
      "active_count": 4,
      "closed_count": 2,
      "href": "http://www.betterplace.dev/en/api_v3/???groups.json"
    },
    {
      "rel": "blogposts",
      "blogpost_count": 7,
      "payout_blogposts": 2,
      "href": "http://www.betterplace.dev/en/api_v4/organisations/care/blogposts.json"
    },
    {
      "rel": "self",
      "href": "http://www.betterplace.dev/en/api_v4/organisations/care.json"
    },
    {
      "rel": "platform",
      "href": "http://www.betterplace.org/de/organisations/care"
    }
  ]
}
```

