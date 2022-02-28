
# Fundraising Event Details ⇄ [List](fundraising_events_list.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/fundraising_events/19267.json
```

The details of a betterplace.org fundraising events (donate money).

**For [betterplace.org clients](../README.md#client-api):**
Use this resource as follows: `/clients/PERMALINK/fundraising-events/ID.json`


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
    <td><code>19267</code></td>
    <td>yes</td>
<td>

Fundraising Event id as an integer number ≥ 1.

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
      <td><code>Gemeinsam gegen Ebola: Deine Spende für Westafrika</code></td>
<td>

Max 50 character

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code>Lorem ipsum</code></td>
<td>

A description of the fundraising event. This may contain any of the
following HTML tags: ```a, b, br, div, em, i, iframe, img, li, ol, p, strong, ul```.
Max 25.000 characters.


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
      <th align="left">donations_prohibited</th>
      <td><code>boolean</code></td>
      <td><code>false</code></td>
<td>

True if the fundraising event must not and cannot receive donations.
This might happen if the event was closed by the manager,
blocked by a platform administrator or the donation activation
time is in the future.

Please check this flag whenever you display a donation button.
Should you show a button for an event that cannot receive donations
the user will open the donation form and see an error message on
betterplace.org instead!


</td>
    </tr>
    <tr>
      <th align="left">closed_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone) when the fundraising event was closed
by the manager.


</td>
    </tr>
    <tr>
      <th align="left">activate_donations_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone). Donations are prohibited until this
date and time is reached. Defaults to NULL.


</td>
    </tr>
    <tr>
      <th align="left">donations_count</th>
      <td><code>number</code></td>
      <td><code>42</code></td>
<td>

Count of confirmed donations for this fundraising event

</td>
    </tr>
    <tr>
      <th align="left">donor_count</th>
      <td><code>number</code></td>
      <td><code>46</code></td>
<td>

⚠️ DEPRECATED!
This value is deprecated and will be removed after 2021-12-31.
Please update your code to use the `donations_count`.

Number of unique donors, based on the payment-email-address


</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>232323</code></td>
<td>

How many cents were already raised with the fundraising event

</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td><code>null &#124; number</code></td>
      <td><code>12382</code></td>
<td>

How many cents were requested to be raised with the fundraising event.
This value is optional! The manager decides if his event has a goal or not.


</td>
    </tr>
    <tr>
      <th align="left">forwarded_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents were already forwarded to a project.

</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td><code>null &#124; number</code></td>
      <td><code>5</code></td>
<td>

% financed. This value is only present in case the manager
decided to add a <code>requested_amount_in_cents</code>.


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

The public face of the fundraising event / fundraising event manager

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
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
(<a href="fundraising_event_details.md">fundraising event details</a>)


</td>
    </tr>
    <tr>
<th align="left">

featured_projects

</th>
<td>

A list of <a href="projects_list.md">projects</a> are currently supported by the fundraising event.

Please note that this project list has no fixed relation to the list of projects that received money by this fundraising event (see <a href="fundraising_events_featured_projects_list.md">Featured Projects List</a>).
A Fundraising event manager can change the list of supported projects at any time; regardless if they received money before.


</td>
    </tr>
    <tr>
<th align="left">

blog_posts

</th>
<td>

Link to <a href="blog_posts_list.md">blog posts list</a>


</td>
    </tr>
    <tr>
<th align="left">

forwardings

</th>
<td>

Provides a list of forwarded amounts and their receiving projects.

Each fundraising event can have multiple projects that it supports. The fundraising event manager specifies the amount that is forwarded from the fundraising event to the project.
Please note that this list of forwarded donations and their corresponding receiving projects is not required to be in sync with the <a href="fundraising_events_featured_projects_list.md">Featured Project List endpoint</a>.
To find out if all donations of the fundraising event have been forwarded, please sum the amounts provided by this api endpoint and compare it to the donated amount attribute of the fundraising event api endpoint.


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

opinions

</th>
<td>

Link to <a href="opinions_list.md">donations/opinions list</a>


</td>
    </tr>
    <tr>
<th align="left">

new_client_donation

</th>
<td>

Link to the donation form. Templated, needs insertion of the client_id.


</td>
    </tr>
    <tr>
<th align="left">

new_donation

</th>
<td>

Link to the regular donation form.


</td>
    </tr>
    <tr>
<th align="left">

header_picture

</th>
<td>

Optional additional image to be used when promoting the fundraising event.
**This is an experimental feature. Please use it with caution. We might change or remove it any time without notice.**


</td>
    </tr>
    <tr>
<th align="left">

new_message

</th>
<td>

Send message to this fundraising event via betterplace.org

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
  "id": 19267,
  "created_at": "2014-09-23T21:17:06+02:00",
  "updated_at": "2019-05-29T00:45:18+02:00",
  "content_updated_at": "2015-06-28T11:32:11+02:00",
  "title": "Gemeinsam gegen Ebola: Deine Spende für Westafrika",
  "description": "Das Ebola-Virus ist für uns* in Westafrika allgegenwärtig: Schüttelt man zur Begrüßung noch die Hand, obwohl die Regierungen davon abraten? Tritt man die Dienstreise in das vom Virus betroffene Nigeria an? Droht die Quarantäne, wenn man bei der Ausreise aus der Region unter Erkältung und Fieber leidet? <br><br>Für die Menschen in Sierra Leone, Liberia und Guinea sind das Luxusprobleme. Dort ist ein normaler Alltag nicht mehr möglich. Im Familienkreis oder der Nachbarschaft gibt es möglicherweise Tote zu beklagen. Der Zugang zu Gesundheitsdienstleistungen ist, auch für andere häufig auftretende Krankheiten wie Malaria, erschwert und kann teilweise nicht mehr gewährleistet werden. <br><br>Viele Ärzte und Krankenschwestern sind selbst gestorben oder haben Angst, sich selbst anzustecken, da es an grundsätzlichen Dingen wie Schutzkleidung und Arzneimitteln fehlt. Unsere Spenden unterstützen Action Medeor beider Ausrüstung zweier neu aufgebauter Isolierstationen in Monrovia, Liberia.<br><br>Die internationale Gemeinschaft reagiert nur sehr langsam – obwohl das Virus bereits seit Anfang des Jahres mehr als 2500 Menschen den Tod gekostet hat. Die langfristigen Folgen für die Volkswirtschaften, die Gesundheitssysteme und das Zusammenleben der Menschen in der Region sind verheerend. <br><br>Wir müssen jetzt handeln, um den Menschen vor Ort und ihren Helfern die notwendigen Materialien zukommen zu lassen. Wir denken dabei auch an unsere Freunde hier in der Region, die wir auf Dienstreisen kennen gelernt haben oder die als Ärzte in Alarmbereitschaft versetzt wurden. Helft uns dabei, den Menschen in ihrer Notlage zu helfen: Teilt diesen Link mit anderen und spendet, auch kleine Beiträge sind willkommen! <br><br>* Jonas lebt seit mehr als zwei Jahren im Senegal, Johanna war für knapp zwei Monate im benachbarten Gambia. Wir beide haben in den letzten Wochen die Nachrichtenlage verfolgt und mit den Menschen vor Ort über die Unsicherheit gesprochen. <br><br>Bild: Jonas Wipfler, Liberia, 2013",
  "tax_deductible": true,
  "donations_prohibited": true,
  "closed_at": "2015-06-28T11:32:11+02:00",
  "activate_donations_at": null,
  "donations_count": 134,
  "donor_count": 0,
  "donated_amount_in_cents": 858280,
  "requested_amount_in_cents": null,
  "forwarded_amount_in_cents": 858280,
  "progress_percentage": null,
  "contact": null,
  "profile_picture": {
    "links": [
      {
        "rel": "fill_960x500",
        "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/019/267/fill_960x500_Liberia_1.jpg"
      },
      {
        "rel": "fill_730x380",
        "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/019/267/fill_730x380_Liberia_1.jpg"
      },
      {
        "rel": "fill_618x322",
        "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/019/267/fill_618x322_Liberia_1.jpg"
      },
      {
        "rel": "fill_410x214",
        "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/019/267/fill_410x214_Liberia_1.jpg"
      },
      {
        "rel": "fill_270x141",
        "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/019/267/fill_270x141_Liberia_1.jpg"
      },
      {
        "rel": "original",
        "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/019/267/crop_original_Liberia_1.jpg"
      }
    ]
  },
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/fundraising_events/19267.json"
    },
    {
      "rel": "featured_projects",
      "href": "https://api.betterplace.org/de/api_v4/fundraising_events/19267/featured_projects.json"
    },
    {
      "rel": "blog_posts",
      "href": "https://api.betterplace.org/de/api_v4/fundraising_events/19267/blog_posts.json"
    },
    {
      "rel": "forwardings",
      "href": "https://api.betterplace.org/de/api_v4/fundraising_events/19267/forwardings.json"
    },
    {
      "rel": "platform",
      "href": "https://www.betterplace.org/de/fundraising-events/19267-gemeinsam-gegen-ebola-deine-spende-fuer-westafrika"
    },
    {
      "rel": "opinions",
      "href": "https://api.betterplace.org/de/api_v4/fundraising_events/19267/opinions.json"
    },
    {
      "rel": "new_client_donation",
      "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/fundraising-events/19267",
      "templated": true
    },
    {
      "rel": "new_donation",
      "href": "https://www.betterplace.org/de/donate/platform/fundraising-events/19267"
    },
    {
      "rel": "new_message",
      "href": "https://www.betterplace.org/de/messages/new"
    }
  ]
}
```

