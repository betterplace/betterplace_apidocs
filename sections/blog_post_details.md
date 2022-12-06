
# Project Blog Post Details ⇄ [List](blog_posts_list.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1114/blog_posts/88972.json
```

The details of a blog post of a betterplace.org project.
The details and list view show the same data.

**For [betterplace.org clients](../README.md#client-api):**
There is no client-scoped URL.
Please use the API calls that are provided inside the client project _url_ response
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
    <td><code>1114</code></td>
    <td>yes</td>
<td>

Project id as an integer number.

</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>88972</code></td>
    <td>yes</td>
<td>

Blogpost id as an integer number.

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
  "id": 88972,
  "created_at": "2013-10-30T12:39:27+01:00",
  "updated_at": "2013-10-30T12:39:27+01:00",
  "lang": "en",
  "type": "BlogPost",
  "title": "First Climbing Contest Held in Afghanistan",
  "published_at": "2013-10-30T12:39:27+01:00",
  "body": "<p><img src=\"http://skateistan.org/sites/default/files/users/duncan.buck/1381505_10201192263663306_1801301726_n.jpeg\"><br></p>\n<p>On\r\n Saturday 28th September, Skateistan Kabul's volunteers and staff took \r\npart in the inaugural indoor climbing competition held at the facility, \r\nwith both girls and boys competing (ages 11-22). This was the 1st \r\nclimbing competition that has taken place at Skateistan and the 1st \r\nknown climbing contest held in Afghanistan!<br><br>The climbing \r\ncompetition had both female and male categories with contests that \r\nincluded speed climbing and fastest rope coil. The competition was \r\njudged by our amazing volunteer climbing teachers, including the \r\ncompetition organiser Gio Trambaiolo who has been instrumental in \r\nteaching climbing to the Skateistan volunteers. Gio has volunteered as a\r\n climbing teacher nearly each week for well over a year. Skateistan is \r\nextremely lucky to have such a wonderful team of dedicated volunteers, \r\nwho include around a dozen foreigners with certified climbing \r\nbackgrounds.</p>\n<p>\" Everyone did very well, it's amazing to\r\n see how the instructors and volunteers have progressed over the past \r\nfew months. \" - Gio, volunteer climbing teacher</p>\n<p>Each \r\nweek since June 2012, climbing lessons have been provided \r\nto Skateistan's Youth Leaders, who are Afghan staff and volunteers with \r\nthe project. They have learned climbing techniques, as well as built \r\nup trust and respect for each other through the sport. It is been \r\ninspiring to watch the volunteers develop as climbers and to see the \r\nhigh skill level our Youth Leaders have developed since the program took\r\n shape last year. Through the program, 14 young Afghans (50% girls) have\r\n received certificates to be Beginner Climbing Instructors, and they now\r\n facilitate climbing classes with more than 400 students who attend \r\nSkateistan.</p>\n<p>A brief prize ceremony was held the following week to \r\ngive the final results of the competition, as well as some prizes which \r\nwere given to everyone who participated.</p>We\r\n want to thank all the climbing volunteers who have created a hugely \r\nsuccesful sports program for our staff and students. We wish to thank \r\nGiovanni Trambaiolo, Sheilagh Henry, Kate Hughes, Mindy Visser, Colin R,\r\n Erin Blankenship, Jeffery Dow, Kelsey Noonan, Sarah-Jean \r\nCunningham, and Stephanie Faser. Your constant creativity and innovative\r\n training have made climbing one of the leading activities for the Youth\r\n Leaders at Skateistan. The development of students who attend your \r\nclasses has been a great pleasure to watch, and will benefit hundreds of\r\n children who will continue to be taught by their Afghan peers.<p><br><img src=\"http://skateistan.org/sites/default/files/users/duncan.buck/2013-09-24-peace-day-eventimg_1269.jpg\"></p>\n<p><br></p>\n<br>",
  "author": null,
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/blog_posts/88972.json"
    },
    {
      "rel": "platform",
      "href": "https://www.betterplace.org/de/projects/1114-unterstuetze-skateistan-sport-bildung-fuer-kinder/news/88972"
    },
    {
      "rel": "documentation",
      "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
    }
  ]
}
```

