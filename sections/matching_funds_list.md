
# Matching Funds List ⇄ [Details](matching_fund_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/matching_funds.json?facets=state%3Aactivated
```

A list of betterplace.org matching funds.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>28013</code></td>
    <td>no</td>
<td>

Optional project id as an integer number ≥ 14.
Allows to filter the list of matching funds.
This way one can show a list of matching funds where
the given project is part of the matching fund projects list.


</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>state:activated</code></td>
    <td>no</td>
<td>

Filter the result set by <code>state</code> (activated|closed)
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
  "total_entries": 8,
  "offset": 0,
  "total_pages": 4,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 11,
      "created_at": "2015-10-29T17:06:32+01:00",
      "updated_at": "2016-10-27T16:34:28+02:00",
      "activated_at": "2015-10-31T08:33:12+01:00",
      "title": "Fressnapf verdoppelt deine Spende",
      "description": "",
      "company_name": "Fressnapf",
      "client_id": "fressnapf",
      "provided_amount_in_cents": 1000000,
      "donated_amount_in_cents": 1000000,
      "state": "closed",
      "logo_url": "http://www.betterplace.test/uploads/matching_fund/logo/000/000/011/bp1477578868_Logo_Fressnapf.png",
      "maximum_matching_amount_in_cents": 10000,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds/11.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/matching-funds/11-fressnapf"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds/11/projects.json"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/matching_fund_details.md"
        }
      ]
    },
    {
      "id": 34,
      "created_at": "2016-04-13T15:57:01+02:00",
      "updated_at": "2016-11-29T14:54:07+01:00",
      "activated_at": "2016-07-07T09:59:35+02:00",
      "title": "2016-07-07 Gut für Köln und Bonn",
      "description": "Die Sparkasse KölnBonn verdoppelt Deine Spende auf gut-fuer-koeln-und-bonn.de!",
      "company_name": "Die Sparkasse KölnBonn",
      "client_id": "sk-koelnbonn",
      "provided_amount_in_cents": 997500,
      "donated_amount_in_cents": 997500,
      "state": "closed",
      "logo_url": null,
      "maximum_matching_amount_in_cents": 10000,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds/34.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/matching-funds/34-die-sparkasse-kolnbonn"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds/34/projects.json"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/matching_fund_details.md"
        }
      ]
    }
  ]
}
```

