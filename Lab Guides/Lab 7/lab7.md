# Lab 7 - Optimize financial analysis and reporting for Zava Retail finance operations with Microsoft 365 Copilot

**Estimated Duration:** 40 minutes

## Lab objectives 

In this lab, you explore how Microsoft 365 Copilot enhances the daily
workflow of finance professionals by embedding AI assistance directly
into Excel, Teams, and Copilot Chat. The lab demonstrates how Copilot
accelerates data interpretation, improves collaboration, transforms
meeting content into actionable tasks, and helps produce strategic
reports that support faster, better-informed business decisions.

## Scenario

Acting as a Financial Analyst at Zava Retail, you use Copilot to analyze
product cost data, summarize, and organize finance meeting outcomes,
generate follow-up communications, and evaluate a potential acquisition
through structured financial and operational analysis. Through these
guided scenarios, you experience how Copilot can reduce manual effort,
improve accuracy, and turn complex financial information into clear,
decision-ready insights for leadership.

**Key Personas**

- **Financial Analyst (You):** Leads data analysis, reporting, and
  strategic financial evaluation.

- **Robin Kline – Finance Manager:** Provides business context,
  priorities, and decision-making direction.

- **Amari Rivera – Finance Team Member:** Contributes operational
  finance inputs and action items.

- **Quincy Brooks – Finance Team Member:** Supports financial planning
  and task execution.

- **Miguel Reyes – Finance Team Member:** Assists with analysis and
  cross-functional finance coordination.

- **Eric Solomon – Finance Team Member:** Contributes to compliance,
  reporting, and follow-up actions.

- **Executive Leadership Team:** Reviews insights generated from Copilot
  outputs to guide strategic decisions on product launch and acquisition
  planning.

## Exercise 1: Use Copilot in Excel to Analyze New Product Line COGS

The Finance team is finalizing Cost of Goods Sold (COGS) estimates for
Zava Retail's new Zava Home product line. As the team's lead financial
analyst, you are tasked with verifying the latest COGS data provided by
the Merchandising team and ensuring leadership can easily review the
most relevant numbers.

### Task 1: Understanding Copilot in Excel

Complete the following steps in order:

1. Open web browser and navigate to **+++https://excel.cloud.microsoft/+++**. Click **Sign in** button.
   ![](./media/m1.png)
2. Enter the following credentials to login into web Excel:
   - Username - +++@lab.CloudPortalCredential(User1).Username+++
   - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++
  ![](./media/m2.png)
  ![](./media/m3.png)
  ![](./media/m4.png)
3. Click **Upload a file**.
   ![](./media/m5.png)
   
6.  Navigate to **C:\Labfiles\Lab7-Lab files** and open the **Zava Home COGS Estimates.xlsx** file.
   
    ![](./media/m6.png)
    ![](./media/m7.png)

8.  Select the Copilot icon to open Copilot chat.
   
    ![](./media/m8.png)

9.  To analyze the dataset, paste the prompt below and select
    **Send** button:
    
    ```
    I'm a financial analyst for Zava Retail. I was asked to analyze
    the Zava Home COGS Estimates spreadsheet for Zava Retail's new Zava
    Home product line. Can you please review the dataset in this
    spreadsheet and provide two things in a new sheet: (1) a clear
    description of each key column and its purpose, and (2) a list of any
    missing or inconsistent data points that could affect accuracy.
    Present your findings in a concise, structured format in a new sheet.
    ```

    ![](./media/m9.png)

10. Review the output:
   
    ![](./media/m10.png)
    
## Exercise 2: Use Copilot in Teams to Summarize Meeting Notes

In your role as a Financial Analyst for Zava Retail, you joined a
meeting with Robin Kline, Zava Retail's Finance Manager, and other
Finance department members including Amari Rivera, Quincy Brooks, Miguel
Reyes, and Eric Solomon. You didn't have time to take detailed notes, so
you turned to Copilot for help.

### Task 1: Summarize Meeting Notes

1.  Navigate to +++https://m365.cloud.microsoft+++, select **App Launcher** in the navigation pane.
   
    ![](./media/kk1.png)

2.  Select **Teams**.  
      
   ![](./media/kk2.png)
  
3.  From left navigation list select Copilot to open the Copilot Chat in Teams.
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%207/media/image8.png)

4.  In the Copilot description box, paste the following prompt and
    select the **Send** button.  

    ```
    Generate a downloadable summary. Review the summary to ensure it
    includes decisions, next steps, and responsibilities. Ask Copilot to
    generate a downloadable file for distribution to the meeting
    participants. Download the document that Copilot generated
    ```

    ![](./media/m13.png)

5.  Review the output:  
      
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%207/media/image10.png)

### Task 2: Creating a Task List

After reviewing the next steps in the report summary, ask Copilot to
generate a detailed task list for each participant based on the action
items in the notes.

1.  To generate a task list, paste the below prompt in the description
    box and select **Send** icon.  

    ```
    Based on the action items and next steps in the meeting summary,
    create a detailed task list for each participant. Assign
    responsibilities clearly and include suggested deadlines or priority
    levels for each task, such as high, medium, or low priority where
    appropriate
    ```
    
    ![](./media/m14.png)

2.  Review the output:  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%207/media/image12.png)
    
    > Note: Generated outputs are non-deterministic and may vary across users, sessions, and environments.

### Task 3: Generate a Calendar Invite

In follow-up to the timeline, ask Copilot to draft a calendar invite for
the team to reconvene.

1.  To generate a calendar, paste the below prompt in the description
    box and select the **Send** icon.  

    ```
    Draft a follow-up email to the team summarizing the meeting
    outcomes and including the assigned task list with responsibilities,
    deadlines, and priority levels for each participant.
    ```
    
    ![](./media/m15.png)
    
2.  Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%207/media/image14.png)
    >Note: Generated outputs are non-deterministic and may vary across users, sessions, and environments.

## Exercise 3: Use Copilot Chat to Analyze a Potential Acquisition

Zava Retail's executive team is evaluating the potential acquisition of
Relecloud, Ltd. Robin Kline, Zava Retail's Finance Manager, sent you a
detailed business perspective for Relecloud that provides an overview of
the company's market position, financial performance, customer and sales
insights, operations and capabilities, intellectual property, product
roadmap, risks and challenges, and future outlook.

This task demonstrates how Copilot Chat can extract, categorize, and
structure complex financial information into actionable summaries — and
how detailed prompts consistently produce more satisfactory results than
high-level, vague ones.

### Task 1: Create a business perspective summary 

1.  Navigate back to the Microsoft 365 Copilot home page and select
    **Work** mode.(Work mode ensures Copilot uses secure internal business context,
    while Web mode searches public external sources.)
    
    ![](./media/kk3.png)
2. Select the **+ icon** in the prompt field and then select **Upload images and files**.
   ![](./media/kk4.png)
3. Select **Relecloud Business Perspective.docx** file from **C:\Labfiles\Lab7-Lab files**.
   ![](./media/m18.png)
4. Paste the following prompt in the prompt field and selec **Send** button to execute the prompt.
    
    ```
    Review the attached Relecloud Business Perspective document and
    create a business perspective summary with the following three sections:
    (1) Relecloud’s financial data, (2) Operations analysis of Relecloud,
    and (3) Integration plan for the acquisition. Present the summary in a
    clear and structured executive format suitable for leadership review.
    ```
    
    ![](./media/kk5.png)

5.  Review the output:
   
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%207/media/image17.png)

### Task 2: Expand the Summary and generate a comprehensive report

After reviewing the initial summary, ask Copilot to generate a more
comprehensive version of the report with deeper analysis and visuals.  
  
1. In the Copilot prompt field, paste the following prompt and select
the **Send** button.

    ```
    Expand the previous Relecloud acquisition report and include all
    prior information, plus the following additional analysis:
  
    1.  Financial Analysis Section:
  
    - Valuation and deal structure, including valuation multiples and deal
      structure implications
  
    - Financial health and ratios, including liquidity, solvency,
      profitability trends, gross-to-net retention by cohort, regional ARR
      dynamics, and cash flow analysis
  
    - Revenue and customer concentration, including revenue breakdown,
      concentration risks by customer and sector, churn drivers, and
      retention trends
  
    - Include line or bar charts showing revenue, EBITDA, net income, gross
      margin, and operating margin trends over time
  
    2.  Operations Analysis Section:
  
    - Cost structure and efficiency, including COGS, OpEx, efficiency
      metrics, and scalability assessment
  
    - Competitive positioning, including SWOT analysis and peer
      benchmarking
  
    - Include a SWOT Matrix visual summarizing strengths, weaknesses,
      opportunities, and threats
  
    - Include a Scalability Assessment Diagram illustrating DevSecOps
      maturity, infrastructure readiness, and organizational scalability.
  
    3.  Integration Planning Section:
  
    - Synergy and integration modeling, including synergy realization
      opportunities, integration risks, and post-merger integration
      planning
  
    - Leadership and organizational review, including management track
      record and organizational structure assessment
  
    - Include an Integration Timeline (Gantt Chart) showing phases and
      milestones for post-merger integration
  
    - Format the report as a detailed executive acquisition analysis
      suitable for finance leadership decision-making
    ```
  
    ![](./media/m20.png)

2. Review the output:
   
  ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%207/media/image19.png)

## Summary

In this lab, you worked as a Financial Analyst at Zava Retail and used
Microsoft 365 Copilot across Excel, Teams, and Copilot Chat to support
major business initiatives. In Excel, you analyzed COGS data for the
Zava Home product line to identify cost drivers, outliers, and insights
for leadership review. In Teams, you summarized finance meeting notes,
generated participant-specific task lists, drafted follow-up
communications, and supported policy-related documentation. In Copilot
Chat, you developed a detailed acquisition analysis of Relecloud,
progressing from an initial summary to a comprehensive financial report
with visuals and integration planning.
