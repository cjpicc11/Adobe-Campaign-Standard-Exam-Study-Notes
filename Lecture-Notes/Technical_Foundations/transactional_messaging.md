# Transactional Messaging Course Notes

## Overview of Transactional Messaging

### Define Transactional Messaging
- Real-time or near real-time
- Triggered
- Notification type deliveries

### Use Cases for Transactional Messaging
- Order Confirmation
- Registration Confirmation
- Opt in confirmation
- Postal delivery notification
- Password reset notification

### Benefits of Transactional Messaging
- Reduced IT costs through centralization
- Higher open and click-through rates
- Opportunity for additional sales by including limited marketing content
- For known Profiles, ability to enrich the transactional message with Profile data

### Steps to Configure Transactional Messaging
1. Configure an event
2. Personalize the transactional message
3. Test and publish the template
4. Integrate via API calls

## Defining an Event
### Feature Updates
- This video covers the original use case of sending an email notification and storing delivery and tracking logs in the event history
- Since we recorded this video, the UI has changed to accommodate Mobile (SMS) and targeting profiles
- Although not demonstrated here, Mobile (SMS) works similarly to email
- You can now send transactional *marketing* messages that target profiles.  This is demonstrated in the Transactional Marketing Messages video

### Shipment notification business case
1. Customer's order has shipped
2. Customer sent a notification

## Configuring Transactional Messaging
This module was primarily a demo.

## Managing Transactional Templates

### Template Lifecycle and Event Processing
- Draft:  API is not available
- Published:  API is available

- Publishing an Event creates an API
- Unpublishing an Event deletes the REST API for that event.

- When templates are in unpublished Callers receive a routing failed.

- Pausing Templates will queue any incoming events.

- Resuming templates will process events that are queued that have not yet expired.

- When you unpublish a paused template queued events are deleted, and you cannot publish that template again until after 24 hours.

### Managing Change
To rollout an Event API, initially:
1. Publish the event
2. Configure the template
3. Publish the template.

To modify the API call parameters (for example, to add an element):
1. Unpublish the template
3. Modify the event
3. (proceed as above)

To modify the message content:
1. Modify the template
2. Publish the template

To buffer transactional message requests:
1. Pause the template
2. When ready, resume the template

To stop sending transactional messages:
1. Unpublish the template