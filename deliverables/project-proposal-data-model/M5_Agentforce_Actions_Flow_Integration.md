---
generator: pandoc
title: "-"
viewport: width=device-width, initial-scale=1.0, user-scalable=yes
---

# M5. Agentforce Actions & Flow Integration

## Project

**AI-Powered Loan Processing Assistant**

## Milestone

**M5 --- Agentforce Actions & Flow Integration**

------------------------------------------------------------------------

## Overview

In this milestone, I connected the Agentforce setup from M4 with
Salesforce Flow so the information collected during the conversation
could be used to create a real **Loan Application** record.

The main work in this stage was creating the **Create Loan Application**
Agent Action, preparing the **Create Loan Application Screen Flow -
V1**, and connecting both through the **Collect Applicant Information**
topic.

The final process is:

**User → Loan Assistant Agent → Collect Applicant Information → Create
Loan Application Action → Create Loan Application Screen Flow - V1 →
Loan Application Record → Confirmation**

This moved the project from collecting information through conversation
to actually using that information inside Salesforce.

------------------------------------------------------------------------

# 5.1 Agent Action for Loan Application Creation

## Objective

The purpose of this step was to give the Agent a way to start the loan
application creation process after the required information had been
collected.

I used an Agent Action named **Create Loan Application**. The action was
added to the **Collect Applicant Information** topic in the Loan
Assistant Agent.

The action receives the values collected during the Agentforce
conversation and passes them to the loan application creation process.

### Agent Action Configuration

  -----------------------------------------------------------------------
  Item                                Configuration
  ----------------------------------- -----------------------------------
  Action Name                         **Create Loan Application**

  Action Type                         Agent Action

  Topic                               **Collect Applicant Information**

  Purpose                             Create a new Loan Application
                                      record

  Inputs                              `varApplicantName`,
                                      `varContactEmail`, `varLoanAmount`,
                                      `varLoanType`

  Output                              `varLoanApplicationId`

  Status                              Configured
  -----------------------------------------------------------------------

### Input Variables

-   `varApplicantName` --- applicant's full name.
-   `varContactEmail` --- applicant's email address.
-   `varLoanAmount` --- requested loan amount.
-   `varLoanType` --- selected loan type.

The output is `varLoanApplicationId`, which holds the identifier
returned after the Loan Application is created.

### Why I Used One Creation Action

I kept the record creation as one action instead of creating a separate
action for every field. The Agent first collects the required values.
After the information is complete and confirmed, the **Create Loan
Application** action passes those values to the Flow.

### Screenshot

**\[Insert Screenshot --- Create Loan Application Agent Action
configuration\]**

*Figure 1. Create Loan Application Agent Action configured under the
Collect Applicant Information topic.*

**\[Insert Screenshot --- Agent Action input/output mapping\]**

*Figure 2. Input and output mapping for the Create Loan Application
action.*

------------------------------------------------------------------------

# 5.2 Screen Flow for Loan Application Creation

## Objective

The next step was to create the Salesforce Flow that receives the
applicant information and creates the Loan Application record.

The Flow was created as a **Screen Flow** named **Create Loan
Application Screen Flow - V1**.

The Flow collects:

-   Applicant Full Name
-   Email
-   Requested Loan Amount
-   Loan Type

### Flow Variables

  -----------------------------------------------------------------------
  Variable                            Purpose
  ----------------------------------- -----------------------------------
  `varApplicantName`                  Stores the applicant's full name

  `varContactEmail`                   Stores the applicant's email
                                      address

  `varLoanAmount`                     Stores the requested loan amount

  `varLoanType`                       Stores the selected loan type

  `varCreatedLoanId`                  Stores the ID of the created Loan
                                      Application record
  -----------------------------------------------------------------------

### Screenshot

**\[Insert Screenshot --- Flow variables\]**

*Figure 3. Variables used by the Create Loan Application Screen Flow -
V1.*

------------------------------------------------------------------------

## Loan Application Form

I added a Screen element named **Loan Application Form**.

The screen collects the information required to submit the application.

  Field                   Stored In
  ----------------------- --------------------
  Applicant Full Name     `varApplicantName`
  Email                   `varContactEmail`
  Requested Loan Amount   `varLoanAmount`
  Loan Type               `varLoanType`

### Screenshot

**\[Insert Screenshot --- Loan Application Form\]**

*Figure 4. Loan Application Form used to collect the required
application information.*

------------------------------------------------------------------------

## Create Loan Application Record

After the screen, the Flow uses the record-creation step to create the
**Loan Application** record.

The information collected from the screen is passed into the
corresponding Loan Application fields. This is the point where the
information collected from the user becomes an actual Salesforce record.

### Screenshot

**\[Insert Screenshot --- Create Records element\]**

*Figure 5. Create Loan Application Record element in the Flow.*

------------------------------------------------------------------------

## Confirmation Screen

After the record is created, the Flow displays a confirmation screen.

The created record ID is stored in `varCreatedLoanId`, allowing the Flow
to keep the identifier of the new Loan Application.

### Screenshot

**\[Insert Screenshot --- Confirmation Screen\]**

*Figure 6. Confirmation screen displayed after the Loan Application
record is created.*

------------------------------------------------------------------------

## Final Flow Structure

``` text
Start
   ↓
Loan Application Form
   ↓
Create Loan Application Record
   ↓
Confirmation Screen
   ↓
End
```

### Screenshot

**\[Insert Screenshot --- Complete Flow Canvas\]**

*Figure 7. Complete Create Loan Application Screen Flow - V1 canvas.*

------------------------------------------------------------------------

# 5.3 Agentforce and Flow Integration

After testing the Flow, I connected it to the Agentforce action.

The **Create Loan Application** Agent Action was configured under the
**Collect Applicant Information** topic. The Agent collects the required
information first. Once the information is available and the user
confirms it, the action starts the loan application creation process.

The action inputs are:

``` text
varApplicantName
varContactEmail
varLoanAmount
varLoanType
```

The returned Loan Application identifier is:

``` text
varLoanApplicationId
```

### End-to-End Process

``` text
User
  ↓
Loan Assistant Agent
  ↓
Collect Applicant Information
  ↓
Create Loan Application Action
  ↓
Create Loan Application Screen Flow - V1
  ↓
Create Loan Application Record
  ↓
Confirmation
```

The Agent does not create the record directly. It collects the
information and passes it through the configured action and Flow. This
keeps the conversational part in Agentforce and the record-creation
logic in Salesforce Flow.

------------------------------------------------------------------------

## Integration Test

I tested the integration using a representative loan application
scenario.

The test checked that:

1.  The conversation starts with the Loan Assistant Agent.
2.  The **Collect Applicant Information** topic handles the request.
3.  The required applicant information is collected.
4.  The loan amount and loan type are provided.
5.  The user confirms the collected information.
6.  The **Create Loan Application** action is executed.
7.  The **Create Loan Application Screen Flow - V1** processes the
    information.
8.  A new **Loan Application** record is created in Salesforce.
9.  The created record matches the information provided during the
    conversation.
10. The Agent provides confirmation after the process is completed.

### Screenshot

**\[Insert Screenshot --- End-to-end Agentforce conversation\]**

*Figure 8. Agentforce conversation showing the loan application
information being collected and the creation process being completed.*

**\[Insert Screenshot --- Created Loan Application record\]**

*Figure 9. Loan Application record created through the Agentforce and
Flow integration.*

------------------------------------------------------------------------

# M5 Deliverables and Outcomes

  -----------------------------------------------------------------------
  Requirement                         Outcome
  ----------------------------------- -----------------------------------
  Agent Actions for Data Capture      The **Create Loan Application**
                                      Agent Action was configured in the
                                      Collect Applicant Information
                                      topic.

  Screen Flow for Loan Application    The **Create Loan Application
  Creation                            Screen Flow - V1** was created to
                                      collect the required information
                                      and create a Loan Application
                                      record.

  Flow Variables                      Applicant name, email, loan amount,
                                      loan type, and the created record
                                      ID were handled through Flow
                                      variables.

  Agentforce Integration              The Agent Action was connected to
                                      the Flow using the configured input
                                      and output variables.

  End-to-End Testing                  The Agentforce conversation, action
                                      execution, Flow processing, record
                                      creation, and confirmation were
                                      tested.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Result

By the end of M5, the Loan Assistant Agent was connected to an actual
Salesforce record-creation process.

The Agent can collect the main application information and pass it to
the **Create Loan Application** action. The action then uses the
**Create Loan Application Screen Flow - V1** to create the Loan
Application record.

This was an important step because the Agentforce assistant is no longer
limited to collecting information. The information collected during the
conversation can now be used in the Salesforce application process.

The next milestone, **M6 --- Custom LWC & Reporting**, focuses on the
custom Lightning Web Component, reports, and dashboard used to monitor
the loan applications.
