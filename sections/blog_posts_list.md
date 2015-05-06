
# Project Blog Posts List ⇄ [Details](blog_post_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/projects/1114/blog_posts.json
```

A list of betterplace.org projects blog posts.
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**

* _Project-Blogposts:_ There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.

* _All Blogposts:_ Clients can retrieve a list of all blogpost of all client-projects:
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
    <td>yes</td>
    <td>Project-id as an integer number ≥ 14.</td>
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
      <th align="left">lang</th>
      <td>string</td>
      <td>en</td>
      <td>Blog posts have only one language at the moments</td>
    </tr>
    <tr>
      <th align="left">type</th>
      <td>string</td>
      <td>PayoutBlogPost</td>
      <td>Blogposts can be created by a user <code>BlogPost</code>
to update your donors about new developments
or as part of the payout process <code>PayoutBlogPost</code>
where you tell what needs you payed our and
what you plan to do with the money.
</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>Thank you from Beijing</td>
      <td></td>
    </tr>
    <tr>
      <th align="left">body</th>
      <td>string</td>
      <td>I am so happy to hear about the first donation for the Good Gifted Garden. If I told Chun …</td>
      <td>The body has html like links, embeded videos, pictures.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="payout-ref" href="#payout">
            ↓payout
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td></td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="author-ref" href="#author">
            ↓author
          </a>
        </th>
      <td>string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke"
</td>
    </tr>
  </table>
### <a id="payout" href="#payout-ref">↑Nested Attributes: payout</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="payout.needs-ref" href="#payout.needs">
            ↓payout.needs
          </a>
        </th>
      <td>array</td>
      <td>TODO</td>
      <td>TODO</td>
    </tr>
  </table>
### <a id="payout.needs" href="#payout.needs-ref">↑Nested Attributes: payout.needs</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">payout.needs.need_title</th>
      <td>string</td>
      <td>Schoolbooks</td>
      <td>Title of the need</td>
    </tr>
    <tr>
      <th align="left">payout.needs.payout_amount_in_cents</th>
      <td>string</td>
      <td>2300</td>
      <td>Amount paid out to that need</td>
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
(<a href="blog_post_details.md">blog post details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">documentation</th>
      <td>Link to this resource in the documentation
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
  "total_entries": 0,
  "offset": 0,
  "total_pages": 0,
  "current_page": 1,
  "per_page": 2,
  "data": [

  ]
}
```

