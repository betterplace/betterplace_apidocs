
# Fundraising Challenge: Contest Details

```Rebol
GET http://jop.betterplace.dev/de/api_v4/contests/1.json
```

The details of a contest.

One fundraising challenge can have multiple contests, each with
it's own timeframe (begins_at, ends_at).

The contest level only shows general information.
Everything else is part of the [result lists](fundraising_challenge_contest_results_list.md).


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
      <th align="left">begins_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">ends_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>250</td>
      <td>Sum of all donations in cents
that are counted as part of this fundraising challenge.
</td>
    </tr>
    <tr>
      <th align="left">donation_count</th>
      <td>number</td>
      <td>5</td>
      <td>Number of donations
that are counted as part of this fundraising challenge.
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
      <th align="left">results</th>
      <td>The <a href="fundraising_challenge_contest_results_list.md">contest result list</a>
includes all participants, their position in this contest
and a link to more details about the participant.
</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 1,
  "created_at": "2014-08-12T12:56:01+02:00",
  "updated_at": "2014-10-13T16:05:39+02:00",
  "begins_at": "2014-09-29T00:00:00+02:00",
  "ends_at": "2014-10-12T23:59:00+02:00",
  "donated_amount_in_cents": 2020088,
  "donation_count": 1367,
  "links": [
    {
      "rel": "results",
      "href": "https://api.betterplace.org/de/api_v4/contests/1/results.json"
    }
  ]
}
```

