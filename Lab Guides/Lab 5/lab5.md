# Improve communication and work coordination across Zava Retail stores with a Frontline Agent

**Estimated Duration:** 40 minutes

## Lab objectives

In this lab, you will create a Frontline Operations Agent using
Microsoft 365 Copilot Agent Builder. The agent will help frontline
workers, store managers, and supervisors handle daily operations,
customer service, shift readiness, compliance, and escalation workflows.
You will configure agent instructions, upload enterprise knowledge
sources, test prompts, validate outputs, and optimize responses. After
completing this lab, you will be able to: 

- Create a Microsoft 365 Copilot custom agent

- Configure frontline retail agent instructions

- Upload knowledge sources for grounding

- Test store operations prompts

- Improve frontline productivity with AI

- Build reusable retail frontline agent templates

## Scenario

Zava Retail is a rapidly expanding multi-format retail chain operating:

- 250 stores across urban, suburban, and tier-2 markets

- 8,000 employees including cashiers, floor associates, warehouse staff,
  supervisors, and managers

- Presence across multiple regions, each with different staffing
  patterns and customer behavior

- Heavy seasonal demand spikes during festivals, clearance sales, school
  openings, and holiday promotions

- Thousands of frontline operational requests every week

Zava Retail has invested in Microsoft 365 and wants to modernize store
execution using a Microsoft 365 Copilot Frontline Agent.

**Key Challenges:**

- Managers spend too much time answering repetitive questions

- Store processes are inconsistent across locations

- Seasonal sales create staffing and service pressure

- New hire onboarding takes too much manual effort

- Operational issues are escalated at a slow pace

To solve these challenges, Zava Retail deploys a **Microsoft 365 Copilot
Frontline Agent** accessible in Copilot chat, Microsoft Teams, and
mobile devices for store workers. The agent becomes a 24x7 AI operations
Assistant for multiple retail stores. The Zava Frontline Agent will help
8,000 employees across 250 stores work more efficiently by giving
instant, consistent answers and reducing dependence on managers.

**Key Personas:**

**Patricia Gray – Operations Head**

The regional operations manager at Zava Retail oversees multiple stores
and ensures consistent execution across locations. The major challenges
include:

- Needs visibility into recurring issues across stores

- Tracks store performance and staffing gaps

- Requires faster escalation handling across regions

**Marie Brown – Store / Sales Associate**

The store associate at Zava Retail supports customers on the sales
floor, manages shelf availability, and assists with promotions. The
major challenges include:

- Needs quick answers on product locations and promotions

- Faces stock shortage questions from customers

- Requires guidance during peak store traffic

**David Turner – Cashier**

The cashier at Zava Retail handles billing transactions, customer
payments, and checkout queues. The major challenges include:

- Needs support resolving pricing or discount issues

- Manages long queues during rush hours

- Requires quick access to refund and return policies

**Fratini Greens – Store Manager**

The store manager at Zava Retail is responsible for store performance,
customer satisfaction, and team productivity. The major challenges
include:

- Receives repetitive operational questions from staff

- Needs visibility into daily store priorities

- Must balance staffing, sales, and service quality

## Exercise 1: Create the Frontline Agent

Patricia logs into Copilot to review Festive Campaign readiness.

1.  Navigate to +++<https://m365copilot.com/>+++ to open Microsoft 365
    copilot page. 

2.  Enter the **User ID** in the field and then click on
    the **Next** button to proceed. 

     ![](./media/image1.png)

3.  Enter **Password** in the field and then click on the **Sign
    in** button and click on the **Yes** to stay Signed in. 

    ![](./media/image2.png)

4.  Explore the Copilot chat environment.

    ![](./media/image3.png) 

5.  In the left **navigation pane**, look for **All Agents**.

    ![](./media/image4.png)


6.  Select **Create** to start building a new agent.

    ![](./media/image5.png)

7.  When the **Agent creation panel** opens, paste the following details
    in respective fields to build the agent.

    - **Name:** +++Frontline Operations Assistant+++

    - **Description:** +++Supports store staff, field workers, frontline
    teams with schedules, SOPs, customer help, daily operations.+++

    - **Instructions:** 
    ```
    You are a frontline operations assistant for
    employees.  
    Help workers with shift guidance, store procedures, customer service
    responses, escalation steps, daily checklists, safety reminders, and
    quick answers.  
    Keep responses concise and mobile-friendly.
    ```

    ![](./media/image6.png)

8.  Navigate to **Knowledge** section to add knowledge sources.
    Select **Upload from device**.

    ![](./media/image7.png)

9.  Select the below files from the Lab files and select **Open**.

    - SOP PDFs

    - Employee handbook

    - Store checklist

    - FAQ docs

    - Policy docs

    - Shift guides

    ![](./media/image8.png)

10. Verify that all the selected files are uploaded in the Knowledge
    sources.

    ![](./media/image9.png)

11. Click **Create** to publish the agent.

    **Note:** Wait for 5-10 minutes for the agent building process
    completion.

    ![](./media/image10.png)

    ![](./media/image11.png)

12. Once the agent is created successfully, click **Go to agent** to
    start using the agent.

     ![](./media/image12.png)

## Exercise 2: Access Frontline Operations Agent in Microsoft Teams

Patricia Gray (Regional operations manager) is seeking for an overview
of the operational activities and get the key operations related queries
of Zava Retail on Microsoft Teams for better visibility.

1.  Navigate to Microsoft Teams
    +++[https://teams.cloud.microsoft.com]+++(https://teams.cloud.microsoft.com+++/) and
    sign in with your credentials.

    ![](./media/image1.png)

    ![](./media/image2.png)

2.  Open Microsoft Teams. Select **Copilot** icon from the left
    navigation pane.

    ![](./media/image13.png)

3.  Go to **Expand Navigation** icon to open the menu.
    Select **Frontline Operations Agent** to open and access the agent.

    ![](./media/image14.png)

4.  Now, Patricia can use the agent directly inside Teams. **Frontline
    Operations Agent** can be accessed under Microsoft Teams.

    ![](./media/image15.png)
5. Before interacting with Researcher agent we have to first provide some demo campaign emails, so the Researcher Agent can access relevant data and produce meaningful insights and summaries. Hence naivagte to C:\Labfiles\Lab3-Lab to get the demo campaign emails. You can send these emails to the current user using your email.

6.  Now navigate back to the Researcher agent, paste the following prompt in the prompt
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

    ![](./media/image16.png)

7.  Wait for the **Researcher Agent** to gather and summarize the data
    review the Researcher agent carefully. The Researcher Agent may ask
    clarifying questions. Select the report length as “Short” and select
    “Go ahead with your best judgement” and select **Execute** button.

    ![](./media/image17.png)

8.  Review the Researcher agent’s response: 

    The agent searches across Outlook, Teams, and SharePoint documents to
    retrieve the following:

    - Aggregates insights

    - Builds structured summary

    - Campaign progress

    - Vendor updates

    - Risks

    - Strategic insights

9. Review the output:

    ![](./media/image18.png)

    ![](./media/image19.png)

    ![](./media/image20.png)

    ![](./media/image21.png)

    ![](./media/image22.png)

    ![](./media/image23.png)

    ![](./media/image24.png)

    ![](./media/image25.png)

## Exercise 3: Action and Decision Intelligence

This exercise will help Frontline Operations Agent perform a task or
take a specific action based on the data, findings, or situation.

### Task 1: Identify Startup Checklist

1.  Navigate to +++<https://m365copilot.com/>+++ Microsoft 365 copilot
    page. 

2.  David Turner, Cashier at Zava Retail is starting the day and looking
    for a quick checklist. To execute this step, go to the Frontline
    Operations agent, paste the below given prompt in the field, and
    then click on the **Execute** button. 

    +++I am opening cashier. Give me first 20-minute startup checklist.+++

    ![](./media/image26.png)

3.  Review the output:

    ![](./media/image27.png)

### Task 2: Resolve Customer Issues

1.  Navigate to +++<https://m365copilot.com/>+++ Microsoft 365 copilot
    page. 

2.  Marie Brown, Store Associate wants to resolve recurring issues faced
    by customers at the Zava Retail store. To execute this step, go to
    the Frontline Operations Agent, paste the below given prompt in the
    field and then click on the **Execute** button. 

    +++Customer says wrong discount applied. What should I do?+++

    ![](./media/image28.png)

3.  Review the output:

    - The agent will fetch the official policies and SOPs from knowledge
    source and provide the response.

    ![](./media/image29.png)

    ![](./media/image30.png)

4.  Paste the below given prompt in the field and then click on
    the **Execute** button. 

    +++Product out of stock during sale. What are the next steps?+++

    ![](./media/image31.png)

5.  Review the output:

    ![](./media/image32.png)

    ![](./media/image33.png)

### Task 3: Store Manager Scenario

1.  Navigate to +++<https://m365copilot.com/>+++ Microsoft 365 copilot
    page. 

2.  Fratini Greens, Store Manager wants to understand the top priorities
    during weekend rush at retail store, retrieve new hires onboarding
    checklist, and resolve other managerial concerns. To execute this
    step, go to the Frontline Operations Agent, paste the below given
    prompt in the field, and then click on the **Execute** button. 

    +++Create my top 5 priorities for Store \#118 during weekend rush.*+++

    ![](./media/image34.png)

3.  Review the output:

    ![](./media/image35.png)

    ![](./media/image36.png)

4.  Paste the below given prompt in the field, and then click on
    the **Execute** button. 

    +++A new hire joined today as sales associate. Give Day 1 onboarding
    checklist.+++

    ![](./media/image37.png)

5.  Review the output:

    ![](./media/image38.png)

    ![](./media/image39.png)

### Task 4: Multi-persona Role Testing

1.  Navigate to +++<https://m365copilot.com/>+++ Microsoft 365 copilot
    page. 

2.  Patricia Gray, Operations Head is looking for query resolution from
    multiple roles including cashier, store associate, and new hire. To
    execute this step, go to the Frontline Operations Agent, paste the
    below given prompt in the field and then click on
    the **Execute** button. 

    ```
    As a regional operations manager, identify top recurring operational
    issues likely across 250 Zava stores and recommend fixes.*

    *Cashier: Help with queue rush handling  
    Supervisor: Closing checklist  
    Manager: Weekly priorities  
    New Hire: First shift guidance  
    Regional Lead: Store risk summary
    ```

    ![](./media/image40.png)

3.  Review the output:

    ![](./media/image41.png)

    ![](./media/image42.png)

    ![](./media/image43.png)

    ![](./media/image44.png)

### Task 5: Review and Refine the Output 

1.  Evaluate whether the Frontline Operations Agent’s summary meets your
    expectations. 

2.  If results are too broad or missing key details, refine your
    prompt. 

    **Example**: “Narrow this summary to focus only on critical risks and
    delivery blockers.”

3.  Export or copy the summary for documentation, reports, or meeting
    notes. 

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image45.png)

    **Note:** Here is a brief overview of the tasks associated with each
    icon shown in the screenshot: 

    ![](./media/image46.png)

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

**Summary**

In this lab, learners explored how Zava Retail can improve store
operations using a **Microsoft 365 Copilot Frontline Operations Agent**.
With 250 stores, 8,000 employees, and high seasonal demand, Zava Retail
needed a scalable solution to reduce manager workload, improve
consistency, and support frontline staff in real time.

In this lab, you created a custom agent to help store associates,
cashiers, supervisors, and managers with daily tasks such as opening and
closing procedures, shift readiness, promotions, returns, stock issues,
safety incidents, and escalations.

The agent was grounded using SOPs, policies, FAQs, checklists, and
training documents, then tested through real retail scenarios and
persona-based prompts.

By the end of the lab, learners demonstrated how the Zava Frontline
Agent can:

- Reduce repetitive questions to managers

- Improve consistency across stores

- Speed up onboarding for new hires

- Enable faster issue resolution

- Improve frontline productivity and customer service

This lab showed how AI-powered frontline agents can help Zava Retail
scale operations while empowering employees with instant support.

 
