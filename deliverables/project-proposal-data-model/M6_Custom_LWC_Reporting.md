---
generator: pandoc
title: "-"
viewport: width=device-width, initial-scale=1.0, user-scalable=yes
---

# M6. Custom LWC & Reporting

## Project

**AI-Powered Loan Processing Assistant**

## Milestone

**M6 --- Custom LWC & Reporting**

------------------------------------------------------------------------

## Overview

For M6, I focused on the part of the project that helps users view and
understand the loan applications after they have been created.

I completed three main parts:

-   A custom Lightning Web Component for tracking loan applications.
-   Reports for viewing loan applications by status and loan type.
-   A dashboard that brings the main loan application information
    together.

The aim was to make the information easier to view without having to
open every Loan Application record separately.

------------------------------------------------------------------------

# 6.1 Basic Custom Lightning Web Component (LWC)

## Loan Application Progress Tracker

I created a custom Lightning Web Component called **Loan Application
Progress Tracker**.

The component displays active loan applications in a table. It shows the
application name, applicant, loan amount, status, and loan type.

The component uses the Apex method `LoanController.getActiveLoans` to
retrieve the records.

### Information displayed

  Column                  Salesforce Field
  ----------------------- -------------------------
  Loan Application Name   `Name`
  Applicant Name          `Applicant_Name__c`
  Loan Amount             `Loan_Amount__c`
  Status                  `Application_Status__c`
  Loan Type               `Loan_Type__c`

The loan amount is displayed using the currency format, while the other
values are shown as normal text.

### LWC HTML

The component uses `lightning-card` for the main container and
`lightning-datatable` to display the loan applications.

::: {#cb1 .sourceCode}
``` {.sourceCode .html}
<template>
    <lightning-card
        title="Loan Application Tracking"
        icon-name="custom:custom17">

        <div class="slds-m-around_medium tracker-container">

            <template if:true={loans}>
                <lightning-datatable
                    key-field="Id"
                    data={loans}
                    columns={columns}
                    hide-checkbox-column>
                </lightning-datatable>
            </template>

            <template if:true={error}>
                <div class="slds-text-color_error slds-p-around_small">
                    An error occurred while loading the loan application data.
                    Please verify your access permissions.
                </div>
            </template>

        </div>
    </lightning-card>
</template>
```
:::

### JavaScript

The JavaScript file defines the table columns and uses the Apex method
to load the active loan applications.

::: {#cb2 .sourceCode}
``` {.sourceCode .javascript}
import { LightningElement, wire } from 'lwc';

import getActiveLoans from '@salesforce/apex/LoanController.getActiveLoans';

const COLUMNS = [
    { label: 'Loan Application Name', fieldName: 'Name' },
    { label: 'Applicant Name', fieldName: 'Applicant_Name__c' },
    { label: 'Loan Amount', fieldName: 'Loan_Amount__c', type: 'currency' },
    { label: 'Status', fieldName: 'Application_Status__c' },
    { label: 'Loan Type', fieldName: 'Loan_Type__c' }
];

export default class LoanProgressTracker extends LightningElement {

    loans;
    error;
    columns = COLUMNS;

    @wire(getActiveLoans)
    wiredLoans({ error, data }) {
        if (data) {
            this.loans = data;
            this.error = undefined;
        } else if (error) {
            this.error = error;
            this.loans = undefined;
        }
    }
}
```
:::

The component also includes a simple error message. If the records
cannot be loaded, the user sees an error message instead of an empty
component.

### Component Metadata

The component is exposed for use on Salesforce App, Home, and Record
Pages.

::: {#cb3 .sourceCode}
``` {.sourceCode .xml}
<?xml version="1.0" encoding="UTF-8"?>

<LightningComponentBundle xmlns="http://soap.sforce.com/2006/04/metadata">

    <apiVersion>60.0</apiVersion>

    <isExposed>true</isExposed>

    <targets>
        <target>lightning__AppPage</target>
        <target>lightning__HomePage</target>
        <target>lightning__RecordPage</target>
    </targets>

</LightningComponentBundle>
```
:::

### CSS

The CSS is kept simple because the component mainly uses Salesforce
Lightning styling.

::: {#cb4 .sourceCode}
``` {.sourceCode .css}
.tracker-container {
    min-height: 100px;
}
```
:::

### Adding the LWC to the Loan Application Record Page

After creating the component, I added **Loan Application Tracking** to
the Loan Application Record Page.

The component appears below the loan information and displays the
available loan applications in a table.

**\[Insert Screenshot --- Loan Application Record Page with Loan
Application Tracking LWC\]**

*Figure 6.1. Loan Application Record Page showing the custom Loan
Application Tracking component.*

------------------------------------------------------------------------

# 6.2 Reports on Loan Applications

I created two reports to check the loan application data from different
views.

## Report 1 --- Loan Applications by Status

The first report groups the Loan Application records by **Application
Status**.

The report currently contains the loan applications available in the
Salesforce org and shows the applicant, loan amount, loan type, and
status.

The status report helps provide a quick view of how many applications
are New, In Review, or Rejected.

The report contains **7 records** with a total loan amount of
**\$1,095,000** in the current sample data.

**\[Insert Screenshot --- Loan Applications by Status report\]**

*Figure 6.2. Loan Applications grouped by Application Status.*

------------------------------------------------------------------------

## Report 2 --- Loan Applications by Loan Type

The second report groups the applications by **Loan Type**.

The current sample data contains:

  Loan Type     Total Loan Amount
  ----------- -------------------
  Business               \$30,000
  Home                  \$250,000
  Personal              \$815,000
  **Total**       **\$1,095,000**

This report makes it easier to see which loan types represent the
largest part of the current application data.

**\[Insert Screenshot --- Loan Applications by Loan Type report\]**

*Figure 6.3. Loan Applications grouped by Loan Type.*

------------------------------------------------------------------------

# 6.3 Dashboard Creation

After creating the reports, I used them to build the **Loan Processing
Overview** dashboard.

The dashboard provides a simple overview of the current loan application
data.

It includes:

### Loan Applications by Status

A donut chart is used to show the distribution of the loan applications
according to their current status.

### Loan Applications by Loan Type

A column chart shows the total loan amount for each loan type.

The dashboard currently shows the following loan-type totals:

-   Business --- \$30,000
-   Home --- \$250,000
-   Personal --- \$815,000

The total represented in the reports is **\$1,095,000**.

**\[Insert Screenshot --- Loan Processing Overview dashboard\]**

*Figure 6.4. Loan Processing Overview dashboard showing loan application
status and loan type metrics.*

------------------------------------------------------------------------

# M6 Deliverables and Outcomes

  -----------------------------------------------------------------------
  Requirement                         Outcome
  ----------------------------------- -----------------------------------
  Basic Custom Lightning Web          Created the Loan Application
  Component                           Tracking LWC and added it to the
                                      Loan Application page.

  LWC Data Display                    The component displays application
                                      name, applicant name, loan amount,
                                      status, and loan type.

  Reports on Loan Applications        Created reports for loan
                                      applications by status and by loan
                                      type.

  Dashboard Creation                  Created the Loan Processing
                                      Overview dashboard using the loan
                                      application reports.

  Data Visibility                     The LWC, reports, and dashboard
                                      provide different ways to view the
                                      current loan application data.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Result

M6 added a clearer way to monitor the loan applications in the project.

The custom LWC gives users a direct list of the active applications,
while the reports provide grouped views of the same data. The dashboard
then gives a quick overview using charts.

Together, these features make the Salesforce application easier to
monitor and give the user a better view of the current loan processing
activity.

The next milestone is **M7 --- Testing, Security & Trust Layer**, where
the solution can be tested more thoroughly and the security and Einstein
Trust Layer considerations can be documented.
