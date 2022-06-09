
# Client Donation Details ⇄ [List](client_donations_list.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/d0d35e347873169aec71.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

The details of a betterplace.org client donation.
The details and list view show the same data.


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
    <td><code>volksfreund</code></td>
    <td>yes</td>
<td>

The betterplace.org-internal client permalink.

</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>d0d35e347873169aec71</code></td>
    <td>yes</td>
<td>

The donation token that the client donation form passed to the
callback url or the client_reference that was provided by the client.


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
      <th align="left">amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>10100</code></td>
<td>

Donated amount in cents

</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td><code>string</code></td>
      <td><code>"confirmed"</code></td>
<td>

At the moment, all donations that are returned by the API are "confirmed".
Unconfirmed donations do not show up at all or disappear after they were revoked.
Revocations usually take place during the first 14 days – but there are no guarantees.

Please make sure to check for the "confirmed" state in your application explicitly since
we might add a "revoked" state in the future.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="donor-ref" href="#donor">
            ↓donor
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

Donor information, if available.


</td>
    </tr>
    <tr>
      <th align="left">message</th>
      <td><code>null &#124; string</code></td>
      <td><code>"This is a great project. In spring 2007 I travelled around the area together with my children and …"</code></td>
<td>

An optional message by users.

The body may contain html with any of the following HTML tags:
```b, br, em, i, li, ol, p, strong, ul```.


</td>
    </tr>
    <tr>
      <th align="left">token</th>
      <td><code>string</code></td>
      <td><code>ofMmTgfiPL-n1dDlNmFWqTQN</code></td>
<td>

A token uniquely identifies a donation on the platform.


</td>
    </tr>
    <tr>
      <th align="left">client_reference</th>
      <td><code>string</code></td>
      <td><code>922ec9b-etc</code></td>
<td>

Client Donations can be identified via a custom client reference token.

This <code>client_reference</code> can be provided by users of our
<a href="../donation_form/third_party_app_donation_form.md">
ThirdPartyApp custom donation form for organisations</a>, for example.


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
      <th align="left">receiver_type</th>
      <td><code>string</code></td>
      <td><code>"Project"</code></td>
<td>

Client donations may go to a <code>Project</code>,
a Project's <code>Element</code>, a <code>FundraisingEvent</code>,
a <code>Pool</code>.


</td>
    </tr>
    <tr>
      <th align="left">receiver_id</th>
      <td><code>number</code></td>
      <td><code>1114</code></td>
<td>

The id of the project, project element or fundraising event.

</td>
    </tr>
    <tr>
      <th align="left">receiver_title</th>
      <td><code>string</code></td>
      <td><code>"Skateistan Afghanistan"</code></td>
<td>

The title of the project, project element or fundraising event.

</td>
    </tr>
  </table>

### <a id="donor" href="#donor-ref">↑Nested Attributes: donor</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">donor.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">donor.name</th>
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
          <a id="donor.picture-ref" href="#donor.picture">
            ↓donor.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
<td>

User profile picture or a fallback image

</td>
    </tr>
  </table>

### <a id="donor.picture" href="#donor.picture-ref">↑Nested Attributes: donor.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">donor.picture.fallback</th>
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

receiver

</th>
<td>

Link to the <a href="project_details.md">project details</a>,
<a href="need_details.md">project need details</a>,
<a href="fundraising_event_details.md">fundraising event details</a>,
that is associated with this donation.<br>
Right now, there is no api end point for donations that are
redirect or donated to the client pool.


</td>
    </tr>
    <tr>
<th align="left">

self

</th>
<td>

Link to this resource itself
(<a href="client_donation_details.md">client donation details</a>)


</td>
    </tr>
    <tr>
<th align="left">

donor.platform

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

donor.contact_data

</th>
<td>

The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.


</td>
    </tr>
    <tr>
<th align="left">

donor.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

donor.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
</table>

## Response Example

```json
{
  "amount_in_cents": 1000,
  "state": "confirmed",
  "donor": null,
  "message": "",
  "token": "1f47f78e98ed63d5d1fe",
  "client_reference": null,
  "created_at": "2010-10-28T14:44:49+02:00",
  "receiver_type": "Project",
  "receiver_id": 4807,
  "receiver_title": "Kleinbus für den Palais e.V. Trier",
  "links": [
    {
      "rel": "receiver",
      "href": "https://api.betterplace.org/de/api_v4/projects/4807.json"
    },
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/1f47f78e98ed63d5d1fe.json"
    }
  ]
}
```

