# Lab 12 – Orchestrating multi-agent AI for retail using Copilot Studio and Fabric

## Objective:

Build an intelligent, multi-agent retail assistant using Microsoft
Copilot Studio and Microsoft Fabric. In this lab, you
will design and implement a customer-facing AI system that orchestrates
across specialized agents to handle product discovery, customer support,
policy queries, and real-time operational insights.

## Scenario: “Zava Outdoor Retail Assistant”

A premium outdoor retail brand (focused on **camping & trekking gear**)
wants to build an intelligent assistant that:

- Helps customers **discover products** (backpacks, tents, accessories)

- Answers **policy-related questions** (returns, shipping, refunds)

- Handles **support queries**

- Provides **guided recommendations for outdoor trips**

## Exercise 1: Create Copilot Studio agent

In this exercise, you will create the primary Copilot Studio agent that
acts as the central interface for customer interactions. This agent will
be responsible for handling support queries and grounding responses
using enterprise knowledge sources.

### Task 1: Create the agent and configure knowledge sources

In this task, you will create the **TrailAssist Concierge** agent,
configure its behavior, and ground it with knowledge sources related to
shipping, returns, and customer support policies.

1.  Login to +++https://copilotstudio.microsoft.com/+++ with your
    login credentials

    - Username - +++@lab.CloudPortalCredential(User1).Username+++

    - TAP - +++@lab.CloudPortalCredential(User1).AccessToken+++

2.  Select **Get Started** to activate the Copilot Studio trial.

    ![](./media/image1.png)

3.  Select **Agents** -> **+ Create blank agent**.
    ![](./media/m1.png)
   
4.  Enter the name **+++TrailAssist Concierge+++** and then click **Create**.
    ![](./media/m2.png)

5.  Select **Edit** to edit the details of the agent and enter the below
    description and select **Save**.

    ```
    A customer-facing AI assistant that helps users with order support, returns, refunds, and shipping queries while coordinating
    with a product specialist agent for recommendations and product-specific
    details.
    ```
    ![](./media/m3.png)

    ![](./media/m4.png)

6.  Select **Edit** against Instructions to add instructions to the
    agent.

    ![](./media/m5.png)

7. Enter the below instructions and select **Save**.
    ```
    You are TrailAssist Concierge, a helpful and professional retail assistant for an outdoor gear company.

    Your responsibilities:
    - Answer questions related to returns, refunds, shipping, and customer support.
    - Use the provided knowledge base to give accurate answers.
    - If a question is about products (such as backpacks, tents, camping gear, recommendations, or comparisons), delegate the query to the connected product specialist agent.
    - Always provide clear, structured, and polite responses.

    Guidelines:
    - Be concise but informative.
    - If unsure, ask clarifying questions.
    - Do not hallucinate product details-rely on the product agent.
    ```
    ![](./media/m6.png)

8. Select **Settings** to update the agent’s settings.

    ![](./media/m7.png)

9. Under **Knowledge**, **disable** **Allow ungrounded
    responses** and **Use information from the web** options and then
    select **Save**.

    ![](./media/m8.png)

10. Once the changes are saved, close the Settings pane.

    ![](./media/m9.png)

11. Back in the Overview page of the agent, select **+ Add knowledge**.

    ![](./media/image10.png)

12. **Browse** for the files, select the files under **C:\Labfiles\MCS
    Agent** and click **Open**.

    ![](./media/image11.png)

    ![](./media/image12.png)

13. In the next screen, select **Add to agent**.

    ![](./media/image13.png)

    ![](./media/image14.png)

14. Ensure that the added documents change to **Ready** state.

    \[!Alert\] It may take up to 10 mminutes for the status to change to
    "Ready".

    ![](./media/m10.png)

    You have successfully created and configured the Copilot Studio agent
    and grounded it with relevant knowledge sources to handle customer
    support and policy-related queries.

## Task 2: Test the agent

In this task, you will test the agent to validate that it correctly
retrieves and responds using the configured knowledge sources.

1.  Select the Test pane from the top right.
    ![](./media/m11.png)
2.  Enter the following prompt in the prompt field:

    +++How long does delivery take to metro cities?+++

    ![](./media/image16.png)

3.  You can see that the agent replies from the added knowledge source.

    ![](./media/m12.png)

4.  Try another prompt as below and observe the response

    +++Can I return a product after 7 days?+++

    ![](./media/image18.png)

    ![](./media/m13.png)

    You have verified that the agent can accurately respond to user queries
    using its knowledge base, ensuring reliable and grounded interactions.

    You have successfully built the foundational Copilot Studio agent that
    serves as the orchestrator for customer interactions.

## Exercise 2: Create Fabric Data Agent

In this exercise, you will enhance the solution by introducing a
Fabric Data Agent to provide real-time insights from structured business
data.

### Task 1: Create Lakehouse and load data

In this task, you will create a Fabric workspace and Lakehouse, and load
structured datasets required for operational insights.

1.  Open +++https://app.fabric.microsoft.com+++ from
    a new tab.
    ![](./media/m25.png)

2.  Select **Workspaces -> +New Workspace**.

    ![](./media/m26.png)

3.  Enter the name of the workspace as +++fabws@lab.LabInstance.Id+++
    and select **Apply**.

    ![](./media/image52.png)

    ![](./media/image53.png)

4.  Select **+ New item** -\> **Lakehouse** to add a Lakehouse.

    ![](./media/image54.png)

    ![](./media/image55.png)

5.  Enter the Lakehouse name as +++lh@lab.LabInstance.Id+++ and
    select **Create**.

    ![](./media/image56.png)

6.  Select **Upload files**.

    ![](./media/m28.png)

7.  Navigate to **C:\Labfiles\Fabric Data Agent**, select all the csv
    files under it and click **Open**. Then select **Upload**.

    ![](./media/image58.png)

    ![](./media/image59.png)

8.  Close the pane once all the files are uploaded.

    ![](./media/image60.png)

9. Select the 3 dots next to the **customer** file, select **Load to
    Tables** -\> **New table**.

    ![](./media/image61.png)

10. Select **Load** in the **Load file to new table** modal.

    ![](./media/image62.png)

    ![](./media/image63.png)

11. Ensure that the data is loaded as table.

    ![](./media/m29.png)

12. **Repeat** the process for the other files as well to load
    the **products**, **orders** and **inventory** tables.

    ![](./media/m30.png)

You have successfully created the Lakehouse and loaded structured data,
enabling data-driven capabilities for your solution.

### Task 2: Create Fabric Data Agent

In this task, you will create the **TrailOps Analyst** Fabric Data Agent
and configure it to answer queries based on structured data.

1.  From the left pane, select the **Workspace** and select **+ New
    item**.

    ![](./media/m31.png)

2.  Select **Data agent** from the list to create a new Fabric Data
    Agent..

    ![](./media/image67.png)

3.  Enter the name as +++TrailOpsAnalyst+++ and select **Create**.

    ![](./media/image68.png)

4.  Once the agent is created, a data source needs to be added to it.
    Select **Add a data source**.

    ![](./media/m32.png)

5.  Select the Lakehouse - +++lh@lab.LabInstance.ID+++ and
    select **Add**.

    ![](./media/image70.png)

6.  **Select** all the four **tables** from the left pane.
    ![](./media/m33.png)

7.  Select **Setup** -\> **Instructions** and add the below instructions
    to the agent.
    ```
    You are TrailOps Analyst, a data specialist for retail operations.

    Your responsibilities:

    - Answer queries using structured data such as orders, inventory,
        customers, and shipments.

    - Provide accurate, concise, and data-backed responses.

    - Perform aggregations, summaries, and filtering when needed.

    Guidelines:

    - Only answer based on available data.

    - If data is not available, say so clearly.

    - Do not answer product recommendation or policy-related questions.

    - Focus on insights, trends, and real-time operational data.
    ```

    ![](./media/m34.png)

8. Test the agent with the below question:
    +++Which products are low in stock?+++
    Observe that the agent replies based on the data in the
    lakehouse.

    ![](./media/m35.png)

    ![](./media/m36.png)

9. Select **Publish** to publish the agent.

    ![](./media/m37.png)

    ![](./media/m38.png)

You have successfully created and configured the Fabric Data Agent to
provide insights based on business data.

### Task 3: Add Fabric Data Agent to the Copilot Studio agent

In this task, you will integrate the Fabric Data Agent with the Copilot
Studio agent to enable real-time data-driven responses.

1.  In the Copilot studio, Select **Agents** tab from the **TrailAssist
    Concierge** agent in Copilot Studio.

    ![](./media/image76.png)

2.  Select **+ Add an agent**, **Connect to an external
    agent** -\> **Microsoft Fabric**.

    ![](./media/image77.png)

3.  **Create new connection** to establish connection with Fabric.

    ![](./media/image78.png)
    ![](./media/m39.png)

5.  Select **Create** to proceed.

    ![](./media/image79.png)

6.  Follow the prompts to add the **TrailOpsAnalyst** agent to the
    Copilot Studio agent.

    ![](./media/image80.png)

    ![](./media/image81.png)

7.  Enter the below description and select **Add and configure**.
    ```
    A data-driven AI agent that provides real-time insights on orders,
    inventory, customer activity, and operational metrics using structured
    data from Fabric Lakehouse.
    ```

    ![](./media/m40.png)

You have successfully integrated the Fabric Data Agent, enabling the
Copilot Studio agent to access real-time operational insights.

## Task 4: Test the agent

In this task, you will test the end-to-end solution to validate that the
Copilot Studio agent orchestrates across all connected agents.

1.  Select the **Test** pane.

    ![](./media/image84.png)

2.  Enter +++Show the recent orders+++ and
    click **Send**. **Allow** connection for the first time to proceed.

    ![](./media/image85.png)

    ![](./media/image86.png)

3.  Navigate to the **Activity** tab to view the result. You can also
    see that the agent has internally called the **Fabric Data
    Agent** to answer the question.

    ![](./media/image87.png)

4.  Send +++Which products are low in stock?+++ questions in the Test
    pane and see the output coming from the Fabric Data agent.

    ![](./media/image88.png)

    ![](./media/image89.png)

The Copilot Studio base agent now orchestrates the request to the
Foundry or Fabric agents or answers itself based on the type of the
question and the purpose of the agent.

You have validated that the Copilot Studio agent can intelligently route
queries and orchestrate responses across multiple specialized agents.

You have successfully completed the multi-agent architecture by adding a
data-driven agent, enabling real-time insights and advanced
orchestration.

## Summary:

In this lab, you built an intelligent multi-agent retail assistant using Microsoft Copilot Studio and Microsoft Fabric. You started by creating the TrailAssist Concierge agent in Copilot Studio, configuring its behavior, and grounding it with enterprise knowledge to accurately answer customer support, shipping, returns, and policy-related questions.

You then created the TrailOps Analyst Fabric Data Agent by connecting it to a Fabric Lakehouse containing retail business data. This specialized agent provides data-driven insights based on structured information such as customers, products, orders, and inventory.

Finally, you integrated the Fabric Data Agent with the Copilot Studio agent, enabling intelligent orchestration between customer support knowledge and real-time operational data. By the end of this lab, you implemented a modern AI solution that combines grounded knowledge, structured data, and agent orchestration to deliver accurate and context-aware retail assistance.
