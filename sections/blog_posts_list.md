
# Blog Posts List ⇄ [Details](blog_post_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1114/blog_posts.json?fundraising_event_id=19267
```

A list of the blog posts of a betterplace.org project or fundraising event.
Results are contained in a *data* attribute.

Recommended order is `&order=published_at:desc`.

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

Project id as an integer number.

</td>
  </tr>
  <tr>
    <th align="left">fundraising_event_id</th>
    <td><code>19267</code></td>
    <td>no</td>
<td>

Fundraising Event id as an integer number.

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
      <th align="left">published_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

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
      <td><code>null &#124; object</code></td>
      <td><code></code></td>
<td>

The user that wrote the blog post.

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
  "total_entries": 103,
  "offset": 0,
  "total_pages": 52,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 3900,
      "created_at": "2009-03-10T13:21:31+01:00",
      "updated_at": "2020-09-07T11:22:14+02:00",
      "lang": "de",
      "type": "BlogPost",
      "title": "Skateistan in N24",
      "published_at": "2009-03-10T13:21:31+01:00",
      "body": "<p>Kommenden Freitag (13.03.), 12:30 Uhr, gibt es eine halbe Stunde Skateistan auf dem Nachrichtensender N24. Reinschauen lohnt sich!</p>",
      "author": {
        "id": 9238,
        "name": "Kiana Schulz (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/009/238/fill_100x100_bp1584570257_original_maxn_skate.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/009/238/crop_original_bp1584570257_original_maxn_skate.jpg"
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
          "href": "https://api.betterplace.org/de/api_v4/blog_posts/3900.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-unterstuetze-skateistan-sport-bildung-fuer-kinder/news/3900"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    },
    {
      "id": 3917,
      "created_at": "2009-03-11T20:46:27+01:00",
      "updated_at": "2020-09-07T11:22:09+02:00",
      "lang": "de",
      "type": "BlogPost",
      "title": "Mirwais",
      "published_at": "2009-03-11T20:46:27+01:00",
      "body": "<p>Wir haben unsere erste Unterstützung erfahren - vielen Dank dafür auch im Namen von Mirwais, der dadurch seine Arbeit für Skateistan fortsetzen kann. An dieser Stelle möchte ich Mirwais etwas näher vorstellen: </p>\r\n<p>INTERVIEW WITH Mirwais Ghulam Mohammad</p>\r\n<p>HOW DID YOU FIND OUT ABOUT SKATEBOARDING?\r\nI was washing cars in Macrorayan when I first saw Oliver, Sharna, Shams, Mirwais and Moneer skating. I left the car I was washing and went to join the other children playing on the skateboards. I really liked it the first time. From then on, every time I saw Oliver and the others riding their motorcycles piled high with skateboards I would leave the cars and go to them to practice skating. After some months, Oliver asked me to join the Skateistan team.</p>\r\n<p>WHAT WERE YOU DOING BEFORE JOINING THE SKATEISTAN TEAM? \r\nBefore joining Skateistan, I was washing cars for 7 years. I had a number of special customers who would look for me, four foreigners and eighteen Afghans. For a four-wheel drive, I would make 80 Afghanis (around 1 Euro) for one hours work. I wash between 3 and 4 cars on a good day but I have to pay 20% of my wages to the guards who work nearby so they could buy tobacco. They are much bigger than me! In winter it was an especially difficult job to clean the cars as it is often below freezing and it is hard to scrape the ice from under the cars.</p>\r\n<p>WHAT IS YOUR ROLE IN SKATEISTAN? \r\nI have been working for Skateistan for one and a half months. I am very happy in my job, I take care of the Skateistan office and guesthouse and make sure all the equipment is clean and oiled, ready for skating. When we teach the children, it is my job to help them as much as possible and make sure everyone is sharing the boards. I teach the boys new tricks and collect all the boards at the end of each session.</p>\r\n<p>WHAT DO YOU LIKE BEST ABOUT SKATEBOARDING?\r\nI like learning how to ollie, drop off ledges and skate fast around the transition of the fountain that we skate. My favourite trick is to ollie and I practice this as much as I can in my spare time. I can now ollie almost 20 cm off the ground.</p>\r\n<p>DO ANY OF YOUR SIBLINGS SKATE? \r\nTwo of my younger brothers are skating. They wanted to learn after watching me skate. Now I teach them how to drop into the fountain, how to ollie and how to skate fast around the transition of the fountain.</p>\r\n<p>WHAT DO YOU THINK OF SEEING FEMALE SKATEBOARDERS IN KABUL? \r\nI think it is good that there are girls skating. When I first saw the girls skating, it inspired me to try harder so I could be as good as them. Some of the girls skate better than the boys!</p>\r\n<p>WHAT WOULD YOU LIKE TO DO IN THE FUTURE? \r\nI would like to keep skateboarding and eventually become the champion skater of Afghanistan!</p>\r\n<p>Mirwais Ghulam Mohammad is 16 years old and has four brothers and three sisters.</p>",
      "author": {
        "id": 9238,
        "name": "Kiana Schulz (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/009/238/fill_100x100_bp1584570257_original_maxn_skate.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/009/238/crop_original_bp1584570257_original_maxn_skate.jpg"
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
          "href": "https://api.betterplace.org/de/api_v4/blog_posts/3917.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-unterstuetze-skateistan-sport-bildung-fuer-kinder/news/3917"
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

