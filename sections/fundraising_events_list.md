
# Fundraising Event List ⇄ [Details](fundraising_event_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/fundraising_events.json?facets=closed%3Afalse&order=rank%3ADESC&q=Die+Eckerts&scope=location
```

A list of betterplace.org fundraising events (donate money).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
Use this resource as follows: `/clients/PERMALINK/fundraising-events.json`.

To guarantee stable search results, all clients are required to specify at least one facet
and order with each request as explained below.


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

Use the scope to specify how the search-query <code>q</code> should behave:
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
<td>

Search query. The searches behaviour is based on the scope.

</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>closed:false</code></td>
    <td>no</td>
<td>

Filter the result set.
<br>
It is strongly recommended to <strong>specify facets</strong> with each request.
A recommended set of facets is
<code>closed:false| prohibit_donations:false</code>
(without the spaces) which only shows active fundraising events that can receive donations.
<br>
<em>Supported filters are:</em>
<ul>
<li><code>prohibit_donations:true/false</code>
<li><code>completed:true/false</code> –
is this fundraising event fully financed (100 %)? See <code>completed_at</code>
<li><code>closed:true/false</code> –
has this fundraising event been closed by its manager? See <code>closed_at</code>
<li><code>prohibit_donations:true/false</code> –
are donations to this fundraising event forbidden at the moment? Closed and blocked
fundraising events will always return true, for example.
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>rank:DESC</code></td>
    <td>no</td>
<td>

Order the result set.
<br>
It is strongly recommended to <strong>specify an order</strong> with each request.
The default order might change at any time without notice.
A recommended order is
<code> score:desc|closed:asc|completed:asc|rank:desc|last_donation_at:desc</code>
(without the spaces).
<br>
<em>Supported orders are:</em>
<ul>
<li><code>score:ASC/DESC</code> – as provided by the search engine whenever a search term
is given.
<li><code>rank:ASC/DESC</code> – a betterplace.org-specific, platform-wide activity indicator
<li><code>last_donation_at:ASC/DESC</code>
<li><code>completed:ASC/DESC</code>
<li><code>closed:ASC/DESC</code>
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
  "total_entries": 5,
  "offset": 0,
  "total_pages": 2,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 39294,
      "created_at": "2021-09-26T23:25:57+02:00",
      "updated_at": "2021-10-09T19:25:08+02:00",
      "content_updated_at": "2021-10-09T19:25:08+02:00",
      "title": "My birthday stream",
      "description": "<div>Do we want to do something really good together? How about supporting together via this fundraiser \"Tree by tree for our climate - plant rainforest trees!\" from OroVerde - The Tropical Forest Foundation? I chose this organization because their work is very close to my heart. Both I and OroVerde - The Tropical Forest Foundation appreciate your support, because really every contribution helps!<br><br>Why do I use betterplace.org for this? Donating here is safe and uncomplicated and I can keep you informed about updates. Of course you will get a donation receipt for tax purposes at the beginning of next year.<br><br>\n</div>",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "activate_donations_at": null,
      "donations_count": 0,
      "donor_count": 0,
      "donated_amount_in_cents": 0,
      "requested_amount_in_cents": null,
      "forwarded_amount_in_cents": 0,
      "progress_percentage": null,
      "contact": {
        "id": 593528,
        "name": "Elijah Lange (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/593/528/fill_100x100_bp1615732713_Stitch.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/593/528/crop_original_bp1615732713_Stitch.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/593528"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/593528/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_960x500_birthday_default.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_730x380_birthday_default.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_618x322_birthday_default.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_410x214_birthday_default.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_270x141_birthday_default.png"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/crop_original_birthday_default.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/39294.json"
        },
        {
          "rel": "featured_projects",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/39294/featured_projects.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/39294/blog_posts.json"
        },
        {
          "rel": "forwardings",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/39294/forwardings.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/39294-my-birthday-stream"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/39294/opinions.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/fundraising-events/39294",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/fundraising-events/39294"
        },
        {
          "rel": "new_message",
          "href": "https://www.betterplace.org/de/messages/new?recipient=593528"
        }
      ]
    },
    {
      "id": 40476,
      "created_at": "2022-10-20T16:43:47+02:00",
      "updated_at": "2022-10-20T17:21:21+02:00",
      "content_updated_at": "2022-10-20T16:43:47+02:00",
      "title": "FundraisingEventProject test",
      "description": "<div>Wollen wir zusammen was richtig Gutes machen? Wie wäre es damit, gemeinsam über diese Spendenaktion „Deine Spende für den SHEROES Fund“ von Amadeu Antonio Stiftung zu unterstützen? Ich habe mir diese Organisation ausgesucht, da mir iadwawadwhre Arbeit sehr am Herzen liegt. Sowohl ich als auch Amadeu Antonio Stiftung freuen uns über deine Unterstützung, denn wirklich jeder Beitrag hilft!<br><br>\n</div><div>Warum ich dafür betterplace.org nutze? Das Spenden ist hier sicher und unkompliziert und ich kann euch über Updates auf dem Laufenden halten. Natürlich bekommt ihr Anfang nächsten Jahres auch eine Spendenbescheinigung für die Steuer.<br><br>\n</div>",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "activate_donations_at": null,
      "donations_count": 0,
      "donor_count": 0,
      "donated_amount_in_cents": 0,
      "requested_amount_in_cents": 50000,
      "forwarded_amount_in_cents": 0,
      "progress_percentage": null,
      "contact": {
        "id": 609657,
        "name": "Manuel Hartwig (display)",
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
            "href": "https://www.betterplace.org/de/users/609657"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/609657/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_960x500_birthday_default.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_730x380_birthday_default.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_618x322_birthday_default.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_410x214_birthday_default.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/fill_270x141_birthday_default.png"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/assets/default/fundraising_event_profile_picture/crop_original_birthday_default.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/40476.json"
        },
        {
          "rel": "featured_projects",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/40476/featured_projects.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/40476/blog_posts.json"
        },
        {
          "rel": "forwardings",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/40476/forwardings.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/40476-fundraisingeventproject-test"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/40476/opinions.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/fundraising-events/40476",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/fundraising-events/40476"
        },
        {
          "rel": "new_message",
          "href": "https://www.betterplace.org/de/messages/new?recipient=609657"
        }
      ]
    },
    {
      "id": 33831,
      "created_at": "2019-12-12T11:20:45+01:00",
      "updated_at": "2022-10-25T13:43:37+02:00",
      "content_updated_at": "2019-12-12T12:38:12+01:00",
      "title": "LPGjustJohnny - Spenden für die letzte Hilfe",
      "description": "<div>Durch eigene Erfahrungen habe ich unglaublich Respekt vor Menschen die Hospizdienst, also das Begleiten eines Menschen auf seinem letzten Lebensabschnitt, leisten. Hierfür gibt es Deutschlandweit einige Einrichtungen, die genau auf so etwas spezialisiert sind.<br><br>Der Ansatz von \"Die Pusteblume\" geht aber darüber hinaus und möchte die Menschen in deren gewohnten Umfeld (also meist Zuhause) betreuen. Gerade durch privaten Erlebnisse dieses Jahr kann ich hier einen absoluten Mehrwert erkennen, da Menschen in ihren eigenen vier Wänden ein oftmals würdevolleres Leben und Ende finden können.<br><br>Ich bitte euch herzlichst für diese Idee zu spenden, mit Hilfe euer Spenden soll in erster Linie das Angebot an dich Menschen herangetragen werden -  <strong>die Gruppe der Hospizhelfer handelt hierbei ehrenamtlich!<br><br></strong><br>\n</div>",
      "tax_deductible": true,
      "donations_prohibited": true,
      "closed_at": "2021-01-22T08:05:19+01:00",
      "activate_donations_at": null,
      "donations_count": 61,
      "donor_count": 60,
      "donated_amount_in_cents": 151850,
      "requested_amount_in_cents": 150700,
      "forwarded_amount_in_cents": 151850,
      "progress_percentage": 100,
      "contact": {
        "id": 581863,
        "name": "Jana Wulf (display)",
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
            "href": "https://www.betterplace.org/de/users/581863"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/581863/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/033/831/fill_960x500_bp1576146766_Spendenstream.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/033/831/fill_730x380_bp1576146766_Spendenstream.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/033/831/fill_618x322_bp1576146766_Spendenstream.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/033/831/fill_410x214_bp1576146766_Spendenstream.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/033/831/fill_270x141_bp1576146766_Spendenstream.png"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/033/831/crop_original_bp1576146766_Spendenstream.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/33831.json"
        },
        {
          "rel": "featured_projects",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/33831/featured_projects.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/33831/blog_posts.json"
        },
        {
          "rel": "forwardings",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/33831/forwardings.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/33831-lpgjustjohnny-spenden-fuer-die-letzte-hilfe"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/33831/opinions.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/fundraising-events/33831",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/fundraising-events/33831"
        },
        {
          "rel": "new_message",
          "href": "https://www.betterplace.org/de/messages/new?recipient=581863"
        }
      ]
    }
  ]
}
```

