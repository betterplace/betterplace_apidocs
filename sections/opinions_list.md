
# Opinions List ⇄ [Details](opinion_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/projects/1114/opinions.json?facets=has_message%3Atrue&order=created_at%3AASC
```

A list of betterplace.org projects opinions (donate money).

```Rebol
GET https://api.betterplace.org/de/api_v4/fundraising_events/19267/opinions.json?facets=has_message:true&order=created_at:AASC
```
A list of betterplace.org fundraising event opinions (donate money).

Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**

* _Project-Opinions:_ There is no client-scoped-url.
  Please use the api calls that are provided inside the client project _url_ response
  to make sure you only request data that is associated with one of your projects.

* _Fundraising-Event-Opinions:_ There is no client-scoped-url.
  Please use the api calls that are provided inside the client fundraising event _url_ response
  to make sure you only request data that is associated with one of your fundraising event.

* _All Opinions:_ Clients can retrieve a list of all opinions of all client-projects:
  ```Rebol
  GET https://api.betterplace.org/de/api_v4/clients/{client_id}/opinions.json
  ```


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
    <td>no</td>
    <td>Project-id as an integer number ≥ 14.
This url-part is required in case you want to show project opinions.
Also check the URL example in the introduction.
</td>
  </tr>
  <tr>
    <th align="left">fundraising_event_id</th>
    <td><code>19267</code></td>
    <td>no</td>
    <td>Fundraising-event-id as an integer number ≥ 1.
This url-part is required in case you want to show fundraising event opinions.
Also check the URL example in the introduction.
</td>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>volksfreund</code></td>
    <td>no</td>
    <td>The betterplace.org-internal client permalink.'
This url-part is required for the "all opinions" list.
Also check the URL exampin the introduction.
</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>created_at:ASC</code></td>
    <td>no</td>
    <td>Order the result by
<code>created_at</code> (default), <code>id</code>, <code>score</code>
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>has_message:true</code></td>
    <td>no</td>
    <td>Filter the result set:
<ul>
<li><code>facets=score:positive</code> / <code>negative</code> only positive / negative opinion
<li><code>facets=has_donation:true</code> / <code>false</code> only opinions with / without a donation
<li><code>facets=has_message:true</code> / <code>false</code> only opinions with / without a message
</ul>
It is possible to set multiple facet filters.
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
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>5000</td>
      <td>If the opinion was created as part of a donation, this shows the opinions text</td>
    </tr>
    <tr>
      <th align="left">score</th>
      <td>string</td>
      <td>positive</td>
      <td>Opinions can be positive or negative. Negative opinions usually get
a comment as answer very fast but there is no API for opinion-comments yet.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="author-ref" href="#author">
            ↓author
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>The author. DonorOpinion may be anonymous,
PlainOpinions and VisitorOpinion require a logged in user.
</td>
    </tr>
    <tr>
      <th align="left">message</th>
      <td>null &#124; string</td>
      <td>"This is a great project. In spring 2007 I travelled around the area together with my children and …"</td>
      <td>An optional message users can provide to tell others
why they like or dislike this project
</td>
    </tr>
  </table>
### <a id="author" href="#author-ref">↑Nested Attributes: author</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">author.name</th>
      <td>null &#124; string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".

In the case of donation-opinions the name might also be
empty/null for anonymous donations for anonymous donations.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="author.picture-ref" href="#author.picture">
            ↓author.picture
          </a>
        </th>
      <td>string</td>
      <td>//asset1.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</td>
      <td>User profile picture or a fallback image</td>
    </tr>
  </table>
### <a id="author.picture" href="#author.picture-ref">↑Nested Attributes: author.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">author.picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="opinion_details.md">opinion details</a>)
</td>
    </tr>
    <tr>
      <th align="left">project</th>
      <td>Link to the project this opinion belongs to
(<a href="project_details.md">project details</a>)
</td>
    </tr>
    <tr>
      <th align="left">fundraising_event</th>
      <td>Link to the fundraising event this opinion belongs to
(<a href="fundraising_event_details.md">fundraising event details</a>)
</td>
    </tr>
    <tr>
      <th align="left">author.platform</th>
      <td>The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.
</td>
    </tr>
    <tr>
      <th align="left">author.contact_data</th>
      <td>The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">author.picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">author.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 4,
  "offset": 0,
  "total_pages": 2,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 704744,
      "created_at": "2015-04-30T15:06:33+02:00",
      "updated_at": "2015-04-30T15:06:33+02:00",
      "donated_amount_in_cents": 2000,
      "score": "positive",
      "author": null,
      "message": "",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/opinions/704744.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 704747,
      "created_at": "2015-05-06T09:15:44+02:00",
      "updated_at": "2015-05-06T09:15:58+02:00",
      "donated_amount_in_cents": 2000,
      "score": "positive",
      "author": {
        "name": "Test H.",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            }
          ]
        },
        "links": [

        ]
      },
      "message": "",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/opinions/704747.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 704746,
      "created_at": "2015-04-30T15:09:55+02:00",
      "updated_at": "2015-04-30T15:09:55+02:00",
      "donated_amount_in_cents": 2000,
      "score": "positive",
      "author": null,
      "message": "",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/opinions/704746.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    }
  ]
}
```

