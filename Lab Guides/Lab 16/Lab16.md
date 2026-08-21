# Lab 16 - Orchestrating multi-agent AI for retail using Copilot Studio, Microsoft Foundry, and Fabric

**Estimated Duration: 60 Minutes**

##Overview:

Build an intelligent, multi-agent retail assistant using Microsoft
Copilot Studio, Microsoft Foundry, and Microsoft Fabric. In this lab,
you will design and implement a customer-facing AI system that
orchestrates across specialized agents to handle product discovery,
customer support, policy queries, and real-time operational insights.

## Scenario: “Zava Outdoor Retail Assistant”

A premium outdoor retail brand (focused on **camping & trekking gear**)
wants to build an intelligent assistant that:

- Helps customers **discover products** (backpacks, tents accessories)

- Answers **policy-related questions** (returns, shipping, refunds)

- Handles **support queries**

- Provides **guided recommendations for outdoor trips**

## Exercise 1: Create Copilot Studio agent**

In this exercise, you will create the primary Copilot Studio agent that
acts as the central interface for customer interactions. This agent will
be responsible for handling support queries and grounding responses
using enterprise knowledge sources.

### Task 1: Create the agent and configure knowledge sources

In this task, you will create the **TrailAssist Concierge** agent,
configure its behavior, and ground it with knowledge sources related to
shipping, returns, and customer support policies.

1.  Open the browser and enter the following URL to navigate to Copilot
    Studio.
    +++https://copilotstudio.microsoft.com/+++

2.  Sign in using the following credentials:

    - Username - +++@lab.CloudPortalCredential(User1).Username+++

    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++

    ![](./media/image1.png)

    ![](./media/image2.png)

    ![](./media/image3.png)

3.  Turn off the **New Experience** Toggle.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image4.png)

4.  Select **Get Started** to activate the Copilot Studio trial.

    ![](./media/image5.png)

5.  Select **Agents** -\> **+ Create blank agent**.

    ![A screenshot of a computer Description automatically
    generated](./media/image6.png)

6.  Enter the name +++**TrailAssist Concierge+++** and then
    click **Create**.

    ![](./media/image7.png)

7.  On the Overview page of the Agent, click **Edit** to edit the
    details of the agent.

    ![A screenshot of a computer Description automatically
    generated](./media/image8.png)

8.  Enter the below **description** and select **Save**.

    ```
    A customer-facing AI assistant that helps users with order support,
    returns, refunds, and shipping queries while coordinating with a
    product specialist agent for recommendations and product-specific
    details.
    ```

    ![](./media/image9.png)

9.  Select **Edit** against Instructions to add instructions to the
    agent.

    ![A screenshot of a computer Description automatically
    generated](./media/image10.png)

10. Enter the below instructions and select **Save**.

    ```
    You are TrailAssist Concierge, the primary AI assistant for an outdoor
    retail company.

    Your responsibilities:

    - Answer customer questions related to returns, refunds, shipping,
    delivery, warranties, exchanges, and general customer support using
    the provided knowledge sources.

    - Coordinate with connected specialist agents whenever a request falls
    outside your domain.

    - Provide clear, concise, and professional responses.

    Delegation Rules:

    - For any product-related question (including backpacks, tents,
    camping gear, hiking equipment, product specifications, comparisons,
    recommendations, or trip planning), delegate the request to the
    connected TrailGearExpert agent.

    - For any operational or business data question (including inventory,
    orders, customers, shipments, or sales), delegate the request to the
    connected TrailOpsAnalyst agent.

    - Invoke the appropriate specialist agent only once for each user
    request.

    - Do not invoke the same specialist agent multiple times for the same
    question unless the user asks a new or different question.

    - After receiving a response from a specialist agent, immediately
    return that response to the user.

    - Do not perform additional reasoning, knowledge searches, or delegate
    the same request again after a specialist agent has responded.

    - Do not rewrite, summarize, expand, or modify the specialist agent's
    response.

    - Do not combine multiple responses from the same specialist agent.

    - If the specialist agent cannot answer the request, inform the user
    that the requested information is unavailable instead of invoking the
    agent again.

    Knowledge Usage:

    - Use your own knowledge sources only for returns, refunds, shipping,
    warranties, and customer support.

    - Never answer product or operational data questions yourself.

    - Never use your own knowledge sources for product recommendations or
    business data.

    Conversation Guidelines:

    - Be friendly, professional, and concise.

    - Ask clarifying questions only if the user's request is ambiguous
    before delegating.

    - Never hallucinate information.

    - Use only verified information from your knowledge sources or the
    connected specialist agents.

    ```

    ![A screenshot of a computer Description automatically
    generated](./media/image11.png)

11. Select **Settings** to update the agent’s settings.

    ![A screenshot of a computer Description automatically
    generated](./media/image12.png)

12. Under **Knowledge**, **disable** **Allow ungrounded
    responses** and **Use information from the web** options and then
    select **Save**.

    ![A screenshot of a computer Description automatically
    generated](./media/image13.png)

13. Once the changes are saved, close the Settings pane.

    ![](./media/image14.png)

14. Back in the Overview page of the agent, select **+ Add knowledge**.

    ![](./media/image15.png)

15. On the Add Knowledge window, click **select to browse** and upload
    the files.

    ![A screenshot of a computer Description automatically
    generated](./media/image16.png)

16. Select all the files under **C:\Lab Files\MCS Agent** and
    click **Open**.

    ![](./media/image17.png)

17. In the next screen, select **Add to agent**.

    ![A screenshot of a computer Description automatically
    generated](./media/image18.png)

    ![](./media/image19.png)

18. Ensure that the added documents change to **Ready** state.

    **Note:** It may take up to 10 minutes for the status to change to
    "Ready".

    ![](./media/image20.png)

You have successfully created and configured the Copilot Studio agent
and grounded it with relevant knowledge sources to handle customer
support and policy-related queries.

### Task 2: Test the agent

In this task, you will test the agent to validate that it correctly
retrieves and responds using the configured knowledge sources.

1.  Select the Test pane from the top right.

    ![](./media/image21.png)

2.  Enter the following prompt in the prompt field:

    +++How long does delivery take to metro cities?+++

    ![](./media/image22.png)

3.  You can see that the agent replies from the added knowledge source.

    ![](./media/image23.png)

4.  Try another prompt as below and observe the response

    +++Can I return a product after 7 days?+++

    ![](./media/image24.png)

    ![](./media/image25.png)

    You have verified that the agent can accurately respond to user
    queries using its knowledge base, ensuring reliable and grounded
    interactions.

    You have successfully built the foundational Copilot Studio agent that
    serves as the orchestrator for customer interactions.

## Exercise 2: Foundry agent

In this exercise, you will enhance the solution by creating a
specialized product expert agent using Microsoft Foundry and integrating
it with the Copilot Studio agent.

### Task 1: Create Foundry resource

In this task, you will create the **TrailGear Expert** agent in Foundry
and configure it with product-specific knowledge to enable intelligent
recommendations and comparisons.

**Note:** In order to successfully build and test this agent, we
must **add a role assignment** to your user account in the Azure Portal
by completing the following steps:

1.  Open a new tab, enter the following URL to navigate to the Azure
    portal.

    +++https://portal.azure.com/+++

2.  From the homepage of Azure portal, select your **Subscriptions**.

3.  On the left navigation pane, select **Access Control (IAM)**.

4.  Select **+ Add**, then select **Add Role Assignment**.

5.  Search for and select **Azure AI Administrator**, then
    select **Next**.

6.  Under the **Members** tab, leave the *Assign access to* as **User,
    group or service principal**.

7.  Select **+ Select Members**

8.  Enter your cloud credential username: , select your user name and
    press **Select** to apply.

9.  Select **Review and Assign** twice on the bottom of the page and
    wait for the role assignment to complete.

10. On the left navigation pane, select **Settings-\>Resource Providers**

11. In the search bar, search Microsoft.BotService.

12. Select the three vertical dots(…) and select Register.

13. Wait for 3-4 mins to register.

14. On the Home page of the Azure portal, select **Foundry** from
    the **Home** page.

    ![](./media/image26.png)

15. Select **Use with Foundry** -\> **Foundry** -\> **+ Create** to
    create the new Foundry resource.

    ![A screenshot of a computer Description automatically
    generated](./media/image27.png)

16. Enter the below details, select the nearest region and
    select **Review + create**.

    - Resource Group - **@lab.CloudResourceGroup(ResourceGroup1).Name**

    - Name - +++resource@lab.LabInstance.Id+++

    - Location - **@lab.CloudResourceGroup(ResourceGroup1).Location**

    - Default project name - +++proj@lab.LabInstance.Id+++

    ![](./media/image28.png)

17. Select **Create** in the next screen.

    ![](./media/image29.png)

18. Once the resource is created, select **Go to resource** and then
    select **Go to Foundry portal**. This will take you to
    the **Microsoft Foundry** page.

    ![](./media/image30.png)

    ![](./media/image31.png)

    ![](./media/image32.png)

19. Select **Build** from the top menu since you will be building a new
    agent now.

    ![](./media/image33.png)

20. Click **Assign me the Foundry User role**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image34.png)

21. Wait for 5 mins and then refresh the window.

    ![](./media/image35.png)

22. Select **New agent -\> Build an agent** to create a new product
    expert agent.

    ![A screenshot of a computer Description automatically
    generated](./media/image36.png)

23. Enter the name of the agent as +++**TrailGearExpert+++** and then
    select **Create and Open playground**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image37.png)

24. Once the agent is created, enter the below instructions in the
    Instructions area of the agent and then select **Save**.
    ```
    You are TrailGear Expert, a product specialist for outdoor and camping
    gear.

    Your responsibilities:

    - Provide accurate and detailed information about products such as
    backpacks, tents, and camping accessories.

    - Recommend products based on user needs (e.g., trekking duration,
    weather conditions, group size).

    - Compare products when asked.

    - Use only the provided knowledge sources.

    Guidelines:

    - Ask follow-up questions if user intent is unclear.

    - Provide structured recommendations (features, use case, why it
    fits).

    - Do not answer questions related to refunds, shipping, or
    support-those are handled by another agent.
    ```

    ![](./media/image38.png)

25. Select the **Upload files** option -\> **Browse for files**.

    ![](./media/image39.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image40.png)

26. Navigate to **C:\Lab Files\Foundry agent**, select all the files
    under it and select **Open**.

    ![](./media/image41.png)

27. Select **Attach** to add the files to the agent.

    ![](./media/image42.png)

28. Once all the configuration is done, select **Save** to save the
    agent.

    ![A screenshot of a computer Description automatically
    generated](./media/image43.png)

29. From the agent page, click **Publish (1)**, and then select **Teams
    & Microsoft 365 Copilot (2)**.

    ![](./media/image44.png)

30. In the Publish to Teams and Microsoft 365 window add:

    - Agent name set to **TrailGearExpert**

    - Short description:

        ```
        Provides expert recommendations and product information for outdoor
        and camping gear, including backpacks, tents, and accessories.

        ```

    - Description:

        ```
        TrailGear Expert helps customers choose the right outdoor and camping
        equipment based on their needs. It provides accurate product
        information, compares products, and recommends suitable gear for
        activities such as hiking, trekking, camping, and backpacking. The
        agent asks follow-up questions when needed and uses only approved
        knowledge sources to ensure reliable recommendations. It does not
        handle refunds, shipping, or customer support inquiries, which are
        managed by a separate agent.
        ```
    - Author: Enter the current user name, such as : **odl_user\_**@lab.LabInstance.Id

31. Then click to **Next: Publish** options

    ![A screenshot of a computer Description automatically
    generated](./media/image45.png)

32. Choose who can use the agent: **Just you**. Then select **Publish**.

    ![](./media/image46.png)

33. Select done. Now, you have successfully created and configured the
    Foundry agent to provide detailed product knowledge and
    recommendations.

    ![](./media/image47.png)

### Task 2: Connect Foundry agent to Copilot Studio agent

In this task, you will connect the Foundry agent to the Copilot Studio
agent, enabling seamless delegation of product-related queries.

1.  Navigate back to the Copilot Studio - **TrailAssist Concierage
    agent** and select the **Agents** tab.

![](./media/image48.png)

2.  Select **Connect to an external agent** -\> **Microsoft Foundry** to
    add the agent created in the Foundry.

    ![](./media/image49.png)

3.  Select **Create new connection** to establish connection with the
    Foundry.

    ![](./media/image50.png)

4.  Navigate back to the Foundry tab, select **Home** and copy
    the **Project endpoint** from there.

    ![](./media/image51.png)

5.  Paste the copied endpoint in the Copilot Studio - create connection
    pane and then select **Create**.

    ![](./media/image52.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image53.png)

6.  Once the connection is established, click **Next**.

    ![](./media/image54.png)

7.  Enter the below details and select **Add and configure**.

    - **Name:** **TrailGearExpert**

    - **Description:**

        ```
        A specialized AI agent that provides detailed

        product knowledge, comparisons, and personalized recommendations

        for outdoor gear including backpacks, tents, and camping

        accessories.
        ```

    - **Agent Id:** **TrailGearExpert**

    ![A screenshot of a web page Description automatically
    generated](./media/image55.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image56.png)

You have successfully integrated the Foundry agent, enabling the Copilot
Studio agent to delegate product-specific queries to a specialized
agent.

### Task 3: Test the agent

In this task, you will test the integrated setup to validate that
product-related queries are correctly routed to the Foundry agent.

1.  Open the Test pane and enter the following prompt in the prompt
    field and select **Send** button:

    +++Which backpack is best for a 3 day trek?+++

    ![A screenshot of a computer Description automatically
    generated](./media/image57.png)

2.  The first time, it will ask to open the **connection
    manager** and **connect**. Follow the prompts and create the
    connection and then ask the same question in the Test pane.

    ![A screenshot of a computer Description automatically
    generated](./media/image58.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image59.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image60.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image61.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image62.png)

3.  From the Activity tab, open the latest activity to see the details
    of the chat. You can see that the agent has invoked the
    TrailGearExpert - Foundry agent to answer this question.

    ![A screenshot of a computer Description automatically
    generated](./media/image63.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image64.png)

You have validated that the Copilot Studio agent can successfully invoke
the Foundry agent to handle product-related queries.

You have extended your solution by adding a specialized product agent,
demonstrating agent collaboration and domain-specific intelligence.

## Exercise 3: Create Fabric Data Agent

In this exercise, you will further enhance the solution by introducing a
Fabric Data Agent to provide real-time insights from structured business
data.

### Task 1: Create Lakehouse and load data

In this task, you will create a Fabric workspace and Lakehouse, and load
structured datasets required for operational insights.

1.  In the new Tab, enter the following URL to navigate to the Microsoft
    Fabric portal.

    +++https://app.fabric.microsoft.com+++

    ![A screenshot of a computer Description automatically
    generated](./media/image65.png)

2.  Select **Workspaces -\> + New Workspace**.

    ![A screenshot of a computer Description automatically
    generated](./media/image66.png)

3.  Enter the name of the workspace
    as +++fabws@lab.LabInstance.Id+++ and
    select **Apply**.

    ![A screenshot of a computer Description automatically
    generated](./media/image67.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image68.png)

4.  Select **+ New item** -\> **Lakehouse** to add a Lakehouse.

    ![A screenshot of a computer Description automatically
    generated](./media/image69.png)

    ![A screenshot of a search engine Description automatically
    generated](./media/image70.png)

5.  Enter the Lakehouse name
    as +++lh@lab.LabInstance.Id+++ and
    select **Create**.

    ![A screenshot of a computer Description automatically
    generated](./media/image71.png)

6.  Select **Upload files**.

    ![A screenshot of a computer Description automatically
    generated](./media/image72.png)

7.  Navigate to **C:\Lab Files\Fabric Data Agent**, select all the csv
    files under it and click **Open**. Then select **Upload**.

    ![A screenshot of a computer screen Description automatically
    generated](./media/image73.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image74.png)

8.  Close the pane once all the files are uploaded.

    ![A screenshot of a computer Description automatically
    generated](./media/image75.png)

9.  Select the 3 dots next to the **customer** file, select **Load to
    Tables** -\> **New table**.

    ![A screenshot of a computer Description automatically
    generated](./media/image76.png)

10. Select **Load** in the **Load file to new table** modal.

    ![A screenshot of a computer Description automatically
    generated](./media/image77.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image78.png)

11. Ensure that the data is loaded as table.

    ![A screenshot of a computer Description automatically
    generated](./media/image79.png)

12. **Repeat** the **steps 15-17** for the other files as well to load
    the **products**, **orders** and **inventory** tables.

    ![A screenshot of a computer Description automatically
    generated](./media/image80.png)

You have successfully created the Lakehouse and loaded structured data,
enabling data-driven capabilities for your solution.

### Task 2: Create Fabric Data Agent

In this task, you will create the **TrailOps Analyst** Fabric Data Agent
and configure it to answer queries based on structured data.

1.  From the left pane, select the **Workspace** and select **+ New
    item**.

    ![](./media/image81.png)

2.  Select **Data agent** from the list to create a new Fabric Data
    Agent.

    ![A screenshot of a computer Description automatically
    generated](./media/image82.png)

3.  Enter the name as **TrailOpsAnalyst** and select **Create**.

    ![](./media/image83.png)

4.  Once the agent is created, a data source needs to be added to it.
    Select **Add a data source**.

    ![](./media/image84.png)

5.  Select the
    Lakehouse +++lh@lab.LabInstance.Id+++ and
    select **Add**.

    ![A screenshot of a computer Description automatically
    generated](./media/image85.png)

6.  **Select** all the four **tables** from the left pane.

    ![A screenshot of a computer Description automatically
    generated](./media/image86.png)

7.  Select **Setup** -\> **Instructions** and add the below instructions
    to the agent.

    ```
    You are TrailOps Analyst, a data specialist for retail operations.

    Your responsibilities:

    - Answer queries using structured data such as orders, inventory, customers, and shipments.

    - Provide accurate, concise, and data-backed responses.

    - Perform aggregations, summaries, and filtering when needed.

    Guidelines:

    - Only answer based on available data.

    - If data is not available, say so clearly.

    - Do not answer product recommendations or policy-related questions.

    - Focus on insights, trends, and real-time operational data.

    ```

    ![](./media/image87.png)

8.  Test the agent with the below question and observe that the agent
    replies based on the data in the lakehouse.

    +++Which products are low in stock?+++

    ![A screenshot of a computer screen Description automatically
    generated](./media/image88.png)

    ![](./media/image89.png)

9.  Select **Publish** to publish the agent.

    ![](./media/image90.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image91.png)

You have successfully created and configured the Fabric Data Agent to
provide insights based on business data.

### Task 3: Add Fabric Data Agent to the Copilot Studio agent

In this task, you will integrate the Fabric Data Agent with the Copilot
Studio agent to enable real-time data-driven responses.

1.  In the Copilot studio, Select **Agents** tab from the **TrailAssist
    Concierge** agent in Copilot Studio.

    ![](./media/image92.png)

2.  Select **+ Add an agent**, **Connect to an external
    agent** -\> **Microsoft Fabric**.

    ![A screenshot of a computer Description automatically
    generated](./media/image93.png)

3.  **Create new connection** to establish connection with Fabric.

    ![](./media/image94.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image95.png)

4.  Select **Create** to proceed.

    ![A screen shot of a computer Description automatically
    generated](./media/image96.png)

5.  Follow the prompts to add the **TrailOpsAnalyst** agent to the
    Copilot Studio agent.

    ![](./media/image97.png)

    ![](./media/image98.png)

6.  Enter the below description and select **Add and configure**.
    ```
    A data-driven AI agent that provides real-time insights on orders,
    inventory, customer activity, and operational metrics using structured
    data from Fabric Lakehouse.
    ```

    ![](./media/image99.png)

You have successfully integrated the Fabric Data Agent, enabling the
Copilot Studio agent to access real-time operational insights.

### Task 4: Test the agent

In this task, you will test the end-to-end solution to validate that the
Copilot Studio agent orchestrates across all connected agents.

1.  Select the **Test** pane.

    ![](./media/image100.png)

2.  Enter +++**Show the recent orders+++** and
    click **Send**. **Allow** connection for the first time to proceed.

    ![A screenshot of a computer Description automatically
    generated](./media/image101.png)

    ![](./media/image102.png)

3.  Navigate to the **Activity** tab to view the result. You can also
    see that the agent has internally called the **Fabric Data
    Agent** to answer the question.

    ![](./media/image103.png)

4.  Send **Which products are low in stock?** questions in the Test pane
    and see the output coming from the Fabric Data agent.

    ![A screenshot of a chat Description automatically
    generated](./media/image104.png)

    ![A screenshot of a computer Description automatically
    generated](./media/image105.png)

The Copilot Studio base agent now orchestrates the request to the
Foundry or Fabric agents or answers itself based on the type of the
question and the purpose of the agent.

You have validated that the Copilot Studio agent can intelligently route
queries and orchestrate responses across multiple specialized agents.

You have successfully completed the multi-agent architecture by adding a
data-driven agent, enabling real-time insights and advanced
orchestration.

## Summary:

In this lab, you created the **Retail Assistant**, a modern AI solution
for an outdoor retail company. You began by building a Copilot Studio
agent that serves as the primary customer interface for handling support
and policy-related queries. You then extended its capabilities by
integrating a specialized product expert agent built using Microsoft
Foundry to provide intelligent product recommendations. Finally, you
added a Fabric Data Agent to enable real-time insights from structured
business data such as orders and inventory.

Now, you will have implemented a fully functional multi-agent system
that demonstrates orchestration, specialization, and data-driven
intelligence.
