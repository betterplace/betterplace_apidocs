Volunteering
===================================

Volunteering List
-------------------

```nginx
GET http://betterplace.dev/en/api_v4/volunteering.json?nelat=51.123&nelng=12.123&swlat=51.001&swlng=12.001
```

Retrieve a list of all volunteering as a JSON result set,
that contains the results in its *data* attribute.


### Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>nelat</th>
    <td><code>51.123</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The northeast corner's latitude.</td>
  </tr>
  <tr>
    <th>nelng</th>
    <td><code>12.123</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The northeast corner's longitude.</td>
  </tr>
  <tr>
    <th>swlat</th>
    <td><code>51.001</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The southwest corner's latitude.</td>
  </tr>
  <tr>
    <th>swlng</th>
    <td><code>12.001</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The southwest corner's longitude.</td>
  </tr>
</table>

### Example response

```json
{
  "total_entries": 2965,
  "offset": 3,
  "total_pages": 989,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "id": 9071,
      "title": "joe betterplace",
      "latitude": 50.0631,
      "longitude": 8.24334,
      "links": [
        {
          "rel": "self",
          "href": "http://www.betterplace.dev/en/api_v4/volunteering/9071.json"
        }
      ]
    },
    {
      "id": 11969,
      "title": "Hello world",
      "latitude": 52.4979,
      "longitude": 13.448,
      "links": [
        {
          "rel": "self",
          "href": "http://www.betterplace.dev/en/api_v4/volunteering/11969.json"
        }
      ]
    },
    {
      "id": 17682,
      "title": "Das ist ein verdammt langer Titel, der auf jeden Fall umgebrochen",
      "latitude": 52.469,
      "longitude": 13.5532,
      "links": [
        {
          "rel": "self",
          "href": "http://www.betterplace.dev/en/api_v4/volunteering/17682.json"
        }
      ]
    }
  ],
  "format": "json"
}
```


Volunteering Details
-------------------

```nginx
GET http://betterplace.dev/en/api_v4/volunteering/23.json
```

Retrieve the details for one volunteering offer as a single JSON object.

### Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>id</th>
    <td><code>23</code></td>
    <td>required</td>
    <td>Volunteering-id as an integer number ≥ 1.</td>
  </tr>
</table>

### Example response

```json
{
  "format": "json",
  "created_at": "2013-01-03T14:21:01Z",
  "updated_at": "2013-01-03T14:21:01Z",
  "latitude": 52.5094,
  "longitude": 13.4588,
  "city": "Berlin",
  "street": "Wühlischstr 27",
  "country": "Germany",
  "zip": "10245",
  "id": 1,
  "title": "Hausaufgaben ausdenken",
  "description": "Supi klasse tolle Schueler quaelen, muhahar",
  "carrier": {
    "name": "CARE Deutschland-Luxemburg e.V.",
    "links": [
      {
        "rel": "logo",
        "href": "http://www.betterplace.org/paperclip/000/222/445/thumb_CARE_Logo_4C_Rand.png"
      }
    ]
  },
  "vacancies": 5,
  "image": {
    "description": "",
    "links": [
      {
        "rel": "thumb",
        "href": "http://www.betterplace.dev/uploads/bettertime/job_description_image/handle/4/thumb__T2eC16Z___QE9s3HFhL_BQLlglg1wg__48_72.jpeg"
      },
      {
        "rel": "medium",
        "href": "http://www.betterplace.dev/uploads/bettertime/job_description_image/handle/4/medium__T2eC16Z___QE9s3HFhL_BQLlglg1wg__48_72.jpeg"
      }
    ]
  },
  "contact": {
    "name": "Johannes Opper",
    "phone": "",
    "email": "jop@betterplace.org"
  },
  "topics": [
    "Development cooperation ",
    "Children & youth",
    " Culture & sports"
  ],
  "activities": [
    "consulting/coaching",
    "office work",
    "writing/translating",
    "tutoring/reading"
  ],
  "links": [
    {
      "rel": "self",
      "href": "http://www.betterplace.dev/en/api_v4/volunteering/1.json"
    }
  ]
}
```

