# Lab 1 - Transform Zava Retail store operations with a Smart Email Triage & Productivity Agent

**Estimated duration:** 40 minutes

## Lab objectives

This lab introduces the Workflows Agent in Microsoft 365 Copilot as an
AI-powered orchestration engine that goes beyond traditional automation.
Instead of building static workflows, you will design intelligent,
adaptive workflows (agents) that can plan, execute, and improve tasks
using natural language. In this lab, you will build an Intelligent Email
Triage Agent for Zava Retail that:

- Runs every weekday morning

- Reviews unread emails (last 24 hours)

- Identifies urgent/actionable emails

- Categorizes emails intelligently

- Generates summaries + next steps

- Sends structured output to Microsoft Teams

- Uses Work IQ to provide productivity insights

## Scenario

Zava Retail, a rapidly growing omnichannel retailer, faced increasing
operational complexity due to high volumes of communication across
customers, suppliers, and internal teams. With expansion across
e-commerce platform, 50+ physical stores, vendor and supplier ecosystem,
customer support and marketing teams, email became the primary but
inefficient channel for critical business interactions. Zava Retail
teams receive hundreds of emails daily from:

- Customers (complaints, returns, inquiries)

- Suppliers (inventory updates, delays)

- Internal teams (approvals, escalations)

This results in:

- Missed urgent emails

- Slow response times

- Employee burnout due to overload

- Lack of visibility into priorities

To address this challenge, Zava Retail is looking to implement an
AI-powered Intelligent Workflow Agent using Microsoft 365 Copilot to
automate email triage, highlight urgent and actionable items, deliver
insights to workload and productivity, and provide real-time
productivity insights.

**Key Personas**

1.  **Marie Brown – Customer Support Manager**

The customer support manager at Zava Retail manages the customer support
inbox, handles escalations and SLA (Service-level agreement) compliance,
and coordinates with logistics and SLA compliance.

2.  **David Turner – Supply Chain Coordinator**

The supply chain coordinator at Zava Retail tracks vendor
communications, manages inventory updates and delays, and coordinates
with warehouses.

3.  **Patricia Gray – Operations Head**

The operations head at Zava Retail oversees the business operations
across departments, tracks productivity and workload, and ensures
operational efficiency.

# Lab Prerequisites

**Licensing & Access**

- Microsoft 365 Copilot license

- Workflows Agent (Frontier or GA) enabled.

- Access to Outlook, Teams

- Viva Insights (Work IQ data enabled)

- Permission to access:

  - Microsoft Graph / Insights data

**DLP & Connector Requirements (Admin setup)**

Your organization’s DLP policy must allow:

- AI actions (Power Platform connector)

- Dataverse (AI prompt)

- Microsoft 365 connectors:

    - Outlook

    - Teams

    - SharePoint

    - Planner

    - Approvals

These are required to ensure that workflows can read emails, post to
Teams, and summarize content.

## Exercise 1: Access Workflows Agent

You are Marie (Customer Support Manager) logging into Microsoft 365
Copilot to automate email triage.

1.  Navigate to +++<https://m365.cloud.microsoft/chat/>+++ to
    open Microsoft 365 Copilot.

2.  Sign in with your Microsoft 365 Copilot account credentials.

    ![](./media/image1.png)

3.  Enter the password and click **Yes**, to stay signed in.

    ![](./media/image2.png)

    ![](./media/image3.png)

4.  After successful login, you will see **Copilot Chat** home page.

    ![](./media/image4.png)

5.  In the **left navigation**, select **All Agents** and explore the
    Agent store.

    ![](./media/image5.png)

    ![](./media/image6.png)

6.  Scroll down and look for **Workflows (Frontier)** option under
    “Built by Microsoft” header.

    ![](./media/image7.png)

7.  Select **Add** to add the **Workflows Agent (Frontier)**.

    ![](./media/image8.png)

## Exercise 2: Build Zava Email Triage Agent

### Task 1: Open Workflows Agent

1.  Go to Microsoft 365 Copilot home page.

2.  Navigate to **Agents \> Workflows (Frontier)**.

    ![](./media/image9.png)

    > **Note:** You will see a chat interface of Workflows (Frontier).

    ![](./media/image10.png)

### Task 2: Describe the Workflow in Natural Language

1.  Define Business Logic (Prompt)

    Paste the below prompt and click **Send**.
    ```

    Each weekday morning, review unread emails from the last 24 hours.  
    Focus on:  
    - Customer complaints and escalations  
    - Supplier/vendor updates  
    - Internal approvals or urgent requests
 
    Categorize emails into:

    - Urgent – Needs immediate action

    - Action Required – Needs response

    - FYI – Informational

    For each email include:  
    - Sender  
    - Subject  
    - Summary  
    - Any deadlines  
    - Suggested next steps  
    
    Highlight:  
    - Customer complaints impacting SLA  
    - Supplier delays affecting inventory  
    
    Send the structured summary to myself on Microsoft Teams email id -
    User1-60850421@LODSPRODMCA.onmicrosoft.com.
    ```

    > **Note:** The email id will be changed to the username you are
    currently using to execute this lab.

    ![](./media/image11.png)

2.  Select **Save** on the top right corner of the **Workflow** window
    to run the actions automatically. Your workflow is now created and
    ready to test.

    ![](./media/image12.png)
3. Once the workflow is saved, open your email and send some sample email to the current user to verify that the workflow triggers a notification in Microsoft Teams. 
    Navigate to **C:/Labfiles/Lab 1 - Lab files** to get sample email.  
    ![](./media/image122.png)

4.  Once the sample emails are sent, select **Test** to review the output.

    ![](./media/image13.png)

4.  Once the testing is successful, it will show the test duration and
    result as success confirmation.

    ![](./media/image14.png)

    Once the test process is completed, review that it:

    - Creates scheduled trigger (weekday mornings)

    - Connects to:

        - Outlook (email ingestion)

        - Dataverse AI (reasoning)

        - Teams (output delivery)


    - Applies AI reasoning for categorization and summarization.

    You did not configure connectors manually—Copilot did it.

    > **Note:** Test process can take 5-10 minutes. Wait until the process
    is completed.

### Task 3: Validate Output 

After processing your prompt, you will see the run results:

1. Emails detected.

    > Note: You need to send different types of sample emails to the
    account to verify that the workflow triggers a notification in Microsoft
    Teams. If you do not have any new unread emails in your inbox, you will
    need to do send test emails to validate the workflow and outputs.

    ![](./media/image15.png)

2.  Email categorization accuracy.

    ![](./media/image16.png)

3.  Teams message format.

    Ensure that the Teams message format is matching the Outlook email
    details.

    ![](./media/image17.png)

    ![](./media/image18.png)

4.  If something looks wrong:

    - Update the prompt

    - Re-test

5.  Check for the following test results for Zava Retail.

    - Are customer complaints in urgent?

    - Are supplier delays highlighted?

    - Are summaries actionable?

    - Is Teams message structured clearly?

## Exercise 3: Add Human-in-the-Loop

Marie Brown (Customer Support Manager) wants approval before sending
summaries to leadership team.

1.  Navigate to +++<https://m365.cloud.microsoft/chat/>+++ to
    open Microsoft 365 Copilot.

2.  Go to **Workflows (Frontier)** agent.

3.  Paste the below prompt in the chat and select **Save**.

    ```
    When a summary is generated from Outlook emails categorized as
    Action Required:

    Before sending the summary:

    Send a Microsoft Teams approval request to me including the summary
    content.

    If approved:

    Send the summary via email.

    If rejected:

    Stop the workflow and notify me in Teams.

    Start the workflow when a new email arrives. Once the approval or
    rejection action is taken, stop sending the approval emails to the
    user.
    ```

    ![](./media/image19.png)

4.  Once the workflow is saved, select **Test**.

    ![](./media/image20.png)

5.  Review the output of approval prompt.

    - Approval step added

    - Control retained for critical communication

6.  The approval step will be added and the email will be received with
    “Approve” and “Reject” options.

    ![](./media/image21.png)

    ![](./media/image22.png)

7.  Select **Approve** and enter “*Approved”* in the comments. Select
    **Submit**.

    ![](./media/image23.png)

8.  Once the approval is received, review the confirmation email.

    ![](./media/image24.png)

9.  When the approval step is completed, the email summary is sent
    automatically.

    ![](./media/image25.png)

    > **Note:** If the request is Rejected, the summary will not be sent.

## Exercise 4: Autonomous Workflow

Marie Brown (Customer Support Manager) wants to reduce missed
follow-ups.

1.  Navigate to +++<https://m365.cloud.microsoft/chat/>+++ to
    open Microsoft 365 Copilot.

2.  Go to **Workflows (Frontier)** agent.

3.  Paste the below prompt in the chat and select **Save**.
    ```
    When a new email arrives in Outlook with "Urgent" in the email
    subject:  
    Send a Microsoft Teams reminder with Urgent timeline to respond to the
    email.  
    If there is no email response until 5 minutes:  
    Send an escalation notification on email and Microsoft Teams.”

    “When a new email arrives in Outlook with "Urgent" in the email
    subject:  
    Send a Microsoft Teams reminder to
    “User1-60891280@lodsprodmca.onmicrosoft.com” to respond to the email
    instantly.  
    If the email is still not responded in 2 hours:  
    Send an escalation notification to Microsoft Teams.
    ```

    > **Note:** The email id will be changed to the username (Email ID) you
    are currently using to execute this lab.

    ![](./media/image26.png)

4.  Once the workflow is saved, select **Test**.

    ![](./media/image27.png)

5.  Review the outcome:

    - Automated follow-ups

    - Escalation logic activated

6.  Review the automated follow-up message sent on Teams. It ensures
    that the urgent emails are not missed.

    ![](./media/image28.png)

7.  Once the mentioned time of 2 hours is passed, review the automated
    escalation message on Teams.

    > **Note:** Currently, the last step of the workflow cannot be
    > executed. The flow will send the Teams message after the 2-hour mark
    > is reached.

    ![](./media/image29.png)

## Exercise 5: Integrate Work IQ to retrieve Zava Leadership Insights

Patricia Gray (Operations Head) wants visibility into workload and
burnout risks at Zava Retail.

### Task 1: Add Workload Analysis

1. Navigate to
[**https://m365.cloud.microsoft/chat/**](https://m365.cloud.microsoft/chat/)
to open Microsoft 365 Copilot.

2. Go to **Workflows (Frontier)** agent.

3. Paste the below prompt in the chat and select **Save**.
    ```
    Analyze my email workload patterns.  
    When a new email arrives in Outlook*

    After every new email received:

    Send me a summary in Microsoft Teams at
    User1-60901006@LODSPRODMCA.onmicrosoft.com that includes:

    - Total number of emails received on the same day

    - Number of emails marked as High Importance on the same day

    - Number of emails received after 6 PM, in non-working hours.

    Include a short note indicating if workload is high based on these
    counts.
    ```
    > **Note:** The email id will be changed to the username (Email ID) you
    are currently using to execute this lab.

    ![](./media/image30.png)

4. Select **Test**.

    ![](./media/image31.png)

5. Review the output:

    - Adds Work IQ intent to workflow

    - Extends AI reasoning layer

6. Review the Email workload summary and intensity.

    ![](./media/image32.png)

### Task 2: Classify Workload

1. Navigate to +++<https://m365.cloud.microsoft/chat/>+++ to
open Microsoft 365 Copilot.

2. Under **Workflows (Frontier)** agent, paste the below prompt in the
chat and select **Save**.
    ```
    Classify the workload into:  
    - Low  
    - Moderate  
    - High  
    Also flag the following conditions:  
    - Email overload  
    - After-hours work  
    - Urgent response pressure
    ```

    ![](./media/image33.png)

3. Select **Test**.

    ![](./media/image34.png)

4. Review the output:

    - Adds classification logic

    - Introduces conditional reasoning

    - Tags workload states

5. After test run, verify:

    - Workload category appears (Low/Moderate/High)

    - Flags are visible in output

    ![](./media/image35.png)

### Task 3: Generate Insights

1. Navigate to +++<https://m365.cloud.microsoft/chat/>+++ to
open Microsoft 365 Copilot.

2. Under **Workflows (Frontier)** agent, paste the below prompt in the
chat to turn raw signals into leadership insights. Select **Save**.

    ```
    When a new email arrives, analyze today’s email workload and
    patterns.

    Based on today’s email workload and patterns, identify:  
    - Risks such as burnout or overload  
    - Inefficiencies in handling emails  
    - Missed priorities  
    Provide 3 actionable recommendations to improve productivity.
    ```

    ![](./media/image36.png)

3. Once the workflow is saved, Select **Test**.

    ![](./media/image37.png)

4. Review the output:

    - Adds insight generation layer

    - Uses AI reasoning to interpret patterns

    - Produces structured recommendations

5. After running the workflow, check Teams output includes:

    - Risks (e.g., burnout risk)

    - Inefficiencies

    - Missed priorities

    - 3 recommendations

    ![](./media/image38.png)

### Task 4: Add Adaptive Intelligence

1. Navigate to +++<https://m365.cloud.microsoft/chat/>+++ to
open Microsoft 365 Copilot.

2. Under **Workflows (Frontier)** agent, paste the below prompt in the
chat to make the agent dynamic and context-aware. Select **Save**.
    ```

    When work activity is detected outside business hours (after 6 PM):

    If the number of assigned tasks is greater than 5:

    Send a notification in Microsoft Teams to me that includes:

    - A message indicating high workload and potential overload risk

    - A list of current tasks*

    Also include suggestions to:

    - Delegate some tasks to team members

    - Rebalance workload for the next day
    ```

    ![](./media/image39.png)

3. Select **Test**.

    ![](./media/image40.png)

4. Review the output:

    - Adds **conditional logic (IF-THEN)**

    - Enables adaptive responses

    - Personalizes recommendations

5. Review the output after the test run is completed. When the workload
is high, enhanced recommendations will appear automatically. The
overload risk is also highlighted explicitly.

    ![](./media/image41.png)

## Summary

In this lab, you learned how the Workflows Agent in Microsoft 365
Copilot enables a shift from static automation to AI-powered, adaptive
workflows. Instead of predefined rules, you built an intelligent agent
that understands context, makes decisions, and improves over time.

You created an Email Triage Agent for Zava Retail that runs every
weekday, reviews recent unread emails, identifies urgent items,
categorizes messages, generates summaries with next steps, and shares
structured outputs in Microsoft Teams. It also uses Work IQ to provide
productivity insights.

As a result, Zava Retail reduced email overload, improved response
times, automated task handling, and minimized missed escalations while
demonstrating how AI-driven agents can enhance operational efficiency
and decision-making.
