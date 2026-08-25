# M4. Agentforce Fundamentals & Configuration

## Project

**AI-Powered Loan Processing Assistant**

## Milestone

**M4 — Agentforce Fundamentals & Configuration**

## Overview

In this milestone, I configured the Agentforce assistant for the loan application project. I created the agent, added the required topics, and tested the instructions to make sure the agent could collect the information needed for a loan application.
The main goal of this milestone was to set up the Loan Assistant Agent and configure it for the loan application use case. I focused on creating the agent, adding the required topics, and testing the instructions before moving to the Agentforce actions and Flow integration.
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

I kept the agent focused on the loan application process. The idea was to make it ask for the main information needed from an applicant instead of trying to answer unrelated questions.
- Collect the basic applicant information.
- Ask for the loan amount and loan type.
- Confirm the information provided by the user.
- Keep the conversation focused on the loan application.
- Prepare the agent for the next integration step.

<img width="1910" height="836" alt="image" src="https://github.com/user-attachments/assets/f9f04d22-2c88-4d04-830b-135e47b54532" />
*Figure 1. Loan Assistant Agent created in the Salesforce Developer Edition.*

---

## 4.2 Agent Topics and Instructions

### Objective

After creating the agent, the next step was to define the main topics that the assistant should handle.

I created the topics around the information that the agent needs during the first stage of a loan application. I kept the topics limited to the project requirements so the agent has a clear purpose.

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

I configured the agent instructions to keep the conversation short and focused. The agent asks for missing information, uses information already provided, and confirms the important loan details before continuing.
The agent should:

- Ask for missing information.
- Avoid asking for information that the user already provided.
- Confirm the loan amount and loan type.
- Keep the conversation related to the loan application.
- Do not make loan approval or rejection decisions.
- Keep the conversation related to the loan application.
- Move the user to the next step after collecting the required information.

<img width="1908" height="791" alt="image" src="https://github.com/user-attachments/assets/9423cd1d-9b73-468d-b234-7f7f6105606b" />
*Figure 2. Agent topics configured for the loan-processing use case.*

<img width="1900" height="818" alt="image" src="https://github.com/user-attachments/assets/f3c17b4b-18df-48af-a635-14c2f2796d2b" />

<img width="1902" height="818" alt="image" src="https://github.com/user-attachments/assets/e314247e-6fba-4f85-8e9a-5d58e4e12ae8" />


---

## 4.3 Basic Prompt Engineering

### Objective

For the prompts, I focused on making the questions short and easy to answer. I tested the wording around the main fields such as applicant name, loan amount, and loan type.
The project does not require the assistant to provide complex financial advice. The main purpose of the prompts is to help the agent collect the correct information and guide the user through the loan application process.

### Prompt Design Principles

The main points I considered when writing the prompts were:
- Keep questions clear.
- Ask for the required information step by step.
- Confirm important values.
- Use information already provided by the user.
- Keep the agent within the loan application scope.
---

<img width="1917" height="817" alt="image" src="https://github.com/user-attachments/assets/fc3f7f5d-149d-4637-b84c-9fc6b6fd7f4e" />

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

By the end of M4, I had created the Loan Assistant Agent and configured the main topics and instructions needed for the loan application process. I also prepared the agent for the next milestone, where it will be connected to Agentforce Actions and the loan creation Flow.



Instead of building the loan application process only through traditional Salesforce screens, the project now has an Agentforce assistant that can interact with the user conversationally and guide the initial loan application process.

This provides the foundation required for M5, where the assistant will be connected to Salesforce Flow and Agentforce Actions to move from conversation and information gathering into actual Salesforce record creation and automation.
