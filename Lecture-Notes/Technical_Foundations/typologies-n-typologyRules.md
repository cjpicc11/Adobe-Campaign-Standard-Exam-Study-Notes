# Typologies & Typology Rules Notes

## Overview of Typologies Module

### Typologies

**Typologies are:**
- Used to apply business rules prior to sending a delivery
- Grouping of typology rules
- Associated to the delivery templates

### Out-of-the-Box Typologies
**The following typologies are provide out of the box**
- Default typology: Applied to deliveries by default (includes rules to enforce industry best practices)
- Notification typology:  Applied to operational messages (technical workflows)
- Transactional message typologies (mc_mcTypology and mcTypology):  Applied to transactional messages

### Typology Rules
**There are two types of typology rules:**
1. Control rules
2. Filtering rules

### Control Rules
**Control rules:**
- Check the validity and quality of the message content
- Ensure deliveries are compliant and follow industry best practices
- Are provided out-of-the-box
- Cannot be created or modified
- Generate an error, a warning or an informational entry in the delivery log
  - An error will stop the delivery

> An example:  Check *unsubscription link* checks for the presence of an unsubscription URL

### Filtering Rules
Filtering rules:
- Exclude part of the target according to criteria defined in a query
- Ensure contact lists:
  - Are clean with limited bounced
  - Meet business requirements
  - Meet legal requirements
- Are provided out of the box
- Can be created and modified by an administrator

> An Example:  Quarantine checks for quarantine email addresses; excludes them from the target.

### Typology Rules:  Execution Order
**Typology rules are executed in the following sequence:**
1. Control rules, applied at the start of targeting
2. Out-of-the-box Filtering rules
3. Custom Filtering rules
4. Control rules, applied at the end of targeting
5. Control rules, applied at the start of personalization
5. Control rules, applied at the end of personalization

## Creating Typologies

### Steps to Create Typologies
1. Duplicate default typology
2. Configure custom typology rule
3. Associate typology rule to custom typology
4. Associate custom typology to custom delivery template