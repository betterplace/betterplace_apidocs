<img src="images/betterplace.svg" alt="betterplace.org" width="400" />

# This documents covers betterplace APIs and api-like products

Betterplace offers 4 distinct types of apis and api like products.


## [API V4](api_v4_readme.md)
This is the latest API for betterplace.org. It's a REST-style API that returns JSON.
It is split into a public API which is free to use for everybody and a client API which requires a contract with betterplace but provides a range of additional features.
For more information click the following links
  - [Public API](api_v4_readme.md#public-api)
  This Api is fully public and unauthenticated. While everybody is free to use it to build private projects based on it we reserve the rights to throttle as we see fit in case of aggressive polling. It only includes public data which would also be found on public pages of the betterplace.org site.
  - [Client API](api_v4_readme.md#client-api)
  This API provides special features for companies and organisations as part of the services offered by our [betterplace solutions](http://www.betterplace-solutions.de). This client access requires a special contract.

## Iframe donation form
An Iframe donation form that can be embedded on your website to collect to donations through betterplace.org. this is only available to project or organisation managers of charities which are registered in Germany.
After your registration and creation of a project on betterplace.org you can generate a code snippet which you can embed on your website.
You can find more information by clicking on "Donation form"/"Spendenformular" in the project manage area or by following this link.

`https://www.betterplace.org/de/manage/projects/<your Project ID>/iframe_donation_form/new`

## Streaming Widgets and Donation Webhooks
You can use our public API to show donation statistics and other details of your fundraising event. But we also have out-of-the box features for livestreams that you can use.

These products include:
* Customizable streaming widgets to be included in OBS or other broadcasting software
  * Highest donation
  * Current donation volume
  * Last donor comments
  * Top Donor
  * Donor leader board
  * Alerts with gifs and sounds
  * Last donation
  * and many more... this part of the product is currently in active development
* Voting/Polling functionality to interact with your community
* Webhooks from betterplace.org to your system whenever your fundraising event receives a donation. Which can be used for sellout streams, alerts and similar customized functionality.

You can find more information and examples of streams like Friendly Fire and März mit Herz on our [dedicated page for streamers](https://www.betterplace.org/c/spenden-sammeln/charity-stream), watch our [livestream widget tutorial video](https://www.youtube.com/watch?v=3-DkrkkPC4o) or reach out to our team at charitystream@betterplace.org for expert support with your charity stream idea.

## Example apps
* "Deutsch-Tansanische Partnerschaft e.V." uses this API to present their betterplace.org projects right on their website: [Project list](http://www.dtpev.de/unterstuetzen/projekte), [Project details](http://www.dtpev.de/unterstuetzen/projekte/one-child-one-light)
* ["Förderverein Freie Netzwerke e.V."](http://foerderverein.freie-netzwerke.de/spenden/) uses this API to present their betterplace.org projects right on their website.
* ["Alfred-Kunze-Sportpark"](http://alfred-kunze-sportpark.de/teilziele.php) uses this API to present all needs for their one betterplace.org project right on their website.
* ["Earthship Tempelhof"](http://www.earthship-tempelhof.de/#spenden) uses this API to embed our integrated donation form (iframe) alongside information about the project status.
* _Please send us your sites to api@betterplace.org_

## About betterplace.org
Learn more about betterplace at https://www.betterplace.org/c/about-us/

## License of this documentation
See the [license file](LICENSE).

## Shareable URL
Share these docs with your friends and family:
[api-docs.betterplace.org](https://api-docs.betterplace.org)
