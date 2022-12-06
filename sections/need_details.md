
# Project Need Details ⇄ [List](needs_list.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1114/needs/59220.json
```

The details of a betterplace.org project need (donate money).
The details and list view show the same data per project need.

**For [betterplace.org clients](../README.md#client-api):**
There is no client-scoped URL.
Please use the API calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.


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
    <td><code>1114</code></td>
    <td>yes</td>
<td>

Project id as an integer number.

</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>59220</code></td>
    <td>yes</td>
<td>

Need-id as an integer number.

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



</td>
    </tr>
    <tr>
      <th align="left">completed</th>
      <td><code>boolean</code></td>
      <td><code>false</code></td>
<td>

True if the need is 100 % financed

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
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are donated already.
This includes all donations that can be given to a need
(direct donation, forwarding of project donation,
forwarding of organisation donation,
forwarding of fundraising event donations,
offline donations and also(!) external donations)


</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are still needed to complete the need

</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How much money is needed in total

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
(<a href="need_details.md">need details</a>)


</td>
    </tr>
    <tr>
<th align="left">

project

</th>
<td>

Link to the related <a href="project_details.md">project's details</a>


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
</table>

## Response Example

```json
{
  "id": 357682,
  "created_at": "2021-11-23T13:43:53+01:00",
  "updated_at": "2022-08-30T08:42:43+02:00",
  "title": "Skateistan: A New Chapter",
  "description": "Unser Ziel: im Laufe des nächsten Jahres auf 20 Standorte zu expandieren und jede Woche 4 500 Schüler zu erreichen. Helft uns, das nächste Kapitel der Geschichte von Skateistan zu schreiben!",
  "completed": false,
  "progress_percentage": 22.03,
  "donated_amount_in_cents": 110135,
  "open_amount_in_cents": 389865,
  "requested_amount_in_cents": 500000,
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/projects/1114/needs/357682.json"
    },
    {
      "rel": "project",
      "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
    },
    {
      "rel": "new_client_donation",
      "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/1114?need_id=357682",
      "templated": true
    },
    {
      "rel": "new_donation",
      "href": "https://www.betterplace.org/de/donate/platform/projects/1114?need_id=357682"
    }
  ]
}
```

