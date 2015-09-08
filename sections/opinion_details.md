
# Opinion Details ⇄ [List](opinions_list.md)

```Rebol
GET http://jop.betterplace.dev/de/api_v4/projects/38/opinions/22.json
```

The details of a betterplace.org opinion.
This may be a [project](project_details.md) opinion
or a [fundraising event](fundraising_event_details.md) opinion.
The details and list view show the same data.

This will always show the data if a valid opinion id is given, even if that opinion
does not belong to the project in the URL.

**For [betterplace.org clients](../README.md#client-api):**
There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
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
    <td><code>38</code></td>
    <td>yes</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>22</code></td>
    <td>yes</td>
    <td>Blog-post-id as an integer number ≥ 9.</td>
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
      <td>The amount donated, but only if the user allowed the amount to be
visible. Most donation forms allow the donor to specify if they
want their amount to be visible. As a default, the donated amount
is visible.

Known issue: For forwarding donations (money that is formwareded from a fundraising event to a project)
this field is always empty, which is wrong.
</td>
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
why they like or dislike this project.
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
  "id": 22,
  "created_at": "2007-11-24T14:14:02+01:00",
  "updated_at": "2007-11-24T14:14:02+01:00",
  "score": "positive",
  "author": {
    "name": "G. Krabbe",
    "picture": {
      "fallback": true,
      "links": [
        {
          "rel": "fill_100x100",
          "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/759/fill_100x100_original_Schule_Leutersdorf_2.JPG"
        },
        {
          "rel": "original",
          "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/000/759/crop_original_original_Schule_Leutersdorf_2.JPG"
        }
      ]
    },
    "links": [
      {
        "rel": "platform",
        "href": "https://www.betterplace.org/de/users/giesela_k"
      },
      {
        "rel": "contact_data",
        "href": "https://api.betterplace.org/de/api_v4/users/759/contact_data.json"
      }
    ]
  },
  "message": "Ich bin zweimal in Bolivien gewesen, auch in El Alto und im COMPA, und ich habe gesehen, wie schwer das (Über-)leben für viele Leute ist. Wie wichtig Bildung ist, sollte ich als ehemalige Lehrerin ja wissen.... Das hier vorgestellte Projekt erinnert mich an die Fahrbibliotheken in der ehemaligen DDR; und wenn hier benachteiligten Kindern und Jugendlichen in Gegenden ohne kulturelle Infrastruktur eine adäquate Form von Bildung ermöglicht werden soll, ist das nur zu unterstützen. Nach meinen Möglichkeiten werde ich das Projekt unterstützen.",
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/projects/35/opinions/22.json"
    },
    {
      "rel": "project",
      "href": "https://api.betterplace.org/de/api_v4/projects/35.json"
    }
  ]
}
```

