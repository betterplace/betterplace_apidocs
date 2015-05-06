# Changelog
All notable changes to the betterplace.org API v4 will be documented in this
file. Notifications about changes will also be send to the [mailing list for
service announcements](README.md#mailing-list-for-service-announcements).

## 2015-04-28
### Added
- Added API endpoint for clients to query donor data if permission was granted. See details at
  [**Client** Donor Contact Data](sections/donor_contact_data_details.md)

## 2015-04-07
### Added

- Added two API endpoints for client statistics.
  0. [**Client** Project Statistics](sections/client_project_statistics.md)
  0. [**Client** Fundraising Event Statistics](sections/client_fundraising_event_statistics.md)

## Deprecated
- [**Client** Details](sections/client_details.md): All statistic values. This end point will be removed after 31.5.2015

## 2015-03-05
### Added
- Added API endpoints for fundraising events and linked to them from all
  relevent resources. This includes related features for clients as well.
  See [here](sections/fundraising_events_list.md) and
  [here](sections/fundraising_event_details.md).

### Deprecated
- [Fundraising Events Details](sections/fundraising_event_details.md#response-links)
  - **profile_picture:** fill_618x322, fill_270x141
- [Fundraising Events List](sections/fundraising_events_list.md#response-links)
  - **profile_picture:** fill_618x322, fill_270x141
- [Matching Fund Projects List](sections/matching_fund_projects_list.md#response-links)
  - **profile_picture:** fill_618x322, fill_270x141
- [Project Details](sections/project_details.md#response-links)
  - **profile_picture:** fill_618x322, fill_270x141
- [Projects List](sections/projects_list.md#response-links)
  - **profile_picture:** fill_618x322, fill_270x141
- [Volunteering Details](sections/volunteering_details.md#response-links)
  - **profile_picture:** fill_618x322, fill_270x141
  - **image:** fill_618x322, fill_270x141, original, thumb, medium, regular
- [Volunteering List](sections/volunteering_list.md#response-links)
  - **profile_picture:** fill_618x322, fill_270x141
  - **image:** fill_618x322, fill_270x141, original, thumb, medium, regular

### Removed
- Nothing.

### Fixed
- Nothing.

## 2015-02-16
### Added
- Added client API endpoint for submit donation pledges to.
  See [here](sections/client_donation_pledges.md)
- Added client API endpoint to subscribe to project newsletters.
  See [here](sections/client_mailing_subscriptions.md).

### Deprecated
- Authentication via <code>api_token</code> parameter and <code>Api-Token</code> header is
  deprecated in favor of using basic authentication.

### Removed
- Nothing.

### Fixed
- Reworked order and hierarchy in readme.


## 2015-01-15
### Added
- Added the <code>around</code> parameter for project and volunteering
  listings, that sorts by distance to its value.

### Deprecated
- Nothing.

### Removed
- Nothing.

### Fixed
- Nothing.


## 2014-11-18

### Added
- Fallback flag for profile pictures to indicate whether the given picture is a
  default picture or was uploaded by the user

### Deprecated
- Nothing.

### Removed
- Nothing.

### Fixed
- Nothing.


## 2014-09-05

### Added
- Clarify the order behaviour for fundraising challenge results.

### Deprecated
- Nothing.

### Removed
- Nothing.

### Fixed
- Nothing.


## 2014-08-14

### Added
- This CHANGELOG, following the ideas of http://keepachangelog.com/
- Refactor the previous changelog to follow this convention.
- Update todo-note in table of content
- Add two more websites to "Example Integrations" for ThidPartyApp Donation
  Form

### Deprecated
- Nothing.

### Removed
- Previous Changelog in README

### Fixed
- Nothing.



## 2014-08-11

### Added
- Add Fundraising Challenge to API and Documentation

### Deprecated
- Nothing.

### Removed
- Nothing.

### Fixed
- Nothing.



## 2014-01 - 2014-04
This is the aggrgated changelog for all changes for this time interval.

### Added
* 2013-06-20: Add client.pool_balance_in_cents property, see doc for details
* 2013-06-14: Add platform-link to blog_posts-details
* 2013-05-15: Opinions have a link to the project now. All API-link are "api.betterplace.org" now (not www. anymore). Opinions have have a facets=has_message-Feature now.
* 2013-04-19: Change the naming of api-docu-files to follow rails-pluralization-convention.
* 2013-04-19: Added 'client project-tag list' (a list of all project-tags for a client) and 'client project-tag projects list' (a list of all projects for a client-project-tag).
* 2013-04-17: Add project pictures API. Please note the DEPRICATION warning for the project- and volunteering-profilepicture (sizes large, profile and thumb are deprecated and therefore renamed.)

### Deprecated
- Nothing.

### Removed
* 2014-03-04: Remove all deprecated picture links from responses.
* 2014-01-26: Remove the beta-flag; add matching-fund api; add code and usage examples; minor improvements

### Fixed
* 2013-04-18: Fixed project opinions. Add client opinions-feature. Note that many of the opinions-facets changed! Please re-read this part of the documentation.



## 2014-01 - 2014-04
This is the aggrgated changelog for all changes for this time interval.

### Added
* 2012-04-15: Add "Client Project-Tag Project List".
* 2012-03-03: Add picture size 'large' and 'original' to image list for projects. Please note that the images-part of the API ist still beta and might change slightly in the future.
* 2012-03-28: The project-list now returns the full result-set for each project. The minimal result set is gone for now but will be added later. The default-number of results changed to 20 for all lists.
* 2012-05~15: Add known issues, improve documentation, add opinion.donated_amount_in_cents, project.description returns html now
* 2012-03-13: Update TOC, fix opinions-details and -list response, fix empty documentation (@tordans)
* 2012-03-12: Several updates to readme, updates to descriptions for clients, updated opinions-docu, added know-issues and changelog sections (@tordans)

### Deprecated
- Nothing.

### Removed
* 2012-05~15: Removed opinion.with_donation

### Fixed
- Nothing.



## 2012-03-11

### Added
- Initial version (@betterplace)

### Deprecated
- Nothing.

### Removed
- Nothing.

### Fixed
- Nothing.



---

# Vorlage

## 2014-0x-xx

### Added
- Nothing.

### Deprecated
- Nothing.

### Removed
- Nothing.

### Fixed
- Nothing.
