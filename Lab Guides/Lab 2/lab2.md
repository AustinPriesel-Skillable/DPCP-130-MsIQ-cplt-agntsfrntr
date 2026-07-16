# Lab 2 - Elevate Zava Retail intelligence with a Researcher Agent for smarter insights and reporting

**Estimated duration:** 40 minutes

## Lab objective

In this lab, you will learn how to use the Researcher Agent in Microsoft
365 to gather, summarize, and analyse organization-related
information. The Researcher Agent can collect relevant data from your
documents, emails, chats, and Teams messages, helping you create
summaries, reports, and follow-ups on a given project or topic. After
completing this lab, you will be able to: 

- Locate and launch the **Researcher Agent** in Microsoft 365. 

- Use prompts to gather recent discussions, documents, and emails. 

- Interact with follow-up questions to refine results. 

- Generate summaries, reports, or action items related to a topic. 

- Explore advanced prompt use cases such as progress updates, meeting
prep, and document discovery. 

## Scenario

Zava Retail, a fast-growing omnichannel retailer, was preparing for a
large-scale Festive Collection campaign launch across online
marketplace, physical stores, supplier ecosystem, and customer support
operations. Over the last 90 days, multiple teams have been working on
vendor onboarding, marketing campaigns, inventory planning, and customer
support readiness. While multiple teams contributed to the initiative,
critical information was scattered across emails, Teams chats,
documents, and meeting notes—making it difficult for leadership to gain
a unified view.

At Zava Retail, all the critical information is scattered across various
communication channels. The critical information includes:
- Emails (vendor discussions, escalations)
- Teams chats (campaign planning)
- Documents (strategy decks, reports)
- Meeting notes

Due to the information fragmentation, there is no single source of truth
and leadership team cannot see the project status, risks, and
dependencies. It takes a lot of manual effort to gather the required
updates due to which the action items are lost in conversations and
decision-making process is also delayed.

To solve this, Zava Retail adopted the **Researcher Agent in Microsoft
365 Copilot** to consolidate, analyze, and transform fragmented data
into actionable business intelligence—enabling faster and more informed
decision-making.

**Key Personas**

**Patricia Gray – Operations Head**

The operations head at Zava Retail oversees campaign readiness, aligns
cross-functional teams, and drives executive decisions. The major
challenges include:

- Needs a 360° view of campaign readiness

- Cannot manually review hundreds of emails/docs

- Needs quick insights before leadership meetings

## Exercise 1: Access the Researcher Agent 

Patricia logs into Copilot to review Festive Campaign readiness.

1.  Navigate to +++https://m365copilot.com/+++ Microsoft 365 copilot
    page. 

2.  Enter the **Username** - +++@lab.CloudPortalCredential(User1).Username+++ in the field and then click on
    the **Next** button to proceed. 

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image1.png)

3.  Enter **TAP Token** - +++@lab.CloudPortalCredential(User1).AccessToken+++ in the field and then click on the **Sign
    in** button and click on the **Yes** to stay Signed in. 

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image2.png)
    ![](./media/b1.png)

4.  Explore the Copilot chat environment.

    ![](./media/b2.png)

5.  In the left **navigation pane**, look for **Agents**. 

    - If **Researcher** appears directly under the **Agents** section \>
    select **Researcher**. 

    ![](./media/b3.png)

    - If not, select **More agents**. In the **Agent Store** window, under
    the **Built by Microsoft** section, select **Researcher**. 

    ![](./media/b4.png)

6.  The **Researcher Agent window** opens in a new pane. 

    ![](./media/b6.png)

## Exercise 2: Run Your First Research Prompt (Campaign Intelligence)

Patricia wants a complete overview of campaign progress for Zava Retail.

1.  Before interacting with agent first we will send some demo campaign emails to the current lab user with your emial. So the Researcher Agent can access relevant data and produce meaningful insights and summaries. You can get demo campaign email from **C:\Labfiles\Lab2-Lab** files.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image71.png)
2. To view sample email navigate to +++https://outlook.office365.com/mail+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image300.png)

3. Go to the Researcher agent, paste the following prompt in the prompt
    field, and then click on the **Execute** button.
   
    ```
    Help me gather and summarize all recent discussions, documents, and
    emails related to Zava Retail Festive Campaign from the past 90 days.

    Include:

    - Campaign planning progress

    - Vendor onboarding updates

    - Inventory readiness

    - Marketing campaign activities

    - Key risks or delays 
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image8.png)

4.  Wait for the **Researcher Agent** to gather and summarize the data
    review the Researcher agent carefully. The Researcher Agent may ask
    clarifying questions. Select the report length as “Short” and select/enter
    “Go ahead with your best judgement” and select **Send** button.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image9.png)

    >[!Note] Ensure that demo campaign emails and Teams messages are
    shared beforehand so the Researcher Agent can access relevant data and
    produce meaningful insights and summaries.

5. Review the Researcher agent’s response: 

    The agent searches across Outlook, Teams, and SharePoint documents to
    retrieve the following:
    
    - Aggregates insights
    
    - Builds structured summary
    
    - Campaign progress
    
    - Vendor updates
    
    - Risks
    
    - Strategic insights

6. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image10.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image11.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image12.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image13.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image14.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image15.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image16.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image17.png)
    > Note: Generated outputs are non-deterministic and may vary across users, sessions, and environments.

## Exercise 3: Action and Decision Intelligence 

Patricia Gray needs clear next steps and decisions. This exercise will
help Researcher Agent perform a task or take a specific action based on
the data, findings, or situation.

### Task 1: Identify Action Items

1.  In the Researcher agent, paste the below given prompt in the
    field and then click on the **Send** button. 

    +++List all action items related to the Zava Festive Campaign.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image18.png)

2.  Review the output:

    - Action items such as “Pending approval”, “Pending confirmation”,
    “Under review” are identified as **Action Items**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image19.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image20.png)

### Task 2: Key Decisions

1. Under the Researcher agent, paste the below given prompt in the
field and then click on the **Send** button. 

    +++Summarize key decisions made across emails and Teams discussions for
    the campaign.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image21.png)

2.  Review the output:

    - The key decisions related to multiple action items and teams are
    summarized in the output.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image22.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image23.png)

### Task 3: Draft Leadership Email

1. Select **new chat** button to start new chat
2. Under Researcher agent, paste the below given prompt in the chat
panel and then click on the **Send** button. 

    +++Draft an email to the leadership team summarizing campaign readiness and participation.+++

    ![](./media/b7.png)

3. Wait for the **Researcher Agent** to gather and summarize the data
review the Researcher agent carefully. The Researcher Agent may ask
clarifying questions. Select the report length as “Short” and select/Enter “Go
ahead with your best judgement” and select the **Send** button.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image25.png)

4.  Review the output: 

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image26.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image27.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image28.png)

### Task 4: Meeting Preparation (Executive Readiness)

Meeting preparation prompts help you gather background
information, summarize key updates, and identify action items or
discussion points before a meeting. They ensure that all participants
come informed and ready to contribute effectively. Patricia has a
leadership review meeting in next week and she want to be prepared for
the upcoming meeting.

1.  Under the Researcher agent, paste the below given prompt in the
    field and then click on the **Send** button. 

    +++Help me prepare for an upcoming meeting by summarizing recent communication and shared files about.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image29.png)

2.  Wait for the **Researcher Agent** to gather and summarize the data
    review the Researcher agent carefully. The Researcher Agent may ask
    clarifying questions. Select the report length as “Short” and select/enter
    “Meeting is the Q2 Sales Review on April 10” and select the
    **Send** button.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image30.png)

3.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image31.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image32.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image33.png)

4.  Paste the below given prompt in the field and then click on
    the **Send** button.

    +++What topics have been discussed in past weekly team syncs?+++

    ![](./media/b8.png)
    
5.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image35.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image36.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image37.png)

### Task 5: Progress and Status Analysis

Progress and status updates help you to review
achievements, identify gaps, and plan next steps. Patricia Gray wants to
update the current status, blockers, and overall campaign progress to
the leadership team.

1.  Under Researcher agent, paste the below given prompt in the field
    and then click on the **Send** button.   
    +++Summarize the current status and blockers for the Zava Festive Campaign.+++

    ![](./media/b9.png)

2.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image39.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image40.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image41.png)

### Task 6: Identify Gaps and Risks

This section helps identify missing information, unclear points, or
areas needing further investigation from research, meetings, or ongoing
project activities. Summary Prompts help you articulate what’s unclear,
while Action Prompts guide you to resolve or explore these gaps
further. Patricia wants to uncover hidden risks.

1. Start new conversation.
   ![](./media/b10.png)

2.  Under Research agent window, paste the below given prompt in the
    field and then click on the **Send** button. 

    +++What open questions or gaps remain in the Zava Festive Campaign?+++

    ![](./media/b11.png)

4.  Wait for the **Researcher Agent** to gather and summarize the data
    review the Researcher agent carefully. The Researcher Agent may ask
    clarifying questions. Select the report length as “Short” and select
    “Analyze sales data and customer feedback for gaps” and select the
    **Send** button.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image43.png)

5.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image44.png)

### Task 7: Document Discovery and Insights 

This section helps users or AI tools explore, analyse, and extract
valuable information from existing documents, reports, or shared
repositories. It focuses on identifying key insights, patterns, or
references that can guide research, planning, or project documentation. 
It helps you to find latest campaign documents and insights.

1.  Under Researcher agent, paste the below given prompt in the field
    and then click on the **Send** button.

    +++Find the latest version of Zava Festive Campaign plan and summarize key updates.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image45.png)

2.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image46.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image47.png)

3.  Enter the below given prompt in the field and then click on
    the **Send** button.   
    +++Summarize contents of shared documents related to campaign planning.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image48.png)

4.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image49.png)

### Task 8: Generate Executive Communication

Use the Researcher Agent to help communicate findings to your
team. Patricia needs a leadership update.

1.  Under Researcher Agent, paste the below given prompt in the field
    and then click on the **Send** button. 

    ```
    Draft an executive summary email on Zava Festive Campaign covering:

    - Progress

    - Risks

    - Key decisions

    - Next steps
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image50.png)

2.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image51.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image52.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image53.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image54.png)

### Task 9: Review and Refine the Output 

1.  Evaluate whether the Researcher Agent’s summary meets your
    expectations. 

2.  If results are too broad or missing key details, refine your
    prompt. 

    >[!Knowledge]: “Narrow this summary to focus only on critical risks and delivery blockers.”

3.  Export or copy the summary for documentation, reports, or meeting
    notes. 

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image55.png)

    >[!Note] Here is a brief overview of the tasks associated with each
    icon shown in the screenshot: 

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%202/media/image56.png)

    1.  **Clipboard Icon** – Likely used for **copying or
        pasting** content. 

    2.  **Thumbs-Up Icon** – Typically indicates **liking or approving** an
        item or action. 

    3.  **Thumbs-Down Icon** – Generally used to **dislike or
        disapprove** something. 

    4.  **Speaker Icon** – Represents **audio settings or volume control**. 

    5.  **Pencil Icon** – Commonly used for **editing or writing** tasks. 

    6.  **Clock with Arrow Icon** – Tooltip says **"Add to recent page"**,
        which means it adds the current item to your **recently accessed
        pages** for quick reference. 

## Summary 

In this lab, you explored how the Researcher Agent in Microsoft 365
Copilot helps transform scattered organizational data into actionable
insights and high-quality outputs. Instead of manually searching across
emails, documents, and chats, you used natural language prompts to
gather, analyze, and refine information efficiently.

In the Zava Retail scenario, you used the agent to gather updates,
generate summaries, identify risks, and create reports—giving leadership
a clear view of campaign readiness.

As a result, Zava Retail reduced information silos, improved
decision-making, and automated research to transform fragmented
communication into a single source of truth.

 
