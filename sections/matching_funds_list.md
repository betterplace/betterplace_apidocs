
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
    <td><code>1</code></td>
    <td>no</td>
<td>

Optional project id as an integer number.
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
  "current_page": 1,
  "offset": 0,
  "per_page": 2,
  "total_entries": 1,
  "total_pages": 1,
  "data": [
    {
      "id": 1,
      "created_at": "2023-07-24T14:20:40+02:00",
      "updated_at": "2023-07-24T14:20:40+02:00",
      "activated_at": "2023-07-24T14:20:40+02:00",
      "title": "Matching Fund 1",
      "description": "rollin rollin rollin..",
      "company_name": "Company Name",
      "client_id": null,
      "provided_amount_in_cents": 0,
      "donated_amount_in_cents": 0,
      "state": "closed",
      "logo_url": null,
      "maximum_matching_amount_in_cents": 10000,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds/1.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/matching-funds/1-company-name"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds/1/projects.json"
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

