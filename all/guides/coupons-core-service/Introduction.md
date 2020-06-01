SortOrder: 0
# Coupons Core Service

## What is it?
Coupons core service exposes coupon management capabilities. It is a standalone coupons management service and provides coupons management per tenant.

## Onboarding
Coupon service supports only known applications.
Each application mapped to specific tenant. 
Based on the customer we will either allocate new tenant or map to existing one, 
if it's an external application, you need to define your app at https://dev.wix.com and then provide an appDefId as a tenantID. 


