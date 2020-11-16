# User Management Module

## Configuring Permissions in ACS

### Access Management
To configure access management in ACS:
- Configure permissions in ACS
- Manage users in Adobe Experience Cloud

### Configuring Permissions
Permissions are attributed to Security groups, and users that are assigned to a Security group inherit its permissions.

- Permissions are rights and restrictions to access functionality and objects within Adobe Campaign Standard (ACS)
- Permissions are based on two concepts:
  - Roles
  - Organizational units

### Roles
Roles are rights that define authorizations to perform tasks (create, modify, delete).
- Provided out-of-the-box
- You cannot create custom roles

Key Roles:
- ADMINISTRATION: Access the Administration menu
- START DELIVERIES:  Validate prepared deliveries
- PREPARE DELIVERIES:  Create, edit, and start delivery preparation
- EXPORT:  Export data
- GENERIC IMPORT:  Import data
- WORKFLOW:  Create, configure, and execute workflows
- DATAMODEL:  Run publications and create custom resources

### Partitioning Data
Organizations may want to restrict marketers access to only their relevant data.
- In Adobe Campaign, you can partition data - for example, by region, business unit, or brand
- Organizational units allow you to define a hierarchy for accessing objects
- All objects and users in Campaign must be linked to an organizational unit
- Only the unit **All** exists for organizational units out of the box
- You can create additional units, but all units must roll up to **All**

### Organizational Unit Access Levels
A user's unit defines their access level:
- Read-only access to all of the objects in its parent units
- Read/write access to all objects in its unit and child units
- No access to objects in parallel branches

### Partitioning Data - Example
|Objects in ACS|Organizational Unit|We.Retail NAM Marketer Access
|---|---|---|
|Data Loading Workflow|We.Retail|Read
|Retargeting Campaign|We.Retail/Canada|Read/Write
|Opt-Out Landing Page|We.Finance|No Access
|Opt-Out Landing Page|We.Finance|No Access
|Newsletter Delivery|We.Retail/LATAM|No Access
|Email Delivery|We.Airline|No Access

### Partitioning Profiles
Partitioning is applied to objects by default-for example, on Campaigns and Deliveries.

- Out-of-the-box partitioning is not available for Profiles
- The organizational unit field is not available in the profiles resources out of the box
- You may need to restrict a marketer's access to profiles based on their organizational unit

**WARNING**: You must extend the Profiles resources with an organizational field, and this must be done prior to importing profiles.
- Existing profiles will not have an organizational unit value
- Profiles with no organizational unit value cannot be accessed by users

### Security Groups
Some Security groups are provided out of the box.
- Default securityu groups access the **All** organizational unit.
- Custom Security groups are created to define custom access requirements and are required to:
  - Partition data by organizational unit
  - Assign custom combination roles to a user.

### Multiple Security Group Assignment
A user can be assigned to multiple securityu groups
- Users assigned to several groups:
  - inherit the cumulated roles
  - belong to the highest org unit
- Users will lose access if they are assigned to parallel units.

## Configuring Permissions in ACS

### Exercise:  Creating Organizational Units
We.Company has 2 brands:
- We.Retail
- We.Finance

They have operations in Canada and in the USA

We.Company wants to partition their data by brand and by country within each brand.

### Exercise:  Creating Security Groups
**User 1 - We.Retail Admins**
- Administrator Roles
- We.Retail Org

**User 2 - We.Retail Canada Users**
- Standard User Roles
- Canada Org

**User 3 - We.Retail USA Users**
- Standard Users Roles
- USA Org


## Managing Users in the Adobe Experience Cloud

### Managing Users in the Experience Cloud
- Manage users in the Experience Cloud Admin Console
- Product profiles represent Campaign Security groups
- Add users to the Experience Cloud, and assign them to product profile(s)
- Experience Cloud synchronizes with the Campaign security group
  - Users are added to the corresponding Campaign security group(s), and inherit permissions.

### Product Profiles
- Default product profiles exist in the Experience Cloud that match default security groups
- Custom product profiles need to be created to match custom security groups in ACS

> **WARNING**:  Strict naming convention must be respected for correct synchronization.

Naming Convention Example:  Campaign Standard - [ACS Tenant ID] - [ACS security group ID]

### Experience Cloud Administrative Types
Experience Cloud Administrative rights are required to add users to Campaign and define the level of access required to manage users.

There are two administrative types that allow adding users to Campaign:

- Product Administrator
- Product Profile Administrator

### Product Administrator vs. Product Profile Administrator

#### Product Administrator

A Product Administrator manages the Campaign product in the Experience Cloud and can perform the following tasks:
- Add users to the Experience Cloud organization, but not remove them.
- Add users to or remove them from a product profile.
- Add or remove Product Profile Administrator
- Add or remove Product Administrator
- Create new product profiles

#### Product Profile Administrator
A Product profile Administrator manages assigned profiles and can perform the following tasks:  
- Add users to the Experience Cloud organization, but not remove them
- Add users to or remove them from a product profile

## Adding Users to ACS
### Exercise:  Adding Users to Campaign Standard
Steps:
1. Create product profiles for each custom security group created in the previous lesson.
2. Add one user to each group

|Product Profile|User Account (example)|
|---|---|
|WeRetail Admins|Adobe ID #1:  WeRetailAdmin|
|WeRetail Canada Users|Adobe ID #2:  WeRetailCanadaUser|
WeRetail USA Users|Adobe ID #3:  WeRetailUSAUser|

> **Note:  You can create an Adobe ID at: https://accounts.adobe.com/

*The Rest of the Module is the practice Demo...*
