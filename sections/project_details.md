
# Project Details ⇄ [List](projects_list.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1114.json
```

The details of a betterplace.org project (donate money).

**For [betterplace.org clients](../README.md#client-api):**
Use this resource as follows: `/clients/PERMALINK/projects/ID.json`


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
    <td><code>1114</code></td>
    <td>yes</td>
<td>

Project id as an integer number ≥ 14.

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

DateTime (ISO8601 with Timezone) when the project was created by the
project manager.


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
      <th align="left">activated_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone) when the project was activated
by us, otherwise it is null.


</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

Max 50 character

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

A description of the project. This may contain any of the following
HTML tags: ```a, b, br, div, em, i, iframe, img, li, ol, p, strong, ul```.


</td>
    </tr>
    <tr>
      <th align="left">summary</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

A short summary of the project..


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

True if the project must not receive donations. This might happen, for example,
if a tax receipt of German tax authorities ran out.

Please check this flag whenever you display a donation button.
Should you show a button for a project that cannot receive donations
the user will open the donation form and see an error message on
betterplace.org instead!


</td>
    </tr>
    <tr>
      <th align="left">completed_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone) of the moment the project was fully
funded (100% `progress_percentage`).

A completed project may still be active (as in not closed).
See `closed_at for details.


</td>
    </tr>
    <tr>
      <th align="left">closed_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone) when the project was closed by the
project manager.

A closed project does not have to be fully funded.
See `completed_at` for details.


</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are needed to complete the project

</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are donated already.
This includes:
- sum of all donations
- sum of all forwardings to the project
- external donations

Subtracting:
- backwardings from the project


</td>
    </tr>
    <tr>
      <th align="left">positive_opinions_count</th>
      <td><code>number</code></td>
      <td><code>13</code></td>
<td>

Number of positive opinions that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.

DEPRECATED 2017-06-23

Use `donations_count` and `comments_count` instead. There is no distinction
between positive and negative comments any more, all opinions were converted
into comments.


</td>
    </tr>
    <tr>
      <th align="left">negative_opinions_count</th>
      <td><code>number</code></td>
      <td><code>0</code></td>
<td>

Number of *negative* opinions (usually 0) that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.
Critical opinions are part of the betterplace.org
["Web of trust"](http://www.betterplace.org/c/hilfe/woran-erkenne-ich-dass-ein-projekt-vertrauenswurdig-ist/).

DEPRECATED 2017-06-23

Always returns 0. Don't use this field any more.


</td>
    </tr>
    <tr>
      <th align="left">donations_count</th>
      <td><code>number</code></td>
      <td><code>42</code></td>
<td>

Count of confirmed donations for this project

</td>
    </tr>
    <tr>
      <th align="left">newsletter_subscriptions_count</th>
      <td><code>number</code></td>
      <td><code>42</code></td>
<td>

Count of active newsletter subscriptions for this project.

EXPERIMENTAL 2019-02-21

Can be removed at any time. Use with caution


</td>
    </tr>
    <tr>
      <th align="left">comments_count</th>
      <td><code>number</code></td>
      <td><code>24</code></td>
<td>

Count of all comments for this project. This contains positive and negative
reviews of the project, questions and answers by the project manager, as
well as comments from users.


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
      <th align="left">progress_percentage</th>
      <td><code>number</code></td>
      <td><code>82</code></td>
<td>

% financed. Note: We have legacy projects with substantial
donation needs (pre ~2014). This percentage includes those needs.


</td>
    </tr>
    <tr>
      <th align="left">incomplete_need_count</th>
      <td><code>number</code></td>
      <td><code>6</code></td>
<td>

Number of needs that still need donations

</td>
    </tr>
    <tr>
      <th align="left">completed_need_count</th>
      <td><code>number</code></td>
      <td><code>12</code></td>
<td>

Number of completed needs

</td>
    </tr>
    <tr>
      <th align="left">blog_post_count</th>
      <td><code>number</code></td>
      <td><code>8</code></td>
<td>

Number of blogposts (all types)

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

The public face of the project / project manager

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

The organisation that carries this project

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
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="active_matching_fund-ref" href="#active_matching_fund">
            ↓active_matching_fund
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

**DEPRECATED** Do not use this data. We will remove the nested
matching fund data in the future.

To get this data follow the active_matching_fund link and retrieve
the data from the appropriate endpoint.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="closed_notice-ref" href="#closed_notice">
            ↓closed_notice
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

**This is an experimental feature and is still under heavy development. Please use it with caution.**


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

### <a id="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td><code>string</code></td>
      <td><code>"Till B."</code></td>
<td>

The carrier can be an organisation or user.

</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td><code>string</code></td>
      <td><code>"Berlin"</code></td>
<td>

The city in which the carrier resides

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier.picture-ref" href="#carrier.picture">
            ↓carrier.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code></code></td>
<td>

The organisation logo, user profile picture or a fallback image

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
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.created_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.activated_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.title</th>
      <td><code>string</code></td>
      <td><code>ACME Matching Everything</code></td>
<td>

Our matching fund's name

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.description</th>
      <td><code>string</code></td>
      <td><code>It's all about matching donations…</code></td>
<td>

The description of the matching fund

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.company_name</th>
      <td><code>string</code></td>
      <td><code>ACME</code></td>
<td>

The company that supports it

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.client_id</th>
      <td><code>string</code></td>
      <td><code>clientname</code></td>
<td>

The client to which the matching fund belongs

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.provided_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the company provided to be matched

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the company already donated

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.state</th>
      <td><code>string</code></td>
      <td><code>activated</code></td>
<td>

Current state of this matching fund: either activated or closed

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.logo_url</th>
      <td><code>string</code></td>
      <td><code>http://example.com/images/logo.png</code></td>
<td>

The URL of the logo image.

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.maximum_matching_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>10000</code></td>
<td>

Up to this amount donations get matched by the matching fund

</td>
    </tr>
  </table>

### <a id="closed_notice" href="#closed_notice-ref">↑Nested Attributes: closed_notice</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">closed_notice.text</th>
      <td><code>null &#124; string</code></td>
      <td><code>Thank you for the successful funding.</code></td>
<td>

A close notice from the project manager

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
(<a href="project_details.md">project details</a>)


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

pictures

</th>
<td>

Link to <a href="project_pictures_list.md">project pictures list</a>


</td>
    </tr>
    <tr>
<th align="left">

needs

</th>
<td>

Link to <a href="needs_list.md">project needs list</a>


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

active_matching_fund

</th>
<td>

Link to <a href="matching_fund_details.md">matching fund</a>


</td>
    </tr>
    <tr>
<th align="left">

video

</th>
<td>

Link to a youtube video of this project


</td>
    </tr>
    <tr>
<th align="left">

matching_funds

</th>
<td>

Link to <a href="matching_funds_list.md">matching funds list</a>


</td>
    </tr>
    <tr>
<th align="left">

categories

</th>
<td>

Link to <a href="categories_list.md">categories list</a>


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

carrier.self

</th>
<td>

Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
Note: Since the there is no api for users yet, this is only
set for organisations.


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

carrier.picture.original

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
    <tr>
<th align="left">

active_matching_fund.self

</th>
<td>

Link to this resource itself
(<a href="matching_fund_details.md">matching fund details</a>)


</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund.platform

</th>
<td>

Permalink to betterplace.org

</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund.projects

</th>
<td>

Link to the <a href="projects_list.md">list of projects</a>
belonging to this matching fund


</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund.documentation

</th>
<td>

Link to this resource in the documentation


</td>
    </tr>
    <tr>
<th align="left">

closed_notice.call_to_action

</th>
<td>

A link to a final blog post, the next project url or any other followup
information for the donors.


</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 1114,
  "created_at": "2022-02-28T11:19:40+01:00",
  "updated_at": "2022-02-28T11:20:01+01:00",
  "street": null,
  "zip": null,
  "city": null,
  "country": null,
  "content_updated_at": "2022-02-28T11:19:40+01:00",
  "activated_at": null,
  "title": "Skateistan",
  "description": null,
  "summary": null,
  "tax_deductible": true,
  "donations_prohibited": true,
  "completed_at": null,
  "closed_at": null,
  "open_amount_in_cents": 400065,
  "donated_amount_in_cents": 9724787,
  "positive_opinions_count": 1183,
  "negative_opinions_count": 0,
  "donations_count": 1183,
  "newsletter_subscriptions_count": 460,
  "comments_count": 0,
  "donor_count": 0,
  "progress_percentage": 96,
  "incomplete_need_count": 1,
  "completed_need_count": 109,
  "blog_post_count": 103,
  "contact": null,
  "carrier": {
    "id": 1054,
    "name": "Skateistan",
    "city": "Berlin",
    "picture": {
      "links": [
        {
          "rel": "fill_100x100",
          "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/fill_100x100_bp1523439289_Skateistan_facebook-01.png"
        },
        {
          "rel": "original",
          "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/crop_original_bp1523439289_Skateistan_facebook-01.png"
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
        "href": "https://betterplace-assets.betterplace.org/assets/default/project_profile_picture/fill_960x500_default.jpg"
      },
      {
        "rel": "fill_730x380",
        "href": "https://betterplace-assets.betterplace.org/assets/default/project_profile_picture/fill_730x380_default.jpg"
      },
      {
        "rel": "fill_618x322",
        "href": "https://betterplace-assets.betterplace.org/assets/default/project_profile_picture/fill_618x322_default.jpg"
      },
      {
        "rel": "fill_410x214",
        "href": "https://betterplace-assets.betterplace.org/assets/default/project_profile_picture/fill_410x214_default.jpg"
      },
      {
        "rel": "fill_270x141",
        "href": "https://betterplace-assets.betterplace.org/assets/default/project_profile_picture/fill_270x141_default.jpg"
      },
      {
        "rel": "original",
        "href": "https://betterplace-assets.betterplace.org/assets/default/project_profile_picture/crop_original_default.jpg"
      }
    ]
  },
  "active_matching_fund": null,
  "closed_notice": null,
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
    },
    {
      "rel": "platform",
      "href": "https://www.betterplace.org/de/projects/1114-skateistan"
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
      "rel": "categories",
      "href": "https://api.betterplace.org/de/api_v4/projects/1114/categories.json"
    },
    {
      "rel": "new_client_donation",
      "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/1114",
      "templated": true
    },
    {
      "rel": "new_donation",
      "href": "https://www.betterplace.org/de/donate/platform/projects/1114"
    }
  ]
}
```

