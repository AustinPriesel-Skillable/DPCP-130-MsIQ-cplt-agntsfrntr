# Lab 12 - Build a Multi-agent Campus Assistant for the Education industry with Copilot Studio

## Scenario

Riverbend University, home to about 18,000 students, sees the same requests flood in every semester: fee balance checks to Student Services, exam timetable calls to the Examinations Office, and document questions to the Admissions inbox. Last semester the Student Services helpdesk logged over 6,400 tickets, and an audit found roughly 70% were repetitive, two-minute questions buried behind a multi-day queue.

The tipping point came when a first-year student, Aditi Sharma, had to email three separate departments and wait four business days for a bonafide certificate — nearly missing her visa appointment. Priya Nair, Riverbend's Director of IT Services, took the incident to the digital transformation steering committee, which approved a pilot: one AI assistant in Microsoft Teams that gives students instant, accurate answers without them ever needing to know which department or system holds the data — with one hard rule: no guessing. Fee, grade, and exam data must come straight from Dataverse, and admissions answers must come straight from the official prospectuses.

Priya has assigned you, a Power Platform developer on her team, to build and ship this pilot. In this lab, you'll build **Atlas**, the orchestrator agent students talk to using Github Copilot Harness, and connect it to a **Campus Services Agent** that uses MCP to work with Dataverse data. You'll also add academic and admissions capabilities using **grounded knowledge and custom skills**, and create a workflow that sends bonafide certificate requests to a university staff member for approval. By the end, you'll publish Atlas to Teams and Microsoft 365 Copilot and validate the student experience from request to approval.

## Lab Objective

By the end of this lab, you will be able to:

- Provision and populate **Microsoft Dataverse** tables to provide a shared data foundation for student and university information.

- Build an **orchestrator agent in Copilot Studio** that understands student requests and routes them to the appropriate campus service capabilities.

- Build a **Campus Services Agent** that uses the **Model Context Protocol (MCP)** to securely access and manage live Dataverse records.

- Enhance the solution with **grounded knowledge sources and custom skills** to handle academic and admissions-related student requests.

- Create a **workflow with human approval** to process bonafide certificate requests and notify the appropriate university staff member.

- Connect the agents and workflow to the **Atlas orchestrator** and validate the end-to-end student experience.

- Publish the solution to **Microsoft Teams and Microsoft 365 Copilot** and test it from a student's perspective.


## Exercise 0: Provision the Dataverse Data Foundation

This exercise establishes the system of record that every agent in this
lab will read from and write to. You will create six Dataverse tables
and populate one of them from a sample CSV file to confirm the import
pattern works. This foundation must be in place before any agent can
retrieve real student, academic, or financial data.

### Task 1: Import Source Data into Dataverse Tables

1.  Open a web browser and navigate to +++https://make.powerapps.com+++.

2.  Log in using the following credentials:

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image1.png)![A screenshot of a login box
AI-generated content may be incorrect.](./media/image2.png)![A
screenshot of a computer error AI-generated content may be
incorrect.](./media/image3.png)![A person holding a computer
AI-generated content may be incorrect.](./media/image4.png)

3.  From the left-navigation menu, select **Tables-\>+ New
    table-\>Create new tables**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image5.png)

4.  Select **Import an Excel file or .CSV**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image6.png)

5.  Select from device.

    ![A screenshot of a file AI-generated content may be
    incorrect.](./media/image7.png)

6.  Select the **BookCatalog.csv** file from C:\LabFiles and choose
    **Open**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image8.png)

7.  Select **Import**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image9.png)

8.  Once the import completes, select **Save and exit(twice).**

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image10.png)
    
    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image11.png)

9.  Open the newly created table and confirm the imported rows match the
    source CSV file.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image12.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image13.png)

10. Repeat the same table-creation pattern to add the following tables
    from C:\LabFiles, which the agents in later exercises will depend
    on:

    - Exam Timetable Entry

    - Fee Record

    - Grade Card

    - Student

    - Certificate Request

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image14.png)

## Exercise 1: Build Atlas, the Orchestrator Agent

Atlas is the single front door for every student interaction — the agent
students actually talk to. In this exercise, you will create Atlas, give
it routing instructions for three future specialist agents, ground it in
general university documents, and confirm it responds sensibly before
any child agents exist.

### Task 1: Create and Configure the Atlas Agent

1.  Open a browser and navigate to Copilot Studio  
    +++https://copilotstudio.microsoft.com/+++ and log in using the
    following credentials:

    ![A screenshot of a computer screen AI-generated content may be
    incorrect.](./media/image15.png)
    
    ![A screenshot of a login screen
    AI-generated content may be incorrect.](./media/image16.png)
    
    ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image17.png)

2.  From the home page, select **Agent** to create a new agent.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image18.png)

3.  Enter the name of the agent as +++Atlas+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image19.png)

4.  Enter the following instructions in the instruction field:

    ```

    You are Atlas, the university's intelligent student support assistant.

    Your responsibilities:

    - Welcome students and answer general university-related questions

    whenever possible, using your own knowledge sources.

    - Route any request involving fees, certificates, enrolment, grades,

    GPA, exam timetables, admissions, or eligibility to the Campus

    Services Agent.

    - Coordinate responses when a student's request involves both a

    general question and a specialist request — answer the general part

    yourself, delegate the specialist part, and combine both into a

    single clear reply.

    Guidelines:

    - Be friendly, concise, and professional in every response.

    - Do not answer on behalf of the Campus Services Agent when the

    request should be delegated.

    - Do not make up information. Use the connected agent and available

    knowledge sources to provide accurate responses.

    - If you cannot find sufficient information, politely inform the

    student and recommend contacting the university helpdesk.
    ```

    ![A screenshot
    of a computer AI-generated content may be
    incorrect.](./media/image20.png)

### Task 2: Ground Atlas in General University Knowledge

1.  From the right panel, under Knowledge, remove the **Search all
    websites** option, so Atlas answers only from trusted sources.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image21.png)

2.  Select the **Knowledge** tab to add a knowledge source.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image22.png)

3.  Select **Drag and drop or click to upload**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image23.png)

4.  Upload the following files from C:/Labfiles/CampusFiles:

    - Campus_faq.pdf

    - Student_handbook.pdf

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image24.png)

5.  Select **Add to agent** to attach both files as grounding sources.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image25.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image26.png)

6.  Select **Publish** to publish the agent.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image27.png)

### Task 3: Test Atlas in the Preview Pane

1.  Select the **Preview** tab at the top of the screen.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image28.png)

2.  Enter the following prompt and select **Send**:

    +++Hi Atlas! Can you introduce yourself and explain how you can help
    me?+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image29.png)

3.  Review Atlas's response and confirm it introduces itself, describes
    its role, and references the categories of help it can provide.
    
    ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image30.png)

## Exercise 2: Build the Campus Services Agent 

Student Services requests — fee balances, certificates, enrolment status
— require real-time, per-student data rather than static documents. In
this exercise you will build a child agent that connects to Dataverse
through an MCP server, giving it the ability to securely read and write
live student records on Atlas's behalf.

### Task 1: Create and Configure the Campus Services Agent

1.  Expand the left navigation menu and select **Agents**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image31.png)

2.  Select **New Agent**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image32.png)

3.  Enter agent name as +++Campus Services Agent+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image33.png)

4.  Enter instructions in the **Intrusions** field:

    ```

    You are the Campus Services Agent for Riverbend University.

    This agent works as a connected agent for Atlas. Atlas delegates to

    you whenever a student needs fee, certificate, enrolment, grade,

    GPA, exam timetable, or admissions information.

    Responsibilities

    - Fee balances, certificate requests, and enrolment status: retrieve

    and, when requested, create/update records using the Dataverse MCP

    tools (Fee Record, Student, Student Request tables).

    - Grades, GPA, and academic performance: use the Academic Advisor

    skill together with the Dataverse MCP tools (Grade Card table).

    - Exam timetable, exam dates, and venues: retrieve directly from the

    Exam Timetable Entry table using the Dataverse MCP tools.

    - Admissions questions (eligibility, required documents, application

    process, deadlines): use the Admissions Advisor skill together with

    the knowledge sources. Do not use MCP tools for these questions —

    Admissions has no live Dataverse data.

    Guidelines

    - Before retrieving or updating any student-specific information,

    ask the student for their Student ID if it has not already been

    provided.

    - Verify the Student ID exists in the Student table before returning

    any fee, grade, or exam data.

    - Confirm details with the student before performing any update that

    modifies university records (e.g. submitting a certificate request).

    - Never guess or invent fees, grades, exam schedules, or admissions

    policy. If information cannot be found, say so clearly and recommend

    contacting the relevant office.

    - Return concise, structured responses suitable for Atlas to present

    to students.​‌

    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image34.png)

5.  From the right panel, under Knowledge, remove the **Search all
    websites** toggle to prevent this agent from answering from public
    web content.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image35.png)

6.  Select **Knowledge → Drag and drop or click to upload**.

7.  Upload the following two files from C:\Labfiles\CampusFiles:

    - exame_regulation.pdf

    - Admission_faq.pdf

    Select **Add to agent**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image36.png)

### Task 2: Connect the Agent to the Dataverse MCP Server

1.  From the right panel, select **Tools**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image37.png)

2.  Select the **Model Context Protocol(MCP)** filter

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image38.png)

3.  Search for +++Dataverse+++ in the search bar and select **Microsoft
    Dataverse MCP** **Server**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image39.png)

8.  Expand the connection drop-down and select **Create new
    connection**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image40.png)

9.  Select **Create** to authorize the connection.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image41.png)

10. Select the current user account.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image42.png)

11. Select **Add** to attach the MCP server as a tool for this agent.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image43.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image44.png)

### Task 3: Add the Academic Advisor Skill (Live-Data Domain)

1.  Select **Skills**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image45.png)

2.  Select the **Create from blank** tab. Create the skill with the
    following values:

    - **Name:** +++academic-advisor+++

    - **Description:** +++Use this skill whenever a student asks about GPA,
    grades, academic performance, semester results, or subject marks.+++

    - **Instructions:**

    ```
    You help students understand their academic performance.

        Use this skill only when the student asks about:
        - Current GPA
        - Grade Card
        - Semester Results
        - Subject Grades
        - Academic Performance
        - CGPA / Percentage
        - Failed or Passed subjects

        Procedure
        1. Verify that a Student ID has been provided; if not, ask for it.
        2. Use the Dataverse MCP Server to verify the Student ID exists in
            the Student table.
        3. Retrieve the student's academic records from the Grade Card table.
        4. Summarize GPA, semester, subject grades, and overall standing.
        5. If no record exists, clearly explain that no academic record was
            found.
        6. Never invent grades or GPA. Keep the response concise and
            student-friendly.

    ```

    ![A screenshot of a computer screen AI-generated content may be
    incorrect.](./media/image46.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image47.png)

### Task 4: Add the Admissions Advisor Skill (Knowledge-Only Domain)

1.  Select **Skills** again.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image48.png)

2.  Select the **Create from blank** tab. Then create the skill with the
    following values:

    - **Name:** admissions-advisor

    - **Description:** Use when a prospective student asks about admission
    eligibility, application procedures, required documents, or admission
    deadlines.

    - **Instructions:**

    ```
    You help prospective students understand Riverbend University's
        admission process.

        Use this skill only when the student asks about:
        - Admission eligibility
        - Required documents
        - Application process
        - Admission deadlines
        - Program requirements

        Procedure
        1. Identify what program or course the student is asking about.
        2. Use the knowledge sources to locate the relevant admission
            requirements.
        3. Explain the eligibility criteria clearly.
        4. List the required documents.
        5. Explain the application process step by step.
        6. Mention deadlines if available.
        7. If information is unavailable, recommend contacting the
            Admissions Office.

        Guardrails
        - Never invent eligibility rules, deadlines, or document
        requirements.
        - Always answer from the knowledge sources.

    ```

    Select **Create**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image49.png)

3.  Select **Publish**, then **Save and Publish**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image50.png)

## Exercise 3: Connect Campus Services Agent to Atlas

### Task 1: Connect the Specialist Agent to Atlas

1.  Expand the left navigation menu, select **Agents.**

2.  Select **Atlas** agent.

3.  Select **Connected agents**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image51.png)

4.  Select **Campus Services Agent**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image52.png)

5.  Enter the following description in the **description** field and
    select **Connect**.

    ```
    Handles fee balances, certificate requests, enrolment verification,
    grades, GPA, exam timetables, and admissions questions (eligibility,
    documents, application process, deadlines). Combines Microsoft
    Dataverse with knowledge sources and two specialized skills to
    deliver accurate, data-grounded answers on Atlas's behalf.
    ```
    Select **Connect**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image53.png)

6.  Now you can view your child agent in the Connect agent section.

7.  Select **Publish** to publish the agent.

### Task 2: Validate End-to-End Testing

1.  Select **Preview** from the top bar. Enter the following prompt to
    test how the Atlas agent invokes the Student Services Agent

    +++I want to check my fee balance. My Student ID is STU007.+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image54.png)

2.  Review the output.

    ![A screenshot of a chat AI-generated content may be
    incorrect.](./media/image55.png)

    ![](./media/image56.png)

3.  To verify the output returned by the Student Services Agent, open a
    new tab and navigate to +++https://make.powerapps.com+++.

4.  Select Tables and open the **Fee Record** table.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image57.png)

5.  You can see that the result return by the agent is same as the data
    enter in the table.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image58.png)

6.  Enter the following prompt and click the Send button.

    +++ Can you show me my grade card? Student ID STU003.+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image59.png)

7.  Review the output. This will invoke the academic-advisor skill.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image60.png)
    
    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image61.png)

## Exercise 4: Create a workflow 

A certificate request shouldn't go straight to Student Services without
the student confirming it first. In this exercise, you will build a
workflow that drafts a request email, sends it to the student for their
own review and approval, and only forwards it to Student Services once
they say yes — updating the request's status in Dataverse at each stage.

### Task 1: Create a workflow

1.  Expand the left navigation menu and select **Workflows**.

    ![](./media/image62.png)

2.  Select **New workflow**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image63.png)

3.  Name it +++Certificate Request Notification+++

4.  Click on Start trigger step, and select **When an agent calls the
    flow** as trigger type.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image64.png)

5.  Click +Add an input under the input section of the When an agent
    calls the Workflow trigger window.

    ![Screens screenshot of a chat AI-generated content may be
    incorrect.](./media/image65.png)

6.  Select **Text** as input type.

    ![](./media/image66.png)

7.  Enter +++StudentID+++ as a input.

    ![](./media/image67.png)

8.  Similarly, add the following inputs as a **Text** type:

    - +++StudentEmail+++

    - +++RequestPurpose+++

    ![](./media/image68.png)

9.  Select the + **sign** present on the right side of the trigger to
    add the next step.

    ![A screenshot of a chat AI-generated content may be
    incorrect.](./media/image69.png)

10. In the Add windows, search for +++Compose+++ and then select
    **Compose** action

    ![](./media/image70.png)

6.  Enter the following to draft the request email from the inputs:

    ```
    Dear Student Services Team,

    I would like to request a Bonafide certificate.

    Reason: {Reason}

    Student ID: {StudentID}

    Thank you.
    ```

    Here, {Reason} is entered as dynamic content, so click on the
    thunderbolt icon and then select **RequestPurpose** under When an
    agent calls the flow.

    ![](./media/image71.png)

    ![](./media/image72.png)

7.  Similarly, {StudentID} will enter as dynamic content, so click on
    the thunderbolt icon and then select Reason under

    ![](./media/image73.png)

    ![A screenshot of a chat AI-generated content may be
    incorrect.](./media/image74.png)

8.  Select the + **sign** present on the right side of the trigger to
    add the next step.

    ![](./media/image75.png)

9.  Search for +++Human review+++, and select **Request information**.

    ![A screenshot of a review AI-generated content may be
    incorrect.](./media/image76.png)

8.  Configure the action:

    - **Title:** +++Review your bonafied request before it's sent+++

    - **Message:** +++Please review the email below. You can edit the
    wording before it goes to Student Services.\n\n+++ Then insert the
    output of the **Compose** action by clicking on the Thunderbolt icon.

    - **Assigned to:** Enter the current username

    - **Channel:** Outlook

    ![](./media/image77.png)

    ![A screenshot of a computer AI-generated
    content may be
    incorrect.](./media/image78.png)

    ![](./media/image79.png)

9.  Select **Add an input → Yes/No** as input type, name it
    +++SendRequest+++, and label it +++Send this to Student Services?+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image80.png)

    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image81.png)

    ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image82.png)

10. Select the + **sign** present on the right side of the trigger to
    add the next step.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image83.png)

11. Select if/Else condition.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image84.png)

12. Enter the branch name as +++Yes branch+++.

13. Configure the condition:

    - **Condition:** Select **OR**

    - **Property:** Select Thundarbolt icon-\> **SendRequest** output
    **from** Request information

    - **Operator:** Select **Equals**

    - **Value:** Enter **+++** Yes+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image85.png)

    ![](./media/image86.png)

    ![](./media/image87.png)

    ![](./media/image88.png)

14. On the **Yes branch**, select its own **+** sign to add next step.

    ![](./media/image89.png)

15. Search for +++send email+++ and then select **Send an email** under
    Office 365 Outlook section

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image90.png)

16. Configure the email block:

    - Connection: Select **Create new connection** -\> Select **Create**.

    - To: Enter the current username.

    - Subject: Enter +++New certificate request — Action needed+++

    - Body: Enter
    ```
    A new certificate request has been submitted.

    Student ID: Select Thunderbolt icon-> When an agent calls the flow-> StudentID
    Student Email: Select Thunderbolt icon -> When an agent calls the flow-> StudentEmail
    Request: Select Thunderbolt icon -> When an agent calls the flow-> RequestPurpose

    Please process this request.

    ```

    ![](./media/image91.png)

17. After **Send an email**, still on the Yes branch, select **+** and
    add **Respond to the agent**.

    ![A screenshot of a chat AI-generated content may be
    incorrect.](./media/image92.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image93.png)

18. Select +Add an output. Then select Text.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image94.png)

    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image95.png)

19. Enter output as +++Status+++ = +++Sent+++.

    ![](./media/image96.png)

20. Again, select +Add an output. Then select **Text**.

    ![](./media/image97.png)

21. Enter output as +++ message+++ = +++Staff has been notified+++.

    ![](./media/image98.png)

22. On the **Else branch**, select its own separate **+** and add
    **Respond to the agent**.

    ![](./media/image99.png)

    ![](./media/image100.png)

23. Select +Add an output. Then select Text.

    ![](./media/image101.png)

    ![](./media/image102.png)

24. Enter output as +++ status+++ = +++ Cancelled+++.

    ![](./media/image103.png)

25. Again, select +Add an output. Then select **Text**.

    ![](./media/image104.png)

26. Enter output as +++ message+++ = +++ Request cancelled by
    student+++.

    ![](./media/image105.png)

27. The complete workflow will look like this.

    ![](./media/image106.png)

28. Select Publish to publish the workflow.

    ![](./media/image107.png)

### Task 2: Connect the Workflow to the agent

1.  Expand the left navigation menu, select **Agents**, and open
    **Campus Services Agent**.

    ![](./media/image108.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image109.png)

2.  Select **Tools → Add a tool**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image110.png)

3.  Select the **Workflows** filter and choose **Certificate Request
    Notification**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image111.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image112.png)

4.  Update the agent’s instructions; add the following set of
    instructions in the responsibilities section.

    ```

    Certificate requests:

    Collect Student ID, request type, and reason; verify the Student

    ID exists in the Student table using the Dataverse MCP tool, and

    retrieve the student's email.

    Create the Student Request record with Status = "Draft" using the

    Dataverse MCP tool.

    Call the Certificate Request Notification workflow tool, passing

    Student ID, Student Email, Request Type, and Reason. This sends

    the drafted request email to the student for their own review —

    it does not notify staff yet.

    Wait for the workflow's response (status, message).

    If status is "Sent": update the Student Request record to

    Status = "Sent to Student Services" using the Dataverse MCP tool,

    then tell the student their request has been sent to Student

    Services and will be processed shortly. Do not claim it has been

    read or acted on — only that it has been sent.

    If status is "Cancelled": update the Student Request record to

    Status = "Cancelled" using the Dataverse MCP tool, then tell the

    student their request was not sent and ask what they'd like to

    change before trying again.

    After calling the workflow, if status is "PendingStudentReview," tell
    the student: "I've sent a review email to your Outlook inbox — please
    check it and approve or decline the request. Once you respond, it will
    move forward automatically." End your turn there; do not wait for or ask
    about the outcome in this conversation

    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image113.png)

5.  Select Publish.

## Exercise 5: Publish Atlas to Microsoft Teams and Microsoft 365 Copilot

A working agent only creates value once students can actually reach it.
In this final exercise you will publish Atlas as a channel in Microsoft
Teams and Microsoft 365 Copilot, then run a real end-to-end test —
submitting a certificate request as a student would — and confirm the
request lands correctly in Dataverse.

### Task 1: Publish Atlas to Teams and Microsoft 365 Copilot

1.  From the Atlas agent page, expand the **Publish** dropdown and
    select **Teams + Microsoft 365**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image114.png)

2.  Select Save and Publish.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image115.png)

3.  Select **See agent in Teams** to add Atlas agent in Teams.

    ![](./media/image116.png)

4.  Select **Use this web app instead-\>** **Add**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image117.png)

    ![](./media/image118.png)

5.  Select **Open**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image119.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image120.png)

### Task 2: Test the End-to-End Student Experience in Teams

1.  In the Teams chat with Atlas, enter the following prompt and click
    send button:

    +++I need a bonafide certificate for my visa application. My Student ID is
    STU002.+++

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image121.png)

2.  Open a new tab in your web browser and navigate to
    +++https://outlook.cloud.microsoft/+++.

3.  There, you will receive an email to get approval from you for your
    application. So, select Yes and select submit.

    ![A screenshot of a computer screen AI-generated content may be
    incorrect.](./media/image122.png)

4.  An email will be sent to Student Service team for there approval.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image123.png)

    Note: Here we are using the same email address for both the student
    and Student Services role in this lab; that's why you'll see two
    emails. In a real deployment, these would be different mailboxes.

5.  Navigate back to Teams, and you will receive the confirmation.

    ![A screenshot of a computer screen AI-generated content may be
    incorrect.](./media/image124.png)

8.  To verify the output returned by the Campus Services Agent, open a
    new tab and navigate to +++https://make.powerapps.com+++.

9.  Select Tables and open the **Student Request** table.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image125.png)

10. Confirm a new certificate request record now exists for **STU002**,
    matching what you submitted in Teams. 

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image126.png)

## Summary

In this lab, you built a complete multi-agent student support solution for Riverbend University. You provisioned Dataverse as the shared data foundation, then built **Atlas**, the orchestrator agent that understands student intent and routes requests to the appropriate campus service capabilities.

The **Campus Services Agent** uses MCP to securely access and manage live Dataverse data, while academic and admissions capabilities use **grounded knowledge and custom skills** to handle student questions. You also created a **human approval workflow** that routes bonafide certificate requests to a university staff member for review and approval.

You connected these capabilities to Atlas, validated the end-to-end student experience, and published the solution to **Microsoft Teams and Microsoft 365 Copilot**. The resulting pattern provides students with a single conversational entry point while ensuring requests are handled using the appropriate data, knowledge, and approval processes.

