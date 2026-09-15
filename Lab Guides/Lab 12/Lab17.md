# Lab 17 - Build a Multi-Agent System for the Education Industry to Automate Student Services

## Scenario

Riverbend University, home to about 18,000 students, sees the same requests flood in every semester: fee balance checks to Student Services, exam timetable calls to the Examinations Office, and document questions to the Admissions inbox. Last semester the Student Services helpdesk logged over 6,400 tickets, and an audit found roughly 70% were repetitive, two-minute questions buried behind a multi-day queue.

The tipping point came when a first-year student, Aditi Sharma, had to email three separate departments and wait four business days for a bonafide certificate — nearly missing her visa appointment. Priya Nair, Riverbend's Director of IT Services, took the incident to the digital transformation steering committee, which approved a pilot: one AI assistant in Microsoft Teams that gives students instant, accurate answers without them ever needing to know which department or system holds the data — with one hard rule: no guessing. Fee, grade, and exam data must come straight from Dataverse, and admissions answers must come straight from the official prospectuses.

Priya has assigned you, a Power Platform developer on her team, to build and ship this pilot. In this lab, you'll build **Atlas**, the orchestrator agent students talk to, and connect it to three specialist child agents — **Student Services**, **Academic**, and **Admissions** — each wired to exactly the data, knowledge, and skills it needs. By the end, you'll publish Atlas to Teams and Microsoft 365 Copilot and prove a request like Aditi's can be resolved in one conversation, not four business days.

## Lab Objective

By the end of this lab, you will be able to:
- Provision and populate Microsoft Dataverse tables from source data to
  serve as the system of record for student, academic, and financial data.

- Build an orchestrator agent in Copilot Studio that interprets a
  student's intent and routes it to the correct specialist agent.

- Build a child agent that uses the **Model Context Protocol (MCP)** to
  securely read and write live Dataverse records.

- Build a child agent that combines **MCP tools**, **grounded knowledge
  sources**, and **custom skills** to handle multi-faceted academic requests.

- Build a child agent that relies purely on **knowledge sources** and
  **skills** to answer admissions questions without live data access.

- Connect all specialist agents to the orchestrator and validate
  end-to-end multi-agent routing.

- Publish the orchestrator agent to Microsoft Teams and Microsoft 365
  Copilot and validate the experience from a student's point of view.


## Exercise 0: Provision the Dataverse Data Foundation

This exercise establishes the system of record that every agent in this lab will read from and write to. You will create six Dataverse tables and populate one of them from a sample CSV file to confirm the import pattern works. This foundation must be in place before any agent can retrieve real student, academic, or financial data.

### Task 1: Import Source Data into Dataverse Tables

1. Open a web browser and navigate to +++https://make.powerapps.com+++.

1. Log in using the following credentials:

    - Username - +++@lab.CloudPortalCredential(User1).Username+++
    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++

    ![A screenshot of a computer screen AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image1.png)

    ![A screenshot of a login box AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image2.png)

    ![A screenshot of a computer error AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image3.png)

    ![A person holding a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image4.png)


1. From the left-navigation menu, select **Tables-\>+ New table-\>Create new tables**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image5.png)

1. Select **Import an Excel file or .CSV**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image6.png)

1. Select from device C:\Labfiles\CampusTablesfiles.

    ![A screenshot of a file AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image7.png)

1. Select the **BookCatalog.csv** file and choose **Open**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image8.png)

1. Select **Import**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image9.png)

1. Once the import completes, select **Save and exit(twice).**

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image10.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image11.png)

1. Open the newly created table and confirm the imported rows match the source CSV file.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image12.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image13.png)

1. Repeat the same table-creation pattern to add the following tables, which the agents in later exercises will depend on:

    - Exam Timetable Entry
    - Fee Record
    - Grade Card
    - Student
    - Student Request

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image14.png)


## Exercise 1: Build Atlas, the Orchestrator Agent

Atlas is the single front door for every student interaction — the agent students actually talk to. In this exercise you will create Atlas, give it routing instructions for three future specialist agents, ground it in general university documents, and confirm it responds sensibly before any child agents exist.

### Task 1: Create and Configure the Atlas Agent

1. Open a browser and navigate to Copilot Studio using the url +++https://copilotstudio.preview.microsoft.com/+++ and login using the following credentials:

    - Username - +++@lab.CloudPortalCredential(User1).Username+++
    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++

    ![A screenshot of a computer screen AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image15.png)

    ![A screenshot of a login screen AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image16.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image17.png)


1. From the left navigation, select **Agents**.

    ![A screenshot of a phone AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image18.png)

1. Select **New Agent**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image19.png)

1. Enter the name of the agent as +++Atlas+++

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image20.png)

1. Enter the following instructions in the instruction field:

    +++You are Atlas, the university's intelligent student support assistant. Your responsibilities: - Welcome students and answer general university-related questions whenever possible. - Route fee, certificate, enrolment, and other student service requests to the Student Services Agent. - Route academic queries such as grades, GPA, timetables, attendance, and course information to the Academic Agent. - Route admission-related queries, including program information, eligibility, application requirements, and admission processes, to the Admissions Inquiry Agent. - Coordinate responses across multiple connected agents when a student's request involves more than one area. Guidelines: - Be friendly, concise, and professional in every response. - Use connected agents whenever a request requires specialized knowledge or access to university data. - Do not answer on behalf of a specialist agent when the request should be delegated. - If a request contains multiple questions, determine which connected agents are needed and combine their responses into a single, clear answer. - Do not make up information. Use connected agents and available knowledge sources to provide accurate responses. - If you cannot find sufficient information, politely inform the student and recommend contacting the university helpdesk.+++

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image21.png)


### Task 2: Ground Atlas in General University Knowledge

1. From the right panel, under Knowledge, remove the **Search all websites** option, so Atlas answers only from trusted sources..

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image22.png)

1. Select the **Knowledge** tab to add a knowledge source.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image23.png)

1. Select **Drag and drop or click to upload**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image24.png)

1. Upload files. Browse for the following files from C:/Labfiles/CampusFiles:

    - Campus_faq.pdf
    - Student_handbook.pdf

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image25.png)


1. Select **Add to agent** to attach both files as grounding sources.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image26.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image27.png)

1. Select **Publish** to publish the agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image28.png)


### Task 3: Test Atlas in the Preview Pane

1. Select the **Preview** tab at the top of the screen.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image29.png)

1. Enter the following prompt and select **Send**:

    +++Hi Atlas! Can you introduce yourself and explain how you can help
    me?+++

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image30.png)

1. Review Atlas's response and confirm it introduces itself, describes its role, and references the categories of help it can provide.
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image31.png)


## Exercise 2: Build the Student Services Agent with Live Dataverse Access

Student Services requests — fee balances, certificates, enrolment status — require real-time, per-student data rather than static documents. In this exercise you will build a child agent that connects to Dataverse through an MCP server, giving it the ability to securely read and write live student records on Atlas's behalf.

### Task 1: Create and Configure the Student Services Agent

1. Expand the left navigation menu and select **Agents**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image32.png)

1. Select **New Agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image33.png)

1. Enter agent name as +++Student Services Agent+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image34.png)

1. Enter instructions in the +++Intrusions+++ field:

    ```

    You are the Student Services Agent for Riverbend University.

    Your primary responsibility is to assist students with administrative
    and student service requests by securely interacting with university
    data stored in Dataverse.

    Responsibilities:

    Help students with questions related to tuition fees, enrollment
    records, certificate requests, and other student services.

    Retrieve student information using the available Dataverse MCP tools.

    Create or update student service records in Dataverse when requested,
    such as submitting or updating certificate requests.

    Clearly explain the information returned or updated through the MCP
    tools in a student-friendly manner.

    Guidelines:

    Respond in a friendly, professional, and concise manner.

    Before retrieving or updating any student-specific information, ask the
    student to provide their Student ID if it has not already been provided.

    Use the appropriate Dataverse MCP tool to retrieve, create, or update
    records based on the student's request.

    Confirm the details with the student before performing any update that
    modifies university records.

    If the Student ID is invalid or no matching record is found, politely
    ask the student to verify the Student ID.

    Never guess, assume, create, or modify student information without using
    the available MCP tools.

    If a request cannot be completed using the available tools, politely
    inform the student and recommend contacting the Student Services Office
    for further assistance.​‌

    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image35.png)

1. From the right panel, under Knowledge, remove the **Search all websites** toggle to prevent this agent from answering from public web content.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image36.png)


### Task 2: Connect the Agent to the Dataverse MCP Server

1. From the right panel, select **Tools**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image37.png)

1. Select the **Model Context Protocol(MCP)** filter

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image38.png)

1. Search for +++Dataverse+++ in the search bar and select **Microsoft Dataverse MCP** **Server**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image39.png)

1. Expand the connection drop-down and select **Create new connection**.

1. Select **Create** to authorize the connection.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image40.png)

1. Select **Add** to attach the MCP server as a tool for this agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image41.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image42.png)

1. Select **Publish**. Then select **Save and publish**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image43.png)


## Exercise 3: Build the Academic Agent with MCP, Knowledge, and Skills

Academic requests span two very different needs: live data (grades, exam timetables) and static policy (examination regulations). In this exercise you will build the most capable agent in the system — one that combines Dataverse access, a grounded knowledge source, and two purpose-built skills that route each request to the right retrieval method.

### Task 1: Create and Configure the Academic Agent

1. Expand the left navigation menu and select **Agents**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image44.png)

1. Select New agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image45.png)

1. Enter the name of the agent +++Academic Agent+++.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image46.png)

1. Enter the following instructions in the +++Instruction+++ field:

    +++You are the Academic specialist agent for Riverbend University. This agent is designed to work as a connected agent for Atlas. Atlas delegates academic requests to you whenever a student needs information about grades, GPA, exam schedules, examination regulations, or other academic records. Responsibilities • Retrieve GPA and grade card information. • Retrieve exam schedules. • Answer examination policy questions using the provided knowledge source. • Read academic records stored in Microsoft Dataverse. Guidelines • Assume Atlas has already determined that this request belongs to Academic Services. • Focus only on academic-related requests. • Use the Microsoft Dataverse MCP Server whenever academic information must be retrieved. • If the student has not provided a Student ID, politely ask for it. • Before retrieving any academic record, verify that the Student ID exists in the Student table. • Retrieve academic information from these Dataverse tables when appropriate: - Student - Grade Card - Exam Schedule • Use the Exam Regulations knowledge source whenever the student asks about: - Examination rules - Attendance requirements - Passing criteria - Re-evaluation - Supplementary examinations - Academic regulations • Use the Academic Advisor skill for requests involving: - GPA - Grades - Academic performance - Semester results - Subject scores • Use the Exam Planner skill for requests involving: - Exam timetable - Exam dates - Exam locations - Upcoming examinations - Examination schedule • Never guess grades, GPA, exam schedules, or academic policies. • Return concise, structured responses suitable for Atlas to present to students. • If information cannot be found, clearly explain the reason instead of generating an answer.+++

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image47.png)

1. Remove the **Search all websites** option from the Knowledge Pane.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image48.png)

1. Select **Knowledge**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image49.png)

1. Select **Drag and drop or Click to upload** button to add a knowledge source.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image50.png)

1. Select **exame_regulation.pdf**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image51.png)

1. Select **Add to agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image52.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image53.png)

1. Select **Tools**.
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image54.png)

1. Select **Model Context Protocol(MCP)** -\>Enter +++Dataverse+++ in the search bar-\>Select **Microsoft Dataverse MCP Server**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image55.png)

1. Select **Add**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image56.png)


### Task 2: Add the Academic Advisor and Exam Planner Skills

1. Select **Skills** to add skills to the agent.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image57.png)

1. Select the **Create from blank** tab.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image58.png)

1. Create the **Academic Advisor** skill with the following values:

    - Name: +++academic-advisor+++
    - Description:

        `Use this skill whenever a student asks about GPA, grades, academic performance, semester results, or subject marks.`

    - Instructions:
    +++You help students understand their academic performance. Use this skill only when the student asks about: - Current GPA - Grade Card - Semester Results - Subject Grades - Academic Performance - CGPA - Percentage - Failed or Passed subjects Procedure 1. Verify that a Student ID has been provided. 2. If no Student ID is available, politely ask for it. 3. Use the Dataverse MCP Server to verify the Student ID exists in the Student table. 4. Retrieve the student's academic records from the Grade Card table. 5. Summarize: - GPA - Semester - Subject grades - Overall academic standing 6. If no record exists, clearly explain that no academic record was found. 7. Never invent grades or GPA. 8. Keep the response concise and student friendly.+++ Select **Create.**

    ![A screenshot of a computer screen AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image59.png)


1. Again, select **Tools** from the menu to create an Exam Planner skill. So enter the following values in **Create from blank** tab:

    - Name: +++Exam Planner+++
    - Description:

        `Use this skill whenever a student asks about exam dates, examination timetable, examination venue, or upcoming examinations.`

    - Instructions:
    +++You help students find examination schedules and understand examination requirements. Use this skill only when the student asks about: - Exam timetable - Exam dates - Upcoming examinations - Examination schedule - Exam venue - Exam room - Next exam Procedure 1. Verify that a Student ID has been provided. 2. If no Student ID is available, politely ask for it. 3. Verify the Student ID using the Student table. 4. Retrieve examination information from the Exam Schedule table. 5. Present: - Subject - Exam Date - Time - Venue 6. If the student asks about examination rules, attendance requirements, passing criteria, re-evaluation, or supplementary exams, answer using the Exam Regulations knowledge source. 7. Never invent examination dates or policies. 8. Clearly explain if no timetable is available.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image60.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image61.png)


1. Select **Publish** to publish the agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image62.png)

1. Select **Save and Publish**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image63.png)


## Exercise 4: Build the Admissions Agent with Knowledge and Skills

Unlike the previous two agents, Admissions never needs to touch live student records — every answer it gives comes from published prospectuses and FAQs. In this exercise you will build a knowledge-and-skills-only agent, showing that not every specialist in a multi-agent system needs live data access to be useful.

### Task 1: Create and Configure the Admissions Agent

1. Expand the left navigation menu and select **Agents**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image64.png)

1. Select **New agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image65.png)

1. Enter the name of the agent +++Admissions Agent+++.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image66.png)

1. Enter the following instructions in the +++Instructions+++ field:

    +++You are the Admissions specialist agent for Riverbend University. This agent works as a connected agent for Atlas. Atlas delegates admission-related questions whenever a prospective student needs guidance about admissions, eligibility, scholarships, application procedures, or required documents. Responsibilities • Answer admission-related questions using the provided knowledge sources. • Explain admission eligibility requirements. • Explain required documents for admission. • Explain the admission application process. • Answer scholarship-related questions. • Explain international admission requirements. • Provide application deadlines when available. Guidelines • Assume Atlas has already determined this request belongs to Admissions. • Focus only on admission-related questions. • Always answer using the provided knowledge sources. • Never invent admission policies, eligibility criteria, deadlines, or scholarship information. • If multiple programs have different requirements, clearly explain the differences. • If the requested information is unavailable, recommend contacting the Admissions Office. • Return concise and structured responses so Atlas can present the final answer.+++

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image67.png)

1. Remove the **Search All website** option from the Knowledge pane.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image68.png)

1. Select **Knowledge** to add a knowledge source.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image69.png)

1. Add the following PDF files from C:\Labfiles\CampusFiles:

    - Postgraduate_prospectus.pdf
    - Undergraduate_prospectus.pdf
    - Admission_faq.pdf

    Select **Add to agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image70.png)


1. Select **Skills** to add new skills to the agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image71.png)

1. Select **Create from blank** tab. Then enter the following values:

    - Name: +++admissions-advisor+++
    - Description: +++Use when a prospective student asks about admission
    eligibility, application procedures, required documents, admission deadlines, or international admissions.+++

    - Instruction:
    +++You help prospective students understand Riverbend University's admission process. When to use this skill - Admission eligibility - Required documents - Application process - Admission deadlines - International admissions - Program requirements - Minimum qualifications Procedure 1. Identify what program or course the student is asking about. 2. Use the available knowledge sources to locate the relevant admission requirements. 3. Explain the eligibility criteria clearly. 4. List the required documents. 5. Explain the application process step by step. 6. Mention any important deadlines if available. 7. If information is unavailable, recommend contacting the Admissions Office. Guardrails - Never invent eligibility rules. - Never invent deadlines. - Never guess document requirements. - Always answer from the knowledge sources.+++

    Select **Create**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image72.png)


1. Select Skill again to add one more skill.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image73.png)

1. Select **Create from blank** tab. Then enter the following values:

    - Name: +++scholarship-advisor+++
    - Description: +++Use when a student asks about scholarships, financial
    aid, tuition assistance, fee waivers, or scholarship eligibility.+++

    - Instruction:
    +++You help prospective students understand scholarships offered by Riverbend University. When to use this skill - Merit scholarships - Sports scholarships - Financial aid - Need-based scholarships - Scholarship eligibility - Scholarship renewal - Scholarship deadlines Procedure 1. Determine what scholarship information the student needs. 2. Search the scholarship handbook. 3. Explain the eligibility criteria. 4. Explain the application process. 5. Mention important deadlines if available. 6. Explain renewal conditions when applicable. Guardrails - Never invent scholarship policies. - Never promise scholarship approval. - Always answer using the scholarship handbook.+++

    Select **Create**.

    ![A screenshot of a computer screen AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image74.png)


1. Select **Publish**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image75.png)

1. Select **Save and publish**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image76.png)


## Exercise 5: Connect All Specialist Agents to Atlas

A specialist agent is only useful once Atlas knows it exists. In this exercise you will connect all three child agents to Atlas as connected agents, publish the updated orchestrator, and run three end-to-end tests to confirm each type of request is routed to the correct specialist and returns accurate, data-grounded answers.

### Task 1: Connect the Specialist Agents to Atlas

1. Expand the left navigation menu, select **Agents.**

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image77.png)

1. Select **Atlas** agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image78.png)

1. Select **Connect agents**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image79.png)

1. Select **Admissions Agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image80.png)

1. Enter the following description in the +++description+++ field and select **Connect**.

    +++Assists prospective and newly admitted students by answering questions about admissions, eligibility criteria, application requirements, required documents, important deadlines, scholarships, and university programs using trusted admissions knowledge sources and specialized guidance skills.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image81.png)

1. Once again, select **Connect agents**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image82.png)

1. Select **Academic Agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image83.png)

1. Enter the following description in the +++Description+++ field and select **Connect**.

    +++Provides academic support by answering questions about GPA, grade cards, exam timetables, and university academic regulations. Combines Microsoft Dataverse with academic knowledge sources and specialized skills to deliver accurate academic information.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image84.png)

1. Select **Connect agents**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image85.png)

1. Select **Student Services Agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image86.png)

1. Enter the following description in the +++Description+++ field and select **Connect**.

    +++Handles administrative student services, including fee balance enquiries, certificate requests, enrolment verification, and other student service requests. Retrieves and updates student information from Microsoft Dataverse and processes administrative requests on behalf of Atlas.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image87.png)

1. Select **Publish** to publish the agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image88.png)


### Task 2: Validate End-to-End Multi-Agent Routing

1. Select **Preview** from the top bar. Enter the following prompt to test how the Atlas agent invokes the Student Services Agent

    +++I want to check my fee balance. My Student ID is STU007.+++

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image89.png)

1. Review the output.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image90.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image91.png)

1. To verify the output returned by the Student Services Agent, open a new tab and navigate to +++https://make.powerapps.com+++.

1. Select Tables and open the **Fee Record** table.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image92.png)

1. You can see that the result return by the agent is same as the data enter in the table.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image93.png)

1. Select **New chat** to start a new conversation.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image94.png)

1. Enter the following prompt to test how the Atlas agent invokes the Academic Agent:

    `Show my latest grades. Student ID: STU007`

    Select the **Send** button to execute this prompt.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image95.png)

1. Review the response and confirm Atlas invoked the Academic Agent and returned grade data consistent with the Grade Card table.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image96.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image97.png)

1. Enter the following prompt to test how the Atlas agent invokes the Admissions Agent:

    +++What documents are required when applying for admission?+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image98.png)

1. Review the response and confirm Atlas invoked the Admissions Agent and answered using the admissions knowledge sources rather than inventing an answer.
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image99.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image100.png)


## Exercise 6: Publish Atlas to Microsoft Teams and Microsoft 365 Copilot

A working agent only creates value once students can actually reach it. In this final exercise you will publish Atlas as a channel in Microsoft Teams and Microsoft 365 Copilot, then run a real end-to-end test — submitting a certificate request as a student would — and confirm the request lands correctly in Dataverse.

### Task 1: Publish Atlas to Teams and Microsoft 365 Copilot

1. From the Atlas agent page, expand the **Publish** dropdown and select **Teams + Microsoft 365**..

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image101.png)

1. Choose **Make agent available in Microsoft 365 Copilot** option to turn on Microsoft 356. Select **Save and publish**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image102.png)

1. Select **See agent in Teams** to add Atlas agent in Teams.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image103.png)

1. Select **Add**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image104.png)

1. Select **Open**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image105.png)


### Task 2: Test the End-to-End Student Experience in Teams

1. In the Teams chat with Atlas, enter the following prompt::

    +++I need a bonafide certificate for my visa application.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image106.png)

1. When Atlas (via the Student Services Agent) asks for your Student ID, respond with:

    +++My Student ID is STU008.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image107.png)

1. When prompted for confirmation before the record is created, respond with: +++yes+++.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image108.png)

1. To verify the output returned by the Student Services Agent, open a new tab and navigate to +++https://make.powerapps.com+++.

1. Select Tables and open the **Student Request** table.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image109.png)

1. Confirm a new certificate request record now exists for **STU008**, matching what you submitted in Teams.:
  
    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2017/media/image110.png)


## Summary

In this lab, you built a complete multi-agent student support system for Riverbend University. You provisioned Dataverse as the shared data foundation, then built **Atlas**, the orchestrator agent that understands student intent and routes requests to three specialist agents — each demonstrating a different Copilot Studio integration pattern:
- **Student Services Agent** — securely reads and writes live
  operational data through an MCP server.

- **Academic Agent** — combines MCP tools, a grounded knowledge source,
  and task-specific skills to handle both live-data and policy questions.

- **Admissions Agent** — answers reliably using knowledge sources and
  skills alone, with no live data connection.


You connected all three specialists to Atlas, validated accurate routing end to end, and published Atlas to Microsoft Teams and Microsoft 365 Copilot — confirming a real student request can flow from a chat message all the way into a Dataverse record.

This pattern — one orchestrator plus specialized connected agents, each using only the tools it needs — is reusable for any department or industry that wants to automate service requests without sacrificing accuracy, security, or a single point of contact.




