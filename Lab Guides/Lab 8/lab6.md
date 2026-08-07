# Lab 6 – Build a Store Operations Assistant Copilot Agent for trusted customer success at Zava Retail

**Estimated Duration:** 40 minutes

## Lab objectives 

This lab provides hands-on experience in building intelligent Copilot
Agents using Microsoft IQ principles. You will create a
SharePoint-integrated agent with trusted knowledge boundaries, apply the
five-step customer success framework to align it with a Core Unit of
Work, and validate it through PoC testing. The lab also covers advanced
customization using Copilot Studio, including custom instructions, topic
routing, and multi-agent orchestration by connecting with a second
specialized agent.

## Scenario

Store associates and shift managers often lose valuable time searching
through SOPs, policy documents, and operational guidelines during busy
trading hours, slowing response times, and impacting customer service.
The Store Operations Assistant Copilot Agent empowers frontline retail
workers with instant, contextual access to accurate store procedures in
the flow of work—helping them resolve customer queries faster, ensure
policy compliance, and keep store operations running smoothly during
peak demand.



## Exercise 1: Creating and Configuring Your Copilot Agent 

Microsoft IQ represents a unified intelligence layer that brings
contextual, work-aware AI into your everyday apps and agents. In this
part, you will create a Copilot Agent in SharePoint that is grounded in
verified, organization-specific content — ensuring responses are both
intelligent and trustworthy.

### Task 1: Access the Agent Creation Tool 

1.  Navigate to +++https://m365.cloud.microsoft/+++ to open Microsoft
    365 Copilot.

2.  Sign in with your Microsoft 365 Copilot account.
   
    - Username - +++@lab.CloudPortalCredential(User1).Username+++
    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image1.png)
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image101.png)

3.  Click **Yes**, to stay signed in.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image2.png)
    ![](./media/pp1.png)

4.  From the left navigation bar, select **App Launcher** and then select
    **SharePoint**.
    
    ![](./media/pp2.png)

5.  On the SharePoint home page, create your organization’s site. Select
    **Build** from the left navigation bar.
    
    ![](./media/a3.png)
6. Select **Site** to create your organization’s site.

    ![](./media/a4.png)
7. Select **Standard Team** as a Site template.
   ![](./media/a5.png)
   
8. Select **Use template**.
   ![](./media/a6.png)
9. Paste the site name as +++**ZavaSite**+++ and then click **Create Site** button.

    ![](./media/a7.png)
   
   **Note:** If you encounter any error in **site address** please add 3-digit unique number at the end of ZavaSite to make the address unique.

10. Select **Go to site** to open the newly created site.
    ![](./media/a8.png)
    ![](./media/a9.png)

11. From the **Documents** Section, select **Documents** and then select **Folder upload**.
    ![](./media/pp3.png)
    
12. Navigate to **C:\Labfiles\Lab6-Lab files** and select **HR Document** folder and then select **Open** to add this folder in the site.
    ![](./media/a11.png)
    
13. Select **Upload** to upload the folder in the site.
    ![](./media/a12.png)
    
14. Similarly add the remaining folders individaully in the site.
    - Product Specs Folder
    - Project Updates
    - Shift Handover notes
    - SOP library

    ![](./media/q13.png)

>[!Note] Before testing your Copilot Agent, ensure that all
required source documents (such as project updates, SOP files, product
specifications, shift handover notes, or any other referenced materials)
are uploaded to the appropriate SharePoint site libraries and folders.
The agent can only generate accurate, grounded responses from content
that exists in the site and is accessible through its configured
knowledge sources.

### Task 2: Create a New Agent 

With your SharePoint site open and your frontline scenario selected, you
will now build the agent.  
  
1. Navigate back to M365 Copilot window.
   
2. In the **left navigation**, select **New Agent.** Select **Skip** to move to agent configure page.
   ![](./media/pp4.png)

3. When the **Create new agent panel** opens, paste the following
information in the respective fields:

    - **Agent Name**: `Project Knowledge Assistant`

    - **Description**: `Helps users find project documents and summaries`

    - **Instructions**: `Provide concise answers using only verified information from included SharePoint sources` 

    ![](./media/pp5.png)
   
4. Navigate back to SharePoint window and copy the **HR Document** folder URL.
   ![](./media/a17.png)
   
5.  Navigate back to the M365 Copilot window and under **Knowledge tab** paste the copied URL to add the folder in the agent. 

    ![](./media/a18.png)
    ![](./media/a19.png)

6. Similarly add the remaining folders.
   ![](./media/a20.png)
   
7.  Click **Create** to finalize your agent configuration.  

    ![](./media/pp7.png)
8. Select **Start Chat** to open newly created agent.
   ![](./media/pp8.png)
   ![](./media/pp9.png)

### Task 3: Test Your Agent 

Testing your agent validates both grounding knowledge and the quality of
its responses. This step reflects the Trust dimension of Microsoft IQ —
agents should only surface verified, relevant information.

1.  Navigate back to SharePoint window. Open **Agent Chat** on the right side of the ZavaSite page.

    ![](./media/a24.png)

2.  In the chat field, paste the following prompt and select **Send button**.

    +++"Summarize the project plan”+++
    
    ![](./media/a25.png)

3.  Review the output:  
      
    ![](./media/a26.png)
    
## Exercise 2: Advanced Instruction Authoring in Copilot Studio

The default Instructions field in SharePoint's agent creator is powerful
but limited. Copilot Studio gives you a richer editing surface —
including System Prompt composition, fallback handling, and topic-based
routing — that lets you control exactly how the agent reasons and
responds.

### Task 1: Open Your Agent in Copilot Studio

1.  Navigate back to M365 Copilot window.
2.  Click on ellipsis icon(...) and select **Edit.**
    
    ![](./media/pp12.png)

3.  Select the ellipsis icon on the upper left corner. Select **Copy to
    Copilot studio**.
    
    ![](./media/pp13.png)

4.  A confirmation prompt window will pop-up. Select **Get Started.**
   
    ![](./media/pp10.png)

5.  Select your **Environment** and Click **Continue**.
   
    ![](./media/pp11.png)

6. You will be redirected to the Copilot Studio page. Here you can edit
    the instructions, and paste the below given instructions:  

    ```
    You are the Project Knowledge Assistant.

    Answer only questions related to store operations using the connected SharePoint knowledge sources.
    
    If a connected agent has already handled the user's request, do not repeat the transfer, re-evaluate the same request, or invoke the connected agent again.
    
    Do not rephrase or repeat the connected agent's response.
    
    After a connected agent completes its response, consider the request finished unless the user asks a new question.
    
    Always cite the source document when available.
    ```
    Also remove copy from the agent's name.
    
    ![](./media/pp14.png)
    
7. Click **Create**.
    
    ![](./media/pp15.png)

8. After reviewing your agent, Click **Publish**.

    ![](./media/a33.png)
    
9. Click **Publish** again
    ![](./media/a34.png)

### Task 2: Add a Topic: Out-of-Scope Redirect

Topics in Copilot Studio are rule-based conversation flows that trigger
when specific phrases or conditions are detected. You will create a
short topic that politely redirects users who ask questions outside the
agent's domain.

1.  In Copilot Studio, navigate to **Topics** in the upper menu bar.
   
    ![](./media/a35.png)

2.  Select + **Add a topic \> From blank.**
   
    ![](./media/a36.png)

3.  Paste the name of the topic: +++Out-of-Scope Redirect+++
    
    ![](./media/a37.png)
    
4.  In the Trigger section, paste the following phrases as trigger
    phrases (one per line):

    ```
    - I need help with something else

    - Can you help me with HR?

    - This is not related to my work

    - I have a different question
    ```

    ![](./media/a38.png)

5.  Click **+ icon** below the trigger node to add a Message node.
    Select **Send a Message**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image27.png)  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image28.png)

6.  Paste the following text in the message description box:

    ```
    I am specialized for HR & Payroll Assistant questions. For other
    topics, please contact your team lead or visit the company intranet. Is
    there anything else I can help you with in my area?
    ```
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image29.png)
7. Select the + sign below the message node, then select Topic Management->End conversion.
   ![](./media/pp16.png)

8. Click **Save** to save the topic and then, select **Publish(2 times)** to publish the agent again.
    
   ![](./media/a39.png)
   ![](./media/a40.png)

### Task 3: Test the agent

1.  Select **Test** from the upper navigation bar.
   
    ![](./media/a41.png)

2.  Paste the following prompt, and select the **Send** button:  
    +++Can you help me with HR?+++
    
    ![](./media/a42.png)

3.  Review the output:  
    ![](./media/a43.png)

## Exercise 3: Designing a Multi-Agent Orchestration Pattern

Real enterprise deployments rarely rely on a single agent. Complex
workflows such as a procurement request that touches both inventory data
and HR approval processes, that require multiple specialized agents
working in coordination. This exercise introduces the concept of
multi-agent orchestration and help you design (and partially configure)
a handoff pattern between your primary agent and a second specialized
agent.

### Task 1: Create the Handoff Topic

You will now create a new topic in your primary agent that triggers
whenever a user asks a question outside the primary scope. This topic
will surface a handoff message and when the license supports, it
redirects the user to the second agent.

1.  In Copilot Studio, navigate to **Topics**. Select **+Add a New topic > From blank**.  
    ![](./media/a44.png)

2.  Paste the following information in the topic:  

    **Name**- `Handoff to Secondary Agent`

    **Trigger phrases**: `"payroll", "leave request", "HR policy", "annual leave", "employee record"`

    ![](./media/a45.png)

3.  Click **+** to add a new node.
   
    ![](./media/a46.png)

4.  Select **Send a Message** to add a message node.
   
    ![](./media/a47.png)

5.  In the Message description box, paste the following information:
   
    `That question is outside my area. I'm connecting you to the HR &
    Payroll Agent who can help with that — one moment please`

    ![](./media/a48.png)
    
6. Click Save and **Publish** to save the node and publish the setting
    again.

    ![](./media/a49.png)
    ![](./media/a50.png)
    
### Task 2: Configure the Secondary Agent

Now, we will create a lightweight secondary agent to handles the
out-of-scope queries using multi-agent connections.

1.  In Copilot Studio, select **Agents** from the left navigation
    bar and then select **+Create blank agent**.
    
    ![](./media/a51.png)

2.  Enter the agent name: +++HR & Payroll Assistant+++. Click **Create**
    
    ![](./media/a52.png)

3.  In the **Instructions** field, click **Edit** and then paste the following instructions:

    `You are the HR & Payroll Assistant. You handle queries specifically
    related to store operations. Use only verified content from your
    connected sources. Always cite source and section. If a query falls
    outside your scope, say: "That's outside my remit. Please contact the
    appropriate team`
    
    Click **Save** to save the instruction.
    
    ![](./media/a53.png)

4.  In the Knowledge section, Click **+Add Knowledge** to add knowledge to the agent. add the relevant HR
    document form C:\Labfiles\Lab6-Lab files\HR Document
    You save it on your **SharePoint** site, and
    paste the **URL** here. Or you can also
    upload the file by using “**Add knowledge**” section.

    ![](./media/a54.png)
    
5. Here we are using **SharePoint** to add knowledge.
   ![](./media/a55.png)
   
6. Select **Browse items->More places->ZavaSite**
   ![](./media/a56.png)
   ![](./media/a57.png)
7. Select **HR Document** and then select **Confirm selection**
    ![](./media/a58.png)
8. Click **Add to agent**.
    ![](./media/a59.png)
    ![](./media/a60.png)
9. Select **Publish** to publish the secondary
    agent.
    ![](./media/a61.png)
    ![](./media/a62.png)
    
### Task 3: Add the Secondary Agent to the Primary Agent. 

1. Go to the **Project Knowledge Assistant** Agent.
   
    ![](./media/a63.png)

2. In the **Agent section**, select **+Add**.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image45.png)

3. Select the **HR & Payroll Assistant** from the list.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image46.png)

4. Paste the following description in the description box and then **disable** pass the converstion history to the agent:
   
    ```
    Use this agent when users ask about HR or payroll matters, including
    payslips, leave balances, salary deductions, attendance, tax forms,
    employee benefits, or HR policy questions. Routes employee-related
    workforce support queries to the HR & Payroll Assistant for accurate 
    resolution
    ```
    Click **Add and configure**.
    ![](./media/a64.png)
5. Scroll down and move to the completion step, paste the following message to display:  
  
    `Your request relates to HR and payroll support. Transferring you now to the HR & Payroll Assistant for accurate assistance`

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image48.png)

6. Select **Publish**(twice) to publish the agent.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image49.png)

### Task 4: Test the End-to-End Orchestration

With both agents published, validate the complete handoff flow using the
test scenarios below.

1.  Paste the following prompt in the chat interface:  
      
    `What is my leave balance?`
   
    ![](./media/a65.png)

2.  Review the output:  
    ![](./media/a66.png)
    Note: It will give you multiple outputs.
    
## Summary 

In this lab, you created and configured a SharePoint-grounded Project
Knowledge Assistant in Microsoft Copilot Studio, using verified
SharePoint content to ensure accurate and trusted responses. You scoped
and prioritized agent use cases, defined a Core Unit of Work, and mapped
capabilities using the Work IQ framework. You also conducted a
structured proof of concept, evaluated results for scaling
opportunities, authored advanced conditional instructions, created
out-of-scope redirects, and designed a multi-agent orchestration flow
with structured handoffs between primary and specialized agents.
