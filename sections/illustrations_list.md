
# Illustrations List

```Cirru
GET https://api.betterplace.org/de/api_v4/illustrations.json?facets=project_id%3A10377&order=amount_in_cents%3Adesc
```

A list of betterplace.org project illustrations.
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
    <th align="left">facets</th>
    <td><code>project_id:10377</code></td>
    <td>no</td>
<td>

Filter the result set.
<br>
It is strongly recommended to <strong>specify facets</strong> with each request.
<br>
<em>Supported filters are:</em>
<ul>
<li><code>project_id:10377</code>
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>amount_in_cents:desc</code></td>
    <td>no</td>
<td>

Order the result set.
<br>
It is strongly recommended to <strong>specify an order</strong> with each request.
The default order might change at any time without notice.
<br>
<em>Supported orders are:</em>
<ul>
<li><code>amount_in_cents:asc/desc</code></li>
<li><code>project_id:asc/desc</code></li>
<li><code>created_at:asc/desc</code> and <code>updated_at:ASC/DESC</code>
<li><code>id:asc/desc</code>
</ul>
It is possible to set multiple order parameters.
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
      <th align="left">amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>666</code></td>
<td>

Suggested amount to donate in cents

</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code>Little cheetah kittens need your help</code></td>
<td>

Title of the illustration

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code>The kittens really do need your help, don't hesitate…</code></td>
<td>

More detailed description of the illustration

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="picture-ref" href="#picture">
            ↓picture
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>See below.</code></td>
<td>

Picture to be displayed in the illustration

</td>
    </tr>
  </table>

### <a id="picture" href="#picture-ref">↑Nested Attributes: picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

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

new_donation

</th>
<td>

Link to where a new donation can be made

</td>
    </tr>
    <tr>
<th align="left">

project

</th>
<td>

Link to the project this illustration belongs to
(<a href="project_details.md">project details</a>)


</td>
    </tr>
    <tr>
<th align="left">

picture.fill_410x214

</th>
<td>

Illustration picture with 410×214 Pixel

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
      "id": 2,
      "created_at": "2018-08-28T13:55:58+02:00",
      "updated_at": "2019-01-31T09:27:24+01:00",
      "amount_in_cents": 10000,
      "title": "Trinkwasser ",
      "description": "Bereits mit \"BETRAG\" können wir Wasser-Pumpen erwerben und mehrere syrische Familien mit Trinkwasser versorgen und darüber hinaus die hygienischen Bedingungen verbessern. ",
      "picture": {
        "links": [
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/illustration/picture/000/000/002/fill_410x214_bp1545132708_jordanien-fluechtlinge-kinder_068_160530.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "new_donation",
          "href": "https://api.betterplace.org/de/projects/10377-syrien-hilfe-fur-kinder/donations/new?donation_amount=100&donation_illustration_id=2"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/10377.json"
        }
      ]
    },
    {
      "id": 1,
      "created_at": "2018-08-28T13:49:16+02:00",
      "updated_at": "2019-01-31T09:27:12+01:00",
      "amount_in_cents": 2000,
      "title": "Nahrungsmittel ",
      "description": "Bereits mit BETRAG können wir ein Kind in Syrien einen Monat lang mit Nahrung unterstützen.",
      "picture": {
        "links": [
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/illustration/picture/000/000/001/fill_410x214_bp1545132551_jordanien-fluechtlinge-kinder_013_160530.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "new_donation",
          "href": "https://api.betterplace.org/de/projects/10377-syrien-hilfe-fur-kinder/donations/new?donation_amount=20&donation_illustration_id=1"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/10377.json"
        }
      ]
    },
    {
      "id": 1113,
      "created_at": "2019-01-31T09:26:24+01:00",
      "updated_at": "2019-01-31T09:26:24+01:00",
      "amount_in_cents": 1600,
      "title": "Hygiene-Artikel",
      "description": "Bereits \"BETRAG\" reichen aus, um eine syrische Familie in einem Flüchtlingslager mit Hygiene-Produkten wie Seife, Windeln, Handtüchern und Binden zu versorgen.  ",
      "picture": {
        "links": [
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/illustration/picture/000/001/113/fill_410x214_bp1548923184_syrien-fluechtlinge__1901_21.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "new_donation",
          "href": "https://api.betterplace.org/de/projects/10377-syrien-hilfe-fur-kinder/donations/new?donation_amount=16&donation_illustration_id=1113"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/10377.json"
        }
      ]
    }
  ]
}
```

