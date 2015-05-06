
# Volunteering List ⇄ [Details](volunteering_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/volunteering.json?around=10997+Berlin%2C+Germany&nelat=51.123&nelng=12.123&order=created_at%3AASC&q=Homework+help&scope=location&swlat=51.001&swlng=12.001
```

A list of betterplace.org volunteering offers (donate time).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
This resource is not avaliable at the moment.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">scope</th>
    <td><code>location</code></td>
    <td>no</td>
    <td>Use the scope to specify how the search-query <code>q</code> should behave:
<ul>
<li>"no scope" (default) performs a full text search
<li><code>human_name</code> searches only on the manager-fullname and carrier-fullname.
  Use this to get all entities by "Unicef" or by "Till Behnke".
<li><code>location</code> does a reverse geocoding lookup.
  This lookup returns a bounding-box. We transform this bounding-box in a
  rectangle that is large enough to encapsulate the whole bounding-box.
  We then return all entities that belong to this rectangle.
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">around</th>
    <td><code>10997 Berlin, Germany</code></td>
    <td>no</td>
    <td>Order the results by the distance to the given location from near to far.
<br>
Location can be provided as …
<br>
<em>… Lat/Lng:</em> <code>52.50,13.45</code>
<br>
<em>… ZIP:</em> <code>10997 Berlin, Germany</code>.
We use the centre of the ZIP code area as center for the search.
Please add enough context information (like the Country name)
so google knows what place you are looking for.
<br>
<em>… any location search:</em> All queries other than a float tuple
are send to the google location service. For the provided response we
take a fitting lat/lng value as center of the search. So in theory,
you can use any search that works for google maps.
<br>
Check the <code>around_location</code> to see what latitude/longitude
values have been used for the query.
</td>
  </tr>
  <tr>
    <th align="left">nelat</th>
    <td><code>51.123</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The northeast corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">nelng</th>
    <td><code>12.123</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The northeast corner's longitude.</td>
  </tr>
  <tr>
    <th align="left">swlat</th>
    <td><code>51.001</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The southwest corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">swlng</th>
    <td><code>12.001</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The southwest corner's longitude.</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Homework help</code></td>
    <td>no</td>
    <td>Search query. The searches behaviour is based on the scope.</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>created_at:ASC</code></td>
    <td>no</td>
    <td>Order the result by <code>has_image</code> (default), <code>created_at</code> (second default).
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="http://www.betterplace.org/en/volunteering/list">betterplace.org volunteering list</a>:
<code>has_image:desc| carrier_has_image:desc| created_at:desc</code>
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
      <th align="left">title</th>
      <td>string</td>
      <td>TODO</td>
      <td>Max 100 character unless the volunteering is imported</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>TODO</td>
      <td>TODO</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>An organisation, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">vacancies</th>
      <td>number</td>
      <td>1</td>
      <td>The number of volunteers that are needed, provided by the manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="image-ref" href="#image">
            ↓image
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Each volunteering has one optional image / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>Contact person, contact data and contact address</td>
    </tr>
    <tr>
      <th align="left">topics</th>
      <td>array</td>
      <td>["Development cooperation", "Children & youth"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "Animal & environment protection", "Culture & sports",
"Children & youth", "Development cooperation ", "DisabledEducation", "Elderly people",
"Human rights", "Immigrants", "Invalid", "Local help", "Socially deprived"
</td>
    </tr>
    <tr>
      <th align="left">activities</th>
      <td>array &#124; null</td>
      <td>["consulting/coaching", "office work"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "consulting/coaching", "crafting/gardening", "doing sports",
"doing the chores", "group care", "nursing/parenting", "office work",
"organising/managing", "painting/designing", "tutoring/reading",
"visiting/accompanying", "writing/translating"
</td>
    </tr>
    <tr>
      <th align="left">imported_from</th>
      <td>null &#124; string</td>
      <td>aktion_mensch</td>
      <td>Betterplace imports volunteering offers from Aktions Mensch.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="import_information-ref" href="#import_information">
            ↓import_information
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Meta data concerning the import of this volunteering offer, if it
was indeed imported.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
    </tr>
  </table>
### <a id="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">carrier.longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td>string</td>
      <td>"Viva con Agua de Sankt Pauli e.V."</td>
      <td>An organisation name, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">carrier.street</th>
      <td>string</td>
      <td>"Rosenstr. 3"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td>string</td>
      <td>"Berlin"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.zip</th>
      <td>string</td>
      <td>"10123"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.country</th>
      <td>string</td>
      <td>"Germany"</td>
      <td>Contact data for the organisation</td>
    </tr>
  </table>
### <a id="image" href="#image-ref">↑Nested Attributes: image</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">image.description</th>
      <td>string</td>
      <td></td>
      <td>Image description</td>
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
      <td>string</td>
      <td>Till Behnke</td>
      <td>Fullname of the contact person.
For imported volunteering offers, this is the
contact-name that is provided on import.
</td>
    </tr>
    <tr>
      <th align="left">contact.phone</th>
      <td>string</td>
      <td>030 - 7676 4488 44</td>
      <td>Phone number for direct contact.
No validations on input apply.
</td>
    </tr>
    <tr>
      <th align="left">contact.email</th>
      <td>string</td>
      <td>support@betterplace.org</td>
      <td>Plain text email-address for direct contact
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
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
### <a id="import_information" href="#import_information-ref">↑Nested Attributes: import_information</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">import_information.created_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was actually created.
</td>
    </tr>
    <tr>
      <th align="left">import_information.updated_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was
actually updated last.
</td>
    </tr>
    <tr>
      <th align="left">import_information.import_type</th>
      <td>string</td>
      <td>"Import::ImportFormat"</td>
      <td>Type of import this record originated from.</td>
    </tr>
    <tr>
      <th align="left">import_information.import_id</th>
      <td>string</td>
      <td>"foo:23"</td>
      <td>Unique identifier for this imported record.
</td>
    </tr>
    <tr>
      <th align="left">import_information.imported_at</th>
      <td>string</td>
      <td>"1994-11-15T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the record was imported at
betterplace.
</td>
    </tr>
  </table>
### <a id="profile_picture" href="#profile_picture-ref">↑Nested Attributes: profile_picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">profile_picture.fallback</th>
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
(<a href="volunteering_details.md">volunteering details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">carrier.logo</th>
      <td>The original image version as uploaded by the organisation manager.

Please note: This image might change in the future since this attribute
does not follow the general API pattern for image attributes. You should
subscribe to the change-log newsletter so we can inform you about upcomming changes.
</td>
    </tr>
    <tr>
      <th align="left">image.fill_618x322</th>
      <td>618×322 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.fill_270x141</th>
      <td>270×141 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.original</th>
      <td>Original size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.thumb</th>
      <td>Thumbnail size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.medium</th>
      <td>Medium size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.regular</th>
      <td>Regular size / DEPRECATED, will be removed after 5/2015</td>
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
      <th align="left">profile_picture.fill_960x500</th>
      <td>950×500 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_730x380</th>
      <td>730×380 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_618x322</th>
      <td>618×322 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_410x214</th>
      <td>410×214 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_270x141</th>
      <td>270×141 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">profile_picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 4414,
  "offset": 3,
  "total_pages": 1472,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "id": 18,
      "created_at": "2013-01-28T10:23:14+01:00",
      "updated_at": "2015-01-21T01:30:26+01:00",
      "latitude": 51.3171,
      "longitude": 9.49561,
      "street": "",
      "zip": "34121",
      "city": "Kassel",
      "country": "Deutschland",
      "title": "Awo Büro Aktiv  Kassel- Besuchsdienst für Senioren im Käthe-Richterhaus",
      "description": "<p>Wir suchen Ehrenamtliche, die den alten Menschen in liebevoller Weise den Kontakt zum normalen Leben und Alltag vermitteln. Sie helfen mit, die Lebensqualität der Altenheimbewohner wesentlich zu verbessern, in dem Sie einen Bewohner regelmäßig besuchen oder Unterhaltung für eine Gruppe von alten Menschen anbieten. Sie können sich in folgenden Häusern engagieren.</p>\n\n<p>Sie sollten kommunikativ sein und gut zuhören können, musikalisch sein oder leidenschaftlich gerne spielen. Vielleicht haben Sie einen lieben Hund und</p>\n\n<p>möchten mit diesem gerne pflegebedürftige Menschen besuchen oder Sie haben andere eigene Ideen. Für jeden wird sich hier das Richtige finden!</p>\n\n<p><strong>- Unterstützung bzw selbstständige Durchführung von Gruppenangeboten</strong></p>\n\n<p><strong>- Unterstützung bei der Gartenarbeit</strong></p>\n\n<p><strong>- regelmässiger Besuchsdienst (Einzelbesuche)</strong></p>\n\n<p><strong>- Unterstützung in der Nähstube (1xim Monat)</strong></p>\n\n<p><strong>Bitte wenden Sie sich an unser Awo Büro Aktiv in Kassel Telefon 0561/9284-238 </strong></p>\n\n<p><strong>Bürozeiten: DI und Do von 09:00h -12:00h ansonsten Anrufbeantworter.(Wir rufen Sie umgehend zurück)</strong></p><ul><li>Unfallversicherung</li><li>regelmäßige Informationen</li><li>kostenlose Veranstaltungen</li><li>Fortbildung/Qualifizierungsangebote</li><li>Erstattung entstandener Kosten</li><li>Anleitung durch Fachkräfte</li></ul>",
      "carrier": {
        "latitude": 51.3171,
        "longitude": 9.49561,
        "name": "Freiwilligenzentrum",
        "street": "Spohrstraße 5",
        "city": "Kassel",
        "zip": "34117",
        "country": "Deutschland",
        "links": [
          {
            "rel": "logo",
            "href": ""
          }
        ]
      },
      "vacancies": 1,
      "image": {
        "description": null,
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/thumb_default.betterplace.png"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/medium_default.betterplace.png"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/regular_default.betterplace.png"
          }
        ]
      },
      "contact": {
        "name": "Frank Gerhold",
        "phone": "0561 - 10 24 25",
        "email": "fg@freiwilligenzentrumkassel.de",
        "picture": null,
        "links": [

        ]
      },
      "topics": [
        "Kranke",
        "Menschen mit Behinderung",
        "Senioren"
      ],
      "activities": [

      ],
      "imported_from": "aktion_mensch",
      "import_information": {
        "created_at": "2013-03-15T00:00:00+01:00",
        "updated_at": "2015-01-13T00:00:00+01:00",
        "import_type": "Bettertime::AktionMensch::Import",
        "import_id": "fn-452",
        "imported_at": "2015-01-21T01:30:26+01:00",
        "links": [

        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_960x500_default.betterplace.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_410x214_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/crop_original_default.betterplace.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/18.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/18-awo-buro-aktiv-kassel-besuchsdienst-fur-senioren-im-kathe-richterhaus"
        }
      ]
    },
    {
      "id": 19,
      "created_at": "2013-01-28T10:23:15+01:00",
      "updated_at": "2014-08-22T01:30:31+02:00",
      "latitude": 51.3126,
      "longitude": 9.44618,
      "street": "Willy-Brandt-Platz 1",
      "zip": "34131",
      "city": "Kassel",
      "country": "Deutschland",
      "title": "Betreuung von Reisenden und Besuchern",
      "description": "<p><strong>Wir bieten Ihnen ein Stückchen zu Hause für unterwegs!</strong></p>\n\n<ul><li>Ein-, Aus- und Umsteigehilfen, Auskünfte und kleine praktische Hilfen</li>\n\t<li>Gelegenheit, in gemütlicher Atmosphäre einen Tee oder Kaffee zu trinken</li>\n\t<li>Mutter-Kind-Raum mit Gelegenheit zum Stillen, Wickeln und Ausruhen</li>\n\t<li>Raum für ältere Kinder, um die Wartezeit mit Spielen oder Lesen zu verkürzen</li>\n\t<li>Bei Bedarf gezielte soziale Hilfen und Vermittlung an andere Institutionen.</li>\n\t<li>Kontaktaufnahme mit Angehörigen (z.B. Hinterlegung von Fahrkarten)</li>\n\t<li>Vermittlung von Hilfen an Ihren nächsten Aufenthaltsort.</li>\n</ul>\n\n<p><strong>Die Bahnhofsmission ist an 365 Tagen im Jahr für Sie da:</strong><br/><br/>\nSie finden uns im Bahnhof Wilhelmshöhe, eine Etage über dem Eingangs- und Geschäftsbereich an den Gleisen 7 - 10 (Aufzug vorhanden).<br/><br/>\nTelefon: 05 61 - 3 71 07<br/><br/>\nGerne können Sie auch einen Termin für Ihre Umsteigehilfe vereinbaren oder mit uns absprechen, wann Sie am Bahnhof ankommen. Wir holen Sie am Bahnsteig ab und führen Sie zu unseren Räumen.<br/><br/><strong>Hier finden Sie alle deutschen Bahnhofsmissionen:</strong><br/><br/>www.bahnhofsmission.de</p><ul><li>Tätigkeitsnachweise</li><li>Haftpflichtversicherung</li><li>Fortbildung/Qualifizierungsangebote</li><li>Erstattung entstandener Kosten</li><li>Dienstbesprechungen</li><li>Ausstattung mit Medien / Arbeitsmaterialien</li><li>Anleitung durch Fachkräfte</li><li>Unfallversicherung</li></ul>",
      "carrier": {
        "latitude": 51.3171,
        "longitude": 9.49561,
        "name": "Freiwilligenzentrum",
        "street": "Spohrstraße 5",
        "city": "Kassel",
        "zip": "34117",
        "country": "Deutschland",
        "links": [
          {
            "rel": "logo",
            "href": ""
          }
        ]
      },
      "vacancies": 1,
      "image": {
        "description": null,
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/thumb_default.betterplace.png"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/medium_default.betterplace.png"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/regular_default.betterplace.png"
          }
        ]
      },
      "contact": {
        "name": "Frank Gerhold",
        "phone": "0561 - 10 24 25",
        "email": "fg@freiwilligenzentrumkassel.de",
        "picture": null,
        "links": [

        ]
      },
      "topics": [
        "Kranke"
      ],
      "activities": [

      ],
      "imported_from": "aktion_mensch",
      "import_information": {
        "created_at": "2013-03-15T01:00:00+01:00",
        "updated_at": "2014-08-18T02:00:00+02:00",
        "import_type": "Bettertime::AktionMensch::Import",
        "import_id": "fn-457",
        "imported_at": "2014-08-22T01:30:31+02:00",
        "links": [

        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_960x500_default.betterplace.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_410x214_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/crop_original_default.betterplace.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/19.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/19-betreuung-von-reisenden-und-besuchern"
        }
      ]
    },
    {
      "id": 20,
      "created_at": "2013-01-28T10:23:15+01:00",
      "updated_at": "2014-08-23T01:30:34+02:00",
      "latitude": 51.3171,
      "longitude": 9.49561,
      "street": "",
      "zip": "34117",
      "city": "Kassel",
      "country": "Deutschland",
      "title": "Begleitung schwerkranker und sterbender Menschen und deren Angehöriger",
      "description": "<p>Die Tätigkeit ehrenamtlich Mitarbeitender ist ein wesentlicher Bestandteil des Hospizangebotes, entweder patientennah durch die unmittelbare Begleitung schwerstkranker und sterbender Menschen, die Unterstützung Angehöriger und die Trauerbegleitung.</p>\n<p>Voraussetzung hierfür ist die Teilnahme am Vorbereitungskurs (4 Wochenenden, 6 Abende, Praktikum), sowie die monatlichen Gruppentreffen.</p>\n<p>Patientenferne Einsatzfelder finden sich in den Bereichen Öffentlichkeitsarbeit (Vereinszeitschrift und Fundraising) und Bürotätigkeitsunterstützung.</p>\n\n<p><strong>Was wir bieten:</strong></p>\n<ul style=\"list-style-type:disc;\"><li>einen in sich geschlossenen Grund- und Aufbaukurs<br/></li>\n    <li>einen Lernprozess in der Gruppe für den Einzelnen </li>\n    <li>einen geschützten Raum, in dem Gefühle, Erinnerungen,      Ideen, Eindrücke etc. ihren Platz haben und Vertrauen wachsen kann<br/></li>\n    <li>die Gruppe als tragfähige Gemeinschaft<br/></li>\n    <li>eine Auseinandersetzung mit der eigenen Biographie, der      eigenen Spiritualität, aber auch Schwerem in unserem Leben </li>\n</ul>\n\n\n<p> <strong>Der/die Bewerber/in soll die Bereitschaft mitbringen: </strong></p>\n\n<ul style=\"list-style-type:disc;\"><li>sich auf unterschiedliche Weltanschauungen einzulassen<br/></li>\n    <li>sich mit sich selbst auseinanderzusetzen<br/></li>\n    <li>sich der praxisbegleitenden Reflexion zu stellen<br/></li>\n    <li>sich auf das Lernen in der Gruppe einzulassen (Partner-      und Kleingruppenarbeit)<br/></li>\n    <li>regelmäßig und verbindlich an den Veranstaltungen      teilzunehmen<br/></li>\n    <li>nach Abschluss der Schulung als ehrenamtliche/r      Helfer/in für den Verein tätig zu sein - d.h. insbesondere über      dementsprechende Zeitressourcen zu verfügen.</li>\n    <li>psychische Belastbarkeit in der Auseinandersetzung mit dem Thema Krankheit, Trauer und Tod</li>\n    <li>Empathie</li>\n</ul>\n\n<p><strong>Einsatzort:</strong> Stadtgebiet Kassel</p>\n\n<p><strong><br/></strong></p><ul><li>Supervision</li><li>kostenlose Veranstaltungen</li><li>Haftpflichtversicherung</li><li>Fortbildung/Qualifizierungsangebote</li><li>Erstattung entstandener Kosten</li><li>Erfahrungsaustausch</li><li>Anleitung durch Fachkräfte</li><li>Unfallversicherung</li></ul>",
      "carrier": {
        "latitude": 51.3171,
        "longitude": 9.49561,
        "name": "Freiwilligenzentrum",
        "street": "Spohrstraße 5",
        "city": "Kassel",
        "zip": "34117",
        "country": "Deutschland",
        "links": [
          {
            "rel": "logo",
            "href": ""
          }
        ]
      },
      "vacancies": 1,
      "image": {
        "description": null,
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/thumb_default.betterplace.png"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/medium_default.betterplace.png"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/regular_default.betterplace.png"
          }
        ]
      },
      "contact": {
        "name": "Frank Gerhold",
        "phone": "0561 - 10 24 25",
        "email": "fg@freiwilligenzentrumkassel.de",
        "picture": null,
        "links": [

        ]
      },
      "topics": [
        "Kranke"
      ],
      "activities": [

      ],
      "imported_from": "aktion_mensch",
      "import_information": {
        "created_at": "2013-03-15T01:00:00+01:00",
        "updated_at": "2014-08-19T02:00:00+02:00",
        "import_type": "Bettertime::AktionMensch::Import",
        "import_id": "fn-464",
        "imported_at": "2014-08-23T01:30:34+02:00",
        "links": [

        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_960x500_default.betterplace.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_730x380_default.betterplace.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_410x214_default.betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/assets/default/job_description_profile_picture/crop_original_default.betterplace.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/20.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/20-begleitung-schwerkranker-und-sterbender-menschen-und-deren-angehoriger"
        }
      ]
    }
  ]
}
```

