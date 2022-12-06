
# Matching Fund Details ⇄ [List](matching_funds_list.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/matching_funds/2.json
```

The details of a betterplace.org matching fund.
The details and list view show the same data.


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
    <td><code>2</code></td>
    <td>yes</td>
<td>

matching-fund-id as an integer number.

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
      <th align="left">activated_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code>ACME Matching Everything</code></td>
<td>

Our matching fund's name

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code>It's all about matching donations…</code></td>
<td>

The description of the matching fund

</td>
    </tr>
    <tr>
      <th align="left">company_name</th>
      <td><code>string</code></td>
      <td><code>ACME</code></td>
<td>

The company that supports it

</td>
    </tr>
    <tr>
      <th align="left">client_id</th>
      <td><code>string</code></td>
      <td><code>clientname</code></td>
<td>

The client to which the matching fund belongs

</td>
    </tr>
    <tr>
      <th align="left">provided_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the company provided to be matched

</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the company already donated

</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td><code>string</code></td>
      <td><code>activated</code></td>
<td>

Current state of this matching fund: either activated or closed

</td>
    </tr>
    <tr>
      <th align="left">logo_url</th>
      <td><code>string</code></td>
      <td><code>http://example.com/images/logo.png</code></td>
<td>

The URL of the logo image.

</td>
    </tr>
    <tr>
      <th align="left">maximum_matching_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>10000</code></td>
<td>

Up to this amount donations get matched by the matching fund

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
(<a href="matching_fund_details.md">matching fund details</a>)


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

projects

</th>
<td>

Link to the <a href="projects_list.md">list of projects</a>
belonging to this matching fund


</td>
    </tr>
    <tr>
<th align="left">

documentation

</th>
<td>

Link to this resource in the documentation


</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 2,
  "created_at": "2013-10-14T15:26:19+02:00",
  "updated_at": "2016-10-27T16:34:11+02:00",
  "activated_at": "2013-10-21T09:54:41+02:00",
  "title": "Jetzt mitmachen – OTTO verdoppelt jede Spende!",
  "description": "### OTTO hilft Hamburgs Stadtgrün – helfen Sie mit!\n\nGemeinsam mit der Loki Schmidt Stiftung und der Stadt Hamburg schließen wir Baumlücken in strukturschwachen Stadtteilen. Diese Lücken entstehen aufgrund von Krankheiten oder mangelnder Standfestigkeit der Straßenbäume.\n\n<img src=\"https://download.betterplace.org/matching-funds/mf_2-otto_description-logos.png\" alt=\"\">\n\nSeit 2011 sind Hamburger Bürger aufgerufen, gemeinsam mit den beiden Partner-Organisationen für neue Bäume zu spenden.\n\nBereits in diesem Jahr hat OTTO das Projekt unterstützt und mit 25.000 Euro 50 Baumlücken in Gebieten geschlossen, in denen weniger gespendet wird – nämlich in Mümmelmannsberg, Nettelnburg, Steinbek, Steilshoop und Willhelmsburg!\n\nNun wollen wir noch weitere Bäume pflanzen – und zwar gemeinsam mit Ihnen!\n\n### Das funktioniert folgendermaßen:\n\n1. Sie spenden einen beliebig hohen Betrag auf betterplace.org.  \n2. OTTO verdoppelt Ihren Betrag!  \n3. Sobald durch Sie und OTTO 500 Euro zusammengekommen sind, legt die Stadt Hamburg die restlichen 500 Euro drauf, die für eine Pflanzung notwendig sind.  \n4. Ein Baum wird gepflanzt – Hamburg wird grüner!\n\nIhr Engagement zählt – und OTTO honoriert das mit dieser Verdopplungsaktion bis zu einem Maximalbetrag von 15.000 Euro! Helfen Sie jetzt hier mit!\n\n",
  "company_name": "OTTO",
  "client_id": null,
  "provided_amount_in_cents": 521500,
  "donated_amount_in_cents": 521500,
  "state": "closed",
  "logo_url": "https://www.betterplace.dev/uploads/matching_fund/logo/000/000/002/bp1477578851_OTTO_QUADRAT_4c_M-mid.png",
  "maximum_matching_amount_in_cents": 10000,
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/matching_funds/2.json"
    },
    {
      "rel": "platform",
      "href": "https://www.betterplace.org/de/matching-funds/2-otto"
    },
    {
      "rel": "projects",
      "href": "https://api.betterplace.org/de/api_v4/matching_funds/2/projects.json"
    },
    {
      "rel": "documentation",
      "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/matching_fund_details.md"
    }
  ]
}
```

