
# Fundraising Challenge: Contest Results List

```Rebol
GET https://api.betterplace.org/de/api_v4/contests/1/results.json
```

A list of contest results.
Results are contained in a *data* attribute.

Each result represents the position of a participant [in the given contest.](fundraising_challenge_contest_details.md).

Each result links to the corresponding participant.

**Order:**

The order for the result list is by rank.
The rank is based on the number of donations.
Participants with the same rank / number of donations are ordered by project ID.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">contest_id</th>
    <td><code>1</code></td>
    <td>yes</td>
    <td>Contest-id as an integer number ≥ 0.</td>
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
      <th align="left">rank</th>
      <td>number</td>
      <td>1</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">donation_count</th>
      <td>number</td>
      <td>100</td>
      <td>An integer number ≥ 0</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>5000</td>
      <td>An integer number ≥ 0</td>
    </tr>
    <tr>
      <th align="left">participant_type</th>
      <td>string</td>
      <td>Project</td>
      <td>The type of the participant</td>
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
      <th align="left">participant</th>
      <td>Link to the participant.
The participant type is documented in the type-attribute.
Currently all participants are projects
(<a href="project_details.md">project details</a>).
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 12,
  "offset": 0,
  "total_pages": 4,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 31,
      "created_at": "2014-09-29T00:00:10+02:00",
      "updated_at": "2014-10-13T16:05:39+02:00",
      "rank": 11,
      "donation_count": 4,
      "donated_amount_in_cents": 10000,
      "participant_type": "Project",
      "links": [
        {
          "rel": "participant",
          "href": "https://api.betterplace.org/de/api_v4/projects/18971.json"
        }
      ]
    },
    {
      "id": 32,
      "created_at": "2014-09-29T00:00:10+02:00",
      "updated_at": "2014-10-13T16:05:39+02:00",
      "rank": 9,
      "donation_count": 6,
      "donated_amount_in_cents": 15000,
      "participant_type": "Project",
      "links": [
        {
          "rel": "participant",
          "href": "https://api.betterplace.org/de/api_v4/projects/22000.json"
        }
      ]
    },
    {
      "id": 33,
      "created_at": "2014-09-29T00:00:11+02:00",
      "updated_at": "2014-10-13T16:05:38+02:00",
      "rank": 1,
      "donation_count": 552,
      "donated_amount_in_cents": 704899,
      "participant_type": "Project",
      "links": [
        {
          "rel": "participant",
          "href": "https://api.betterplace.org/de/api_v4/projects/22247.json"
        }
      ]
    }
  ]
}
```

