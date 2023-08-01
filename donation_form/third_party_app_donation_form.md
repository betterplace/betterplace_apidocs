# ThirdPartyApp custom donation form for organisations (BETA)


*BETA: This is the second draft of this documentation. Please send us feedback at product@betterplace.org. Or via pull request. Thanks!*


## Introduction

The ThirdPartyApp custom donation form allows a deep integration of the betterplace.org donation process into your organisations web application.

It is meant for organisations that want to develop and maintain a custom donation experience for their donors.

This feature is distinct from our [json-API v4](https://github.com/betterplace/betterplace_apidocs) which you can use to fetch data from the betterplace.org platform.


### Example Integrations

* [Gaunting Live](https://www.gauting.live/), to support culture in Gauting during the pandemic.
* [Ablass App](http://www.ablass-app.de/), where you can clean your conscience.
* [Tramprennen](https://tramprennen.org/) and [Floßrennen](http://flossrennen.tramprennen.org/) ([GitHub](https://github.com/Club-of-Roam/cor-mgmt)) is a race where you can support one of the teams.
* _(Closed)_ [Donatify me](http://donatify.me/), where you can get Edward to do stuff for you.
* _(Closed)_ [MADAide](http://madaide.org/?page_id=578), where you can donate to mark a specific piece of the football field with your name.
* _(Closed)_ [Seeds of Kindness 3](http://yoursiblings.org/portico/seeds-of-kindness-3), where you get a mp3 download link after your donation. Also there is a leader board and referrer-system.
* _(Closed)_ [Tierheim Berlin](http://www.tierheim-geschenke.de/), where you can view and donate to specific needs of the project.


### UserFlow

This is a typical user flow when you use the ThirdPartyApp custom donation form for organisations:

1. A donor visits your web application
2. You direct the user to your donation area
3. … and from there to the custom donation form on betterplace.org
4. The donation takes place on betterplace.org
5. We redirect the user back to your page and provide callback parameters


### Alternative solutions

Before you start considering the ThirdPartyApp custom donation form please make sure to check out the other online donation tools that betterplace.org provides. Especially the integrated donation form (iFrame). For more, please visit the [German](https://support.betterplace.org/hc/de) or [English help area](https://www.betterplace.org/c/help).



## How to get it

The ThirdPartyApp donation form needs to be set up by betterplace.org.

Please make sure that you can agree to [the terms of use](#terms-of-use) below and send us an email with the following information at product@betterplace.org.

We will check your proposal and get back to you. This is a special service in testing and in beta – so no promises!

**E-Mail:** (all data is required)

```
* Project url: The URL to your betterplace.org's project.
* Description: A short description of the web application that you plan on building.
* Callback url production: The URL that we redirect users to after a successful donation (see 'How to use it').
* Callback url staging: This is optional. betterplace.org can provide a staging system that uses this staging callback url.
* Contact e-mail: To keep you posted about changes.
```


## Terms of use

This is a special service in testing. Nothing is final or fixed. And it's beta. So don't say we didn't warn you!

* There is no support from the betterplace.org team for this feature other than this documentation
* All terms of use and privacy policy of betterplace.org apply
* We will inform you about changes 7 days ahead via the e-mail address that you provided
* Should we consider discontinuing this service we will inform you 3 month ahead
* The code that you write to integrate this donation form in your flow has to be open sourced under Apache License 2.0 for everyones benefit



## How to use it

After everything is set up by betterplace.org (see [How to get it](#how-to-get-it)), you just need to construct the donation form URL and make sure your callback URL can handle the response.


### Donation form URL and input parameter

*Example:*
<pre>
https://www.betterplace.org/de/donate/ablass/projects/480?client_reference=wZo2aZCjJHA2CONAXxIQHt&donation_amount=40
</pre>

<table>
  <tr>
    <td>
      <code>https://www.betterplace.org/</code>
    </td>
    <td>
      Lets start with the domain.
    </td>
  </tr>
  <tr>
    <td>
      <code>en/</code>,
      <code>de/</code>
    </td>
    <td>
      The language for the form.
    </td>
  </tr>
  <tr>
    <td>
      <code>donate/YOUR_APP_ID/</code>
    </td>
    <td>
      The path to the donation form. <code>YOUR_APP_ID</code> will be provided by betterplace.org (see <a href="#how-to-get-it">How to get it</a>).
    </td>
  </tr>
  <tr>
    <td>
      <code>projects/1114</code>,
      <code>fundraising-events/seeds-of-kindness-3</code>
    </td>
    <td>
      The receiver type and id.
    </td>
  </tr>
  <tr>
    <td>
      <code>?client_reference=123</code>
    </td>
    <td>
      OPTIONAL – but this is basically why you would want to use the ThirdPartyApp donation form in the first place! It allows you to give each donation/donor a unique ID in your application. We will send this ID back to you via the callback url. This way you can track which donation went through. This reference should be url safe, e.g. only consist of alphanumeric symbols like a SHA-1 Hash.
      <br/><strong>Watch out:</strong> This field must be blank or provide a <em>unique</em> identifier. Using the same identifier twice will prohibit donations. Please keep that in mind if you create sharing urls that contain parameters. If you choose to provide a client_reference, you can use this value to look up the donation afterwards (see <a href="#handling-the-post-donation">Handling the post donation</a>).
    </td>
  </tr>
  <tr>
    <td>
      <code>&donation_amount=40</code>
    </td>
    <td>
      OPTIONAL: You can pre-set the donation amount in euro.
    </td>
  </tr>
</table>

Please not that the ThirdPartyApp custom donation form does not allow color and layout changes. If you need those, consider using the [integrated donation form (iFrame)](#alternative-solutions).



### Redirect URL and response parameter

This URL is part of the configuration that needs to be done by betterplace.org (see [How to get it](#how-to-get-it)). We will redirect the donor to this URL after a successful donation. We will also extend the URL with the following reponse parameter.

*Cool urls dont change:* We cannot change this URL after we created you ThirPartyApp ID. Please consider redirecting inside your application.

*Example:*
<pre>
https://www.you-app.cool/callback.php?status=DONATION_COMPLETE&donation_client_reference=wZo2aZCjJHA2CONAXxIQHt
</pre>

<table>
  <tr>
    <td>
      <code>https://www.you-app.cool/callback.php</code>
    </td>
    <td>
      The callback URL you provide
    </td>
  </tr>
  <tr>
    <td>
      <code>?status=DONATION_COMPLETE</code>
    </td>
    <td>
      The status which tells you all is good. It’s a bit redundant since there is only this one status ;-)
    </td>
  </tr>
  <tr>
    <td>
      <code>&donation_client_reference=123123</code>
    </td>
    <td>
      The same value that you provided when opening the donation form via <code>donation_client_reference</code>
    </td>
  </tr>
  <tr>
    <td>
      <code>&receiver_type=project&receiver_id=1114</code>,
      <code>&receiver_type=group&receiver_id=seeds-of-kindness-3</code>
    </td>
    <td>
      The receiver type and id that you specified when opening the form. "FundraisingEvent" stands for "Fundraising Event".
    </td>
  </tr>
  <tr>
    <td>
      <code>&amount=6</code>
    </td>
    <td>
      The amount that was actually donated. This corresponts to <code>donation_amount</code> unless the user changed it.
    </td>
  </tr>
  <tr>
    <td>
      <code>&donation_token=STRING</code>
    </td>
    <td>
      A unique token generated by betterplace.org that identifies this donation in our system. You should store this token in your application (see <a href="#handling-the-post-donation">Handling the post donation</a>).
    </td>
  </tr>
</table>



## Handling the post donation

Once you the user clicked on your donation link, there are a number of things that can happen.

Should your application rely on a sum or count of valid donations (for things linke a leader board or a specific way to display a valid donation for example), you need to take care of those things in your application:


```
User opens the ThirdPartyApp donation form with your client_reference
┣ User donates successfully
┃ ┣ Redirect takes place → Case 1
┃ ┗ Redirect breaks → Case 2
┗ User goes away or donation fails → Case 2
```


### Post donation case 1: Reconcilitian

*Szenario:* The user donated successfully and the redirect took place.

*Result:* You receive the DONATION_SUCCESS message via the redirect URL.

You can be sure that the donation was successfully processed and is saved in the betterplace.org database. BUT: There are a few ways that this donation might be canceled again later (by the bank or the user most likely).

*Next steps:* You need to check for at least 14 days if the donation stays "confirmed".

* Option 1: Use the [client_donation_details](../sections/client_donation_details.md) API with the **donation_token** (see [Response parameter](#redirect-url-and-response-parameter)).
* Option 2: Use the [client_donations_list](../sections/client_donations_list.md) API and search for your **client_reference**

The donation is (still) valid, if there is an API response with a **state:"confirmed"** attribute.
The donation is invalid if the API response is a 404 (donation_token) or an the search is empty (client_reference).

Usually the state of a donation will only change during the first 14 days. In some cases however the bookback might take place later. Therefore the trigger to check the donations should probably not be time-based but based on the `open_amount_in_cents` from the [projects-json api response](../sections/project_details.md). Whenever this number changes whithout you getting new donations, you need to check the reconciliation of all donation.

### Post donation case 2: Unknown state

*Szenario A:* The user does not donate and leaves – for whatever reason.
*Szenario B:* The user donated successfully but the redirect _breaks_ (network connectivity, user cancels request, …).

*Result:* You don't know nothing about what's going on. Most importantly: You cannot be sure the donation did _not_ take place.

*Next steps*: Use the [client_donations_list](../sections/client_donations_list.md) API and search for the **client_reference** that you created once the user clicked on the link to the donation form on your website. You should save the client_refernce for this reason when you generate the link (not just when you receive the callback). You should also wait for at least two minutes before you recheck to give the user time to submit the donation.



## Clients of betterplace.org / Whitelabeling

The core for this ThirdPartyApp donation form is the technology that runs our client donation forms. The main difference being, that client donation forms are always whitelabeled to fit the design of the client application. Please get in touch for more information.



## Feedback

Please send us feedback at product@betterplace.org
