
# Fundraising Event List ⇄ [Details](fundraising_event_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/fundraising_events.json?facets=tax_deductible%3Atrue&order=rank%3ADESC&q=Die+Eckerts&scope=location
```

A list of betterplace.org fundraising events (donate money).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
Use this resource like `/clients/PERMALINK/fundraising-events.json`


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
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Die Eckerts</code></td>
    <td>no</td>
    <td>Search query. The searches behaviour is based on the scope.</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>tax_deductible:true</code></td>
    <td>no</td>
    <td>Filter the result set.
Documented and supported filters are:
<ul>
<li><code>tax_deductible:true/false</code>
<li><code>prohibit_donations:true/false</code>
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>rank:DESC</code></td>
    <td>no</td>
    <td>Order the results by <code>score</code> (only when a query (q) is given),
<code>rank</code>, <code>id</code>, <code>progress_percentage</code>,
<code>tax_deductible</code>, <code>created_at</code>, <code>updated_at</code>,
<code>last_donation_at</code>, <code>completed</code>.
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="https://www.betterplace.org/en/projects/list?search_form%5Bfilters%5D%5Btype%5D=Group">betterplace.org fundraising events list</a>:
<code>completed:asc| score:desc | rank:desc| last_donation_at:desc</code>
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
  "total_entries": 1,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 401,
      "created_at": "2008-09-12T16:50:38+02:00",
      "updated_at": "2015-04-10T21:02:34+02:00",
      "title": "Die Eckerts",
      "description": "In Deutschland gibt es 12.673 Telefonbucheinträge mit dem Namen \"Eckert\". Wenn jeder davon nur einen Euro im Monat spenden würde, kämen 152.076 Euro zusammen. Aber fangen wir erst mal mit fünf Eckerts (dafür etwas mehr als ein Euro im Monat) an - bringt auch schon eine ordentliche Summe zusammen, mit der wir hier auf betterplace.org was Gutes tun können.In Deutschland gibt es 12.673 Telefonbucheinträge mit dem Namen \"Eckert\". Wenn jeder davon nur einen Euro im Monat spenden würde, kämen 152.076 Euro zusammen. Aber fangen wir erst mal mit fünf Eckerts (dafür etwas mehr als ein Euro im Monat) an - bringt auch schon eine ordentliche Summe zusammen, mit der wir hier auf betterplace.org was Gutes tun können.In Deutschland gibt es 12.673 Telefonbucheinträge mit dem Namen \"Eckert\". Wenn jeder davon nur einen Euro im Monat spenden würde, kämen 152.076 Euro zusammen. Aber fangen wir erst mal mit fünf Eckerts (dafür etwas mehr als ein Euro im Monat) an - bringt auch schon eine ordentliche Summe zusammen, mit der wir hier auf betterplace.org was Gutes tun können.In Deutschland gibt es 12.673 Telefonbucheinträge mit dem Namen \"Eckert\". Wenn jeder davon nur einen Euro im Monat spenden würde, kämen 152.076 Euro zusammen. Aber fangen wir erst mal mit fünf Eckerts (dafür etwas mehr als ein Euro im Monat) an - bringt auch schon eine ordentliche Summe zusammen, mit der wir hier auf betterplace.org was Gutes tun können.In Deutschland gibt es 12.673 Telefonbucheinträge mit dem Namen \"Eckert\". Wenn jeder davon nur einen Euro im Monat spenden würde, kämen 152.076 Euro zusammen. Aber fangen wir erst mal mit fünf Eckerts (dafür etwas mehr als ein Euro im Monat) an - bringt auch schon eine ordentliche Summe zusammen, mit der wir hier auf betterplace.org was Gutes tun können.In Deutschland gibt es 12.673 Telefonbucheinträge mit dem Namen \"Eckert\". Wenn jeder davon nur einen Euro im Monat spenden würde, kämen 152.076 Euro zusammen. Aber fangen wir erst mal mit fünf Eckerts (dafür etwas mehr als ein Euro im Monat) an - bringt auch schon eine ordentliche Summe zusammen, mit der wir hier auf betterplace.org was Gutes tun können.In Deutschland gibt es 12.673 Telefonbucheinträge mit dem Namen \"Eckert\". Wenn jeder davon nur einen Euro im Monat spenden würde, kämen 152.076 Euro zusammen. Aber fangen wir erst mal mit fünf Eckerts (dafür etwas mehr als ein Euro im Monat) an - bringt auch schon eine ordentliche Summe zusammen, mit der wir hier auf betterplace.org was Gutes tun können.",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "donor_count": 13,
      "donated_amount_in_cents": 92602,
      "requested_amount_in_cents": null,
      "progress_percentage": null,
      "contact": {
        "name": "Moritz E.",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/006/fill_100x100_original_eckert.png"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/006/crop_original_original_eckert.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/moritz_e"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/6/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/000/401/fill_960x500_original_eckert_absolute.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/000/401/fill_730x380_original_eckert_absolute.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/000/401/fill_618x322_original_eckert_absolute.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/000/401/fill_410x214_original_eckert_absolute.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/000/401/fill_270x141_original_eckert_absolute.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/000/401/crop_original_original_eckert_absolute.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/401.json"
        },
        {
          "rel": "featured_projects",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/401/featured_projects.json"
        },
        {
          "rel": "forwardings",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/401/forwardings.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/dieeckerts"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/401/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/401/donations/new"
        }
      ]
    }
  ]
}
```

