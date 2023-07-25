
# Organisations List ⇄ [Details](organisation_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/organisations.json
```

A list of betterplace.org organisations.
Results are contained in a *data* attribute.
The details and list view show the same data per organisation.

**For [betterplace.org clients](../README.md#client-api):**
This resource is not available at the moment.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
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
      <th align="left">latitude</th>
      <td><code>number</code></td>
      <td><code>52.499007</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td><code>number</code></td>
      <td><code>13.44947</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
      <th align="left">street</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Schlesische Straße 26"</code></td>
<td>

Street address

</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td><code>null &#124; string</code></td>
      <td><code>"10997"</code></td>
<td>

ZIP code

</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Berlin"</code></td>
<td>

Name of the city

</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Deutschland"</code></td>
<td>

Name of the country

</td>
    </tr>
    <tr>
      <th align="left">content_updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">slug</th>
      <td><code>string</code></td>
      <td><code>vivaconagua</code></td>
<td>

<a href="http://en.wikipedia.org/wiki/Clean_URL#Slug">URL slug</a>
for the permalink


</td>
    </tr>
    <tr>
      <th align="left">name</th>
      <td><code>string</code></td>
      <td><code>"Viva con Agua de Sankt Pauli e.V."</code></td>
<td>

Name of the organisation

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

A description of the organisation.
This may contain <code>br</code> tags.


</td>
    </tr>
    <tr>
      <th align="left">tax_deductible</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

⚠️ DEPRECATED!

This value is deprecated and will be removed.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td><code>object</code></td>
      <td><code></code></td>
<td>

The public contact person for this organisation.

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="picture-ref" href="#picture">
            ↓picture
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code></code></td>
<td>

TODO

</td>
    </tr>
  </table>

### <a id="contact" href="#contact-ref">↑Nested Attributes: contact</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">contact.name</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Till B."</code></td>
<td>

Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".

In the case of donation-opinions the name might also be
empty/null for anonymous donations for anonymous donations.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
<td>

User profile picture or a fallback image

</td>
    </tr>
  </table>

### <a id="contact.picture" href="#contact.picture-ref">↑Nested Attributes: contact.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

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

self

</th>
<td>

Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)


</td>
    </tr>
    <tr>
<th align="left">

platform

</th>
<td>

Permalink to betterplace.org

</td>
    </tr>
    <tr>
<th align="left">

projects

</th>
<td>

Link to the <a href="projects_list.md">project list</a> of this organisation


</td>
    </tr>
    <tr>
<th align="left">

website

</th>
<td>

Link to the website of this organisation.

</td>
    </tr>
    <tr>
<th align="left">

contact.platform

</th>
<td>

The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.


</td>
    </tr>
    <tr>
<th align="left">

contact.contact_data

</th>
<td>

The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.


</td>
    </tr>
    <tr>
<th align="left">

contact.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

contact.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

picture.fill_200x200

</th>
<td>

200×200 Pixel

</td>
    </tr>
    <tr>
<th align="left">

picture.fill_400x400

</th>
<td>

400×400 Pixel

</td>
    </tr>
    <tr>
<th align="left">

picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

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
      "id": 1,
      "created_at": "2023-07-24T14:20:20+02:00",
      "updated_at": "2023-07-24T14:20:20+02:00",
      "latitude": 52.51349039999999,
      "longitude": 13.4626687,
      "street": "Mainzer Straße 20",
      "zip": "10247",
      "city": "Berlin",
      "country": "Deutschland",
      "content_updated_at": "2023-07-24T14:20:20+02:00",
      "slug": "permalink1",
      "name": "Organisation #1",
      "description": "not a blank description",
      "tax_deductible": true,
      "contact": {
        "id": 1,
        "name": "u. X",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/1"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/1/contact_data.json"
          }
        ]
      },
      "picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_100x100",
            "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.jpg"
          },
          {
            "rel": "fill_200x200",
            "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_200x200_default.jpg"
          },
          {
            "rel": "fill_400x400",
            "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_400x400_default.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/crop_original_default.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/organisations/1.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/organisations/1-organisation-1"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/organisations/1/projects.json"
        },
        {
          "rel": "website",
          "href": ""
        }
      ]
    }
  ]
}
```

