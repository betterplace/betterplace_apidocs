
# Projects List ⇄ [Details](project_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects.json?around=Kabul&around_distance=25km&facets=completed%3Afalse&order=rank%3ADESC&q=Berlin&scope=location
```

A list of betterplace.org projects (donate money).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
Use this resource as follows: `/clients/PERMALINK/projects.json`.

To guarantee stable search results,
all clients are required to specify at least one facet and order with each request as explained
below.


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
    <th align="left">nelat</th>
    <td><code>82.1673907</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The northeast corner's latitude.

</td>
  </tr>
  <tr>
    <th align="left">nelng</th>
    <td><code>74.3555001</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The northeast corner's longitude.

</td>
  </tr>
  <tr>
    <th align="left">swlat</th>
    <td><code>34.5428</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The southwest corner's latitude.

</td>
  </tr>
  <tr>
    <th align="left">swlng</th>
    <td><code>-31.4647999</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The southwest corner's longitude.

</td>
  </tr>
  <tr>
    <th align="left">around</th>
    <td><code>Kabul</code></td>
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
    <th align="left">q</th>
    <td><code>Berlin</code></td>
    <td>no</td>
<td>

Search query. The searches behaviour is based on the scope.

</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>completed:false</code></td>
    <td>no</td>
<td>

Filter the result set.
<br>
It is strongly recommended to <strong>specify facets</strong> with each request.
A recommended set of facets is <code>completed:false| closed:false|
prohibit_donations:false</code> (without the spaces) which
only shows active projects that can receive donations.
<br>
<em>Supported filters are:</em>
<ul>
<li><code>completed:true/false</code> –
is this project fully financed (100 %)? See <code>completed_at</code>
<li><code>closed:true/false</code> –
has this project been closed by the project manager? See <code>closed_at</code>
<li><code>prohibit_donations:true/false</code> –
are donations to this project forbidden at the moment? Closed and blocked projects
will always return true, for example.
<li><code>category_ids:44</code> – does the project belong to this category?
<li><code>category_ids[,]:44,16</code> – does the project belong to any of these categories?
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
A recommended order is <code>score:desc | completed:asc | rank:desc|
last_donation_at:desc</code> (without the spaces). This is the order betterplace.org uses
<a href="http://www.betterplace.org/en/projects/list">for the project list</a>.
<br>
<em>Supported orders are:</em>
<ul>
<li><code>score:ASC/DESC</code> – as provided by the search engine whenever a search term
is given.
<li><code>rank:ASC/DESC</code> – a betterplace.org-specific, platform-wide activity indicator
<li><code>progress_percentage:ASC/DESC</code> – financing goal fulfillment given as 0 to 100
<li><code>completed:ASC/DESC</code> – true (1) or false (0)
<li><code>created_at:ASC/DESC</code> and <code>updated_at:ASC/DESC</code>
<li><code>last_donation_at:ASC/DESC</code>
<li><code>id:ASC/DESC</code>
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

DEPRECATED 2017-06-23

Use `donations_count` instead. There are no opinions and comments outside
of donations anymore.


</td>
    </tr>
    <tr>
      <th align="left">negative_opinions_count</th>
      <td><code>number</code></td>
      <td><code>0</code></td>
<td>

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
      <td><code>0</code></td>
<td>

DEPRECATED 2022-10-24

Always returns 0. Don't use this field any more.


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

% financed

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
    <tr>
      <th align="left">around_distance</th>
      <td><code>number</code></td>
      <td><code>666.23</code></td>
<td>

Distance to around location in meters

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
      <th align="left">carrier.country</th>
      <td><code>string</code></td>
      <td><code>"Deutschland"</code></td>
<td>

The country in which the carrier resides

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

profile_picture.limit_1240x646

</th>
<td>

1240×646 pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.limit_450x235

</th>
<td>

450×235 pixel

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
  "current_page": 1,
  "offset": 0,
  "per_page": 3,
  "total_entries": 3,
  "total_pages": 1,
  "data": [
    {
      "id": 4,
      "created_at": "2023-07-24T14:20:25+02:00",
      "updated_at": "2023-07-24T14:20:28+02:00",
      "latitude": 52.49000000000001,
      "longitude": 13.45,
      "street": null,
      "zip": "10123",
      "city": "Berlin",
      "country": "Deutschland",
      "content_updated_at": "2023-07-24T14:20:27+02:00",
      "activated_at": "2023-07-24T14:20:25+02:00",
      "title": "Closed project",
      "description": "way cool project - my description",
      "summary": "help people to live in peace and have cake",
      "tax_deductible": true,
      "donations_prohibited": true,
      "completed_at": null,
      "closed_at": "2023-07-24T14:20:25+02:00",
      "open_amount_in_cents": 100000,
      "donated_amount_in_cents": 0,
      "positive_opinions_count": 0,
      "negative_opinions_count": 0,
      "donations_count": 0,
      "newsletter_subscriptions_count": 0,
      "comments_count": 0,
      "donor_count": 0,
      "progress_percentage": 0,
      "incomplete_need_count": 1,
      "completed_need_count": 0,
      "blog_post_count": 0,
      "contact": {
        "id": 1,
        "name": "u. X",
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
            "href": "https://www.betterplace.org/de/users/1"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/1/contact_data.json"
          }
        ]
      },
      "carrier": {
        "id": 1,
        "name": "Organisation #1",
        "city": "Berlin",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/crop_original_default.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/1.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/fill_960x500_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/fill_730x380_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/fill_618x322_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/fill_410x214_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/fill_270x141_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/crop_original_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          },
          {
            "rel": "limit_1240x646",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/limit_1240x646_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          },
          {
            "rel": "limit_450x235",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/004/limit_450x235_c1c685a5-0d72-4025-aca2-a26f18efb31d.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "closed_notice": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/4.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/4-closed-project"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/projects/4/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/4/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/de/api_v4/projects/4/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/projects/4/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds.json?project_id=4"
        },
        {
          "rel": "categories",
          "href": "https://api.betterplace.org/de/api_v4/projects/4/categories.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/4",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/projects/4"
        }
      ]
    },
    {
      "id": 3,
      "created_at": "2023-07-24T14:20:23+02:00",
      "updated_at": "2023-07-24T14:20:33+02:00",
      "latitude": 52.49000000000001,
      "longitude": 13.45,
      "street": null,
      "zip": "10123",
      "city": "Berlin",
      "country": "Deutschland",
      "content_updated_at": "2023-07-24T14:20:25+02:00",
      "activated_at": "2023-07-24T14:20:23+02:00",
      "title": "Tax-blocked project",
      "description": "way cool project - my description",
      "summary": "help people to live in peace and have cake",
      "tax_deductible": true,
      "donations_prohibited": false,
      "completed_at": null,
      "closed_at": null,
      "open_amount_in_cents": 800100,
      "donated_amount_in_cents": 0,
      "positive_opinions_count": 0,
      "negative_opinions_count": 0,
      "donations_count": 0,
      "newsletter_subscriptions_count": 0,
      "comments_count": 0,
      "donor_count": 0,
      "progress_percentage": 0,
      "incomplete_need_count": 1,
      "completed_need_count": 0,
      "blog_post_count": 0,
      "contact": {
        "id": 2,
        "name": "u. X",
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
            "href": "https://www.betterplace.org/de/users/2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/2/contact_data.json"
          }
        ]
      },
      "carrier": {
        "id": 2,
        "name": "Organisation #2",
        "city": "Berlin",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/crop_original_default.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/2.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/fill_960x500_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/fill_730x380_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/fill_618x322_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/fill_410x214_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/fill_270x141_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/crop_original_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          },
          {
            "rel": "limit_1240x646",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/limit_1240x646_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          },
          {
            "rel": "limit_450x235",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/003/limit_450x235_a5373ae7-5b4f-4f36-ad16-c8271a6961e1.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "closed_notice": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/3.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/3-tax-blocked-project"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/projects/3/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/3/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/de/api_v4/projects/3/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/projects/3/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds.json?project_id=3"
        },
        {
          "rel": "categories",
          "href": "https://api.betterplace.org/de/api_v4/projects/3/categories.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/3",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/projects/3"
        }
      ]
    },
    {
      "id": 1,
      "created_at": "2023-07-24T14:20:20+02:00",
      "updated_at": "2023-07-24T14:20:40+02:00",
      "latitude": 52.49000000000001,
      "longitude": 13.45,
      "street": null,
      "zip": "10123",
      "city": "Berlin",
      "country": "Deutschland",
      "content_updated_at": "2023-07-24T14:20:23+02:00",
      "activated_at": "2023-07-24T14:20:20+02:00",
      "title": "my little project",
      "description": "way cool project - my description",
      "summary": "help people to live in peace and have cake",
      "tax_deductible": true,
      "donations_prohibited": false,
      "completed_at": null,
      "closed_at": null,
      "open_amount_in_cents": 800100,
      "donated_amount_in_cents": 125000,
      "positive_opinions_count": 3,
      "negative_opinions_count": 0,
      "donations_count": 3,
      "newsletter_subscriptions_count": 1,
      "comments_count": 0,
      "donor_count": 0,
      "progress_percentage": 0,
      "incomplete_need_count": 1,
      "completed_need_count": 0,
      "blog_post_count": 1,
      "contact": {
        "id": 1,
        "name": "u. X",
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
            "href": "https://www.betterplace.org/de/users/1"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/1/contact_data.json"
          }
        ]
      },
      "carrier": {
        "id": 1,
        "name": "Organisation #1",
        "city": "Berlin",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/crop_original_default.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/1.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_960x500_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_730x380_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_618x322_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_410x214_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_270x141_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/crop_original_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          },
          {
            "rel": "limit_1240x646",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/limit_1240x646_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          },
          {
            "rel": "limit_450x235",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/limit_450x235_707219c3-2de7-41e4-9f65-1d4427faa8c6.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "closed_notice": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1-my-little-project"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/projects/1/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/1/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/de/api_v4/projects/1/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/projects/1/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds.json?project_id=1"
        },
        {
          "rel": "categories",
          "href": "https://api.betterplace.org/de/api_v4/projects/1/categories.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/1",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/projects/1"
        }
      ]
    }
  ]
}
```

