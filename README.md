### AnonymousNPSP
How to deal with anonymous donors and donations in Salesforce NPSP

From Cloud for Good (2015)
https://cloud4good.com/announcements/handling-anonymous-donors-with-salesforce/

DONATION LEVEL ANONYMITY
Some donors just wish to have the occasional gift be anonymous for recognition purposes. In this instance, I recommend creating a custom checkbox field on the Opportunity object and checking that box for those gifts the donor has requested be anonymous. When it comes time to pull lists for your annual report, website, newsletter, donor wall or other form of recognition, make sure you include a filter to exclude those gifts.

DONOR LEVEL ANONYMITY
If the donor wishes to always be anonymous there are several ways you can structure that in Salesforce depending on the level of anonymity that is needed. If it is okay for your staff users to know who the donor is and you simply need to ensure that their gifts are not publicly recognized, you can create a custom field on the Account and Contact objects such as a checkbox called Anonymous and in the help text clarify that checking the box means the donor wishes for all of their gifts to remain anonymous. You would then make sure that any time you run lists or reports for recognition purposes you exclude these folks or, if you include anonymous gifts in your recognition lists, make sure the name is Anonymous on those.

If you have a combination of anonymous donors and anonymous gifts you could create a workflow rule that would automatically check the Anonymous box on the opportunity if the Anonymous box was checked on the Account. If the anonymity is indicated at the Contact level and not the Account level you’d need to create a trigger to automatically check the box on all Opportunities from that Contact.

You could also add a custom text field on Opportunities for recognition name. You could either manually complete that with the name the donor wishes to have used for recognition or you could create a workflow rule that fills that text field with Anonymous if the Anonymous checkbox  is checked or the account name from the Opportunity if it is not marked anonymous.

INVISIBLE DONORS
In the circumstance that the anonymous donor should not be visible to all users, things get a little more complicated. With profiles and field level security, you could prevent most users from being able to see a certain field. You wouldn’t want to do this with the standard name fields as obviously your users need to be able to see most donors’ names. What you could do is create a custom field on the Contact (and Account if needed) object for the person’s real name and limit access to this field to only those who should see it. Then you could assign a pseudonym to be used in the standard name fields – you’ll want to have a protocol for how those pseudonyms are created such as Anonymous DonorI, Anonymous DonorII, Anonymous DonorIII, etc. 

Another approach would be to hide all donation data for anonymous donations from all but a select group of users. To do that you would need to change the Organization Wide Default sharing settings to Private for Opportunities.Then you can create a sharing rule that shares all donations which are not marked Anonymous will all users. Then create another sharing rule that shares anonymous donations with the select group of users you wish to have access. Keep in mind when users who do not have access to anonymous donations run a report, it will not include anonymous donations in the totals. 

DONORS ANONYMOUS TO YOUR ORGANIZATION
Then there are situations where no one in your organization actually knows who the donor is. It could be a gift that came through on a third party donation website or cash that was dropped off, etc. In this case the most straightforward way to deal with these donations is to create an account named Anonymous and record all the donations against this account. I do not, however recommend this approach when your organization does know who the donor is.

Respecting a donor’s request for anonymity is critical to your relationship with your donors but your organization should retain the donor’s name and contact information when you have it so that if the donor asks for tax documentation you can provide that. And dumping all anonymous donors into one contact or account will help prevent data skew if you get a large number of these requests.

There are other methods you can use for dealing with anonymity. I have just shared those I use most often. If you have another strategy for dealing with anonymous donors please share it in the comments section below.

From StackExchange:
https://salesforce.stackexchange.com/questions/156877/stop-accounts-from-being-renamed-anonymous-household-with-npsp

I'm working with an education organization with the nonprofit starter pack installed. We're trying to create and update account records for the different colleges our students attend, but whenever we touch a record, it gets renamed to "Anonymous Household".

I'm 99% sure this is because we're using the older One-to-One account model which is causing the NPSP to do goofy things, but I'd like to avoid migrating to the recommended Household model if we can.

Any thoughts on how to resolve this?

Our current NPSP settings are...


Proposed approach for NPSP:
Anonymous Accounts:  Create two custom fields that solve two different problems.  ACTUAL ORGANIZATION (this field name should be changed to reflect the correct Account Type (Organization, Foundation, etc.)) - This tells the ACTUAL name of the donating foundation or organization.  Foundation Recognition Name is ANOTHER field, which is used in communication and maybe reporting to properly attribute the donations from that organization, whose legal name may be unwieldy.  The real Account Name for the organization who whats to be anonymous will be ANONYMOUS FOUNDATION or ANONYMOUS ORGANIZATION, etc.

Anonymous Donations:  Same sort of arrangement, except you only need ONE custom field, which is Donation Recognition Name, or similar.  This field is used to properly refer to the specific donation correctly.  If the donation is anonymous, then you put 'Anonymous' in that field, and this field is used in reports and communications.
