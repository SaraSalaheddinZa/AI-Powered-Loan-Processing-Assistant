# M1. Project Kick-off & Requirements Gathering

## Project
**AI-Powered Loan Processing Assistant**

## Milestone Purpose
M1 establishes the foundation of the project by defining the main requirements, identifying the users involved in the loan application process, listing the information that needs to be stored, and confirming the Salesforce environment used for development.
The work completed in this milestone is used as the starting point for the next milestones, where the requirements are implemented in Salesforce.

---

## 1.1 Project Ownership and Responsibilities

This project was completed individually. I was responsible for the planning, Salesforce configuration, development, testing, documentation, and preparation of the final project deliverables.
Since the project was completed individually, the responsibilities normally divided between a Project Lead, Salesforce Administrator, Developer, and QA role were handled by me throughout the project.
| Assigned To | Responsibility |
|---|---|
| Sara Salaheddin | Project Planning & Coordination. |
| Sara Salaheddin | Salesforce Administration & Configuration. |
| Sara Salaheddin | Salesforce Development. |
| Sara Salaheddin | Testing & Troubleshooting. |
| Sara Salaheddin | Documentation & Deliverables. |

### 1.1.1 Team Communication Protocol

As this is an individual project, communication between team members was not applicable. Project activities were instead tracked through the project milestones and tasks, with documentation and deliverables maintained throughout the development process.

---

## 1.2 Requirement Gathering and User Stories
The project focuses on a simplified loan application process. The main idea is to make it easier to collect loan information, store it in Salesforce, review the application, and track its status.

The solution uses Salesforce as the main platform and Agentforce as the AI-powered assistant. The later milestones build on these requirements by adding automation, Agentforce actions, a custom Lightning Web Component, reporting, and security/testing.

### Core User Stories

**User Story 1 — Loan Applicant**

> As a loan applicant, I want to provide my personal information so that my loan application can be created.

**User Story 2 — Loan Applicant**

> As a loan applicant, I want to provide the requested loan amount and loan type so that my application contains the required loan details.

**User Story 3 — Loan Officer**

> As a loan officer, I want to review application details so that I can understand the applicant's request.

**User Story 4 — Loan Officer**

> As a loan officer, I want to view the application status so that I can track the progress of loan applications.

---

## 1.2.1 Essential Data Fields

The initial requirements identify the following core data fields for a basic loan application:

| Field                 | API Name                | Data Type       | Purpose                                                          |
| --------------------- | ----------------------- | --------------- | ---------------------------------------------------------------- |
| Applicant Name        | `Applicant_Name__c`     | Text(100)       | Stores the applicant's name.                                     |
| Contact Email         | `Contact_Email__c`      | Email           | Stores the applicant's contact email.                            |
| Annual Income         | `Annual_Income__c`      | Currency(16, 2) | Stores the applicant's annual income.                            |
| Loan Amount           | `Loan_Amount__c`        | Currency(16, 2) | Stores the requested loan amount.                                |
| Loan Type             | `Loan_Type__c`          | Picklist        | Identifies the type of loan requested.                           |
| Application Status    | `Application_Status__c` | Picklist        | Tracks the current status of the loan application.               |
| Employment Status     | `Employment_Status__c`  | Picklist        | Stores the applicant's employment status.                        |
| Risk Score            | `Risk_Score__c`         | Number(3, 0)    | Stores the risk score associated with the loan application.      |
| Loan Application Name | `Name`                  | Auto Number     | Provides the unique name/number for the loan application record. |


These fields form the minimum information required for the initial loan application process and provide the foundation for the Salesforce data model in M2.

---

## 1.3 Salesforce Org Setup

I used a Salesforce Developer Edition org as the development environment for the project. The org was used to build, configure, and test the Loan Processing Assistant.

The Salesforce environment is the workspace used for the project components, including the Loan Application object, Lightning App, record pages, Flow automation, Agentforce configuration, custom LWC, reports, and dashboards.

Salesforce provides the Organization Edition value on the Company Information page. This page can be opened from Setup by searching for Company Information in Quick Find. The Organization Edition value appears in the lower-right area of that page.

<img width="1911" height="692" alt="image" src="https://github.com/user-attachments/assets/485aaa29-1461-45be-8d02-8a9121bc0fab" />
Setup → Company Information, with Organization Edition visible as Developer Edition.

---

## M1 Deliverables and Outcomes

| Requirement | Outcome |
|---|---|
| Team Formation and Role Assignment | Project responsibilities defined. |
| Communication Protocol | Project coordination and documentation practices established. |
| Requirement Gathering | Core loan-processing requirements identified. |
| User Stories | Applicant and loan officer user stories documented. |
| Essential Data Fields | Applicant Name, Contact, Loan Amount, Loan Type, and Application Status identified. |
| Salesforce Org Setup | Salesforce development workspace established for implementation. |

---

## M1 Completion Summary

M1 defined the starting requirements for the AI-Powered Loan Processing Assistant. The main users, user stories, required loan information, project responsibilities, and Salesforce development environment were identified.

The information collected in this milestone was then used as the basis for M2, where the requirements were implemented in Salesforce through the Loan Application object, custom fields, Lightning App navigation, and the initial record page design.
**Milestone: M1 — Project Kick-off & Requirements Gathering**

**Status: Completed**
### Reference

- [Salesforce Help — Find Your Edition](https://help.salesforce.com/s/articleView?id=xcloud.overview_finding_edition.htm&language=en_US)
