
# M7 Testing Security Trust Layer
:::

# M7. Testing, Security & Trust Layer

## Project

**AI-Powered Loan Processing Assistant**

## Milestone

**M7 --- Testing, Security & Trust Layer**

------------------------------------------------------------------------

## Overview

In M7, I focused on checking the main parts of the project after
completing the Agentforce, Flow, LWC, reports, and dashboard work.

The purpose of this milestone was to make sure that the main loan
application process works as expected, review the Salesforce access
settings, and document the main security and trust considerations for
using AI with loan-related information.

The work in this milestone was divided into:

-   Agentforce testing and debugging.
-   User Acceptance Testing (UAT) preparation.
-   Security and access review.
-   Einstein Trust Layer considerations.

------------------------------------------------------------------------

# 7.1 Agent Testing and Debugging

## Testing Approach

I tested the main Agentforce process using the **Loan Assistant Agent**.

The testing focused on the conversation and the information that needs
to be collected before a loan application can be created.

The main flow tested was:

``` text
User starts loan request
        ↓
Loan Assistant Agent
        ↓
Collect Applicant Information
        ↓
Collect required information
        ↓
Confirm information
        ↓
Create Loan Application Action
        ↓
Flow
        ↓
Loan Application record
```

### Information Tested

The following information was checked during the test:

-   Applicant Name
-   Contact Email
-   Loan Amount
-   Loan Type

I also checked that the agent does not continue as if the information
was available when a required value is missing.

### Test Cases

  -----------------------------------------------------------------------
  Test                    Expected Result         Result
  ----------------------- ----------------------- -----------------------
  Start a loan            Agent responds and      Passed
  application request     starts the application  
                          conversation            

  Provide applicant name  Agent accepts the name  Passed

  Provide contact email   Agent accepts the email Passed

  Provide loan amount     Agent accepts the       Passed
                          amount                  

  Enter an                Agent should not treat  Passed
  invalid/non-positive    it as a valid loan      
  loan amount             amount                  

  Select loan type        Agent accepts the       Passed
                          selected type           

  Confirm collected       Agent continues to the  Passed
  information             next step               

  Execute Create Loan     Action starts the       Passed
  Application action      application creation    
                          process                 

  Create Loan Application Salesforce record is    Passed
  record                  created                 

  Complete the process    User receives           Passed
                          confirmation            
  -----------------------------------------------------------------------

### Debugging

During testing, I checked the Agentforce Preview and the Flow execution
to make sure the information was passed between the different parts of
the solution.

The Flow debug/test was also used to check the record creation process
and confirm that the values were being received by the Flow.

------------------------------------------------------------------------

# 7.2 User Acceptance Testing (UAT) Preparation

## UAT Purpose

The UAT test is designed from the point of view of a normal user rather
than from the configuration side.

The main question is whether a user can start a loan application and
complete the basic process without needing to understand how Salesforce
is configured behind the scenes.

### UAT Scenario

**Scenario:** Submit a basic loan application using the Loan Assistant
Agent.

### UAT Test Script

  -----------------------------------------------------------------------
  Step                    User Action             Expected Result
  ----------------------- ----------------------- -----------------------
  1                       Open the Loan Assistant Agent is available and
                          Agent                   responds

  2                       Ask to apply for a loan Agent starts the loan
                                                  application
                                                  conversation

  3                       Provide applicant name  Name is accepted

  4                       Provide contact email   Email is accepted

  5                       Provide loan amount     Amount is accepted if
                                                  valid

  6                       Provide loan type       Loan type is accepted

  7                       Review the information  Agent shows/uses the
                                                  collected information

  8                       Confirm the information Application creation
                                                  process starts

  9                       Wait for processing     Flow completes the
                                                  record creation

  10                      Check Salesforce        New Loan Application
                                                  record exists

  11                      Check the record        Values match the
                          details                 submitted information

  12                      Check the LWC/reporting Application is visible
                                                  in the monitoring
                                                  features
  -----------------------------------------------------------------------

### UAT Acceptance Criteria

The test is considered successful when:

-   The agent responds to the user.
-   Required information can be collected.
-   Invalid loan amounts are not accepted as valid values.
-   The application creation process completes.
-   A Loan Application record is created.
-   The created record contains the submitted information.
-   The application can be viewed through the Salesforce solution.


------------------------------------------------------------------------

# 7.3 Security Configuration Review

## Security Review

Because the project handles loan application information, I reviewed the
Salesforce access configuration used for the **Loan Application**
object.

The review focused on making sure that access to the object and its
fields is controlled through Salesforce's standard security model.

The main areas considered were:

-   Object permissions.
-   Field-level security.
-   Record access.
-   Profiles.
-   Permission Sets.
-   Organization-Wide Defaults (OWD).

### Loan Application Object

The main custom object used by the project is:

**Loan Application**

The object contains fields such as:

-   Applicant Name
-   Contact Email
-   Loan Amount
-   Loan Type
-   Application Status
-   Employment Status
-   Annual Income
-   Risk Score

These fields contain information that should only be available to users
who need it for the loan-processing process.

### Field-Level Security

I reviewed the field configuration to make sure the fields used by the
application are available to the required users and are not
unnecessarily exposed.

Particular attention should be given to fields such as:

-   Annual Income
-   Loan Amount
-   Risk Score
-   Contact Email

These fields may contain more sensitive information than general
application fields.

### Record Access

Record-level access should follow the project's intended Salesforce
sharing model.

The review included checking the access settings for the Loan
Application object and considering whether users should be able to see
or edit all applications or only the applications relevant to their
role.

### Profiles and Permission Sets

Profiles provide the base permissions for Salesforce users, while
Permission Sets can be used to provide additional access when required.

For this project, the security review considered whether the users
working with the Loan Application object have the correct permissions
without giving unnecessary access.


------------------------------------------------------------------------

# 7.4 Einstein Trust Layer Discussion

## Why Trust Matters in This Project

The project uses Agentforce to interact with users and collect loan
application information.

Because the information can include personal and financial details,
trust and data protection are important parts of the solution.

The AI assistant should not be treated as an unrestricted system with
access to every piece of Salesforce information.

The main considerations for this project are:

### Data Privacy

The assistant should only use the information needed for the loan
application process.

For example, the agent collects information such as:

-   Applicant Name
-   Contact Email
-   Loan Amount
-   Loan Type

Other information should not be requested unless it is actually required
by the process.

### Controlled Access

The Agentforce assistant should operate within the access provided by
the Salesforce configuration.

Users should not automatically receive access to information just
because an AI assistant is available.

Salesforce security settings, permissions, and access controls remain
important.

### Accuracy

The assistant should not invent loan information or make unsupported
statements.

For example, the Agent should not tell a user that their loan has been
approved unless an actual Salesforce process provides that result.

This is why the project instructions keep the Agent focused on
collecting information and moving the application through the configured
process.

### Human Oversight

The AI assistant is used to support the loan application process.

It is not intended to replace a loan officer's final decision.

A human or approved business process can remain responsible for
decisions that require review.

### Trust and AI Output

The responses generated by the assistant should be treated carefully,
especially when the conversation involves financial information.

The project therefore keeps the Agent's role limited and uses Salesforce
Flow for the actual record-creation process.

------------------------------------------------------------------------

## Trust Layer Considerations for the Loan Assistant

  -----------------------------------------------------------------------
  Area                                Project Consideration
  ----------------------------------- -----------------------------------
  Data Privacy                        Collect only information needed for
                                      the application.

  Access Control                      Use Salesforce permissions and
                                      security settings to control
                                      access.

  Data Accuracy                       Confirm important values such as
                                      loan amount and loan type.

  AI Responses                        Avoid unsupported claims or
                                      invented information.

  Financial Decisions                 The Agent should not independently
                                      approve or reject loans.

  Human Oversight                     Loan decisions can remain subject
                                      to appropriate review.

  Automation                          Use configured Salesforce Flow for
                                      record creation rather than relying
                                      on free-form AI output.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# M7 Deliverables and Outcomes

  -----------------------------------------------------------------------
  Requirement                         Outcome
  ----------------------------------- -----------------------------------
  Agent Testing and Debugging         The Agentforce conversation and
                                      loan application creation process
                                      were tested.

  UAT Preparation                     A basic end-to-end UAT script and
                                      acceptance criteria were prepared.

  Security Configuration Review       Salesforce object, field, record,
                                      profile, and permission
                                      considerations were reviewed.

  Einstein Trust Layer Discussion     Data privacy, controlled access,
                                      accuracy, human oversight, and
                                      responsible AI considerations were
                                      documented.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Result

M7 provided a final review of the main working parts of the solution.

The Agentforce conversation, Flow, Loan Application record creation,
LWC, reports, and dashboard can now be checked as one connected
solution.

The testing also highlighted the importance of keeping the Agent focused
on the information it actually needs and not allowing the AI layer to
make unsupported loan decisions.

The security review added another layer to the project by considering
who should be able to access the loan application information and how
Salesforce permissions can be used to control that access.

------------------------------------------------------------------------

