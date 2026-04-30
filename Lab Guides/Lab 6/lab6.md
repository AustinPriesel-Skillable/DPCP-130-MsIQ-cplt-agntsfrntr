# Lab 6 – Build the Project Knowledge Assistant Copilot Agent with Microsoft IQ for trusted customer success

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

4.  Click **Yes**, to stay signed in.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image2.png)

5.  In the left navigation bar, select **All Agents** and then select
    **SharePoint**.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image3.png)

7.  On the SharePoint home page, create your organization’s site. Click
    **Create site** in the top-left corner and follow the wizard.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image4.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image5.png)

9.  Paste the site name as +++**ZavaSite**+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image6.png)

10. Navigate to **C:\Labfiles\Lab6-Lab files** and **upload** the following folders in your SharePoint
    site:

- Product Specs Folder
- Project Updates
- Shift Handover notes
- SOP
- library
 
![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image7.png)

>[!Note] *Before testing your Copilot Agent, ensure that all
required source documents (such as project updates, SOP files, product
specifications, shift handover notes, or any other referenced materials)
are uploaded to the appropriate SharePoint site libraries and folders.
The agent can only generate accurate, grounded responses from content
that exists in the site and is accessible through its configured
knowledge sources.*

### Task 2: Create a New Agent 

With your SharePoint site open and your frontline scenario selected, you
will now build the agent.  
  
1. Log in to Microsoft Copilot with your Microsoft credentials.

    - Username - +++@lab.CloudPortalCredential(User1).Username+++
    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image1.png)
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image101.png)

3. In the **left navigation**, select **New Agent.**

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image8.png)

4. Select **Create New Agent** from the top left corner.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image9.png)

6. When the **Create new agent panel** opens, paste the following
information in the respective fields:

    - **Agent Name**: `Project Knowledge Assistant`

    - **Description**: `Helps users find project documents and summaries`

    - **Instructions**: `Provide concise answers using only verified information from included SharePoint sources` 

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image10.png)

8.  Navigate to the **Knowledge tab** in the Create new agent panel.
    Enter the URL for your ZavaSite that lists all the required
    documents.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image11.png)

9.  Click **Create** to finalize your agent configuration.  

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image12.png)

### Task 3: Test Your Agent 

Testing your agent validates both grounding knowledge and the quality of
its responses. This step reflects the Trust dimension of Microsoft IQ —
agents should only surface verified, relevant information.

1.  Open **Agent Chat** on the right side of the ZavaSite page.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image13.png)

2.  In the chat field, paste the following prompt and select **Execute
    button**.

    +++"Summarize the project plan” +++
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image14.png)

3.  Review the output:  
      
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image15.png)

## Exercise 2: Advanced Instruction Authoring in Copilot Studio

The default Instructions field in SharePoint's agent creator is powerful
but limited. Copilot Studio gives you a richer editing surface —
including System Prompt composition, fallback handling, and topic-based
routing — that lets you control exactly how the agent reasons and
responds.

### Task 1: Open Your Agent in Copilot Studio

1.  In your browser, navigate directly to +++https://copilotstudio.microsoft.com/+++ Sign in with your M365 lab credentials.
   
    - Username - +++@lab.CloudPortalCredential(User1).Username+++
    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++
      
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image1.png)
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image101.png)

3.  The Knowledge Assistant Agent opens. Click on ellipsis icon and
    Select **Edit.**
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image16.png)

5.  Select the ellipsis icon on the upper left corner. Select **Copy to
    Copilot studio**.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image17.png)

7.  A confirmation prompt window will pop-up. Select **Get Started.**
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image18.png)

9.  Select your **Environment** and Click **Continue**.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image19.png)

11. You will be redirected to the Copilot Studio page. Here you can edit
    the instructions, and paste the below given instructions:  

    ```
    You are the Store Operations Assistant for a retail
    organization. Only answer questions using content from the connected
    SharePoint sources. Always cite the document name and section. If a
    question falls outside your knowledge sources, respond: "I don't
    have that information — please check with your shift manager or
    visit the intranet." Keep responses to 3–5 bullet points. Do not
    speculate or summarize information that is not present in a
    source
    ```
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image20.png)

11. Click **Create**.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image21.png)

13. After reviewing your agent, Click **Publish**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image22.png)

### Task 2: Add a Topic: Out-of-Scope Redirect

Topics in Copilot Studio are rule-based conversation flows that trigger
when specific phrases or conditions are detected. You will create a
short topic that politely redirects users who ask questions outside the
agent's domain.

1.  In Copilot Studio, navigate to **Topics** in the upper menu bar.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image23.png)

3.  Select + **Add a topic \> From blank.**
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image24.png)

5.  Paste the name of the topic: +++Out-of-Scope Redirect.+++
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image25.png)

7.  In the Trigger section, paste the following phrases as trigger
    phrases (one per line):

    ```
    - I need help with something else

    - Can you help me with HR?

    - This is not related to my work

    - I have a different question
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image26.png)

8.  Click **+ icon** below the trigger node to add a Message node.
    Select **Send a Message**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image27.png)  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image28.png)

9.  Paste the following text in the message description box:

    ```
    I am specialized for HR & Payroll Assistant questions. For other
    topics, please contact your team lead or visit the company intranet. Is
    there anything else I can help you with in my area?
    ```
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image29.png)

10. Click **Save** to save the topic and then, select **Publish** to publish the agent again.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image30.png)

### Task 3: Test the agent

1.  Select **Test** from the upper navigation bar.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image31.png)

3.  Paste the following prompt, and select the **Execute** button:  
    +++Can you help me with HR?+++
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image32.png)

4.  Review the output:  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image33.png)

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
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image24.png)

2.  Paste the following information in the topic:  

    **Name**- `Handoff to Secondary Agent`

    **Trigger phrases**: `payroll", "leave request", "HR policy", "annual leave", "employee record"`

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image34.png)

4.  Click **+** to add a new node.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image35.png)

6.  Select **Send a Message** to add a message node.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image36.png)

8.  In the Message description box, paste the following information:
   
    `That question is outside my area. I'm connecting you to the HR &
    Payroll Agent who can help with that — one moment please`

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image37.png)

10. Click Save and **Publish** to save the node and publish the setting
    again.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image38.png)

### Task 2: Configure the Secondary Agent

Now, we will create a lightweight secondary agent to handles the
out-of-scope queries using multi-agent connections.

1.  In Copilot Studio, select **New Agent** from the left navigation
    bar.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image39.png)

3.  In the name section, paste the following name of the agent as below:

    +++HR & Payroll Assistant+++
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image40.png)

5.  In the Instructions field, paste the following instructions:

    `You are the HR & Payroll Assistant. You handle queries specifically
    related to store operations. Use only verified content from your
    connected sources. Always cite source and section. If a query falls
    outside your scope, say: "That's outside my remit. Please contact the
    appropriate team`
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image41.png)

4.  In the Knowledge section, add the relevant HR
    document form C:\Labfiles\Lab6-Lab files\HR Document
    You save it on your **SharePoint** site, and
    paste the **URL** here. Or you can also
    upload the file by using “**Add knowledge**” section.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image42.png)

5.  Select **Publish** to publish the secondary
    agent.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image43.png)

### Task 3: Add the Secondary Agent to the Primary Agent. 

1. Go to the **Project Knowledge Assistant** Agent.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image44.png)

3. In the Agent section, select **+Add**.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image45.png)

5. Select the **HR & Payroll Assistant** from the list.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image46.png)

7. Paste the following description in the description box:
   
    ```
    Use this agent when users ask about HR or payroll matters, including
    payslips, leave balances, salary deductions, attendance, tax forms,
    employee benefits, or HR policy questions. Routes employee-related
    workforce support queries to the HR & Payroll Assistant for accurate
    resolution
    ```
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image47.png)

9. In the completion step, paste the following message to display:  
  
    `Your request relates to HR and payroll support. Transferring you now to the HR & Payroll Assistant for accurate assistance`

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image48.png)

11. Select **Publish** to publish the agent.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image49.png)

### Task 4: Test the End-to-End Orchestration

With both agents published, validate the complete handoff flow using the
test scenarios below.

1.  Navigate to **Project Knowledge Assistant** agent.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image50.png)

3.  Select **Test** in the upper menu bar.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image51.png)

5.  Paste the following prompt in the chat interface:  
      
    `What is my leave balance?`
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image52.png)

7.  Review the output:  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image53.png)
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%206/media/image53.png)

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
