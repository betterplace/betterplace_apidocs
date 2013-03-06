Clients
===================================

Client Details
-------------------

```nginx
GET http://betterplace.dev/en/api_v4/clients/volksfreund.json
```

Retrieve some statistics about one client as a single JSON object.

### Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>slug</th>
    <td><code>volksfreund</code></td>
    <td>required</td>
    <td>Client-slug based on the internal betterplace.org client-table.</td>
  </tr>
</table>

### Output Paramter

<table>
  <tr>
    <th>Parameter</th>
    <th>Always/Sometimes</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>update_at</th>
    <td>Always</td>
    <td>DateTime of the last update for those numbers</td>
  </tr>
  <tr>
    <th>name</th>
    <td>Always</td>
    <td>Name/slug for this client whithin the betterplace.org-client-system</td>
  </tr>
  <tr>
    <th>required_donation_amount_total_in_cents</th>
    <td>Always</td>
    <td>Integer/Cent. The total, required amount of donations for all client-projects</td>
  </tr>
  <tr>
    <th>required_donation_amount_open_in_cents</th>
    <td>Always</td>
    <td>Integer/Cent. The open, required amount of donations for all client-projects</td>
  </tr>
  <tr>
    <th>donated_amount_in_cents</th>
    <td>Always</td>
    <td>Integer/Cent. The sum of all donations for all client-projects</td>
  </tr>
  <tr>
    <th>percent_finance</th>
    <td>Always</td>
    <td>Integer/Percent. The percentage of required_donation_amount_total_in_cents and required_donation_amount_open_in_cents.</td>
  </tr>
</table>

### Example response

```json
{
  "format": "json",
  "updated_at": "2013-01-03T14:21:01Z",
  "name": "volksfreund",

  "required_donation_amount_total_in_cents": 50000,
  "required_donation_amount_open_in_cents": 25000,
  "donated_amount_in_cents": 25000,
  "percent_finance": 50,
}
```

