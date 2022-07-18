# POS - Requirements
## Overall
* POS is the client side terminal that requires offline access
* It is possible to perform day-to-day operations with POS without requiring an active internet connection
* These day-to-day operations are namely
  1. Entering purchase invoices/returns
  2. Entering sales invoices/returns
  3. Payments made and received
* It is possible to view some basic reports from the data entered
* It is possible to sync pos entries with the cloud for additional reporting and functionality
* POS captures all the required details that are required to be fed into the cloud accounting/inventory system


## Login
* Unless integrated with the cloud, the system allows only a single root user
* Username and password of the root user is stored locally
* Root user has access to all POS features
* Root user does not have access to any cloud features
* Security for root user is very basic

## Features common to all source documents
* Following are considered as source documents
  - Purchase invoice
  - Sales invoice
  - Credit Note
  - Debit Note
  - Payment Receipt
  - Payment Voucher
  - Stock Reconciliation
  - Payment Reconciliation
* Below diagram shows the states of a source document
  ![State Diagram](../design/sourcedocumentstates.png)
* Only the documents in Submitted or Posted states are included for pos reports
* Additional states and actions can be introduced through the state machine
* Once submitted, all changes to the source documents are tracked
* Submitted documents cannot be deleted
* Source documents maintain created date, last modified date, created-by and last-modified-by
* Each pos will have a unique active series for source documents
* User can start a new series and mark it as active

## Purchase
* A purchase invoice captures the sales invoice of the supplier and any additional costs involved in that purchase
* Additional costs are used (the sum is distributed) to calculate the cost of good of each item in the purchase
* A purchase invoice can be linked with multiple payment entries
* Outstanding of an invoice can be viewed
* A purchase invoice can be associated with multiple purchase returns
* Purchase invoice can be entered for past and current dates
* Posting a purchase invoice will add entries to the Purchase Journal, and the inventory
* See below for a wireframe 
  //(TODO)