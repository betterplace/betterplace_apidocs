
# Blog Posts List ⇄ [Details](blog_post_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1114/blog_posts.json?fundraising_event_id=19267
```

A list of the blog posts of a betterplace.org project or fundraising event.
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**

* _Project Blogposts:_ There is no client-scoped URL.
Please use the API calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.

* _All Blogposts:_ Clients can retrieve a list of all blogpost of all client projects:
`/clients/PERMALINK/blog_posts.json`


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
<td>

Project id as an integer number ≥ 14.

</td>
  </tr>
  <tr>
    <th align="left">fundraising_event_id</th>
    <td><code>19267</code></td>
    <td>no</td>
<td>

Fundraising Event id as an integer number ≥ 1.

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
      <th align="left">lang</th>
      <td><code>string</code></td>
      <td><code>en</code></td>
<td>

Blog posts have only one language at the moment

</td>
    </tr>
    <tr>
      <th align="left">type</th>
      <td><code>string</code></td>
      <td><code>BlogPost</code></td>
<td>

Blogposts are always created by a user, and this
field always has the value <code>BlogPost</code>.


</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code>Thank you from Beijing</code></td>
<td>



</td>
    </tr>
    <tr>
      <th align="left">body</th>
      <td><code>string</code></td>
      <td><code>I am so happy to hear about the first donation for the Good Gifted Garden. If I told Chun …</code></td>
<td>

The body may contain html such as links, embedded videos, and picture or
any of the following HTML tags:
```a, b, br, div, em, i, iframe, img, li, ol, p, strong, ul```.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="author-ref" href="#author">
            ↓author
          </a>
        </th>
      <td><code>string</code></td>
      <td><code>"Till B."</code></td>
<td>

Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke"


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
      <th align="left">author.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">author.name</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Till B."</code></td>
<td>

Display name of a betterplace.org user.
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
      <td><code>object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
<td>

User profile picture or a fallback image

</td>
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
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

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
(<a href="blog_post_details.md">blog post details</a>)


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

documentation

</th>
<td>

Link to this resource in the documentation


</td>
    </tr>
    <tr>
<th align="left">

author.platform

</th>
<td>

The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.


</td>
    </tr>
    <tr>
<th align="left">

author.contact_data

</th>
<td>

The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.


</td>
    </tr>
    <tr>
<th align="left">

author.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

author.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 95,
  "offset": 0,
  "total_pages": 48,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 7019,
      "created_at": "2009-07-15T08:51:10+02:00",
      "updated_at": "2009-07-15T08:51:10+02:00",
      "lang": "en",
      "type": "BlogPost",
      "title": "Innovative support from a generous hairstylist",
      "body": "<p><br></p><p>Approximately one year ago, a young German hairstyling student read a piece about Skateistan. When she found herself working as a nurse in the German military hospital in Mazar-e-Sharif soon after, the skateboarding students of Kabul lingered in her mind. The soldier, Alexandra H., decided to use her skills to support Skateistan in any way she could — so she began to collect donations by giving haircuts to German soldiers serving in Afghanistan.</p><br><p>News of Alexandra’s “haircuts for a good cause” spread rapidly at Mazar-e-Sharif’s Camp Marmal. Before long, she had given 150 haircuts: at the end of June 2009, she generously handed all of the profits to Skateistan.</p><br><p>Alexandra, who has promised to continue her fundraising efforts for Skateistan when she returns to Germany, has quickly become one of the organization’s most innovative and committed supporters.</p><br>",
      "author": {
        "id": 9238,
        "name": "Maria Schmitz",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/009/238/fill_100x100_bp1575650048_original_maxn_skate.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/009/238/crop_original_bp1575650048_original_maxn_skate.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/9238"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/9238/contact_data.json"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/blog_posts/7019.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-unterstuetze-skateistan-sport-bildung-fuer-kinde-eyluel-camci/news/7019#ppp-sticky-anchor"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    },
    {
      "id": 8076,
      "created_at": "2009-08-18T21:19:02+02:00",
      "updated_at": "2009-08-19T09:38:56+02:00",
      "lang": "de",
      "type": "BlogPost",
      "title": "Sicherheitssets - durch Ihre Spenden finanziert -",
      "body": "<p>Im Bereich \"Fotos anschauen\" wurden Aufnahmen der trainierenden Kinder und Jugendlichen hochgeladen. Die <a href=\"../../../../pictures/0006/9710/69710.jpg\">Sicherheitsausrüstung</a>, die durch Ihre Spenden finanziert wurden, gehören selbstverständlich zu jedem Training dazu.</p><br><p> </p><br><p>Wir sagen an dieser Stelle noch einmal ganz herzlich \"DANKE\"</p><br><p>Das Skateistan-Team</p>",
      "author": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/blog_posts/8076.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-unterstuetze-skateistan-sport-bildung-fuer-kinde-eyluel-camci/news/8076#ppp-sticky-anchor"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    }
  ]
}
```

