The Betterplace API Version 4 (BETA)
============================================

This version of the API is not public at the moment!
============================================

Betterplace has a new version of its API. It's a REST-style API that returns
JSON for serialization.


Table of content
-----------------

Source: https://docs.google.com/a/betterplace.org/document/d/173m4jhzhUViX4D8qXcuQQAobvtbtMZTxSlXKe6J--SY/edit

- General information below

- [Volunteering Search and List, Volunteering Details](sections/volunteering.md)

- [Projects Search and List, Project Details](sections/projects.md)
–– todo: add sorting to list
–– todo: add client-filter to search, list, show
–– todo: add list-view with all the details needed to show the list-search-results without doing an n+1-query
–– todo: add "number_of_donors_for_last_14_days" to search results, based on supporter-table
–––– todo platform: Make sure the supporter-table update_at is actually set, so we really get the last-14-days-donors
–– todo: also add the "number_of_donors" (total), just because it makes sense
–– todo: add full-text-search on all projects (filtered for a client) (example http://www.volksfreund-servicecenter.de/projekte/suche/?suche=Kinder)
–– todo: add result-list for client-tags – maybe by making the client tag a special searchterm, maybe by adding it as a special facet
–– todo: add filter on project-list to only show projects that are financed 100% – this is a facet as well ATM

– [Need List](sections/needs.md)
–– todo: list all needs for a given project
–– todo: add filter "completed"/"uncompleted"
–– todo data: include all data in the list view, no details view for now

– [Donations List](sections/donations.md) – Spenden-Aktivität zeigen. Liste der letzten 8 Spenden auf alle Projekte, die dem Client zugewiesen sind nach Datum, Anzeige von Datum, Betrag, Projektittel, Link zum Projekt
–– todo: list donations
–– todo: add limit (=pagniation)
–– todo: add client-filter so list
–– todo: add sortierung

– [Blogpost List, Blogpost Details](sections/blogposts.md)
–– todo: list blogpost regardless of projects
–– todo: add client-filter to list (only blogposts of projects of the client)
–– todo: add filter for blogpost.type to allow excluding all payout_blogposts
–– todo data list:
––– blogpost.type = blogpost || payout_blogpost to the list-entries
––– title, language, receiver_type (project, fundraising_event, organisation), receiver_id
–– todo data details:
––– reminder: for payout_blogpost also include the table …
–– todo: add project-scope (only show blogposts of one project)

– [Organisations Details](sections/organisations.md)
–– todo: show the details of an organisation, no list ATM
–– todo data: name, lang, description, logo, manager_name, …

– [Client Details](sections/clients.md)
–– todo data details:
––– sum of all money needs on all associated projects
––– sum of all money collected on all associated projects
––– %-financed
––– sum of money still requested for all associated projects


Making a request
----------------

All requests have to be tunneled through **SSL** and their URLs start with
Betterdocs::Global


Response formats
--------------

- json via .json
– jsonp via .js or .jsonp with an optional `callback`-param

*TODO*


Authentication
--------------

All api calls are public at the moment.
There will be feature that require a authentication in the future.


API V1, V2, V3
--------------

betterplace has three depricated APIs. For more information http://www.betterplace.org/de/api/documentation/welcome


Example apps
--------------

*TODO*


About betterplace.org
--------------

*TODO*
