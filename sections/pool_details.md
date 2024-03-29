
# Pool Details

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/payback/pool.json
```

The details of a betterplace.org client pool.

The result is cached for 5 minutes.

**:lock: Only available if authenticated as a client.**
See [betterplace.org clients](../README.md#client-api).

**For [betterplace.org clients](../README.md#client-api):**
Use this resource as follows: `/clients/PERMALINK/pool.json`


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>payback</code></td>
    <td>yes</td>
<td>

The betterplace.org-internal client permalink.

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
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>232323</code></td>
<td>

The amount in cents this pool has received

</td>
    </tr>
    <tr>
      <th align="left">forwarded_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the pool has forwarded to projects.


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
(<a href="pool_details.md">pool details</a>)


</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 4,
  "created_at": "2016-01-14T15:12:34+01:00",
  "updated_at": "2022-02-12T19:55:35+01:00",
  "donated_amount_in_cents": 105828770,
  "forwarded_amount_in_cents": 104036054,
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/clients/payback/pool.json"
    }
  ]
}
```

