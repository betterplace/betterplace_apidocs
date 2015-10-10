![betterplace.org](images/betterplace.jpg "betterplace.org")

# The betterplace.org API Version 4

This is the latest API for betterplace.org. It's a REST-style API that returns
JSON for serialization.
It incorporates some ideas from [hypermedia apis](https://www.google.de/search?q=hypermedia+api)
like the link-strukture.


#### Please provide feedback
Please don't hesitate to provide any feedback about the API and this documentation
at developers@betterplace.org.


#### Mailing list for service announcements
Please send an email to product@betterplace.org to
subscribe to the api-v4-mailing list to receive service announcements
about updates and scheduled downtimes.


## Table of content

0. **General information** [↓ below](#general-information)
  0. Request Parameter Format [↓ below](#request-parameter-format)
  0. Addressing the locale of a resource [↓ below](#addressing-the-locale-of-a-resource)
  0. Pagination [↓ below](#pagination)
  0. Picture formats [↓ below](#picture-formats)
  0. HTTP Status Codes [↓ below](#http-status-codes)
  0. Error Messages [↓ below](#error-messages)
  0. [Changelog](CHANGELOG.md)
  0. Known issues [↓ below](#known-issues)
  0. API Client Libraries [↓ below](#api-client-libraries)
  0. Code examples [↓ below](#code-examples)
  0. Example apps [↓ below](#example-apps)

2. **Public API**
  1. **Projects**
    1. [**Projects** List and Search](sections/projects_list.md)
    1. [**Project** Details](sections/project_details.md)
    1. [Project **Needs** List](sections/needs_list.md)
    1. [Project **Need** Details](sections/need_details.md)
    1. [Project **Blog Posts** List](sections/blog_posts_list.md)
    1. [Project **Blog Post** Details](sections/blog_post_details.md)
    1. [Project **Opinions** List](sections/opinions_list.md)
    1. [Project **Opinion** Details](sections/opinion_details.md)
    1. [Project **Pictures** List](sections/project_pictures_list.md)
    1. [Project **Picture** Details](sections/project_picture_details.md)
  1. **Fundraising Events**
    1. [**Fundraising Events** List and Search](sections/fundraising_events_list.md)
    1. [**Fundraising Events** Details](sections/fundraising_event_details.md)
    1. [Fundraising Event **Opinions** List](sections/opinions_list.md)
    1. [Fundraising Event **Opinion** Details](sections/opinion_details.md)
    1. [Fundraising Event **Featured Projects** List](sections/fundraising_events_featured_projects_list.md)
    1. [Fundraising Event **Forwarding** List](sections/fundraising_event_forwardings_list.md)
  1. **Volunteering**
    1. [**Volunteering** List and Search](sections/volunteering_list.md)
    1. [**Volunteering** Details](sections/volunteering_details.md)
  1. **Organisations**
    1. [**Organisations** List](sections/organisations_list.md)
    1. [**Organisation** Details](sections/organisation_details.md)
  1. **MatchingFunds**
    1. [**MatchingFunds** List](sections/matching_funds_list.md)
    1. [**MatchingFund** Details](sections/matching_fund_details.md)
    1. [MatchingFund **Projects** List](sections/matching_fund_projects_list.md)
  1. **FundraisingChallenge**
    1. [Fundraising Challenge **Contest** Details](sections/fundraising_challenge_contest_details.md)
    1. [Fundraising Challenge Contest **Results** List](sections/fundraising_challenge_contest_results_list.md)

3. **Client API** [↓ below](#client-api)
  0. Client Projects [↓ below](#client-projects)
  0. Client Authentication [↓ below](#client-authentication)
  0. [**Client** Details](sections/client_details.md)
  0. [**Client** Project Statistics](sections/client_project_statistics.md)
  0. [**Client** Fundraising Event Statistics](sections/client_fundraising_event_statistics.md)
  0. [**Client** Donations List](sections/client_donations_list.md)
  0. [**Client** Donor Contact Data](sections/donor_contact_data_details.md)
  0. [**Client** Donation Pledges](sections/client_donation_pledges.md) [:lock:](#client-api)
  0. [**Client** Mailing Subscribtions](sections/client_mailing_subscriptions.md) [:lock:](#client-api)
  0. [**Client** Projects List and Search](sections/projects_list.md) – 
      See client section [and "Client Projects"](#client-api)
  0. [**Client** Project Details](sections/project_details.md) – 
      See client section [and "Client Projects"](#client-api)
  0. [**Client** Blog Posts List](sections/blog_posts_list.md) – See client section
  0. [**Client** Project Opinions List](sections/opinions_list.md) – See client section
  0. [**Client** Tags List](sections/client_tags_list.md)
  0. [**Client**-Project Tags List](sections/client_project_tags_list.md)
  0. [**User** Contact Data Details](sections/contact_data_details.md) [:lock:](#client-api)

4. **Organisation API**
  1. [ThirdPartyApp custom donation form for organisations](donation_form/third_party_app_donation_form.md)


## General information

* The API is https only, all non-https requests will be redirected accordingly
* The response/response format is JSON
* We support [Cross-origin resource sharing (CORS)](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing), so no proxy or JSONP is required
* Authentication: Most api calls are public.
  Some client API feature require authentication. [Learn more](#client-authentication)
* Users, Companies and Portals are not part of the API at this moment.


### Request parameter format

The `order` and `facets` request parameters accept multiple key-value-parameter.
We use the same convention as the [Google Static Maps API V2](https://developers.google.com/maps/documentation/staticmaps/#URL_Parameters).

Example: `foo:bar|lorem:ipsum`

This way you may specify a primary and secondaray sort order like this
`order=rank:DESC|created_at:DESC`, which will cause higher ranked objects to
come first and more recently created objects come first if they have equal
rank.

* Split key and value by a colon `:`
* Split multiple key-value-parameter by a pipe `|` (`%7C`)
* [URL encode](http://de.wikipedia.org/wiki/URL-Encoding) all params, so the Pipe becomes `%7C`
* Note that for readability-reasons we don't URL encode the params in this documentation


### Addressing the locale of a resource
* Some resources offer translated content. To access the translated content you
  need to set the lang-prefix in the API-URL.
  `api_v4/de/projects/…` returns the german translations while
  `api_v4/en/projects/…` return the english translated content. Not translated
  content will fallback to the original content language.
  We currently support content with german or english translations.
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


### Picture formats

Please note that all over the API only the `original` version will always be available. There are more image versions
for different entities, e.g. fill_960x500 for projects. You can use these versions, but they might change in the future!

To avoid problems stay tuned and subscribe to the [Mailing list for service announcements ↑](#mailing-list-for-service-announcements).


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
  Also used for projects that are not part of a given client-scope.
* [HTTP Code `422`](http://httpstatus.es/422)
  if the submitted resource could not be accepted due to erroneous parameters.
* [HTTP Code `500`](http://httpstatus.es/500)
  if a software error on the server was encountered.
* [HTTP Code `503`](http://httpstatus.es/503)
  if the server is unavailable due to high load.


### Error Messages

If an error occurs, a JSON response messages is returned with a `name` and `reason` (optional).
Clients that use the betterplace.org-staging-environment will also see a
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

If errors occur during the creation process of a resource the answer will
contain helpful information about how to resolve the issues. Please note
that this information is not meant to be used in your application directly
but only for your development process. We might change the specs for the
errors-response at any time without further notice.

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

Please contact developers@betterplace.org for more information

* Documentation: Not all resources have a documentation-url as part of the json
* Documentation: The response-table does not show the root-documentation for response-elements with sub-elements (for example carrier.name is documented but carrier is not)
* Blogposts: There is no way yet to filter BlogPosts from PayoutBlogPost


### API Client Libraries

While we currently officially do not offer any client api libraries [Duilio Ruggiero](https://github.com/sinetris) implemented the prototypical
ruby client [bettery](https://github.com/sinetris/bettery).

We would love to hear from you if you plan to use/extend bettery or implement your own client and publish the code.


### Code examples

* [Using the API with PHP](https://gist.github.com/svjv1160/7749784)
* [WordPress Plugin by freifunk](https://github.com/freifunk/www.freifunk.net/tree/master/wp-plugins/betterplace-project-table) which [shows the freifunk projects as a table](http://spenden.freifunk.net)
* _Please send us your code examples to developers@betterplace.org_


### Example apps

* The "Deutsch Tansanische Partnerschaft" uses this API to present their betterplace.org projects right on their website: [Project list](http://www.dtpev.de/unterstuetzen/projekte), [Project details](http://www.dtpev.de/unterstuetzen/projekte/one-child-one-light)
* [The "Förderverein Freie Netzwerke e.V."](http://foerderverein.freie-netzwerke.de/spenden/) uses this API to present their betterplace.org projects right on their website.
* [The "Alfred-Kunze-Sportpark"](http://alfred-kunze-sportpark.de/teilziele.php) uses this API to present all needs for their one betterplace.org project right on their website.
* [The "Earthship Tempelhof"](http://www.earthship-tempelhof.de/#spenden) uses this API to embed our integrated donation form (iframe) with more information about the project status.
* _Please send us your sites to developers@betterplace.org_


## Client API

This API provides special features for companies and organisations as
part of the services offered by our [betterplace solutions](http://www.betterplace-solutions.de/#buergerzeitung).
This client access requires a special contract.
Please [contact us](http://www.betterplace-solutions.de/#buergerzeitung)
with your questions.


### Client Projects

Clients projects are projects on betterplace.org that are associated with a client-user.
This way clients can control what projects are visible on their plattform.

Some URLs have a special scope for clients. Examples:

* `/clients/example/projects`
  will only show projects of the example-client
* `/clients/example/tags/rainforest/projects`
  will only show projects of the example-client and tagged with "rainforest".

If you request data for a project that is not part of the client
projects, the API will return an HTTP error code `404`.


### Client Authentication

Some feature of the betterplace.org client API require your authentication.

* Please use your API Credentials to authenticate with [HTTP Basic Authentication](http://en.wikipedia.org/wiki/Basic_access_authentication#Client_side) username and password.
* Please use the special scope for clients that is described above.

Username, password and client-scope are provided as part of the contract with our
[betterplace solutions](http://www.betterplace-solutions.de/#buergerzeitung).


### Usage example

The local german newspaper "Trierischer Volksfreund"
has it's own donation portal at ["Meine Hilfe zählt"](http://www.meine-hilfe-zaehlt.de/).
All data are pulled from this api. In addition they use the betterplace.org
whitelabel donation form, which is another service betterplace.org provides for clients.


## API V1, V2, V3

betterplace.org has three deprecated APIs. For more information contact product@betterplace.org.


## About betterplace.org

Learn more about betterplace at https://www.betterplace.org/c/about-us/


## License of this documentation

See the [license file](LICENSE).


## Shareable URL

Share this docs with your friends and family:
[api-docs.betterplace.org](https://api-docs.betterplace.org)
