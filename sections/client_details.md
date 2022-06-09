
# Client Details

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/volksfreund.json
```

This API endpoint returns links to more specific information about this client.

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
    <td><code>volksfreund</code></td>
    <td>yes</td>
<td>

The betterplace.org-internal client permalink

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
    <tr>
<th align="left">

projects

</th>
<td>

Link to the <a href="projects_list.md">project list</a> of this client


</td>
    </tr>
    <tr>
<th align="left">

client_donations

</th>
<td>

Link to the <a href="client_donations_list.md">client donations list</a> of this client


</td>
    </tr>
    <tr>
<th align="left">

client_project_tags

</th>
<td>

Link to the <a href="client_tags_list.md">tags list</a> of this client


</td>
    </tr>
    <tr>
<th align="left">

client_fundraising_events

</th>
<td>

Link to the <a href="fundraising_events_list.md">fundraising events list</a> of this client


</td>
    </tr>
    <tr>
<th align="left">

project_mailing_subscriptions

</th>
<td>

Link to the templated <a href="client_mailing_subscriptions.md">client mailing subscriptions</a>
of this client. Replace <code>{project_id}</code> with the ID of a project that is
part of you client projects list.


</td>
    </tr>
    <tr>
<th align="left">

project_statistics

</th>
<td>

Link to the <a href="project_statistics_list.md">project statistics</a> of this client


</td>
    </tr>
    <tr>
<th align="left">

fundraising_event_statistics

</th>
<td>

Link to the <a href="fundraising_event_statistics_list.md">fundraising event statistics</a> of this client


</td>
    </tr>
</table>

## Response Example

```json
{
  "links": [
    {
      "rel": "projects",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/projects.json"
    },
    {
      "rel": "client_donations",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations.json"
    },
    {
      "rel": "client_project_tags",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/tags.json"
    },
    {
      "rel": "client_fundraising_events",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/fundraising_events.json"
    },
    {
      "rel": "project_mailing_subscriptions",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/projects/%7Bproject_id%7D/mailing_subscriptions.json",
      "templated": true
    },
    {
      "rel": "project_statistics",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/project_statistics.json"
    },
    {
      "rel": "fundraising_event_statistics",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/fundraising_event_statistics.json"
    }
  ]
}
```

