# M3. Dynamic UI & Basic Automation

## Project
**AI-Powered Loan Processing Assistant**

## Milestone Purpose

M3 builds on the Loan Application Record Page created in M2. The goal of this milestone is to make the user interface more context-aware and to introduce basic automation using Salesforce Flow.

The milestone covers Dynamic Forms, Dynamic Visibility, Dynamic Actions, and a Record-Triggered Flow.

---

## 3.1 Dynamic Forms and Visibility

Dynamic Forms were used on the Loan Application Record Page to provide a more flexible and contextual way of displaying fields.

Instead of showing every field in the same way for every record, fields or sections can be displayed according to the information stored on the loan application.

One of the project requirements is to use a condition related to **Loan Type**. For example, employment-related information can be shown when the selected Loan Type is **Personal Loan**.

### Dynamic Visibility Logic

The intended behavior is:

- The user opens a Loan Application record.
- The user selects or views the Loan Type.
- The relevant fields or section are displayed when the configured condition is met.
- The user interface remains simpler when the condition is not met.

This makes the record page more relevant to the current application and reduces unnecessary information on the screen.

---

## 3.2 Dynamic Actions

A Dynamic Action was added to the Loan Application Record Page to provide a contextual record action.

The project requirement includes a **Submit for Review** type of action that can be used during the loan application process.

The purpose of the action is to give the user a clear way to move the application to the next stage of processing.

### Expected User Experience

The user opens a Loan Application record and can access the configured action from the record page. The action is displayed according to the configured conditions and is intended to support the application review process.

The action is part of the record page experience and works together with the application's status field and automation.

<img width="1917" height="838" alt="image" src="https://github.com/user-attachments/assets/eaa1d561-0761-4297-bdde-449afb84bc7d" />


---

## 3.3 Simple Record-Triggered Flow

A Record-Triggered Flow was planned/configured to automate part of the loan application process.

The flow is triggered by a change to a Loan Application record. The milestone requirement is to automatically update a field or send a simple email alert when a record is created or when the application status changes to **Submitted**.

### Automation Purpose

The purpose of the flow is to reduce manual processing and make the application lifecycle more consistent.

The basic automation pattern is:

1. A Loan Application record is created or updated.
2. Salesforce checks the configured trigger conditions.
3. The flow evaluates the relevant application information.
4. The configured automated action is performed.
5. The Loan Application continues through the processing lifecycle.

<img width="1912" height="820" alt="image" src="https://github.com/user-attachments/assets/4132e464-9ad1-4795-b03e-310d623dcad8" />
<img width="339" height="775" alt="image" src="https://github.com/user-attachments/assets/52f89893-be59-4b3e-a8b4-d2e76d679bee" />



---

## M3 Feature Summary

| **Feature** | **Purpose** |
|---|---|
| Dynamic Forms | Display relevant Loan Application fields in a more flexible record page layout. |
| Dynamic Visibility | Show or hide fields or sections based on record information such as Loan Type. |
| Dynamic Action | Provide a contextual action for progressing the loan application. |
| Record-Triggered Flow | Automate part of the loan application processing lifecycle. |

---

## M3 Deliverables and Outcomes

| **Requirement** | **Outcome** |
|---|---|
| Dynamic Forms and Visibility | The Loan Application Record Page was enhanced with contextual field/section visibility. |
| Dynamic Actions | A contextual record action was configured for the loan application process. |
| Record-Triggered Flow | A Flow-based automation was configured/planned to respond to Loan Application record events and support status-based processing. |
| Improved User Experience | The record page provides a more focused experience by displaying information according to the application context. |
| Basic Automation | Salesforce Flow was introduced to reduce manual processing and support the loan application lifecycle. |

---

## M3 Testing

The Dynamic UI and automation should be tested using representative Loan Application records.

### Test Scenarios

| **Test** | **Expected Result** |
|---|---|
| Open a Loan Application record | The configured record page loads correctly. |
| Change/view Loan Type | The configured Dynamic Visibility behavior is applied. |
| Check the record actions | The configured Dynamic Action is available according to its conditions. |
| Create/update a Loan Application | The Record-Triggered Flow responds according to its trigger configuration. |
| Change Application Status to Submitted | The configured automation executes the intended action. |

<img width="1907" height="427" alt="image" src="https://github.com/user-attachments/assets/234aa797-e895-4f73-96e6-2c2b44e21461" />


---

## M3 Completion Summary

M3 enhances the basic Loan Application interface created in M2 by adding contextual user interface behavior and Salesforce automation.

Dynamic Forms and Dynamic Visibility make the record page more relevant to the current application. Dynamic Actions provide a contextual way for users to perform an application-related action. The Record-Triggered Flow introduces automation that can respond to changes in Loan Application records.

These features provide the foundation for the next milestone, **M4 — Agentforce Fundamentals & Configuration**, where the AI-powered Loan Assistant Agent is configured.

**Milestone: M3 — Dynamic UI & Basic Automation**

**Status: Completed**
