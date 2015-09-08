
# Fundraising Event Details ⇄ [List](fundraising_events_list.md)

```Rebol
GET http://jop.betterplace.dev/de/api_v4/fundraising_events/19267.json
```

The details of a betterplace.org fundraising events (donate money).

**For [betterplace.org clients](../README.md#client-api):**
Use this resource like `/clients/PERMALINK/fundraising-events/ID.json`


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
    <td>Fundraising-Event-id as an integer number ≥ 1.</td>
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
      <th align="left">title</th>
      <td>string</td>
      <td>Gemeinsam gegen Ebola: Deine Spende für Westafrika</td>
      <td>Max 50 character</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>Lorem ipsum</td>
      <td>Max 25.000 character</td>
    </tr>
    <tr>
      <th align="left">tax_deductible</th>
      <td>boolean</td>
      <td>true</td>
      <td>True if the fundraising event is marked as tax deductible and
can only support tax deductible projects.
If so, Users can request a tax-receipt for their donation
that can be used with the german tax authorities.
</td>
    </tr>
    <tr>
      <th align="left">donations_prohibited</th>
      <td>boolean</td>
      <td>false</td>
      <td>True if the fundraising event must not and cannot receive donations.
This might happen if the event was closed by the manager
or blocked by a platform administrator.

Please check this flag whenever you display a donation button.
Should you show a button for an event that cannot receive donations
the use will open the donation form and see an error message on
betterplace.org instead!
</td>
    </tr>
    <tr>
      <th align="left">closed_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the fundraising event was closed
by the manager.
</td>
    </tr>
    <tr>
      <th align="left">donor_count</th>
      <td>number</td>
      <td>46</td>
      <td>Number of unique donors, based on the payment-email-address</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>232323</td>
      <td>How many cents were already raised with the fundraising event</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How many cents were requested to be raised with the fundraising event.
This value is optional! The manager decides if his event has a goal or not.
</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td>number</td>
      <td>5</td>
      <td>% financed. This value is only present in case the manager
decided to add a <code>requested_amount_in_cents</code>.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>The public face of the fundraising event / fundraising event manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td>//asset1.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</td>
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
(<a href="fundraising_event_details.md">fundraising event details</a>)
</td>
    </tr>
    <tr>
      <th align="left">featured_projects</th>
      <td>A list of <a href="projects_list.md">projects</a> are currently supported by the fundraising event.

Please note, that this project list has no fixed relation to the list of projects that received money by this fundraising event (see <a href="fundraising_events_featured_projects_list.md">Featured Projects List</a>).
A Fundraising event manager can change the list of supported projects at any time; regardless if they received money before.
</td>
    </tr>
    <tr>
      <th align="left">forwardings</th>
      <td>Provides a list of forwarded amounts and their receiving projects.

Each fundraising event can have multiple projects that it supports. The fundraising event manager specifies the amount that is forwarded from the fundraising event to the project.
Please note, that this list of forwarded donations and their corresponding receiving projects is not required to be in sync with the <a href="fundraising_events_featured_projects_list.md">Featured Project List endpoint</a>.
To find out, if all donations of the fundraising event have been forwarded, please sum the amounts provided by this api endpoint and compare it to the donated amount attribute of the fundraising event api endpoint.
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">new_client_donation</th>
      <td>Link to the donation form. Templated, needs insertion of the client_id.
</td>
    </tr>
    <tr>
      <th align="left">new_donation</th>
      <td>Link to the regular donation form.
</td>
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
  "id": 19267,
  "created_at": "2014-09-23T21:17:06+02:00",
  "updated_at": "2015-06-28T11:32:11+02:00",
  "title": "Gemeinsam gegen Ebola: Deine Spende für Westafrika",
  "description": "Das Ebola-Virus ist für uns* in Westafrika allgegenwärtig: Schüttelt man zur Begrüßung noch die Hand, obwohl die Regierungen davon abraten? Tritt man die Dienstreise in das vom Virus betroffene Nigeria an? Droht die Quarantäne, wenn man bei der Ausreise aus der Region unter Erkältung und Fieber leidet? <br><br>Für die Menschen in Sierra Leone, Liberia und Guinea sind das Luxusprobleme. Dort ist ein normaler Alltag nicht mehr möglich. Im Familienkreis oder der Nachbarschaft gibt es möglicherweise Tote zu beklagen. Der Zugang zu Gesundheitsdienstleistungen ist, auch für andere häufig auftretende Krankheiten wie Malaria, erschwert und kann teilweise nicht mehr gewährleistet werden. <br><br>Viele Ärzte und Krankenschwestern sind selbst gestorben oder haben Angst, sich selbst anzustecken, da es an grundsätzlichen Dingen wie Schutzkleidung und Arzneimitteln fehlt. Unsere Spenden unterstützen Action Medeor beider Ausrüstung zweier neu aufgebauter Isolierstationen in Monrovia, Liberia.<br><br>Die internationale Gemeinschaft reagiert nur sehr langsam – obwohl das Virus bereits seit Anfang des Jahres mehr als 2500 Menschen den Tod gekostet hat. Die langfristigen Folgen für die Volkswirtschaften, die Gesundheitssysteme und das Zusammenleben der Menschen in der Region sind verheerend. <br><br>Wir müssen jetzt handeln, um den Menschen vor Ort und ihren Helfern die notwendigen Materialien zukommen zu lassen. Wir denken dabei auch an unsere Freunde hier in der Region, die wir auf Dienstreisen kennen gelernt haben oder die als Ärzte in Alarmbereitschaft versetzt wurden. Helft uns dabei, den Menschen in ihrer Notlage zu helfen: Teilt diesen Link mit anderen und spendet, auch kleine Beiträge sind willkommen! <br><br>* Jonas lebt seit mehr als zwei Jahren im Senegal, Johanna war für knapp zwei Monate im benachbarten Gambia. Wir beide haben in den letzten Wochen die Nachrichtenlage verfolgt und mit den Menschen vor Ort über die Unsicherheit gesprochen. <br><br>Bild: Jonas Wipfler, Liberia, 2013",
  "tax_deductible": true,
  "donations_prohibited": true,
  "closed_at": "2015-06-28T11:32:11+02:00",
  "donor_count": 124,
  "donated_amount_in_cents": 858280,
  "requested_amount_in_cents": null,
  "progress_percentage": null,
  "contact": {
    "name": "J. & J.",
    "picture": {
      "fallback": true,
      "links": [
        {
          "rel": "fill_100x100",
          "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/397/832/fill_100x100_JoJo.jpg"
        },
        {
          "rel": "original",
          "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/397/832/crop_original_JoJo.jpg"
        }
      ]
    },
    "links": [
      {
        "rel": "platform",
        "href": "https://www.betterplace.org/de/users/j_j5"
      },
      {
        "rel": "contact_data",
        "href": "https://api.betterplace.org/de/api_v4/users/397832/contact_data.json"
      }
    ]
  },
  "profile_picture": {
    "fallback": true,
    "links": [
      {
        "rel": "fill_960x500",
        "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/019/267/fill_960x500_Liberia_1.jpg"
      },
      {
        "rel": "fill_730x380",
        "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/019/267/fill_730x380_Liberia_1.jpg"
      },
      {
        "rel": "fill_618x322",
        "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/019/267/fill_618x322_Liberia_1.jpg"
      },
      {
        "rel": "fill_410x214",
        "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/019/267/fill_410x214_Liberia_1.jpg"
      },
      {
        "rel": "fill_270x141",
        "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/019/267/fill_270x141_Liberia_1.jpg"
      },
      {
        "rel": "original",
        "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/019/267/crop_original_Liberia_1.jpg"
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
      "rel": "forwardings",
      "href": "https://api.betterplace.org/de/api_v4/fundraising_events/19267/forwardings.json"
    },
    {
      "rel": "platform",
      "href": "https://www.betterplace.org/de/fundraising-events/ebola"
    },
    {
      "rel": "new_client_donation",
      "href": "https://www.betterplace.org/de/fundraising-events/19267/client_donations/new?client_id=%7Bclient_id%7D",
      "templated": true
    },
    {
      "rel": "new_donation",
      "href": "https://www.betterplace.org/de/fundraising-events/19267/donations/new"
    }
  ]
}
```

