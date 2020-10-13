## Extending the Data Model MOdule

### Benefits
The Adobe Campaign Standard data model can be customized to reflect the data structure of a business, which allows marketers to:

- Target an audience based on business data
- Personalize their messages to clients by including relevant client data.

### Custom Resource
A custom resource is a data object available to Adobe Campaign Standard, accessible through the interface or API's
- User-defined
- Contains:
  - Data structure definition (fields, keys, indexes, links)
  - Screens: control the display in the UI
  - Filters for the data

#### Steps to Create a Custom Resource
1. Create and Configure
2. Define identification keys
3. Create an index
4. Publish
5. Define the screens

### Extend Out-of-the-box Objects
- Adobe Campaign comes with out-of-the-box resources (objects)
- A custom resource can extend an out-of-the-box resource
- Define additions to the object
- Modifications to the existing properties of the object are not possible

#### Custom Resource Publication
- A custom resource is only a definition; saving applies no changes to the database
  - Publish custom resources for the changes to take effect
- Publishing translates the definitions into the underlying technologies that Adobe Campaign Standard uses
  - New schemas
- Publishing updates the database with the schema structure.

### Schemas
Data objects in Adobe Campaign Standard are modeled as XML in schemas.  A schema:
- Defines the XML structure of an object
- Defines the API definition of an object
- Contains no data
- Is generated from the definition of a Custom resource
- Exists for all resources in ACS, not just Custom resources
- Is displayed in the UI for troubleshooting
- Is not editable

### Database
- Tables in the database include data object or resources
- Adobe Campaign Standard uses an API to access an object in the database
- The schema defines the database table and the API definition of that object
- The attributes of the object represent columns in the table
- The data stored in the tables are called entities

### APIs
- API definition of an object specifies how the object is exposed to the ACS application
- All custom resources are accessible through the API to the ACS application
- Some out-of-the-box objects are private and are therefore not accessible through the API

### API Types
There are two types of APIs:
- Internal
  - Used by ACS application to access the data
  - Not to be accessed by end users

- External
  - Public-facing API
  - Accessible to end users through adobe.io

### Metadata
- Different view of the schema
- Metadata that is described through the API
- JSON definition of the schema
- Used by the ACS application to obtain the definition of an object/resource in order to build a query
- Can also be used to troubleshoot

### Identification Keys
Every custom resource must have at least one unique identification key.  Its purpose is to:
- Uniquely identify records
- Create links between resources

### Configuration Options
#### Custom Keys
- One or multiple keys
- A field in the key must be dynamic
- Required to export the custom resource into a package

#### Automatic primary key
- Campaign generates a primary key
- 32-bit (long) or 64 bit sequence (int64)

#### Combination
- Automatic key + custom key(s)

### Indexes

#### Indexes:
- Data structure that improves the speed of data retrieval operations on a database
- Quickly locate data without having to search every row in the database table
- Optimize the performance of SQL queries

#### In Adobe Campaign Standard:
- Indexes are automatically generated for each identification key configured in a custom resource
- Indexes can be added as needed for any field, or combination of fields, in a custom resource

### Publication
- A custom resource is only a definition; saving applies no changes to the database
- For changes to take effect, custom resources must be published
- Publishing:
  - Generates the schemas for the custom resources
  - Updates the database with all changes using those schemas.

#### Publication Options
Two modification options:
- Determin modifications since last publication
  - This will publish changes in ALL custom resources
  - Excludes custom resources with "Do not publish latest modifications" selected

- Repair database structure
  - Repairs database after failure
  - Modifications made directly to database are lost.

#### Publication Process
Two-step approach:
1. Prepare publication
  - Generates the SQL statements
  - Simulates what will occur during the publication phase
  - Generates warnings/errors when data structure changes occur (to avoid data corruption and data loss)

2. Publish
  - Writes the SQL to the database

> **Note:**  Remember that "*Do not publish latest modifications*" must be unchecked.

#### Publication Activities
Activities that occur during publishing:
- Data schema updates
- Screen definition updates
- Navigation tree updates
- Filters updates
- API updates
- Cache refresh

#### publication Logs
- Job Log
  - Previous publications are available in publishing page and batch job
- SQL Script
  - Preview the SQL script to execute
  - Displayed only when there are data structure modifications
  - Screens, filters and navigation tree changes do not generate data structure changes

### Extending Existing Resources
#### Extending Limitations - Data Structure
Data Structure can do **only** these things:
- Create on extension for an existing resource
- Add fields; cannot remove/modify existing fields
- Add custom fields to a custom key; you cannot use any out of the box fields in your custom key
- Create indexes for custom fields; cannot create indexes for out-of-the-box-fields

#### Extending Limitations - Screens
When users modify the screen definition of an existing resource:
- Existing screen definition
- Can modify only a specific area of the existing screen
- Updated in existing web page
  - Not displayed in the Client data

#### Special Case:  Test Profiles
Test Profiles
- Sub-view of profiles
- Add fields from the Profile resource
- Cannot create custom fields specifically for the Test profiles resources
  - Create in profiles resource first

### Link Types
- A link is a relationship that joins two resources
- The link is convigured in one of the two resources
- When configuring the link, you need to determine in which resource to create the link
- There are three types of links
  - 1 cardinality simple link
  - N cardinality collection link
  - 0 to 1 cardinality simple link

#### Link Types - 1 Cardinality Simple Link
- Cardinality of 1:1 from source to target
- Cardinality of 1:N from target back to source
- Example:
  - Transaction -> Profile
  - Link is defined in the **Transactions** resource
  - 1 Transaction -> 1 Profile
  - 1 Profile -> N Transactions

#### Link Types - N Cardinality Collection Link
- Cardinality of 1:N from source to target
- Cardinality of 1:1 from target to source
- Opposite of 1 cardinality simple link
- Example
  - Profile -> Transactions
  - Link is defined in the **Profile** resource
  - 1 Profile -> N Transactions
  - 1 Transaction -> 1 Profile

#### Link Types - 0 to 1 Cardinality Simple Link
  - Cardinality of 0 or 1:1 from source to target
  - Cardinality of 1:N from target to source
  - Creates an outer join on the source
  - Example:
    - Profile -> Households
    - Link is defined in the Profile resource
    - 0 or 1 Profile -> 1 Household
    - 1 Household -> N Profiles

#### Link Properties - Integrity
- Behavior in case of deletion/duplication
- Depends on data integrity requirements
- Example:
  - Transactions table linked to the profile table
  - If a profile record is deleted, do you:
    - a) Delete transaction records?
    - b) Only allow deletion if link is removed?
    - c) Keep the transactions but reinitialize the joined key value?
    - d) Do nothing?

#### Link Properties - Join Definition
**Options for specifying keys to use to join the resources:**
- Use the primary keys to make the join
  - Foreign key field created in the target resource
  - Join created using foreign key in target and primary key in source
- Define specific join conditions
  - Specify a field in each resource
  - Option of creating a constant join

#### Profile Resource Links
- 1:N link from Profile to another resource
- Automatically adds tab to Profile Detail View
- Need to add Profile field in Detail view of linked resource.

### Predefined filters
**A predefined filter:**
- Appears in the Query Editor in the form of pre-configured rules
- Allows administrators to develop complex filter configurations
- Provides the marketer with a simplified interface when defining an audience
- Limits the number of steps it takes to achieve the desired configuration

### Deleting Custom Resources:
- Draft
- Pending re-draft
- Published

**To delete a custom resource:**
- Reset the published custom resource to Draft (re-draft)
- Publish the re-drafted resource
  - This drops all the data from the database (table, screens, APIs)
- Delete the Draft resource can then be deleted
  - Resource in Draft state will be prevented from publishing

### Schema Structure
- The root element of the schema is
  - `<srcSchema></srcSchema>`
- An outermost `<element/>` sub-element is the root element of data entities based on this schema
- It contains `<element/>` and `<attribute/>` sub-elements that describe data entity elements and attributes
- Field=`<attribute/>`=column in db

``` html
    <srcSchema>
        <element>
            <attribute/>
            <element>
                <attribute/>
            </element>
        </element>
    </srcSchema>

```
