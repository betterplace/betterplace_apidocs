
# Organisation Details ⇄ [List](organisations_list.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/organisations/125.json
```

The details of a betterplace.org organisation.
The details and list view show the same data per organisation.

**For [betterplace.org clients](../README.md#client-api):**
There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>125</code></td>
    <td>yes</td>
    <td>Organisation-id as an integer number ≥ 14.</td>
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
      <th align="left">latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">street</th>
      <td>null &#124; string</td>
      <td>"Schlesische Straße 26"</td>
      <td>Street address</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td>null &#124; string</td>
      <td>"10997"</td>
      <td>ZIP code</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td>null &#124; string</td>
      <td>"Berlin"</td>
      <td>Name of the city</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td>null &#124; string</td>
      <td>"Deutschland"</td>
      <td>Name of the country</td>
    </tr>
    <tr>
      <th align="left">slug</th>
      <td>string</td>
      <td>vivaconagua</td>
      <td><a href="http://en.wikipedia.org/wiki/Clean_URL#Slug">URL slug</a>
for the permalink
</td>
    </tr>
    <tr>
      <th align="left">name</th>
      <td>string</td>
      <td>"Viva con Agua de Sankt Pauli e.V."</td>
      <td>Name of the organisation</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th align="left">tax_deductible</th>
      <td>boolean</td>
      <td>true</td>
      <td>True if the organisation is a tax-exempt charity.
If so, Users can request a tax-receipt for donations to that organisation.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td></td>
      <td>The public contact person for this organisation.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="picture-ref" href="#picture">
            ↓picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
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
      <th align="left">contact.name</th>
      <td>null &#124; string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
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
      <td>string</td>
      <td>//asset1.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</td>
      <td>User profile picture or a fallback image</td>
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
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">projects</th>
      <td>Link to the <a href="projects_list.md">project list</a> of this organisation
</td>
    </tr>
    <tr>
      <th align="left">website</th>
      <td>Link to the website of this organisation.</td>
    </tr>
    <tr>
      <th align="left">contact.platform</th>
      <td>The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.
</td>
    </tr>
    <tr>
      <th align="left">contact.contact_data</th>
      <td>The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">contact.picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">contact.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
    <tr>
      <th align="left">picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">picture.fill_200x200</th>
      <td>200×200 Pixel</td>
    </tr>
    <tr>
      <th align="left">picture.fill_400x400</th>
      <td>400×400 Pixel</td>
    </tr>
    <tr>
      <th align="left">picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 125,
  "created_at": "2008-02-06T17:10:42+01:00",
  "updated_at": "2015-06-24T08:40:27+02:00",
  "latitude": 53.55759811401367,
  "longitude": 9.96815967559815,
  "street": "Neuer Kamp 32",
  "zip": "20357",
  "city": "Hamburg",
  "country": "Deutschland",
  "slug": "vivaconagua",
  "name": "Viva con Agua de Sankt Pauli e.V.",
  "description": "Die Organisation Viva con Agua:\r\n\r\nViva con Agua de Sankt Pauli e.V. ist eine international tätige Wasserinitiative und wird vom FC St. Pauli ideell unterstützt. Initiator Benjamin Adrion, ehemaliger Mittelfeldspieler des Fußballclubs, gründete 2005 nach einem Trainingslager auf Kuba den gemeinnützigen Verein. \r\n\r\nZiel der Initiative ist es, die Versorgung mit sauberem Trinkwasser und sanitären Anlagen in Entwicklungsländern nachhaltig zu verbessern. Viva con Agua ist Projektpartner der Welthungerhilfe.\r\n\r\n21 Projekte in 15 Projektländern hat Viva con Agua bereits in Zusammenarbeit mit der Welthungerhilfe realisiert und damit über 300.000 Menschen Zugang zu sauberem Trinkwasser ermöglicht. Des Weiteren haben mehr als 100.000 Schüler und Studenten im deutschsprachigen Raum VcA-Bildungsworkshops, Seminare und Spendenläufe mitgemacht.\r\n\r\nAuszeichnungen:\r\n\r\nISPO Award 2013\r\nHAMMA Award 2012\r\nUtopia Award 2012\r\nB.A.U.M.-Umweltpreis 2011\r\nWerkstatt N-Projekt 2010\r\nBundesverdienstkreuz 2009\r\nUtopia Award 2008\r\nAusgewählter Ort im Land der Ideen 2007 (Schirmherrschaft Bundespräsident Horst Köhler)\r\nBundessieger start social 2007 (Schirmherrschaft Bundeskanzlerin Angela Merkel)\r\ntaz-Panter-Preis 2006 \r\n\r\n\r\nAktivitäten und Initiativen\r\n\r\nViva con Agua veranstaltet laufend Konzerte, Partys, Sport- und Kulturevents, deren Erlöse als Spende in Trinkwasserprojekte fließen.\r\n\r\nSchärfung des Bewusstseins, besonders bei jungen Menschen in Deutschland, für die Themen Wasser und Entwicklungshilfe ist das zweite wichtige Anliegen von Viva con Agua.\r\n\r\nDie Sensibilisierung für diese Bereiche soll einerseits durch die zahlreichen Veranstaltungen von Viva con Agua erfolgen, aber auch in intensiver Bildungsarbeit an Schulen. Damit führt Viva con Agua schon frühzeitig Kinder und Jugendliche an soziales und humanitäres Engagement heran.",
  "tax_deductible": true,
  "contact": {
    "name": "Moritz M.",
    "picture": {
      "fallback": true,
      "links": [
        {
          "rel": "fill_100x100",
          "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/328/374/fill_100x100_Moritz_Meier_2.1.jpg"
        },
        {
          "rel": "original",
          "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/328/374/crop_original_Moritz_Meier_2.1.jpg"
        }
      ]
    },
    "links": [
      {
        "rel": "platform",
        "href": "https://www.betterplace.org/de/users/moritz_m10"
      },
      {
        "rel": "contact_data",
        "href": "https://api.betterplace.org/de/api_v4/users/328374/contact_data.json"
      }
    ]
  },
  "picture": {
    "fallback": true,
    "links": [
      {
        "rel": "fill_100x100",
        "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/125/fill_100x100_VcA_Projektlogo.jpg"
      },
      {
        "rel": "fill_200x200",
        "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/125/fill_200x200_VcA_Projektlogo.jpg"
      },
      {
        "rel": "fill_400x400",
        "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/125/fill_400x400_VcA_Projektlogo.jpg"
      },
      {
        "rel": "original",
        "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/125/crop_original_VcA_Projektlogo.jpg"
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
      "href": "https://www.betterplace.org/de/organisations/vivaconagua"
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
```

