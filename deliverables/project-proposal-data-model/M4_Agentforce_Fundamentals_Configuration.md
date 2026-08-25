# M4. Agentforce Fundamentals & Configuration

## Project

**AI-Powered Loan Processing Assistant**

## Milestone

**M4 — Agentforce Fundamentals & Configuration**

## Overview

This milestone focuses on setting up the Agentforce foundation for the **AI-Powered Loan Processing Assistant**.

The goal was to create an Agentforce assistant that can communicate with users in a simple and clear way, understand the main information needed for a loan application, and guide the user through the initial loan-processing conversation.

The configuration was completed in the Salesforce **Developer Edition** used for the project.

---

## 4.1 Agentforce Setup and Initial Agent Creation

### Objective

The first step was to prepare Agentforce in the Salesforce org and create the initial assistant that will be used for the loan-processing project.

The agent was created with the following project-specific configuration:

| Configuration | Value |
|---|---|
| Agent Name | **Loan Assistant Agent** |
| Purpose | Assist users with the initial loan application process |
| Salesforce Environment | **Developer Edition** |
| Project | **AI-Powered Loan Processing Assistant** |

The **Loan Assistant Agent** is intended to act as the first point of interaction for a user who needs help with a loan application. Instead of requiring the user to navigate through several Salesforce screens immediately, the assistant can guide the conversation and collect the information needed for the next step of the process.

### Configuration Approach

The agent was configured with the project in mind rather than as a general-purpose chatbot. Its role is limited to the loan-processing scenario and focuses on:

- Understanding basic loan application requests.
- Asking for the information required to start a loan application.
- Keeping questions clear and easy to answer.
- Guiding the user through the required information step by step.
- Preparing the information for the later Flow and Agentforce integration.

### Screenshot Evidence

**Screenshot 1 — Loan Assistant Agent**

> Insert a screenshot showing the Agentforce setup page with the **Loan Assistant Agent** selected or created.

**Suggested caption:**  
*Figure 1. Loan Assistant Agent created in the Salesforce Developer Edition.*

---

## 4.2 Agent Topics and Instructions

### Objective

After creating the agent, the next step was to define the main topics that the assistant should handle.

For this project, the topics were kept focused on the basic loan application process. The assistant does not need to handle every possible banking question. Instead, it should concentrate on collecting and explaining the information relevant to the loan application workflow.

### Main Agent Topics

The following topics were defined for the assistant:

| Topic | Purpose |
|---|---|
| **Loan Application Information** | Collect and confirm the basic information needed to start a loan application. |
| **Loan Amount and Type** | Ask the user about the requested loan amount and the type of loan they want to apply for. |
| **Loan Application Guidance** | Explain the next steps and guide the user through the loan application process. |

---

### Topic 1 — Loan Application Information

This topic is responsible for helping the user provide the basic applicant information required for a loan application.

The assistant should ask for information in a simple conversational way and avoid asking for several unrelated values at the same time.

The main information considered by the project includes:

- Applicant Name
- Contact Email
- Employment Status
- Annual Income

### Topic Instructions

The assistant should:

1. Ask the user for their name if it has not already been provided.
2. Ask for a contact email when required.
3. Ask for employment status when it is relevant to the application.
4. Ask for annual income when required.
5. Confirm the information before continuing.
6. Keep the conversation focused on the loan application.

---

### Topic 2 — Loan Amount and Type

This topic focuses on the financial information needed to start the loan application.

The main fields are:

- Loan Amount
- Loan Type

### Topic Instructions

The assistant should:

1. Ask the user how much they would like to borrow.
2. Ask what type of loan they are interested in.
3. Confirm the requested amount and loan type.
4. Avoid making approval decisions or promising that a loan will be approved.
5. Continue to the next stage once the required information has been collected.

The supported loan types in the Salesforce solution include the loan types configured in the **Loan Type** field of the Loan Application object.

---

### Topic 3 — Loan Application Guidance

This topic gives the user basic guidance about the loan application process.

The assistant should:

- Explain what information is needed.
- Tell the user what the next step is.
- Help the user understand what information has already been provided.
- Guide the user toward completing the application.
- Avoid presenting itself as a financial decision-maker.

The assistant is designed to support the process, not replace a human loan officer.

---

## Agent Instructions

The overall instructions for the assistant follow a simple conversational approach.

The agent should:

- Be clear and professional.
- Ask one or a small number of related questions at a time.
- Use the information already provided by the user instead of repeatedly asking for it.
- Confirm important values such as loan amount and loan type.
- Ask follow-up questions when required information is missing.
- Keep the conversation related to the loan application.
- Avoid inventing customer information.
- Avoid making unsupported loan approval or rejection decisions.
- Guide the user toward the next step in the application process.

### Screenshot Evidence

**Screenshot 2 — Agent Topics**

> Insert a screenshot showing the Agentforce topics configured for the **Loan Assistant Agent**.

**Suggested caption:**  
*Figure 2. Agent topics configured for the loan-processing use case.*

**Screenshot 3 — Topic Instructions**

> Insert a screenshot showing one of the configured topics and its instructions.

**Suggested caption:**  
*Figure 3. Instructions configured for an Agentforce loan-processing topic.*

---

## 4.3 Basic Prompt Engineering

### Objective

The prompts were designed to keep the conversation simple and predictable.

The project does not require the assistant to provide complex financial advice. The main purpose of the prompts is to help the agent collect the correct information and guide the user through the loan application process.

### Prompt Design Principles

The prompts follow several simple principles:

1. **Clarity**  
   Questions should be easy for a normal user to understand.

2. **One step at a time**  
   The assistant should avoid overwhelming the user with a long list of questions.

3. **Confirmation**  
   Important information should be confirmed before moving forward.

4. **Context awareness**  
   The assistant should use information that the user has already provided.

5. **Controlled scope**  
   The assistant should stay within the loan-processing use case.

6. **No unsupported decisions**  
   The assistant should not claim that an application has been approved or rejected unless the Salesforce process provides that result.

---

## Example Conversation Prompts

### Applicant Name

A simple prompt can be used to collect the applicant's name:

> "To start your loan application, may I have your full name?"

If the user provides the name, the assistant should acknowledge it and continue to the next required field.

---

### Loan Amount

The assistant can ask:

> "How much would you like to apply for?"

The response should be treated as the requested loan amount and confirmed before continuing.

---

### Loan Type

The assistant can ask:

> "What type of loan would you like to apply for?"

The assistant should use the available loan types configured in Salesforce rather than inventing unsupported values.

---

### Confirmation

Before moving to the next stage, the assistant can confirm the collected information:

> "I have your application information. You requested a [loan type] loan for [loan amount]. Would you like to continue?"

This helps reduce mistakes before the information is passed to the next part of the application process.

---

## Agent Conversation Behavior

A typical interaction for this project follows this pattern:

```text
User:
I want to apply for a loan.

Agent:
Sure. I can help you start a loan application.
May I have your full name?

User:
Sara Salaheddin.

Agent:
Thank you, Sara. What type of loan would you like to apply for?

User:
Personal.

Agent:
How much would you like to apply for?

User:
250000.

Agent:
Thank you. I have a Personal Loan request for 250,000.
Let's continue with the remaining application information.
```

The exact conversation can vary depending on what the user provides, but the general approach remains the same: **collect → confirm → continue**.

---

## Agentforce Configuration Evidence

The following screenshots can be used as evidence for this milestone.

### Screenshot Checklist

| # | Evidence | Screenshot |
|---|---|---|
| 1 | Agentforce setup / Loan Assistant Agent | Required |
| 2 | Agent topics | Required |
| 3 | Topic instructions | Required |
| 4 | Prompt / instruction configuration | Recommended |
| 5 | Agent preview or test conversation | Recommended |

> **Note:** The screenshots should show the actual Salesforce configuration used in the project. They do not need to show every click made during setup; the final configured state is sufficient evidence.

---

## M4 Deliverables and Outcomes

| **Requirement** | **Outcome** |
|---|---|
| Agentforce Setup and Initial Agent Creation | The **Loan Assistant Agent** was created and configured for the loan-processing use case. |
| Agent Topics and Instructions | Topics were defined for collecting loan information and guiding the user through the application process. |
| Basic Prompt Engineering | Clear prompts and conversational instructions were prepared to collect information in a simple step-by-step manner. |
| Project Alignment | The Agentforce configuration was designed to support the later Flow and Agentforce action integration. |

---

## Result

At the end of M4, the Salesforce project had a working Agentforce foundation for the **AI-Powered Loan Processing Assistant**.

The agent has a defined role, focused topics, and instructions that match the project's loan application process. The configuration also prepares the project for the next milestone, where Agentforce will be connected to actions and the loan application creation Flow.

The next stage, **M5 — Agentforce Actions & Flow Integration**, will use this foundation to connect the conversational assistant with Salesforce automation so that information collected during the conversation can be used in the actual loan application process.

---

## Evidence Summary

The M4 implementation is supported by the Salesforce Agentforce configuration and the corresponding screenshots included with this deliverable.

**Recommended GitHub evidence structure:**

```text
M4_Agentforce_Fundamentals_Configuration.md
│
├── Agentforce Agent
├── Agent Topics
├── Topic Instructions
├── Prompt Configuration
└── Agent Testing / Preview
```

---

## Conclusion

M4 established the AI layer of the project.

Instead of building the loan application process only through traditional Salesforce screens, the project now has an Agentforce assistant that can interact with the user conversationally and guide the initial loan application process.

This provides the foundation required for M5, where the assistant will be connected to Salesforce Flow and Agentforce Actions to move from conversation and information gathering into actual Salesforce record creation and automation.
