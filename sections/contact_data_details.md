
# User Contact Data Details

```Cirru
GET https://api.betterplace.org/de/api_v4/users/250285/contact_data.json
```

Name and email for the given user.

Used by api clients to access data about
the managers of projects that belog to this
client.

**:lock: Only available if authenticated as a client and only if this clients has permissions to access this data.**
See [betterplace.org clients](../README.md#client-api).


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">user_id</th>
    <td><code>250285</code></td>
    <td>yes</td>
<td>

User-id as an integer number.

</td>
  </tr>
</table>


## Response Attributes

  <th colspan="4">No response example defined</th>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>
  <th colspan="2">No response example defined</th>
</table>

## Response Example

```json
null
```

