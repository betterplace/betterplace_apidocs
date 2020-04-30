
# Volunteering List ⇄ [Details](volunteering_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/volunteering.json?around=10997+Berlin%2C+Germany&around_distance=25km&nelat=51.123&nelng=12.123&order=content_updated_at%3AASC&q=Homework+help&scope=location&swlat=51.001&swlng=12.001
```

A list of betterplace.org volunteering offers (donate time).
Results are contained in a *data* attribute.

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
  <tr>
    <th align="left">scope</th>
    <td><code>location</code></td>
    <td>no</td>
<td>

Use the scope to specify how the search query <code>q</code> should behave:
<ul>
<li>"no scope" (default) performs a full text search
<li><code>human_name</code> searches only on the manager-fullname and carrier-fullname.
  Use this to get all entities by "Unicef" or by "Till Behnke".
<li><code>location</code> does a reverse geocoding lookup.
  This lookup returns a bounding box. We transform this bounding box to a
  rectangle that is large enough to encapsulate the whole bounding box.
  We then return all entities that are within this rectangle.
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
  <tr>
    <th align="left">around</th>
    <td><code>10997 Berlin, Germany</code></td>
    <td>no</td>
<td>

Order the results by the distance to the given location from near to far.
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
are sent to the google location service. For the provided response we
take a fitting lat/lng value as center of the search. So in theory,
you can use any search that works for google maps.
<br>
Check the <code>around_location</code> to see what latitude/longitude
values have been used for the query.


</td>
  </tr>
  <tr>
    <th align="left">around_distance</th>
    <td><code>25km</code></td>
    <td>no</td>
<td>

In combination with the <code>around</code> parameter the search will be
limited to results whose location is closer than the given value to the
location provided through the <code>around</code> parameter. Possible
values are all integer values followed by <code>m</code> for meters or
<code>km</code> for kilometers, e.g. <code>1000m</code>, <code>1km</code>.
<br>
When <code>around_distance</code> is given without <code>around</code> it
will be ignored.


</td>
  </tr>
  <tr>
    <th align="left">nelat</th>
    <td><code>51.123</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The northeast corner's latitude.

</td>
  </tr>
  <tr>
    <th align="left">nelng</th>
    <td><code>12.123</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The northeast corner's longitude.

</td>
  </tr>
  <tr>
    <th align="left">swlat</th>
    <td><code>51.001</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The southwest corner's latitude.

</td>
  </tr>
  <tr>
    <th align="left">swlng</th>
    <td><code>12.001</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The southwest corner's longitude.

</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Homework help</code></td>
    <td>no</td>
<td>

Search query. The searches behaviour is based on the scope.

</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>content_updated_at:ASC</code></td>
    <td>no</td>
<td>

Order the result by <code>has_image</code> (default),
<code>content_updated_at</code> (second default). Use the optional
<code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="http://www.betterplace.org/en/discover-volunteering">betterplace.org volunteering list</a>:
<code>has_image:desc| carrier_has_image:desc| content_updated_at:desc</code>


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
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code>TODO</code></td>
<td>

Max 100 character

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

A description of the offer. This may contain any of the following
HTML tags: ```a, b, br, div, em, i, iframe, img, li, ol, p, strong, ul```.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>TODO</code></td>
<td>

The organisation that carrier this volunteering

</td>
    </tr>
    <tr>
      <th align="left">vacancies</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

The number of volunteers that are needed, provided by the manager

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="image-ref" href="#image">
            ↓image
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

Each volunteering has one optional image / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>TODO</code></td>
<td>

Contact person, contact data and contact address

</td>
    </tr>
    <tr>
      <th align="left">location_fixed</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether the volunteering offer is limited to a certain location or if it may be
executed remotely.


</td>
    </tr>
    <tr>
      <th align="left">working_time_selection</th>
      <td><code>string</code></td>
      <td><code>regular commitment</code></td>
<td>

Working time selection, specifies if this is a one-time event or if
this volunteering can takes place regulary.


</td>
    </tr>
    <tr>
      <th align="left">working_time_weekends</th>
      <td><code>array</code></td>
      <td><code>["in the mornings"]</code></td>
<td>

Up to three working time preferences. They specify when this volunteering
should take place on weekends.


</td>
    </tr>
    <tr>
      <th align="left">working_time_weekdays</th>
      <td><code>array</code></td>
      <td><code>["in the mornings"]</code></td>
<td>

Up to three working time preferences. They specify when this volunteering
should take place on weekdays.


</td>
    </tr>
    <tr>
      <th align="left">begins_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">ends_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">topics</th>
      <td><code>array</code></td>
      <td><code>["Development cooperation", "Children & youth"]</code></td>
<td>

Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "Animal & environment protection", "Culture & sports",
"Children & youth", "Development cooperation ", "DisabledEducation", "Elderly people",
"Human rights", "Refugees & immigrants", "Invalid", "Local help", "Socially deprived"


</td>
    </tr>
    <tr>
      <th align="left">activities</th>
      <td><code>array &#124; null</code></td>
      <td><code>["consulting/coaching", "office work"]</code></td>
<td>

Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "consulting/coaching", "crafting/gardening", "doing sports",
"doing the chores", "group care", "nursing/parenting", "office work",
"organising/managing", "painting/designing", "tutoring/reading",
"visiting/accompanying", "writing/translating"


</td>
    </tr>
    <tr>
      <th align="left">imported_from</th>
      <td><code>null &#124; string</code></td>
      <td><code>somewhere</code></td>
<td>

Where Betterplace imports volunteering from.

</td>
    </tr>
    <tr>
      <th align="left">import_information</th>
      <td><code></code></td>
      <td><code>TODO</code></td>
<td>

Meta data concerning the import of this volunteering offer, if it
was indeed imported.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code></code></td>
<td>

TODO

</td>
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
      <td><code>number</code></td>
      <td><code>52.499007</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
      <th align="left">carrier.longitude</th>
      <td><code>number</code></td>
      <td><code>13.44947</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td><code>string</code></td>
      <td><code>"Viva con Agua de Sankt Pauli e.V."</code></td>
<td>

An organisation name, Users will be added later

</td>
    </tr>
    <tr>
      <th align="left">carrier.street</th>
      <td><code>string</code></td>
      <td><code>"Rosenstr. 3"</code></td>
<td>

Contact data for the organisation

</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td><code>string</code></td>
      <td><code>"Berlin"</code></td>
<td>

Contact data for the organisation

</td>
    </tr>
    <tr>
      <th align="left">carrier.zip</th>
      <td><code>string</code></td>
      <td><code>"10123"</code></td>
<td>

Contact data for the organisation

</td>
    </tr>
    <tr>
      <th align="left">carrier.country</th>
      <td><code>string</code></td>
      <td><code>"Germany"</code></td>
<td>

Contact data for the organisation

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier.picture-ref" href="#carrier.picture">
            ↓carrier.picture
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code></code></td>
<td>

TODO

</td>
    </tr>
  </table>

### <a id="carrier.picture" href="#carrier.picture-ref">↑Nested Attributes: carrier.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

</td>
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
      <td><code>string</code></td>
      <td><code></code></td>
<td>

Image description

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
      <th align="left">contact.name</th>
      <td><code>string</code></td>
      <td><code>Till Behnke</code></td>
<td>

Fullname of the contact person.


</td>
    </tr>
    <tr>
      <th align="left">contact.phone</th>
      <td><code>string</code></td>
      <td><code>030 - 7676 4488 44</code></td>
<td>

Phone number for direct contact.
No validations on input apply.


</td>
    </tr>
    <tr>
      <th align="left">contact.email</th>
      <td><code>string</code></td>
      <td><code>support@betterplace.org</code></td>
<td>

Plain text email-address for direct contact


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>https://betterplace-assets.betterplace.org/…</code></td>
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
(<a href="volunteering_details.md">volunteering details</a>)


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

inquiries

</th>
<td>

The URL to which inquiries about this offer can be POSTed
(<a href="volunteering_inquiries.md">inquiry details</a>).
Templated, needs insertion of the client_id.


</td>
    </tr>
    <tr>
<th align="left">

carrier.self

</th>
<td>

Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)


</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.fill_200x200

</th>
<td>

200×200 Pixel

</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.fill_400x400

</th>
<td>

400×400 Pixel

</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

image.fill_618x322

</th>
<td>

618×322 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

image.fill_270x141

</th>
<td>

270×141 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

image.original

</th>
<td>

Original size / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

image.thumb

</th>
<td>

Thumbnail size / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

image.medium

</th>
<td>

Medium size / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

image.regular

</th>
<td>

Regular size / DEPRECATED, will be removed after 5/2015

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

profile_picture.fill_960x500

</th>
<td>

950×500 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_730x380

</th>
<td>

730×380 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_618x322

</th>
<td>

618×322 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_410x214

</th>
<td>

410×214 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_270x141

</th>
<td>

270×141 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 723,
  "offset": 3,
  "total_pages": 241,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "id": 7268,
      "created_at": "2013-03-11T18:00:54+01:00",
      "updated_at": "2019-08-05T12:07:53+02:00",
      "latitude": 52.52,
      "longitude": 13.405,
      "street": "Marienstraße 91",
      "zip": "",
      "city": "Berlin",
      "country": "Deutschland",
      "content_updated_at": "2017-11-14T15:02:11+01:00",
      "title": "\"Pate oder Patin werden und mit einem Neuköllner Kind die Welt neu entdecken\"",
      "description": "Bevor wir uns hier in Details verlieren, lassen wir erst einmal unsere Patin Linda zu Wort kommen, denn wer könnte besser Beschreiben, was ein Engagement in unserem Projekt ausmacht, als die Engagierten selbst?<br>http://neukoellner-talente.de/paten/paten-stellen-sich-vor/<br><br>Wer neugierig ist und noch mehr wissen will, kann gerne weiter lesen oder sich gleich bei uns im Büro melden: 030 - 62 73 80 14<br><br>---<br><br>http://neukoellner-talente.de/<br><br>Kinder brauchen Zeit, viel Aufmerksamkeit und eine individuelle Förderung, um ihre Stärken und Begabungen zu entdecken und zu entfalten. Mit ihrem Patenschaftsprojekt »Neuköllner Talente« wendet sich die Bürgerstiftung Neukölln an Kinder im Grundschulalter, die entdecken und zeigen wollen, was in ihnen steckt. Vorrangiges Ziel ist es, durch eine intensive 1:1 Betreuung im Rahmen einer Patenschaft, benachteiligten Kindern in dem multiethnischen Berliner Bezirk die Chance zum Entdecken ihrer Interessen und Begabungen, und die Möglichkeit zur Teilhabe zu eröffnen.",
      "carrier": {
        "latitude": 52.46874,
        "longitude": 13.4341,
        "name": "Bürgerstiftung Neukölln",
        "street": "Dorfplatz 174",
        "city": "Berlin",
        "zip": "12051",
        "country": "Deutschland",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/012/964/fill_100x100_bp1480322689_n__neg_orange_rgb.jpg"
            },
            {
              "rel": "fill_200x200",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/012/964/fill_200x200_bp1480322689_n__neg_orange_rgb.jpg"
            },
            {
              "rel": "fill_400x400",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/012/964/fill_400x400_bp1480322689_n__neg_orange_rgb.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/012/964/crop_original_bp1480322689_n__neg_orange_rgb.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/12964.json"
          }
        ]
      },
      "vacancies": 20,
      "image": {
        "description": "",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_618x322_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_270x141_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "thumb",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/thumb_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "medium",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/medium_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "regular",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/regular_TalentePatInnenaufruf_2.jpg"
          }
        ]
      },
      "contact": {
        "name": "Felix Thomas",
        "phone": "030 627 380 14",
        "email": "491c812ce91d8e4e82fb83b397b852ea58f9ca6f3540cd5d81961f47c93517ec@betterplace.jp",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/293/450/fill_100x100_bp1575676108_Ines_offizielles_Foto_BS.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/293/450/crop_original_bp1575676108_Ines_offizielles_Foto_BS.jpg"
            }
          ]
        },
        "links": [

        ]
      },
      "location_fixed": true,
      "working_time_selection": "egal wann / nach Vereinbarung",
      "working_time_weekends": [

      ],
      "working_time_weekdays": [

      ],
      "begins_at": null,
      "ends_at": null,
      "topics": [
        "Bildung",
        "Kinder & Jugendliche",
        "Kultur, Freizeit & Sport",
        "Flüchtlinge & Migranten"
      ],
      "activities": [
        "besuchen/begleiten"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_960x500_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_730x380_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_618x322_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_410x214_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_270x141_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/crop_original_TalentePatInnenaufruf_2.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/7268.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/7268-pate-oder-patin-werden-und-mit-einem-neukoellner-kind-die-welt-neu-entdecken"
        },
        {
          "rel": "inquiries",
          "href": "https://api.betterplace.org/de/api_v4/clients/%7Bclient_id%7D/volunteering/7268-pate-oder-patin-werden-und-mit-einem-neukoellner-kind-die-welt-neu-entdecken/inquiries.json",
          "templated": true
        }
      ]
    },
    {
      "id": 7402,
      "created_at": "2013-03-18T22:27:45+01:00",
      "updated_at": "2019-11-28T04:30:35+01:00",
      "latitude": 54.0424,
      "longitude": 13.7688,
      "street": "Kirchenweg 185",
      "zip": "17438",
      "city": "Wolgast",
      "country": "Deutschland",
      "content_updated_at": "2019-01-01T09:19:14+01:00",
      "title": "Möchtest Du Dich gern ehrenamtlich engagieren? Dann komm zu uns ins Katzenhaus! Tel. 0174 17 42 010 ",
      "description": "Wir suchen Freiwillige, die uns helfen die über 54 Katzen im Katzenschutzverein zu versorgen. Dazu gehört das Füttern, das Säubern der Katzenklos und natürlich ganz viel streicheln, spielen und schmusen! Jede Hilfe ist willkommen, daher sind regelmäßige Einsätze wünschenswert, aber nicht Voraussetzung. Wir freuen uns auf Dich!",
      "carrier": {
        "latitude": 54.04240036010742,
        "longitude": 13.76879978179932,
        "name": "Katzenschutzverein Wolgast e.V.",
        "street": "Forstweg 178",
        "city": "Wolgast",
        "zip": "17438",
        "country": "Deutschland",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/004/503/fill_100x100_original_391835_297273170296885_1980697066_n.jpg"
            },
            {
              "rel": "fill_200x200",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/004/503/fill_200x200_original_391835_297273170296885_1980697066_n.jpg"
            },
            {
              "rel": "fill_400x400",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/004/503/fill_400x400_original_391835_297273170296885_1980697066_n.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/004/503/crop_original_original_391835_297273170296885_1980697066_n.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/4503.json"
          }
        ]
      },
      "vacancies": 4,
      "image": {
        "description": "Für alle unseren schnurrenden Miezen im Katzenhaus!",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/fill_618x322_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/fill_270x141_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "thumb",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/thumb_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "medium",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/medium_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "regular",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/regular_bp1546329190_20181227_185142.jpg"
          }
        ]
      },
      "contact": {
        "name": "Gina Mayer",
        "phone": "0174 17 42 010",
        "email": "2ba7361a078bffcf98941da663eb82ab483c6c8864637cf6c21cd7cba25d100e@betterplace.jp",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/124/889/fill_100x100_bp1575658219_Logo_Katzenschutzverein.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/124/889/crop_original_bp1575658219_Logo_Katzenschutzverein.jpg"
            }
          ]
        },
        "links": [

        ]
      },
      "location_fixed": true,
      "working_time_selection": "egal wann / nach Vereinbarung",
      "working_time_weekends": [

      ],
      "working_time_weekdays": [

      ],
      "begins_at": null,
      "ends_at": null,
      "topics": [
        "Tierschutz & Umwelt"
      ],
      "activities": [
        "pflegen/betreuen"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/fill_960x500_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/fill_730x380_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/fill_618x322_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/fill_410x214_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/fill_270x141_bp1546329190_20181227_185142.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/402/crop_original_bp1546329190_20181227_185142.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/7402.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/7402-moechtest-du-dich-gern-ehrenamtlich-engagieren-dann-komm-zu-uns-ins-katzenhaus-tel-0174-17-42-010"
        },
        {
          "rel": "inquiries",
          "href": "https://api.betterplace.org/de/api_v4/clients/%7Bclient_id%7D/volunteering/7402-moechtest-du-dich-gern-ehrenamtlich-engagieren-dann-komm-zu-uns-ins-katzenhaus-tel-0174-17-42-010/inquiries.json",
          "templated": true
        }
      ]
    },
    {
      "id": 7435,
      "created_at": "2013-03-20T10:22:43+01:00",
      "updated_at": "2019-12-12T15:47:04+01:00",
      "latitude": 52.5077,
      "longitude": 13.3319,
      "street": "Jägerstraße 170",
      "zip": "10623",
      "city": "Berlin",
      "country": "Deutschland",
      "content_updated_at": "2019-12-12T15:47:04+01:00",
      "title": "Medizinische Hilfe für obdachlose Menschen - Ambulanz, Arztmobil, Krankenwohnung",
      "description": "++ Medizinische Hilfe für obdachlose Menschen ++ Wir behandeln obdachlose Menschen, die keine Krankenversicherung haben und nicht in andere Arztpraxen gehen. Angebote: Krankenwohnung in der Turmstraße, medizinische Ambulanz  am Bahnhof Zoo, Arztmobil. Das Arztmobil ist ein zu einer mobilen Praxis ausgebauter Kleintransporter und fährt dahin, wo sich Obdachlose aufhalten: an bekannte Szeneplätze, vor Suppenküchen etc. Für alle Angebote suchen wir ehrenamtlich engagierte Ärztinnen und Ärzte (mit Approbation) aller Fachrichtungen, gerne auch im Ruhestand, die in der Krankenwhnung, der med. Ambulanz oder im Arztmobil helfen wollen. Der ehrenamtliche Einsatz kann flexibel eingeteilt werden, es gibt eine Aufwandsentschädigung.",
      "carrier": {
        "latitude": 52.55973,
        "longitude": 13.37038,
        "name": "Caritasverband für das Erzbistum Berlin e.V.",
        "street": "Wiesenweg 15",
        "city": "Berlin",
        "zip": "12203",
        "country": "Deutschland",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/013/568/fill_100x100_bp1481028470_logo_caritas_erzbistum_links_web.jpg"
            },
            {
              "rel": "fill_200x200",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/013/568/fill_200x200_bp1481028470_logo_caritas_erzbistum_links_web.jpg"
            },
            {
              "rel": "fill_400x400",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/013/568/fill_400x400_bp1481028470_logo_caritas_erzbistum_links_web.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/013/568/crop_original_bp1481028470_logo_caritas_erzbistum_links_web.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/13568.json"
          }
        ]
      },
      "vacancies": 4,
      "image": {
        "description": "Untersuchung im Arztmobil.",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/fill_618x322_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/fill_270x141_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "thumb",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/thumb_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "medium",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/medium_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "regular",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/regular_Behandlung_Arztmobil.jpg"
          }
        ]
      },
      "contact": {
        "name": "Manuel O",
        "phone": "030666331279",
        "email": "e3c8ec28b2969cd6c892b2ae530e070d35e0f355ce3332cdc0efd3a8570627ab@betterplace.jp",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.jpg"
            }
          ]
        },
        "links": [

        ]
      },
      "location_fixed": true,
      "working_time_selection": "regelmäßig/langfristig",
      "working_time_weekends": [

      ],
      "working_time_weekdays": [
        "vormittags",
        "nachmittags",
        "abends"
      ],
      "begins_at": null,
      "ends_at": null,
      "topics": [
        "Kranke",
        "Menschenrechte",
        "Sozial Benachteiligte"
      ],
      "activities": [
        "pflegen/betreuen"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/fill_960x500_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/fill_730x380_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/fill_618x322_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/fill_410x214_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/fill_270x141_Behandlung_Arztmobil.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/435/crop_original_Behandlung_Arztmobil.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/7435.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/7435-medizinische-hilfe-fuer-obdachlose-menschen-ambulanz-arztmobil-krankenwohnung"
        },
        {
          "rel": "inquiries",
          "href": "https://api.betterplace.org/de/api_v4/clients/%7Bclient_id%7D/volunteering/7435-medizinische-hilfe-fuer-obdachlose-menschen-ambulanz-arztmobil-krankenwohnung/inquiries.json",
          "templated": true
        }
      ]
    }
  ]
}
```

