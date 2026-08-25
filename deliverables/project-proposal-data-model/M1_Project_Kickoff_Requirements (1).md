# M1. Project Kick-off & Requirements Gathering

## Project
**AI-Powered Loan Processing Assistant**

## Milestone Purpose
M1 establishes the foundation of the project by defining the project scope, identifying the main user stories, documenting the essential loan application data, establishing project responsibilities and communication practices, and preparing the Salesforce development environment.

---

## 1.1 Team Formation and Role Assignment

The project responsibilities are organized around the following roles:

| Role | Responsibility |
|---|---|
| Project Lead | Coordinate project scope, milestones, documentation, and deliverables. |
| Salesforce Administrator | Configure Salesforce objects, fields, Lightning App, pages, and access settings. |
| Salesforce Developer | Implement custom development such as LWC, Apex support, Flow integration, and technical components. |
| QA / Tester | Validate functionality, test user journeys, identify issues, and verify the final solution. |

### 1.1.1 Team Communication Protocol

The project follows these communication and coordination practices:

- Track project work through milestones and tasks.
- Keep implementation decisions and documentation organized.
- Report blockers and testing issues before final submission.
- Use consistent Salesforce component and field naming.
- Keep project deliverables and supporting evidence organized in the project repository.

---

## 1.2 Requirement Gathering and User Stories

### Project Problem

Loan processing can involve collecting applicant information, reviewing loan requirements, tracking application status, and communicating the next steps. The project addresses this workflow by using Salesforce as the central platform and Agentforce as an AI-powered assistant.

### Project Scope

The solution is designed to support a simplified loan application process. The planned solution includes:

- Loan Application data management.
- Applicant and loan information capture.
- Application status tracking.
- Salesforce Flow automation.
- Agentforce-based interaction and data collection.
- Custom Lightning Web Component functionality.
- Reports and dashboards for loan application visibility.
- Security and Trust Layer considerations.

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

| Field | Purpose | Expected Data |
|---|---|---|
| Applicant Name | Identifies the applicant. | Text |
| Contact | Stores applicant contact information. | Contact information |
| Loan Amount | Stores the requested loan amount. | Currency |
| Loan Type | Identifies the type of loan. | Picklist |
| Application Status | Tracks the current application stage. | Picklist |

These fields form the minimum information required for the initial loan application process and provide the foundation for the Salesforce data model in M2.

---

## 1.3 Salesforce Org Setup

A Salesforce development environment is used as the implementation workspace for the project.

The environment is used to support:

- Custom Loan Application configuration.
- Lightning App and navigation setup.
- Lightning Record Page configuration.
- Flow automation.
- Agentforce configuration.
- Custom LWC development.
- Reports and dashboards.
- Testing and security configuration.

The Salesforce environment provides the foundation for progressing from requirements gathering into the data model and application configuration stages.

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

M1 establishes the requirements and project foundation for the **AI-Powered Loan Processing Assistant**. The project scope, user needs, essential data fields, responsibilities, communication approach, and Salesforce implementation environment have been defined.

The outputs of this milestone provide the baseline for **M2 — Data Model & Basic UI Setup**, where the identified requirements are translated into Salesforce objects, fields, application navigation, and record page design.

**Milestone: M1 — Project Kick-off & Requirements Gathering**

**Status: Completed**
<img width="1911" height="692" alt="image" src="https://github.com/user-attachments/assets/485aaa29-1461-45be-8d02-8a9121bc0fab" />

