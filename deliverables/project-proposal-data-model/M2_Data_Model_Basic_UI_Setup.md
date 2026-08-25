# M2. Data Model & Basic UI Setup

## Project
**AI-Powered Loan Processing Assistant**

## Milestone Purpose

M2 focuses on building the Salesforce foundation for the loan application process. The requirements identified in M1 were translated into a custom Loan Application object, custom fields, a Lightning App, and a basic Lightning Record Page.

---

## 2.1 Custom Object and Field Creation

A custom Salesforce object named **Loan Application** was created to store the information required for the loan application process.

The object uses an Auto Number field for the Loan Application Name and includes the custom fields needed by the project.

### Loan Application Fields

| Field | API Name | Data Type | Purpose |
|---|---|---|---|
| Loan Application Name | `Name` | Auto Number | Provides an identifier for each loan application record. |
| Applicant Name | `Applicant_Name__c` | Text(100) | Stores the applicant's name. |
| Contact Email | `Contact_Email__c` | Email | Stores the applicant's contact email. |
| Annual Income | `Annual_Income__c` | Currency(16, 2) | Stores the applicant's annual income. |
| Loan Amount | `Loan_Amount__c` | Currency(16, 2) | Stores the requested loan amount. |
| Loan Type | `Loan_Type__c` | Picklist | Identifies the type of loan requested. |
| Application Status | `Application_Status__c` | Picklist | Tracks the current status of the application. |
| Employment Status | `Employment_Status__c` | Picklist | Stores the applicant's employment status. |
| Risk Score | `Risk_Score__c` | Number(3, 0) | Stores the risk score associated with the application. |

Salesforce standard fields such as Owner, Created By, and Last Modified By are also available on the object. These are system fields provided by Salesforce and were not treated as custom business fields.

### Data Model Rationale

The Loan Application object was used as the central record for the project because the main features of the solution work around the loan application lifecycle.

The selected fields support the main information needed to create, review, process, and track an application. The model also includes additional information such as annual income, employment status, and risk score to support the later automation and AI-related parts of the project.

### Evidence

<img width="1900" height="623" alt="image" src="https://github.com/user-attachments/assets/1b8d6610-99ae-4e13-aed7-b351044a8aa0" />

---

## 2.2 Lightning App and Navigation Setup

A Lightning App named **Loan Processing Assistant** was configured for the project.

The application provides the Salesforce workspace used to access the loan application functionality. The **Loan Application** object was added to the app navigation so that users can access loan application records directly from the application.

### Navigation

The main navigation setup includes access to:

- Loan Applications
- Other Salesforce components required by the project

The Lightning App provides the main user interface for working with the loan application records.

### Evidence

<img width="1901" height="693" alt="image" src="https://github.com/user-attachments/assets/1d595cb0-2f81-42f3-833e-b99eb2c64e61" />

---

## 2.3 Record Page Layout Design

A Lightning Record Page was configured for the **Loan Application** object using Lightning App Builder.

The record page is used to display the important loan application information in Salesforce. The page provides the foundation for the dynamic user interface and automation features implemented in later milestones.

The page includes the relevant Loan Application fields and standard Salesforce components needed to view and work with a loan application record.


---

## M2 Deliverables and Outcomes

| **Requirement** | **Outcome** |
|---|---|
| Custom Object Creation | A custom **Loan Application** object was created as the main record used by the project. |
| Custom Field Creation | The required applicant, loan, employment, status, and risk fields were configured with appropriate Salesforce data types. |
| Lightning App Setup | The **Loan Processing Assistant** Lightning App was configured for the project. |
| Navigation Setup | The Loan Application object was added to the Lightning App navigation. |
| Record Page Design | A Lightning Record Page was configured for Loan Application records using Lightning App Builder. |
| Foundation for Later Features | The data model and basic UI provide the foundation for Dynamic Forms, Flow, Agentforce, LWC, reports, and dashboards in later milestones. |

---

## M2 Completion Summary

M2 established the main Salesforce data and user interface foundation for the project.

The Loan Application object and its fields provide the data structure needed by the application. The Loan Processing Assistant Lightning App provides the main navigation, while the Loan Application Record Page provides the basic interface for viewing and working with individual applications.

These components are used as the foundation for **M3 — Dynamic UI & Basic Automation**, where the record page is enhanced with dynamic visibility, dynamic actions, and Flow automation.

**Milestone: M2 — Data Model & Basic UI Setup**

**Status: Completed**
