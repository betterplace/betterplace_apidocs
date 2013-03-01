Projects
===================================

How to fetch a list of projects
-------------------

```nginx
GET http://betterplace.dev/en/api_v4/projects.json?nelat=51.123&nelng=12.123&q=Skateistan&swlat=51.001&swlng=12.001
```

Retrieve the list of all projects as a JSON result set, that
contains the results in its *data* attribute.


### Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>q</th>
    <td><code>Skateistan</code></td>
    <td>optional</td>
    <td>Free text search for parameter *q* in projects</td>
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
  "total_entries": 2,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 1114,
      "name": "Skateistan Afghanistan",
      "latitude": "34.531617284782",
      "longitude": "69.13581752939456",
      "links": [
        {
          "rel": "self",
          "href": "http://www.betterplace.dev/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 6233,
      "name": "Skateistan Cambodia",
      "latitude": "11.55883121490479",
      "longitude": "104.9174423217773",
      "links": [
        {
          "rel": "self",
          "href": "http://www.betterplace.dev/en/api_v4/projects/6233.json"
        }
      ]
    }
  ],
  "format": "json"
}
```


How to get the details of a project
-------------------

```nginx
GET http://betterplace.dev/en/api_v4/projects/1114.json
```

Retrieve the details for one project as a single JSON object.


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
    <td><code>1114</code></td>
    <td>required</td>
    <td>Project-id as an integer number ≥ 1.</td>
  </tr>
</table>

### Example response

```json
{
  "created_at": "2009-03-10T10:12:16Z",
  "updated_at": "2013-01-14T12:21:19Z",
  "latitude": 34.531617284782,
  "longitude": 69.13581752939456,
  "city": "Kabul",
  "street": "Taimani, behind Qasemi Winhouse",
  "country": "Afghanistan",
  "zip": "",
  "id": 1114,
  "title": "Skateistan Afghanistan",
  "tax_deductible": true,
  "outstanding_amount_in_cents": 119369,
  "progress_percentage": 95,
  "description": "With 68% of Afghanistan’s population under the age of 25, Skateistan strongly believes that youth are the ones most capable of bringing about social change.\n\nSkateistan is an Afghan NGO which operates Afghanistan’s (and the world’s) first co-educational skateboarding school. The Skateistan school engages nearly 400 Kabul youth weekly through skateboarding, and provides them with new opportunities in cross-cultural interaction, education, and personal empowerment programs. \n\nThe students (ages 5-17) come from all of Afghanistan’s diverse ethnic and socioeconomic backgrounds, and include 40% female students, hundreds of streetworking children, and youth with disabilities. They develop skills in skateboarding, leadership, problem-solving, multimedia, and creative arts. The students themselves decide what they want to learn; we connect them with a safe space and opportunities for them to develop the skills that they consider important.\n\nFor Afghan girls Skateistan's programming is especially important as there are very few recreational opportunities for females. For example, it is not culturally acceptable for girls in Afghanistan to ride bicycles or play sports in public. \n\nSkateistan has been active in Kabul since 2007 - with our facility built in 2009 - and in that time we’ve seen that Afghan youth of all ethnicities, genders, and socioeconomic backgrounds love to skateboard. Skateistan brings them together, equipping young men and women to lead their communities toward social change and development.\n\nIn 2012 Skateistan will be opening its second Afghan facility in Mazar-e-Sharif, Northern Afghanistan. It will have space to teach up to 1000 youth weekly.\n\nOur program gives hundreds of oppressed youth a voice. Education and the opportunity for self-expression can break the cycles of poverty, illiteracy and exclusion, with sport paving the way.",
  "completed_need_count": 58,
  "incomplete_need_count": 1,
  "news_count": 50,
  "positive_opinions_with_donations_count": 307,
  "positive_opinions_without_donations_count": 16,
  "negative_opinions_count": 1,
  "number_of_all_unique_supporters": 247,
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
  "carrier": {
    "name": "Skateistan",
    "picture": {
      "links": [
        {
          "rel": "profile",
          "href": "http://www.betterplace.org/paperclip/000/279/873/profile_betterplace-logo.png"
        },
        {
          "rel": "thumb",
          "href": "http://www.betterplace.org/paperclip/000/279/873/thumb_betterplace-logo.png"
        }
      ]
    }
  },
  "picture": {
    "links": [
      {
        "rel": "profile",
        "href": "http://www.betterplace.org/paperclip/000/289/158/profile_girls-merza-sm.jpg"
      },
      {
        "rel": "thumb",
        "href": "http://www.betterplace.org/paperclip/000/289/158/thumb_girls-merza-sm.png"
      }
    ]
  },
  "links": [
    {
      "rel": "self",
      "href": "http://www.betterplace.dev/en/api_v4/projects/1114.json"
    },
    {
      "rel": "platform",
      "href": "http://www.betterplace.dev/en/projects/1114-skateistan-afghanistan"
    },
    {
      "rel": "opinions",
      "href": "http://www.betterplace.dev/en/api_v4/projects/1114/opinions.json"
    },
    {
      "rel": "news",
      "href": "http://www.betterplace.dev/en/api_v4/projects/1114/news.json"
    }
  ]
}
```

