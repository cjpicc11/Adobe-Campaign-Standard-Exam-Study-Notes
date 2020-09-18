# Adobe Campaign Standard Lecture Notes

## User Interface

- It is commonly web based.
- Maintains the look and feel of the Adobe Experience Cloud
- Is touch-ready
- Is updated regularly


        The options available on the ACS interface vary by contract and user permissions.

### Dashboard View
![Dashboard_View](/Lecture-Notes/img/acs_dashboard.jpg)*View of first page upon logging in to Adobe Campaign Standard*

### Adobe UI Documentation
[UI Navigation](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)


## Profiles
In ACS, profiles are the target of deliveries in marketing campaigns.

### A profile can represent...
- A Client
- A Prospect
- An individual who has subscribed to a newsletter.
- A Recipient
- A User
- Any other individual you want to target depending on your organization


### Profile Capabilities
- ACS builds rich customer profiles to deliver more relevant and personalized offers based on profiles' preferences.
- You can define the target of deliveries using simple or advanced criteria
- ACS can track profile interactions from both online and offline channels.


### Profile Data
A profile corresponds to one contact stored in the Profiles table of the database.  It contains information to target, qualify and track a contact.  The profile data includes...
- Contact Information (first name, last name)
- Postal Address
- Channel Information (email address, mobile phone number)
- Blacklist Rules (contact rules)
- Subscriptions
- Deliveries

### Ways to Create Profiles
- Manually, directly in the ACS UI
- Using an import workflow (most common)
- Using the API through a web application


## Test Profiles
Test profiles are fictitious profiles containing fabricated contact information.  

### You can use test profiles to...
- Preview Email
- Send Proofs
- Set a trap
- Render Email

### Test Profiles are...
- Stored separately in the database
- Not included in delivery reports

### Preview
The preview feature allows you to preview an email delivery while designing the message.

You can use preview to...
- Test Personalization
- Test Dynamic Content

### Proofs
The proofs feature allows you to send an email delivery before sending the final version to the main target.  

You can use proofs to...
- Obtain approval for the overall message before sending the final version to main target.
- Verify personalization, dynamic content, and links in the message.


### Email Rendering 
<!-- 9/17/2020 09:52 BREAK -->
Email Rendering allows you to view how a message is displayed on a variety of web clients web mails and devices.

You can use Email rendering to verify that your message displays in the best possible way (in various email clients) before sending the final version to profiles.

> Email Rendering is available only in the production instance

Email rendering Test Profiles are read-only and are provided out of the box.


### Traps
The Traps feature lets you target additional profiles that do not match the defined targeting criteria.

**You can use Traps to:**
- Detect Illegal use and distribution of profile data.
        - More commonly used with Direct Mail deliveries
        - Recommended when you are using an external service provider for campaign fulfilment
- Ensure deliveries are receive by profiles
- Send a copy of the delivery to management.

### Steps to create a Test Profile
1. Click on Adobe Campaign logo (upper left hand corner)
2. Click on Profiles & Audiences
3. Click on Test Profiles
4. Click on the Create button
5. Complete Test Profile details (person details, usage, channels, events, address)

### Audiences
An Audience is a list of profiles based on specific criteria.

You can construct audiences to be targeted in marketing campaigns - this allows you to have predefined audiences, instead of creating them for an individual campaign.