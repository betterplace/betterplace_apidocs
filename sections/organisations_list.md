
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
  "total_entries": 2,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 2262,
      "created_at": "2009-11-02T16:12:49+01:00",
      "updated_at": "2018-11-07T09:18:16+01:00",
      "latitude": 50.91569900512695,
      "longitude": 6.94116020202637,
      "street": "Stettiner Straße 82",
      "zip": "50969",
      "city": "Köln",
      "country": "Deutschland",
      "content_updated_at": "2018-06-29T09:01:05+02:00",
      "slug": "unicef",
      "name": "UNICEF",
      "description": "UNICEF, das Kinderhilfswerk der Vereinten Nationen, arbeitet weltweit mit Programmen in rund 150 Ländern. UNICEF hilft, dass das Recht jedes Kindes auf Überleben, Bildung und Schutz Wirklichkeit wird: mit konkreten Projekten, umfassenden Programmen und politischer Lobbyarbeit. UNICEF ist in jedem Land seit vielen Jahren vor Ort und hat ein dichtes Netzwerk lokaler Partner. So ist nachhaltige und effiziente Hilfe möglich. Mit dem jährlichen Geschäftsbericht informiert UNICEF ausführlich über Arbeitsweise, Strukturen und Kosten. Sie finden ihn unter www.unicef.de",
      "tax_deductible": true,
      "contact": {
        "id": 20505,
        "name": "Jana Schuhmacher (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/020/505/fill_100x100_bp1628225975_UNICEF_Logo.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/020/505/crop_original_bp1628225975_UNICEF_Logo.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/20505"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/20505/contact_data.json"
          }
        ]
      },
      "picture": {
        "links": [
          {
            "rel": "fill_100x100",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/002/262/fill_100x100_bp1530255665_UNICEF_fuerjedesKind_Cyan_Vertical_RGB.jpg"
          },
          {
            "rel": "fill_200x200",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/002/262/fill_200x200_bp1530255665_UNICEF_fuerjedesKind_Cyan_Vertical_RGB.jpg"
          },
          {
            "rel": "fill_400x400",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/002/262/fill_400x400_bp1530255665_UNICEF_fuerjedesKind_Cyan_Vertical_RGB.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/002/262/crop_original_bp1530255665_UNICEF_fuerjedesKind_Cyan_Vertical_RGB.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/organisations/2262.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/organisations/2262-unicef"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/organisations/2262/projects.json"
        },
        {
          "rel": "website",
          "href": "http://www.unicef.de"
        }
      ]
    },
    {
      "id": 125,
      "created_at": "2008-02-06T17:10:42+01:00",
      "updated_at": "2022-02-11T00:01:12+01:00",
      "latitude": 53.55759811401367,
      "longitude": 9.96815967559815,
      "street": "Mühlgasse 175",
      "zip": "20357",
      "city": "Hamburg",
      "country": "Deutschland",
      "content_updated_at": "2020-04-09T18:24:12+02:00",
      "slug": "vivaconagua",
      "name": "Viva con Agua de Sankt Pauli e.V.",
      "description": "Viva con Agua aktiviert und inspiriert - für eine Welt ohne Durst!<br><br>Viva con Agua ist ein internationales Netzwerk von Menschen und Organisationen, das sich für den sicheren Zugang zu sauberem Trinkwasser und sanitärer Grundversorgung einsetzt. <br>2006 wurde der gemeinnützige Verein Viva con Agua de Sankt Pauli ins Leben gerufen. <br>Inzwischen unterstützen die Vision „WASSER FÜR ALLE – ALLE FÜR WASSER“ mehr als 15.000 ehrenamtliche Supporter, die mit zahlreichen Aktionen und ebenso viel Spaß Spenden für WASH-Projekte weltweit sammeln – darunter viele Künstler und Musiker. <br>Gemeinsam seinen internationalen und lokalen Partnerorganisationen konnte die Bewegung so bereits über drei Millionen Menschen in WASH-Projekten (WAter, Sanitation, Hygiene) erreichen.<br><br>Neben dem Hamburger Verein zählen mittlerweile die Viva con Agua Stiftung und lokal aktive Organisationen in Uganda, Österreich, den Niederlanden, der Schweiz und neuerdings in Südafrika und Kalifornien zum international tätigen Netzwerk. Darüber hinaus unterstützen die ausgegründeten Social Business Unternehmen Viva con Agua Wasser GmbH, Viva con Agua ARTS gGmbH und Goldeimer gGmbH mit ihren Aktivitäten die Trinkwasser- und Sanitärprojekte von VcA.<br><br>WASSER FÜR ALLE - ALLE FÜR WASSER!",
      "tax_deductible": true,
      "contact": {
        "id": 561728,
        "name": "Lucas\tMason\tAlexander Köhler (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/561/728/fill_100x100_bp1587649479_VCA_Tropfen.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/561/728/crop_original_bp1587649479_VCA_Tropfen.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/561728"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/561728/contact_data.json"
          }
        ]
      },
      "picture": {
        "links": [
          {
            "rel": "fill_100x100",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/000/125/fill_100x100_VcA_Projektlogo.jpg"
          },
          {
            "rel": "fill_200x200",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/000/125/fill_200x200_VcA_Projektlogo.jpg"
          },
          {
            "rel": "fill_400x400",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/000/125/fill_400x400_VcA_Projektlogo.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/000/125/crop_original_VcA_Projektlogo.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/organisations/125.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/organisations/125-viva-con-agua-de-sankt-pauli-e-v"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/organisations/125/projects.json"
        },
        {
          "rel": "website",
          "href": "http://www.vivaconagua.org"
        }
      ]
    }
  ]
}
```

