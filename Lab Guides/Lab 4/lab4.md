# Lab 4 - Automate Zava Retail IT asset management with Microsoft 365 Copilot App Builder

**Estimated Duration:** 40 minutes

## Lab objectives 

In this lab, you will use App Builder inside Microsoft 365 Copilot to
create a fully functional business application — using nothing but
natural language. You will describe what you want, watch Copilot build
it in real time, refine it through conversation, and publish it for your
team. By the end of this lab, you will be able to:

- Access App Builder inside Microsoft 365 Copilot

- Describe a business app in natural language and have Copilot generate
  it

- Navigate the generated app — Dashboard, data views, and functional
  sections

- Refine and iterate the app through conversational prompts

- Publish the finished app and share it with your team

## Scenario

You are an IT Asset Manager at Zava Retail, a growing retail chain with
over 1,200 employees across 15 store locations and a central head
office.

Every quarter, your IT team manually tracks which store managers and
head office staff have been issued laptops, tablets, POS peripherals,
and accessories — using a shared spreadsheet that is constantly out of
date. Nobody knows at a glance:

- Which employees have outstanding equipment requests

- Which assets are assigned, returned, or pending collection

- Which requests are overdue and need chasing

The goal is to build a Zava Retail IT Asset Tracker app using App
Builder — a conversational, no-code tool inside the M365 Copilot. It
gives a live dashboard to manage asset assignments, track request
statuses, and flag overdue items within the IT team.


## Exercise 1: Access App Builder and Describe Your App

App Builder works like a conversation. You describe the app you need in
plain language — the same way you would brief a colleague — and Copilot
builds it. The more specific your description, the more accurate the
first version will be.

### Task 1: Access App Builder

1.  In your browser, navigate to +++https://m365.cloud.microsoft/+++
    Sign in with your credentials.
    
    - Username - +++@lab.CloudPortalCredential(User1).Username+++
    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%204/media/image100.png)
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%204/media/image101.png)
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%204/media/image102.png)
    ![](./media/bb1.png)

2.  On the left-hand navigation pane, click **More agents\>App Builder
    (Frontier)**.
    
    ![](./media/bb2.png)

3.  Select **Add** to add this agent to your environment.  
    ![](./media/bb3.png)

4.  The App Builder interface will open with a conversational input
    field — this is where you describe your app.
    ![](./media/bb4.png)

### Task 2: Describe Your App in Natural Language

1.  In the App Builder input field, paste the following prompt and click
    on **Send** button.
    
    ```
    Build me an IT asset tracking app for Zava Retail. The app should
    let the IT team log equipment assigned to store managers and head office
    employees — including laptops, tablets, POS peripherals, and
    accessories. It should track each item's status as Assigned, Pending
    Collection, or Returned. I need a dashboard that shows total assets, how
    many are currently assigned, how many are pending, and overall
    completion rate. I also need a way to view all employees, manage tasks
    related to asset setup, and a section for IT resources and policies.
    ```
    
    ![](./media/bb5.png)
  
2.  Once generation is complete, a live preview of your app will appear
    on the right side of the screen — with a navigation panel showing
    sections such as Dashboard, Employees, Tasks, Resources, and
    potential Feedback.

    ![](./media/p5.png)
    
3.  On the left side, Copilot will summarize what it built and may
    suggest enhancements. Read through its summary before proceeding.

    ![](./media/p6.png)

## Exercise 2: Refine the App Through Conversation

### Task 1: Add Overdue Flagging to the Dashboard

1.  The generated app likely shows asset counts but may not flag overdue
    items prominently. This is the most operationally critical feature
    for the IT team.

2.  In the App Builder conversation input on the left, paste the below
    prompt and click on the **Send** button.

    ```
    Add a section to the dashboard that highlights overdue asset requests
    — items that have been in Pending Collection status for more than 7
    days. Show the employee's name, asset type, and how many days are
    overdue. 
    ```
    
    ![](./media/p7.png)

3.  Confirm the dashboard now includes an overdue section with the
    fields you specified.  
    ![](./media/p8.png)
    
### Task 2: Add Task Priority Indicators

1.  In the conversation input, paste the following prompt and click on
    **Send** button.

    ```
    In the Tasks section, add priority indicators — High, Medium, and
    Low — for each task. Also add a Due This Week view that filters to show
    only tasks due within the next 7 days
    ```

    ![](./media/p9.png)

2.  Once the response is generated, review the updated Tasks section in
    the preview.

3.  Click into the **Tasks** section and confirm:

    - Priority labels are visible on each task

    - A Due This Week filter or view is available

    ![](./media/p10.png)

### Task 3: Enhance the Employee Section

The IT team needs to see not just a list of employees, but a clear
record of what each person has been issued and whether their setup is
complete.

1.  In the conversation input, paste the following prompt and click on
    **Send** button.

    ```
    In the Employees section, add a column showing each employee's asset
    setup status — either Complete or In Progress. Also add a filter so the
    IT team can view only employees with In Progress status who may need
    follow-up.
    ```

    ![](./media/p11.png)

2.  Review the updated **Employees** section.  
    ![](./media/p12.png)

## Exercise 4: Test the App as a Real IT Team Member Would

### Task 1: Log a New Asset Assignment

1.  In the app preview, navigate to the Asset section.  
    ![](./media/p13.png)

2.  To add a new asset record, paste the following details in respective
    fields.

    - Model: +++**Macbook Air**+++

    - Serial Number: +++**AB568J**+++

    - Type: Select **Laptop**

    - Status: Select **Pending Collection**

    >[!Note] This asset is yet to be assigned.

    ![](./media/p14.png)

3.  Save the record.  
    ![](./media/p15.png)
    
### Task 2: Complete a Task and Check Progress

1.  Navigate to the **Tasks** section.

    ![](./media/p16.png)

2.  Find a task related to Provision new laptop for store manager. Select the checkbox to mark it as
    completed.
    
    ![](./media/p17.png)
    ![](./media/p18.png)
    
3.  Return to the Dashboard and review that the overall completion percentage changes accordingly.

    ![](./media/p19.png)

## Exercise 5: Publish the App and Share It with Your Team

### Task 1: Publish the App

1.  In App Builder, click the **Publish** button in the top-right corner
    of the screen.

2.  Click **Publish**.

    ![](./media/p20.png)

3.  Once published, App Builder will generate a direct link to your app. Select **Share ->Copy link** to
    copy this link.
    
    ![](./media/p21.png)
4. Select **Copy** to copy the link.
   ![](./media/p22.png)
    >[!Note] Save the link in your notes. It will be used in the upcoming task.

### Task 2: Validate the Published App

1.  Open a new browser tab and paste the direct link you have copied in
    Task 1 of the same exercise.
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%204/media/image22.png)

2.  Review that the app loads correctly with:

    - The correct app name and dashboard visible

    - Navigation sections (Employees, Tasks, Resources) accessible

    - The overdue items section present on the dashboard

    ![](./media/p23.png)

### Task 3: Share and Brief Your Team

1.  Return to App Builder. In the conversation input, paste the
    following prompt and click on **Send** button.

    ```
    Draft a brief message I can send to the Zava Retail IT team
    explaining what this app does, how to log a new asset assignment, and
    how to check overdue items. 
    ```
    
   ![](./media/p24.png)

2.  Copilot will generate a ready-to-send team briefing. Review the
    briefing and note any required edits.
    
    ![](./media/p25.png)
    ![](./media/p27.png)
    
3.  Copy the briefing and the direct app link — these are what you would
    share with the IT team in a real deployment.
    ![](./media/p26.png)

## Summary

You have completed this lab if you were able to access App Builder
inside Microsoft 365 Copilot and use natural language to describe the
Zava Retail IT Asset Tracker, resulting in a functional generated app.
Completion also includes navigating through all sections of the
generated app and verifying functionality using an evaluation checklist,
refining the app with at least three targeted conversational prompts,
and testing it end-to-end through a realistic IT scenario that includes
overdue flagging and task completion. In addition, you should have
published the app to a specific group, validated the live published
experience, and generated a team briefing using App Builder’s
conversational interface.
