# Overview of Data Packages

### Data Package
- Allow the exchange of resources between Adobe Campaign instances

- Useful for:
  - Transferring data from one server to another
  - Replicating the configuration of an instance
  - Saving a good version of the configuration of an instance during development

#### Data Package Format
- Zip file containing a resource definition file, and images.
- Resource definition file = XML definition of Adobe Campaign resource **entities** included in the package
- Import and export data packages accessible by Administrators **only**

#### Data Package Contents
**THe purpose of a data package is to deploy configurations.**
- Data packages are not business data such as profiles and transaction data; this data is imported using workflows
- Data packages can contain technical and business configurations:
  - Technical configurations: custom resource definitions, system options, etc.
  - Business configurations: typology rules, templates (program/campaign/workflows/delivery), branding etc.
- Data packages are limited to 5000 entities per resource type

#### Planning Package Contents
- Split into multiple packages
- Examples of common packages:
  - Core package: customizations that won't change often (e.g. custom resources, branding)
  - Security package: security configurations (e.g. users, roles)
  - Application package: business standards configurations (templates)


####  Package Contents - Linked Entities
##### Exporting entities linked by a n-1 or 1-1 link:
- If ownership is configured, they will be exported together
    - Ownership is created when the **integrity** or **revIntegrity** property of a link is set to "own" or "owncopy"
      - Ex: Exporting a Campaign results in children deliveries/workflows being included in the package.  
 - If ownership is not configured, each needs to be added to the package.  For entities linked:
   - Using specific join conditions, the link will be exported
   - Using primary keys, the link will not be exported - the link must be recreated after importing

Exporting entities linked by n-n link:
- Entities of the relationship table are not exported-the link must be recreated after importing

#### General Development Guidelines
- Keep a running list of changes
- Add to the data package specification as you develop
- Can only export/import entities of resources configured with a custom key
- Automatic primary keys are not exported
- Importing data without a key is not allowed
  - Ex:  Profiles resource cannot be exported/imported into another Campaign instance through a data package
  - Need to configure resources with a custom key in order to export their entities in a data package.
- Adobe Campaign maintains internal counters per data/object type
- Counter is used to generate a unique ID for objects
- Entities exported in a data package cannot be configured with an out-of-the-box default ID
  - To avoid name collision due to internal counters on target instance
- Use a custom ID when naming objects
  - Avoid errors when exporting entities in a package
  - Create a nomenclature for your project
  - Allows for easier identification of objects
    - Ex: ID for deliveries: demACME_Sept_ReengagmentWave1

