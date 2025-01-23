# The betterplace.org API Version 4
This is the latest API for betterplace.org. It's a REST-style API that returns
JSON for serialization. It incorporates some ideas from [hypermedia APIs](https://www.google.de/search?q=hypermedia+api)
such as the link structure.
It is split into a public, unauthenticated API and a private, authenticated Client-API. The public API is getting deprecated.

### Table of Contents
1. [Public API](#public-api) (⚠️ deprecated ⚠️)
   - [Endpoints](#endpoints-public-api)
2. [Client API](#client-api)
   - [Client Authentication](#client-authentication)
   - [Client Projects](#client-projects)
   - [Endpoints](#endpoints-public-api)
3. [Technical Details](#technical-details-applying-to-public-api-and-client-api)
   - [Request Parameter Format](#request-parameter-format)
   - [Addressing the Locale of a Resource](#addressing-the-locale-of-a-resource)
   - [Pagination](#pagination)
   - [Sanitization](#sanitization)
   - [Picture Formats](#picture-formats)
   - [HTTP Status Codes](#http-status-codes)
   - [Error Messages](#error-messages)
   - [Known Issues](#known-issues)
   - [API Client Libraries](#api-client-libraries)
   - [Changelog](CHANGELOG.md)
   - [Code Examples](#code-examples)

## Public API
This Api is fully public and unauthenticated. While everybody is free to use it to build private projects based on it we reserve the rights to throttle as we see fit in case of aggressive polling. It only includes public data which would also be found on public pages of the betterplace.org site.

### ⚠️ This api is slowly getting deprecated! ⚠️
This means:
* we will only fix bugs and provide support for registered clients who also use our client API.
* no new features will be added to it
* we do not take any responsibility if things you build based on it suddenly break
* there is no official EOL date and due to it's public and unauthenticated nature we might not have the possibility to inform you if we decide to discontinue providing this api

### Endpoints public api
- Projects
  - [Projects List and Search](sections/projects_list.md)
  - [Project Details](sections/project_details.md)
  - [Project Needs List](sections/needs_list.md)
  - [Project Need Details](sections/need_details.md)
  - [Project Blog Posts List](sections/blog_posts_list.md)
  - [Project Blog Post Details](sections/blog_post_details.md)
  - [Project Categories List](sections/categories_list.md)
  - [Project Opinions List](sections/opinions_list.md)
  - [Project Pictures List](sections/project_pictures_list.md)
  - [Project Picture Details](sections/project_picture_details.md)
- Fundraising Events
  - [Fundraising Events List and Search](sections/fundraising_events_list.md)
  - [Fundraising Events Details](sections/fundraising_event_details.md)
  - [Fundraising Event Opinions List](sections/opinions_list.md)
  - [Fundraising Event Featured Projects List](sections/fundraising_events_featured_projects_list.md)
  - [Fundraising Event Forwarding List](sections/fundraising_event_forwardings_list.md)
- Organisations
  - [Organisations List](sections/organisations_list.md)
  - [Organisation Details](sections/organisation_details.md)

## Client API
This API provides special features for companies and organisations as part of the services offered by our [betterplace solutions](http://www.betterplace-solutions.de).
This client access requires a special contract. Please [contact us](http://www.betterplace-solutions.de) with your questions.

### Client Authentication
Some features of the betterplace.org client API require your authentication.
* Please use your API Credentials to authenticate with [HTTP Basic Authentication](http://en.wikipedia.org/wiki/Basic_access_authentication#Client_side) username and password.
* Please use the special scope for clients that is described [above](#client-projects).
Username, password and client scope are provided as part of a contract with betterplace.org

### Client Projects
Clients projects are projects on betterplace.org that are associated with an api client as part of the services that betterplace.org provides for companies. This way clients can control what projects are visible on their external platform.

Some URLs have a special scope for clients. Examples:

* `/clients/example_client/projects`
  will only show projects of the client "example_client"
* `/clients/example_client/tags/rainforest/projects`
  will only show projects of the client "example_client" that are tagged with "rainforest".

If you request data for a project that is not part of the client
projects, the API will return an HTTP error code `404`.

### Endpoints client API
- Clients
  - [Client Details](sections/client_details.md)
  - [Client Project Statistics](sections/client_project_statistics.md)
  - [Client Fundraising Event Statistics](sections/client_fundraising_event_statistics.md)
- Donations
  - [Client Donation Pledge Creation](sections/client_donation_pledges_creation.md)
  - [Client Donation Pledge Status](sections/client_donation_pledge_status.md)
  - [Client Forwarding Request Creation](sections/client_forwarding_requests_list.md)
  - [Client Forwarding Request Status](sections/client_forwarding_request_details.md)
  - [Client Donations List](sections/client_donations_list.md)
  - [Client Pool Details](sections/pool_details.md)
- Contact Data
  - [User Contact Data Details](sections/contact_data_details.md)
- Projects
  - [Client Projects List and Search](sections/projects_list.md)
  - [Client Project Details](sections/project_details.md)
  - [Client Blog Posts List](sections/blog_posts_list.md)
  - [Client Mailing Subscriptions](sections/client_mailing_subscriptions.md)
- Tags
  - [Client Tags List](sections/client_tags_list.md)
  - [Client-Tag Projects List](sections/client_tag_projects_list.md)
  - [Client-Project Tags List](sections/client_project_tags_list.md)

## Technical details applying to Public API and Client API
* The API is https only, all non-https requests will be redirected accordingly
* The response format is JSON
* We support [Cross-origin resource sharing (CORS)](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing), so no proxy or JSONP is required

### Request parameter format
The `order` and `facets` request parameters accept multiple key-value pairs.
We use the same convention as the [Google Static Maps API V2](https://developers.google.com/maps/documentation/staticmaps/#URL_Parameters).

Example: `foo:bar|lorem:ipsum`

This way you may specify a primary and secondary sort order such as
`order=rank:DESC|created_at:DESC`, which will cause higher ranked objects to
come first and more recently created objects to come first if they have equal
rank.

* Split key and value by a colon `:`
* Split multiple key-value pairs by a pipe `|` (`%7C`)
* [URL-encode](http://de.wikipedia.org/wiki/URL-Encoding) all params, so the pipe becomes `%7C`
* Note that for readability reasons we don't URL-encode the params in this documentation


### Addressing the locale of a resource
* Some resources offer translated content. To access the translated content you
  need to set the lang-prefix in the API URL.
  `api_v4/de/projects/…` returns the German translations while
  `api_v4/en/projects/…` return the English ones. Non-translated
  content will fall back to the original content language.
  We currently support content with German and English translations.
* The same pattern applies to creating resources for a specific language.


### Pagination
All list requests can be paginated with the following parameters.

<table>
  <tr>
    <th>Parameter</th>
    <th>Description</th>
    <th>Default</th>
  </tr>
  <tr>
    <td><code>page</code></td>
    <td>Used to paginate through the list</td>
    <td>1</td>
  </tr>
  <tr>
    <td><code>per_page</code></td>
    <td>The number of entries per page</td>
    <td>20</td>
  </tr>
</table>

The <code>per_page</code> parameter is capped at 200. Any higher value for <code>per_page</code> grants at most 200 results.

The following attributes are returned in all list view responses:

<table>
  <tr>
    <th>Attribute</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><code>total_entries</code></td>
    <td>Count of all entries</td>
    <td>23</td>
  </tr>
  <tr>
    <td><code>offset</code></td>
    <td>The number of entries that are skipped before the current listing begins, <code>= max(page - 1, 0) * per_page</code></td>
    <td>0</td>
  </tr>
  <tr>
    <td><code>total_pages</code></td>
    <td>Count of all pages, based on <code>per_page</code></td>
    <td>42</td>
  </tr>
  <tr>
    <td><code>current_page</code></td>
    <td>What page we are on</td>
    <td>1</td>
  </tr>
  <tr>
    <td><code>per_page</code></td>
    <td>Number of entries per page</td>
    <td>20</td>
  </tr>
</table>


### Sanitization
Every string attribute returned in a JSON document is sanitized HTML. By
default only ```a, b, br, em, i, li, ol, p, strong, ul``` tags are allowed.
If an attribute allows for a different set of tags it is specified in the
documentation of this field under the "Response Attributes" headline.
We might adapt the allowed this set of tags at any time without further notice,
e.g. to avert upcoming security problems.


### Picture formats
Please note that all over the API only the `original` image version will always
be available. There are additional image versions for various entities, e.g.
fill_960x500 for projects. You can use these versions, but they might change in
the future!


### HTTP Status Codes
The following HTTP result codes can be returned:

* [HTTP Code `200`](http://httpstatus.es/200)
  if all is good and
  [HTTP Code `304`](http://httpstatus.es/304)
  if this good thing has not been modified (based on ETag).
* [HTTP Code `201`](http://httpstatus.es/201)
  if a resource was created successfully.
* [HTTP Code `202`](http://httpstatus.es/202)
  if a resource was successfully submitted for delayed processing.
* [HTTP Code `400`](http://httpstatus.es/400)
  if a requested resource could not be created or updated,
  if the submitted data was invalid.
* [HTTP Code `401`](http://httpstatus.es/401)
  if a resource requires [client authentication](#client-authentication)
  but the authentication failed.
* [HTTP Code `403`](http://httpstatus.es/403)
  if a resource requires [client authentication](#client-authentication)
  but no client was authenticated.
* [HTTP Code `404`](http://httpstatus.es/404)
  if a requested resource could not be found.
  Also used for projects that are not part of a given client scope.
* [HTTP Code `422`](http://httpstatus.es/422)
  if the submitted resource could not be accepted due to erroneous parameters.
* [HTTP Code `500`](http://httpstatus.es/500)
  if a software error on the server was encountered.
* [HTTP Code `503`](http://httpstatus.es/503)
  if the server is unavailable due to high load.

### Error Messages
If an error occurs, a JSON response message is returned with a `name` and `reason` (optional).
Clients that use the betterplace.org staging environment will also see a
`backtrace` and `message` property.

Example:

```json
{
  "name": "GeneralError",
  "status": "not_found",
  "status_code": 404,
  "reason": "Record Not Found",
  "backtrace": [
    "/path/to/file:23:in 'method'",
    "/path/to/file:42:in 'method2'"
  ],
  "message": "Couldn't find Project with id=666",
  "links":[]
}
```

If errors occur during the creation process of a resource, the answer will
contain helpful information about how to resolve the issue. Please note
that this information is not meant to be used in your application directly
but only for your development process. We might change the specs for the
error response at any time without further notice.

Example with validation errors:

```json
{
  "name": "GeneralError",
  "status": "unprocessable_entity",
  "status_code": 422,
  "reason": "Cannot Process Submitted Data",
  "backtrace": [
    "/path/to/file:23:in 'method'",
    "/path/to/file:42:in 'method2'"
  ],
  "message": "First name Dies ist ein Pflichtfeld",
  "errors": { "first_name": [ "Dies ist ein Pflichtfeld." ] },
  "links":[]
}
```

### Known issues
Please contact api@betterplace.org for more information

* Documentation: Not all resources have a documentation URL as part of the JSON response
* Documentation: The response table does not show the root documentation for response elements with sub-elements (for example carrier.name is documented but carrier is not)


### API Client Libraries
While we currently do not offer any official client API libraries, [Duilio Ruggiero](https://github.com/sinetris) implemented the prototypical ruby client [bettery](https://github.com/sinetris/bettery).

We would love to hear from you if you plan to use/extend bettery or implement your own client and publish the code.


### Code examples
* [Using the API with PHP](https://gist.github.com/svjv1160/7749784)
* [WordPress Plugin by freifunk](https://github.com/freifunk/www.freifunk.net/tree/master/wp-plugins/betterplace-project-table) which [shows the freifunk projects as a table](http://spenden.freifunk.net)
* _Please send us your code examples to api@betterplace.org_
