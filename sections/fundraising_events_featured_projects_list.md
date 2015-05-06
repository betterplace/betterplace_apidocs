
# Fundraising Event Featured Projects List

```Rebol
GET https://api.betterplace.org/de/api_v4/fundraising_events/19267/featured_projects.json
```

A list of projects that are currently supported by the fundraising event.

**This is an experimental feature and is still under heavy development. Please use it with caution.**


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">fundraising_event_id</th>
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
      <td></td>
      <td>Max 50 character</td>
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
      <td>True if the project marked as tax deductible.
If so, Users can request a tax-receipt that can be used
with the german tax authorities.
[More about this](http://www.betterplace.org/c/hilfe/projekt-steuerlich-absetzbar/).
</td>
    </tr>
    <tr>
      <th align="left">donations_prohibited</th>
      <td>boolean</td>
      <td>false</td>
      <td>True if the project must not receive donations. This might happen, for example,
if a tax-receipt of german tax authorities rans out.

Please check this flag whenever you display a donation button.
Should you show a button for a project that cannot receive donations
the use will open the donation form and see an error message on
betterplace.org instead!
</td>
    </tr>
    <tr>
      <th align="left">completed_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the project was completed</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How many cents are needed to complete the project</td>
    </tr>
    <tr>
      <th align="left">positive_opinions_count</th>
      <td>number</td>
      <td>13</td>
      <td>Number of positive opinions that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.
</td>
    </tr>
    <tr>
      <th align="left">negative_opinions_count</th>
      <td>number</td>
      <td>0</td>
      <td>Number of *negative* opinions (usually 0) that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.
Critical opinions are part of the betterplace.org
["Web of trust"](http://www.betterplace.org/c/hilfe/woran-erkenne-ich-dass-ein-projekt-vertrauenswurdig-ist/).
</td>
    </tr>
    <tr>
      <th align="left">donor_count</th>
      <td>number</td>
      <td>46</td>
      <td>Number of unique donors, based on the payment-email-address</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td>number</td>
      <td>82</td>
      <td>% financed. Note: We have legacy projects with substantial
donation needs. This percentage includes those needs.
</td>
    </tr>
    <tr>
      <th align="left">incomplete_need_count</th>
      <td>number</td>
      <td>6</td>
      <td>Number of needs that still need donations</td>
    </tr>
    <tr>
      <th align="left">completed_need_count</th>
      <td>number</td>
      <td>12</td>
      <td>Number of completed needs</td>
    </tr>
    <tr>
      <th align="left">blog_post_count</th>
      <td>number</td>
      <td>8</td>
      <td>Number of blogposts (all types)</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>The public face of the project / project manager</td>
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
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="active_matching_fund-ref" href="#active_matching_fund">
            ↓active_matching_fund
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
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
### <a id="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td>string</td>
      <td>"Till B."</td>
      <td>The carrier can be an organisation or user.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier.picture-ref" href="#carrier.picture">
            ↓carrier.picture
          </a>
        </th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
      <td>The organisation logo, user profile picture or a fallback image</td>
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
### <a id="active_matching_fund" href="#active_matching_fund-ref">↑Nested Attributes: active_matching_fund</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">active_matching_fund.id</th>
      <td>number</td>
      <td>1</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.activated_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.title</th>
      <td>string</td>
      <td>ACME Matching Everything</td>
      <td>Our matching fund's name</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.description</th>
      <td>string</td>
      <td>It's all about matching donations…</td>
      <td>The description of the matching fund</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.company_name</th>
      <td>string</td>
      <td>ACME</td>
      <td>The company that supports it</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.client_id</th>
      <td>string</td>
      <td>clientname</td>
      <td>The client to which the matching fund belongs</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.provided_amount_in_cents</th>
      <td>number</td>
      <td>12300</td>
      <td>The amount in cents the company provided to be matched</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.donated_amount_in_cents</th>
      <td>number</td>
      <td>12300</td>
      <td>The amount in cents the company already donated</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.state</th>
      <td>string</td>
      <td>activated</td>
      <td>Current state of this matching fund: either activated or closed</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.logo_url</th>
      <td>string</td>
      <td>http://example.com/images/logo.png</td>
      <td>The URL of the logo image.</td>
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
(<a href="project_details.md">project details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">opinions</th>
      <td>Link to <a href="opinions_list.md">opinions list</a>
</td>
    </tr>
    <tr>
      <th align="left">pictures</th>
      <td>Link to <a href="project_pictures_list.md">project pictures list</a>
</td>
    </tr>
    <tr>
      <th align="left">needs</th>
      <td>Link to <a href="needs_list.md">project needs list</a>
</td>
    </tr>
    <tr>
      <th align="left">blog_posts</th>
      <td>Link to <a href="blog_posts_list.md">blog posts list</a>
</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund</th>
      <td>Link to <a href="matching_fund_details.md">matching fund</a>
</td>
    </tr>
    <tr>
      <th align="left">matching_funds</th>
      <td>Link to <a href="matching_funds_list.md">matching funds list</a>
</td>
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
      <th align="left">carrier.self</th>
      <td>Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
Note: Since the there is no api for users yet, this is only
set for organisations.
</td>
    </tr>
    <tr>
      <th align="left">carrier.picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">carrier.picture.original</th>
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
    <tr>
      <th align="left">active_matching_fund.self</th>
      <td>Link to this resource itself
(<a href="matching_fund_details.md">matching fund details</a>)
</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.projects</th>
      <td>Link to the list of projects belonging to this matching fund</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.documentation</th>
      <td>Link to this resource in the documentation
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 1,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 10,
  "data": [
    {
      "id": 1114,
      "created_at": "2009-03-10T11:12:16+01:00",
      "updated_at": "2015-05-06T09:16:46+02:00",
      "latitude": 34.531617284782,
      "longitude": 69.13581752939456,
      "street": "Taimani, behind Qasemi Winhouse",
      "zip": "",
      "city": "Kabul",
      "country": "Afghanistan",
      "title": "Skateistan Afghanistan",
      "description": "With 68% of Afghanistan’s population under the age of 25, Skateistan strongly believes that youth are the ones most capable of bringing about social change.<br /><br />Skateistan is an Afghan NGO which operates Afghanistan’s (and the world’s) first co-educational skateboarding school. The Skateistan school engages nearly 400 Kabul youth weekly through skateboarding, and provides them with new opportunities in cross-cultural interaction, education, and personal empowerment programs. <br /><br />The students (ages 5-17) come from all of Afghanistan’s diverse ethnic and socioeconomic backgrounds, and include 40% female students, hundreds of streetworking children, and youth with disabilities. They develop skills in skateboarding, leadership, problem-solving, multimedia, and creative arts. The students themselves decide what they want to learn; we connect them with a safe space and opportunities for them to develop the skills that they consider important. <br /><br />For Afghan girls Skateistan's programming is especially important as there are very few recreational opportunities for females. For example, it is not culturally acceptable for girls in Afghanistan to ride bicycles or play sports in public. <br /><br />Skateistan has been active in Kabul since 2007 - with our facility built in 2009 - and in that time we’ve seen that Afghan youth of all ethnicities, genders, and socioeconomic backgrounds love to skateboard. Skateistan brings them together, equipping young men and women to lead their communities toward social change and development.<br /><br />In 2012 Skateistan will be opening its second Afghan facility in Mazar-e-Sharif, Northern Afghanistan. It will have space to teach up to 1000 youth weekly.<br /><br />Our program gives hundreds of oppressed youth a voice. Education and the opportunity for self-expression can break the cycles of poverty, illiteracy and exclusion, with sport paving the way.",
      "tax_deductible": true,
      "donations_prohibited": false,
      "completed_at": null,
      "open_amount_in_cents": 807942,
      "positive_opinions_count": 685,
      "negative_opinions_count": 0,
      "donor_count": 538,
      "progress_percentage": 84,
      "incomplete_need_count": 1,
      "completed_need_count": 81,
      "blog_post_count": 88,
      "contact": {
        "name": "E. Kinast",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/130/618/fill_100x100_original_Picture_023.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/130/618/crop_original_original_Picture_023.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/erika_k2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/130618/contact_data.json"
          }
        ]
      },
      "carrier": {
        "name": "Skateistan",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/001/054/fill_100x100_original_betterplace-logo.png"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/001/054/crop_original_original_betterplace-logo.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/1054.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/project/profile_picture/000/001/114/fill_960x500_original_girls-merza-sm.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/project/profile_picture/000/001/114/fill_730x380_original_girls-merza-sm.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/project/profile_picture/000/001/114/fill_618x322_original_girls-merza-sm.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/project/profile_picture/000/001/114/fill_410x214_original_girls-merza-sm.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/project/profile_picture/000/001/114/fill_270x141_original_girls-merza-sm.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/project/profile_picture/000/001/114/crop_original_original_girls-merza-sm.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-skateistan-afghanistan"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds.json?project_id=1114"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/projects/1114/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/projects/1114/donations/new"
        }
      ]
    }
  ]
}
```

