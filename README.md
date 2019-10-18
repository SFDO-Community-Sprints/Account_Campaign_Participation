# Account_Campaign_Participation

### Project Name: Account Campaign Participation

### Project Team

* Team Leader(s): Julie Loyd
* GitHub Scribe(s): Tim Weeks
* List of all Contributors:
Julie Loyd
Tim Weeks
Gabriel Ehri
Beth Saunders
Adam Kramer
Megan Pietruszka
Matthew Poe

### Project Vision (Your first task as a team)
Allow users to track engagement via a Campaign with Organization Accounts.

Use Cases could include:
1- an organization needs to do direct mail or other engagement outreach to Accounts, for example churches, for whom they don't have a known good current Contact, but they have an ongoing relationship with the church as a corporate donor. They don't want to create proxy Contacts to tie to the Campaign because they create other issues (confusion, extra data storage, etc.)

2- an organization wants to send a mailing or other engagement to a Contact who may have both an individual donor/prospect relationship with them and an Affiliation to an Account being solicited for a corporate gift. The same person (Contact) may need to be engaged in both capacities in the same Cqmpaign/engagement. Campaign Members have to be unique within a Campaign.

This would also allow for generation of separate mailing list reports that clearly define those engagements that should be addressed with a business name/address vs. a personal one.

Salesforce has posted in the Success Community that this idea has been prioritized, and therefore, some functionality may be coming to the platform. We would like to, at the very least, document automations and UIs that would need to be created/updated in NPSP to work with Account Campaign Member functionality.


### Project Resources
* Here's an ERD sketch: 
https://www.lucidchart.com/documents/edit/ba4fbd1d-2ce2-4952-a313-770505ba49ed/0_0?shared=true

Notes:
Settings:
1 - Ability to define which Account Record Types should be considered "Organizations" for this function
2- Ability to enable/disable automations defined below

Automations that would need to be created (ideally in TDTM so that they could be managed via NPSP settings):
1 - Population of Account lookup on Account Campaign Member object if the Contact lookup is populated. Automation would look to the Primary Affiliation lookup on that Contact to identify the correct Account, and it would only populate if the Account lookup field is blank. 
2 - Population of Contact lookup on Account Campaign Member object if the Account lookup is populated. The automation would look to the Primary Contact field on the Organization Account, and it would only populate if the Contact lookup is blank.
3 - If the Account and Contact have an Affiliation, update the Role field on the Account Campaign Member record with the current Role from the Affiliation. If there are multiple Affiliations, it should look first for a Primary Affiliation. If there is one, use that. If there isn't, use the one with Status = "Current." If there are multuple Current, non-Primary Affiliations, leave the field blank.
4 - Update to NPSP automation that creates/updates Campaign Members auto Campaign Member update from Opportunity
5 - Rollup fields would need to be added to Campaign for Account Campaign Members to replicate current Campaign Member rollups. Then, formulas would need to be created to combine the Campaign Member and Account Campaign Member rollups. 
6 - If the automation still exists that pre-populates the Campaign on an Opportunity if a Campaign Member for that Contact exists, it would need to be updated to populate on an Account opportunity if the Account has an Account Campaign Member record

UIs/Utilities:
Add Account Campaign Members from a report of Accounts or Affiliations
Add a button for Account Campaign Member mailing list (redirects to a pre-built report, similar to NPSP Household Mailing List). The account campaign member button should NOT automatically de-duplicate, since the same account could have multiple contacts in the mailing list.

Unsolved questions/issues:
How do we keep Campaign Member and Account Campaign Member Statuses in sync?

### Project Team Accomplishments
We created an ERD and documented use cases, automation that would need to be created or updated, Utilities that would be nice to have, and unsolved questions. 

### Future Contributions (AKA what were you unable to finish at the Sprint)
Unknown - it would be great if someone wanted to pick this up and run with it, but it may be a good idea to see what is coming to platform, given the recent post in the Success Community (https://success.salesforce.com/_ui/core/chatter/groups/GroupProfilePage?g=0F93A000000Tudw&fId=0D53A00004Y3dDi - PDF posted in first Comment)

If platform implements something similar to what we are proposing

**Important**: If you have specific asks to help move this project forward we would recommend that you list them here, but also create separate Issues for each and add the label of "help wanted". This is a well-worn best practice for projects living in GitHub.

## Development

To work on this project in a scratch org:

1. [Set up CumulusCI](https://cumulusci.readthedocs.io/en/latest/tutorial.html)
2. Run `cci flow run dev_org --org dev` to deploy this project.
3. Run `cci org browser dev` to open the org in your browser.
