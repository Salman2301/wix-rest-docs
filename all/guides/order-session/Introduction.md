SortOrder: 0
# Order Session V2

## What is it?

A service that manages the order session during a Wix user checkout flow, from the moment a user has the intent to pay for the order until it was submitted and an invoice was created.

This service should be used if you want to integrate with the Wix Checkout component.

## Onboarding
First of all you have to define your app at https://dev.wix.com and come to us with the appDefId.

Note also that the Order Session service supports only WIX users.

## How does Order Session work?
The Order Session encrypts the order data into a JWE token, which is then returned to the caller as the order_session_id. 


![](https://s3.amazonaws.com/wixplorer-readme-images/order-session/OrderSessionsV2Flow.png)

## Permissions

Order Session service supports only server-2-server calls that originated from known appDefIds,
the reason for it is because Order Session service is a multi-tenant service and it treats each **appDefId** as a different tenant. 

To start working with it, please contact the maintainers in the relevant channels provided in the end of the document. 

## Errors
A number of potential errors can be returned by the service:
*   Status.ExpiredOrderSessionException - trying to get expire order session id .
*   Status.MoreThanOneCouponException - trying to create order session with more than one coupon.

## About The API

Order Session V2 service is a <a href="https://github.com/wix-private/platformization-guidelines"> platformized</a> service that encapsulates a set of operations:
  
### Create Order Session

By providing `sessionData`, the service will encrypt the data and return you orderSessionID (Token)

### Get Order Session

By providing `orderSessionId`, will return the OrderSession with OrderSessionID inside


## Common Questions

### Q: Do we have a testkit?

Yes. For `Scala` examples please check the Quick Start guide or look directly into the test-kit module.

### Q: What BI events are part of Order Session v2 service flows?

No BI events are involved in the Order Session flow

### Q: Who should I contact for any other questions?

You can reach us on the Slack channel `billing-discussions`.
