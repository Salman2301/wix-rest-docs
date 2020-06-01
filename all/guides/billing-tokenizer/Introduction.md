SortOrder: 0
# Billing Tokenizer

## What is it?
The Billing Tokenizer service is a PCI service that is part of the Billing API. 
It is used to tokenize sensitive billing details so it does not travel in non PCI environment.
Billing details can be credit card (number and cvv) or iban.

The billing-token, which is a result of the tokenization process, is used for creating/updating a payment source in the Billing API.

## How does the Billing Tokenizer work?
The Billing Tokenizer uses PCI Compliance component for tokenization of the sensitive data. 
The generated token is linked to a specific user, and can not be used by other customers.