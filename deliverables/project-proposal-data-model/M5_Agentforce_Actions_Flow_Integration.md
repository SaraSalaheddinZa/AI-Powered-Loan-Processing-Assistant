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

<img width="1919" height="763" alt="image" src="https://github.com/user-attachments/assets/cc11222f-39c6-495a-99d5-a52c8487a72d" />
The screen flow collects the required loan information, creates the Loan Application record, and displays a confirmation screen after successful creation.
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

<img width="1911" height="738" alt="image" src="https://github.com/user-attachments/assets/f76d7f72-64f4-4641-a56d-5be91245e4f1" />
The screen flow collects the required loan information, creates the Loan Application record, and displays a confirmation screen after successful creation.

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

<img width="1900" height="790" alt="image" src="https://github.com/user-attachments/assets/e17450e3-4551-4530-9d03-36db9785a8a6" />


------------------------------------------------------------------------

## Create Loan Application Record

After the screen, the Flow uses the record-creation step to create the
**Loan Application** record.

The information collected from the screen is passed into the
corresponding Loan Application fields. This is the point where the
information collected from the user becomes an actual Salesforce record.

<img width="1096" height="826" alt="image" src="https://github.com/user-attachments/assets/08ad014b-87b2-45a1-836c-d6557fe95a95" />

------------------------------------------------------------------------

## Confirmation Screen

After the record is created, the Flow displays a confirmation screen.

The created record ID is stored in `varCreatedLoanId`, allowing the Flow
to keep the identifier of the new Loan Application.

<img width="1869" height="791" alt="image" src="https://github.com/user-attachments/assets/f3afafe9-6202-4d71-bea8-e153c314935b" />


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

<img width="1904" height="760" alt="image" src="https://github.com/user-attachments/assets/009706ee-9efd-44df-a179-af85995da1c3" />

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

<img width="1917" height="817" alt="Screenshot 2026-08-25 043100" src="https://github.com/user-attachments/assets/70deaf9e-67e8-46d0-8244-f1c70eaae352" />


<img width="1919" height="639" alt="image" src="https://github.com/user-attachments/assets/454e205c-4f6f-4880-882e-11a155bf9104" />


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
