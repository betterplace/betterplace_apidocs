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

### Known limitation: `load_donation_iframe.js` pollutes the global lexical scope

The snippet that the portal generates includes a remote `<script src=".../load_donation_iframe.js" type="text/javascript">`. That bundle is a non-IIFE-wrapped script that declares roughly 150 single-letter `const`/`let`/`function` identifiers at top level — including a bare `$`, plus other very common single-letter names (`o`, `r`, `s`, `c`, `u`, `d`, `f`, `g`, `h`, `i`, `j`, `k`, `m`, `p`, `t`, `v`, `w`, `x`, `y`, `z`, …). In classic scripts (which is what the snippet uses), all top-level `let`/`const`/`class`/function declarations land in the shared **global lexical environment** of the realm.

Consequence: if any other classic script on the page also declares `let $ = …` or `const $ = …` at top level (a browser extension, a second `iframe-resizer` instance loaded by another plugin, a build artifact from another vendor, …), parsing fails at load time with:

```
Uncaught SyntaxError: Identifier '$' has already been declared
```

Because this is a *parse-time* error, the loader script never runs — so its `loadDonationIframe()` call never fires and the embedding container stays at the spinner forever. The error is reported against the file that loses the race (often a Google Maps API request `js?…&callback=…`), making the actual root cause non-obvious.

**Suggested upstream fix:** wrap the bundle output in an IIFE before it is served, e.g. `(function(){/* bundle */})();`. That keeps all declarations function-scoped and avoids polluting the global lexical environment entirely. Alternatively, serve the bundle as `<script type="module">`, which scopes top-level declarations to the module.

**Workaround for integrators:** until the upstream loader is wrapped, you can skip the JS loader entirely and embed the iframe directly. The URL shape that `getIframeSource()` in the loader builds is:

```
https://www.betterplace.org/<lang>/donate/iframe/<receiver_type>s/<receiver_id>
  ?background_color=<hex without #>
  &color=<hex without #>
  &donation_amount=<1–99>
  &bottom_logo=<true|false>
  &default_payment_method=<""|paypal|stripe|stripe_sepa_debit|apple_pay|google_pay>
  &default_interval=<single|monthly|yearly>
```

Example (project `4667`, default 10 €, accent color `6c9c2e`, one-off):

```html
<iframe
  src="https://www.betterplace.org/de/donate/iframe/projects/4667?background_color=ffffff&color=6c9c2e&donation_amount=10&bottom_logo=true&default_payment_method=&default_interval=single"
  title="Donation form for project 4667"
  loading="lazy"
  referrerpolicy="strict-origin-when-cross-origin"
  style="display:block;border:0;width:100%;max-width:600px;height:800px;background:transparent;">
</iframe>
```

Trade-off: without the bundled `iframe-resizer`, the iframe cannot auto-grow with the form, so a sensible fixed `height` (≈ 780–850 px covers Step 1 + donor-details comfortably) is set instead.

For WordPress sites, a community plugin that builds this URL via a shortcode and a Gutenberg block is available: **[s-a-s-k-i-a/betterplace-donation-embed](https://github.com/s-a-s-k-i-a/betterplace-donation-embed)** (GPL-2.0-or-later, minimal admin UI, no dependency on `load_donation_iframe.js`).

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

## About betterplace.org
Learn more about betterplace at https://www.betterplace.org/c/about-us/

## License of this documentation
See the [license file](LICENSE).

## Shareable URL
Share these docs with your friends and family:
[api-docs.betterplace.org](https://api-docs.betterplace.org)
