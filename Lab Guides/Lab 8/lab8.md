# Lab 8 - Transform After-Sales Repair Operations at Zava Retail with an AI-Powered Declarative Agent

## Objective

In this lab you will build a Declarative Agent with TypeSpec definition
using Microsoft 365 Agents Toolkit. You will create an agent called
RepairServiceAgent, which interacts with repairs data via an existing
API service to help users manage car repair records.

## Scenario
Zava Retail is a global retail and service organization that provides after-sales support for automotive accessories and consumer electronics across multiple regional service centers. As the business scales, the After-Sales Operations team is facing increasing complexity in managing repair requests, tracking service status, and coordinating across technicians and service locations.

Currently, repair operations are managed through a combination of a legacy tracking system and manual API interactions. Service agents must switch between multiple tools to create, update, and retrieve repair records, resulting in delays, inconsistent data updates, and reduced operational efficiency. Managers also lack real-time visibility into repair workloads and service bottlenecks.

To address these challenges, Zava Retail is modernizing its after-sales ecosystem by introducing an AI-powered Declarative Agent named RepairServiceAgent, built using Microsoft 365 Agents Toolkit and TypeSpec-based API design. The agent connects directly to the Repair Service API and enables conversational management of repair operations within Microsoft 365 Copilot.

The RepairServiceAgent provides a unified interface for creating, updating, retrieving, and deleting repair records using natural language, eliminating the need for manual API calls or system navigation. It also enhances decision-making by presenting repair data in structured Adaptive Cards for improved readability and actionability.

**Key personas**
1. Alex Morgan – Service Center Agent
Alex works at a Zava Retail service center and handles daily repair intake and updates. Alex uses the RepairServiceAgent to quickly create, update, and track repair requests without needing to interact with backend systems or APIs.

2. Priya Nair – Repair Technician
Priya is a field repair technician responsible for executing and updating repair tasks. She relies on the agent to view assigned repairs, update job status, and confirm completion with structured repair details and images.

3. Daniel Kim – Service Operations Manager
Daniel oversees repair operations across multiple service centers. He uses the agent to monitor repair volumes, track SLA performance, and identify operational bottlenecks through real-time repair data insights.

4. Sofia Martinez – IT Integration Engineer
Sofia manages the Repair Service API and ensures smooth integration with enterprise systems. She benefits from TypeSpec-driven contracts and declarative agent actions that reduce integration complexity and improve system reliability.

## Declarative agents

**Declarative agents** are a type of agents for Microsoft 365. You can
build one by extending Microsoft 365 Copilot. You define custom
knowledge and custom actions to create agents tailored to a specific
scenario.

Declarative agents use the same infrastructure, orchestrator, foundation
model, and security controls as Microsoft 365 Copilot, which ensures a
consistent and familiar user experience.

![Declarative agent architecture diagram. At the very basis there is the
foundational model of Microsoft 365 Copilot, as well as the same
orchestrator. The agent provides also custom knowledge and grounding
data, and custom skills as actions, triggers, and workflows.. The user
experience is available in Microsoft 365 Copilot.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image1.png)

**Significance of TypeSpec for Declarative Agents**

**What is TypeSpec**

TypeSpec is a language developed by Microsoft for designing and
describing API contracts in a structured and type-safe way. Think of it
like a blueprint for how an API should look and behave including what
data it accepts, returns, and how different parts of the API and its
actions are connected.

**Why TypeSpec for Agents?**

If you like how TypeScript enforces structure in your frontend/backend
code, you'll love how TypeSpec enforces structure in your agent and its
API services like actions. It fits perfectly in design-first development
workflows that align with tools like Visual Studio Code.

Clear Communication - provides a single source of truth that defines how
your agent should behave, avoiding confusion when dealing with multiple
manifest files like in the case of Declarative Agents.

Consistency - ensures all parts of your agent and its actions,
capabilities, etc. are designed consistently following the same pattern.

Automation Friendly - automatically generates OpenAPI specs and other
manifests saving time and reducing human errors.

Early Validation - catches design issues early before writing actual
code for example, mismatched data types or unclear definintions.

Design-First Approach - encourages thinking about agent and API
structure and contracts before jumping into implementation, leading to
better long-term maintainability.

## Exercise 1: Set up the lab environment

In this exercise, you will set up the development environment to build,
test, and deploy the Copilot agents, which will help you achieve
tailor-made AI assistance using Microsoft 365 Copilot.

### Task 1: Install Agents Toolkit

The **Agents Toolkit for Visual Studio Code** requires Visual Studio
Code. In this exercise, you will install the toolkit in Visual Studio
Code.

1.  Open **Visual Studio Code** from the VM. Select **Extensions** from
    the left menu.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image2.png)

2.  Search for and select +++Microsoft 365 Agents Toolkit+++ and click
    on **Install**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image3.png)

3.  Ensure that the toolkit is installed.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image4.png)

4.  Create a new folder named +++ServiceAgent+++ in your Desktop.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image5.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image6.png)

## Exercise 2: Build the base agent with TypeSpec using Microsoft 365 Agents Toolkit

In this exercise, you will build a **Declarative Agent**, define it,
update the actions and test the agent.

### Task 1: Scaffold your base agent project using Microsoft 365 Agents Toolkit

In this task, you will build the **Declarative
Agent** with **TypeSpec** definition using **Microsoft 365 Agents
Toolkit**. You will create an agent called **RepairServiceAgent**, which
interacts with repairs data via an existing API service to help users
manage car repair records.

1.  Locate the **Microsoft 365 Agents Toolkit
    icon** from the VS Code menu on the left and select it. An activity bar will be open. Select the **Create a New Agent/App** button in the activity bar which will open the palette with a list of app templates available on Microsoft 365 Agents Toolkit.
    
    ![m365atk-icon](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image7.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image8.png)

3.  Choose **Declarative Agent** from the list of templates.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image9.png)

4.  Next, select **Start with TypeSpec for Microsoft 365 Copilot** to
    define your agent using TypeSpec.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image10.png)

5.  Next, select **Browse** and then select the
    folder **ServiceAgent** from the Desktop. This is the location,
    where you want the agents toolkit to scaffold the agent project.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image11.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image12.png)

6.  Next, enter the application name as +++RepairServiceAgent+++ and
    select **Enter** to complete the process. You will get a new VS Code
    window with the agent project preloaded.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image13.png)

7.  Select **Yes, I trust the authors** option in the confirmation
    dialog.

8.  You'll need to sign into the **Microsoft 365 Agents Toolkit** in
    order to upload and test your agent from within it.

9.  Within the project window, select the **Microsoft 365 Agents Toolkit
    icon** again from the left side menu. This will open the Agent Toolkit’s activity bar with sections
    like Accounts, Environment, Development etc.

    ![m365atk-icon](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image7.png)

11. Under **Accounts** section select **Sign in to Microsoft 365**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image14.png)

11. This will open a dialog from the editor to sign in or create a
    Microsoft 365 developer sandbox or Cancel. Select **Sign in**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image15.png)

12. Login with your **user name** and **TAP Token** from
    the **Resources** tab.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image16.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image17.png)

13. Once signed in, **close** the browser and go back to the project
    window.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image18.png)

    >[!Note] If there is a message on Custom App Upload Disabled,
    safely ignore it.

### Task 2: Define your agent

The Declarative Agent project scaffolded by the Agents Toolkit provides
a template that includes code for connecting an agent to the GitHub API
to display repository issues. In this lab, you’ll build your own agent
that integrates with a car repair service, supporting multiple
operations to manage repair data.

Before proceeding with the agent definition, take a moment to examine
the Repairs API service to gain a clearer understanding of its
functionality.

**Get to know the repair API service**

You'll need to explore endpoints and payloads of the API service
interactively. Using a **.http** file in Visual Studio Code with the
REST Client extension, which is already installed for you, allows you to
define and send HTTP requests directly from your editor. It's a
lightweight, code-friendly way to test APIs, inspect responses, and
iterate quickly without switching to external tools.

1.  Inside the root folder of the project you just created, create a
    folder called +++**http+++**. Create a new file
    named +++repairs-api.http+++ inside the http folder.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image19.png)

2.  Copy paste below content into the file.
   
    ```
    @base_url = https://repairshub.azurewebsites.net

    ### Get all repair requests
    {{base_url}}/repairs

    ### Get a specific repair request by ID
    {{base_url}}/repairs/1

    ### Create a new repair request
    POST {{base_url}}/repairs
    Content-Type: application/json

    {
    "description": "Repair broken screen",
    "date": "2023-10-01T12:00:00Z",
    "image": "https://example.com/image.png"
    }

    ### Update an existing repair request
    PATCH {{base_url}}/repairs/1
    Content-Type: application/json  

    {
    "id": 1,
    "description": "Repair broken screen - updated",
    "date": "2023-10-01T12:00:00Z",
    "image": "https://example.com/image-updated.png"
    }


    ### Delete a repair request by ID
    DELETE {{base_url}}/repairs/10
    Content-Type: application/json

    {
    "id": 10
    }
    ```

    ![A screenshot of a computer program AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image20.png)

4.  To run each request, hover over each request line (e.g., GET
    {{base_url}}/repairs) and click **Send Request** to see the
    response. Observe the structure of requests and responses and use
    the response data to understand how your agent will interact with
    the API.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image21.png)

    **Repairs API Overview**

    **Base URL**: *https://repairshub.azurewebsites.net*

    | Operation| Column 2 | Column 3 |Column 3 |Column 3 |
    |----------|----------|----------|----------|----------|
    | Get all repair requests | GET  | /repairs  |No  |Retrieve all repair jobs  |
    | Get repair by ID | GET  | /repairs/{id}  |No  |Fetch a specific repair job  |
    | Create a repair request  | POST  | /repairs  |Yes  |Submit a new repair job  |
    | Update a repair request | PATCH  | /repairs/{id}  |Yes  |Modify an existing repair job  |
    | Delete a repair request  | DELETE  | 	/repairs/{id}  |No  |Remove a repair job by ID  |

    Now that you're familiar with the API service, let's move on to
    integrating it with your agent.

**Project Structure**
Within your agent project under **src** folder, you'll discover the core
TypeSpec configuration files: **main.tsp** and **env.tsp**.

The **main.tsp** file serves as the primary definition point for your
agent, containing essential metadata, behavioral instructions, and
capability specifications.

The **env.tsp** file is used by the toolkit to process environment
variables during compilation. This file is generated
from **env/.env.\*** files and offer variables for other TypeSpec files,
so manual updates are not required.

You'll also find an **actions** folder containing template files -
initially including **github.tsp** which demonstrates GitHub API
integration. For this lab, you'll replace this template with your own
action definitions to establish connectivity with the Repairs API
service.

Additionally, there's a **prompts** folder housing
the **instructions.tsp** file, which allows you to define detailed
behavioral instructions and guidance for your agent.

![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image22.png)

**Update the Agent Metadata and Instructions**

1. In the **main.tsp** file you will find the basic structure of the agent.
    Review the content provided by the agents toolkit template which
    includes: -

    - **Agent name** and **description** 1️⃣

    - Basic **instructions** 2️⃣

    - Placeholder code for **actions** and **capabilities** (commented out) 3️⃣

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image23.png)

2. Begin by defining your agent for the repair scenario. Replace
the **@agent** metadata with below code snippet.

    ```
    @agent(
    "RepairServiceAgent",
    "An agent for managing repair information"
    )
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image24.png)

4. Next, configure a conversation starter, the initial prompt that
    begins user-agent interaction. Uncomment the default template section
    and update the title and text fields to match the agent scenario.

    ```
    // Uncomment this part to add a conversation starter to the agent.
    // This will be shown to the user when the agent is first created.
    @conversationStarter(#{
    title: "List repairs",
    text: "List all repairs"
    })
    ```

    This starter prompt needs to trigger a GET operation to retrieve all
    repairs from the service. To enable this behaviour in the agent, you' ll
    need to define the corresponding action. Proceed to the next step to do
    so.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image25.png)

5. Next, go to **prompts/instructions.tsp** and update the instructions.
Replace the entire code block in the file with below code:

    ```
    namespace Prompts {
    const INSTRUCTIONS = """
        ## Purpose
        You will assist the user in finding car repair records based on the information provided by the user.
    """;
    }
    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image26.png)

7. Save the changes to both files using CTRL+S.

### Task 3: Update the action for the agent

1. Next, you will define the action for your agent by opening
    the **actions/github.tsp** file. Rename this file
    to +++actions.tsp+++.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image27.png)
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image28.png)

    You'll return to the **main.tsp** file later to complete the agent
    metadata with the action reference, but first, the action itself must be
    defined. For that open the file **actions.tsp**.

    The default **actions.tsp** template demonstrates how to define an agent
    action, including metadata, service URL, and operation structure.
    Replace the sample GitHub logic entirely with definitions relevant to
    the Repairs API service.

2. After the module-level directives like import and using statements,
replace the existing code up to the point where the "SERVER_URL" is
defined with the snippet below.

    ```
    @service
    @server(RepairsAPI.SERVER_URL)
    @actions(RepairsAPI.ACTIONS_METADATA)
    namespace RepairsAPI{
    /**
    * Metadata for the API actions.
    */
    const ACTIONS_METADATA = #{
        nameForHuman: "Repair Service Agent",
        descriptionForHuman: "Manage your repairs and maintenance tasks.",
        descriptionForModel: "Plugin to add, update, remove, and view repair objects.",
        legalInfoUrl: "https://docs.github.com/en/site-policy/github-terms/github-terms-of-service",
        privacyPolicyUrl: "https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement"
    };

    /**
    * The base URL for the  API.
    */
    const SERVER_URL = "https://repairshub.azurewebsites.net";
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image29.png)

3.  Next, replace the operation in the template code from searchIssues
    to **listRepairs** which is a repair operation to get the list
    of **repairs**. Replace the entire block of code starting just after
    the SERVER_URL definition and ending *before* the final closing
    braces with the snippet below. Be sure to leave the closing braces
    intact. (Line numbers should be 27 to 37)
    
    ```
    /**
    * List repairs from the API 
    * @param assignedTo The user assigned to a repair item.
    */

    @route("/repairs")
    @get  op listRepairs(@query assignedTo?: string): string;
    ```

    ![A screen shot of a computer program AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image30.png)

5.  Now go back to **main.tsp** file and verify the import statement for
    actions. If it still references *./actions/github.tsp*,
    replace *import "./actions/github.tsp";* with the statement below:
    
    ```
    import "./actions/actions.tsp";
    ```
    
    ![A screenshot of a computer program AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image31.png)

7.  Next, in the same file, add the action you just defined into the
agent. After the conversation starters replace the entire
"RepairServiceAgent" namespace with below snippet:

    ```
    namespace RepairServiceAgent{  

    op listRepairs is global.RepairsAPI.listRepairs;   

    }
    ```

    ![A screen shot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image32.png)

### Task 4: (Read only) Understand the decorators

This is a task to understand what we have defined in the TypeSpec file.
Just read through this task. In the TypeSpec files main.tsp and
actions.tsp, you'll find decorators (starting with @), namespaces,
models, and other definitions for your agent.

Check the below details to understand some of the decorators used in
these files

- **@agent** - Defines the namespace (name) and description of the agent

- **@instructions** - Defines the instructions that prescribe the
  behaviour of the agent. 8000 characters or less

- **@conversationStarter** - Defines conversation starters for the agent

- **op** - Defines any operation. Either it can be an operation to
  define agent’s capabilities like op GraphicArt, op CodeInterpreter
  etc., or define API operations like op listRepairs.

- **@server** - Defines the server endpoint of the API and its name

- **@capabilities** - When used inside a function, it defines simple
  adaptive cards with small definitions like a confirmation card for the
  operation

### Task 5: Test your agent

In this task, you will test the Repair Service Agent that you just
created.

1.  Select the **Agents Toolkit extension's** icon, to open the activity
    bar from within your project.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image33.png)

2.  In the activity bar of the Agents Toolkit
    under **LifeCycle** select **Provision**. This will build the app
    package consisting of the generated manifest files and icons and
    side load the app into the catalog only for you to test.

    ![A screenshot of a computer program AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image34.png)

3.  Open your web browser and navigate to
    +++https://m365.cloud.microsoft/chat+++ to open Copilot app and
    click on **Expand Navigation**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image35.png)

4.  Select the **RepairServiceAgent** from the list
    of **Agents** available in the Microsoft 365 Copilot interface. This
    will take a while, and you will be able to see a toaster message
    showing the progress of the task to provision.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image36.png)

5.  Select the conversation starter **List repairs** and send the
    prompt.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image37.png)

6.  If there is a popup that asks for the connection to the API,
    select **Always allow**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image38.png)

7.  This initiates the conversation with your agent and you can see the
    response from the agent with the list of repairs.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image39.png)

## Exercise 3: Enhance Agent capabilities

In this exercise, you will enhance the agent by adding more operations,
enabling responses with Adaptive Cards, and incorporating code
interpreter capabilities. Let’s explore each of these enhancements step
by step. Go back to the project in VS Code.

### Task 1: Modify agent to add more operations

In this task, you will modify the agent and add operations
like **createRepair**, **updateRepair** and **deleteRepair.**

1. Go to file **actions/actions.tsp** and copy paste below snippet just
  after **listRepairs** operation to add new
  operations **createRepair**, **updateRepair** and **deleteRepair**.
  Here you will also define the **Repair** item data model.

    ```
    /**
    * Create a new repair using the API. 
    * When creating a repair, the `id` field is optional and will be generated by the server.
    * The `date` field should be in ISO 8601 format (e.g., "2023-10-01T12:00:00Z").
    * The `title` field based on what repair user wants to create
    * @param repair The repair to create.
    */
    @route("/repairs")  
    @post  op createRepair(@body repair: Repair): Repair;
    
    /**
    * Update an existing repair.
    * The `id` field is required to identify the repair to update.
    * The `date` field should be in ISO 8601 format (e.g., "2023-10-01T12:00:00Z").
    * The `image` field should be a valid URL pointing to the image associated with the repair.
    * @param repair The repair to update.
    */
    @route("/repairs")  
    @patch(#{implicitOptionality: true})
    op updateRepair(@body repair: Repair): Repair;
    
    
    /**
    * Delete a repair.
    * The `id` field is required to identify the repair to delete.
    * @param repair The repair to delete.
    */
    @route("/repairs") 
    @delete  op deleteRepair(@body repair: Repair): Repair;
    
    /**
    * A model representing a repair.
    */
    model Repair {
    /**
    * The unique identifier for the repair.
    */
    id?: string;
    
    /**
    * The short summary or title of the repair.
    */
    title: string;
    
    /**
    * The detailed description of the repair.
    */
    description?: string;
    
    /**
    * The user who is assigned to the repair.
    */
    assignedTo?: string;
    
    /**
    * The optional date and time when the repair is scheduled or completed.
    */
    @format("date-time")
    date?: string;
    
    /**
    * The URL of the image associated with the repair.
    */
    @format("uri")
    image?: string;
    }
    ```
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image40.png)

2.  Now, open **main.tsp** file and add these new operations into the
    agent's action. **Paste** the below snippet after the line **op
    listRepairs is global.RepairsAPI.listRepairs;** inside
    the **RepairServiceActions** namespace.
    
    ```
    op createRepair is global.RepairsAPI.createRepair;
    op updateRepair is global.RepairsAPI.updateRepair;
    op deleteRepair is global.RepairsAPI.deleteRepair;
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image41.png)

2.  Also add a new conversation starter for creating a new repair item
    just after the first conversation start definition.
    
    ```
    @conversationStarter(#{
        title: "Create repair",
        text: "Create a new repair titled \"[TO_REPLACE]\" and assign it to me"
    })
    ```
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image42.png)

### Task 2: Add adaptive card to function reference

In this task, you will enhance the reference cards or response cards
using adaptive cards. Let’s take the **listRepairs** operation and add
an adaptive card for the repair item.

1.  In the project, go to the **adaptiveCards** folder
    under **appPackage** folder. Create a new file
    named +++repair.json+++ and paste the provided code snippet. This
    will define a new adaptive card for the repair object. Ignore the
    default template card that is already present in this folder.
    
     ```
    {
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.5",
        "body": [
        {
            "type": "Container",
            "$data": "${$root}",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "Title: ${if(title, title, 'N/A')}",
                    "weight": "Bolder",
                    "wrap": true
                },
                {
                    "type": "TextBlock",
                    "text": "Description: ${if(description, description, 'N/A')}",
                    "wrap": true
                },
                {
                    "type": "TextBlock",
                    "text": "Assigned To: ${if(assignedTo, assignedTo, 'N/A')}",
                    "wrap": true
                },
                {
                    "type": "TextBlock",
                    "text": "Date: ${if(date, date, 'N/A')}",
                    "wrap": true
                },
                {
                    "type": "Image",
                    "url": "${image}",
                    "$when": "${image != null}"
                }
            ]
        }],  
        "actions": [
            {
                "type": "Action.OpenUrl",
                "title": "View Image",
                "url": "https://www.howmuchisit.org/wp-content/uploads/2011/01/oil-change.jpg"
            }
        ]
    }
    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image43.png)

    ![A screen shot of a computer program
    AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image44.png)

3.  Next, go back to **actions.tsp** file and locate the listRepairs
    operation. Just above the operation definition **@get op
    listRepairs(@query assignedTo?: string): string;**, paste the card
    definition using below snippet.
    
    ```
    @card(#{  dataPath: "$", file: "adaptiveCards/repair.json",    properties: #{ title: "$.title", url: "$.image" } })
    ```

    ![A screenshot of a computer program AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image45.png)

    The above card response will be sent by the agent when you ask about a
    repair item or when agent brings a list of items as its reference.

5.  Continue to add card response for the **createRepair** operation to
    show what the agent created after the POST operation. Copy paste
    below snippet just above the code **@post op createRepair(@body
    repair: Repair): Repair;**
    
    ```

    @card(#{  dataPath: "$", file: "adaptiveCards/repair.json",    properties: #{ title: "$.title", url: "$.image" } })
    ```
    
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image46.png)

### Task 3: Update agent instruction for new operations

1. In the **prompts/instructions.tsp** file, update instructions definition
to have additional directives for the agent. Replace
    the **INSTRUCTIONS** constant with below code:
   
    ```
    const INSTRUCTIONS ="""  
        ## Purpose
        You will assist the user in finding car repair records based on the information provided by the user.

        ## Guidelines
        - You are a repair service agent.
        - You can use the actions to create, update, and delete repairs.
        - When creating a repair item, if the user did not provide a description or date, use the title as the description and put today's date in the format YYYY-MM-DD.
        - Do not use any technical jargon or complex terms.
    """;
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image47.png)

### Task 4: Provision and Test the Agent

In this task, you will take the updated agent who is also now a repairs
analyst to test.

1.  Select the Agents Toolkit's extension icon to open its activity bar
    from within your project.

2.  In the activity bar of the toolkit
    under **LifeCycle,** select **Provision** to package and upload the
    newly updated agent for testing.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image48.png)

3.  Ensure that the provisioning gets succeeded.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image49.png)

    \[!Alert\] **Important:** There are couple of known issues where the
    Provision action in Agents Toolkit may fail with the errors shown below.
    If this happens, simply retry the provisioning process until it
    succeeds.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image50.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image51.png)

4.  Go back to the open **browser** session and do a **refresh**.

5.  In the **RepairServiceAgent**, start by using the conversation
    starter **Create repair**. Replace parts of the prompt to add a
    title, then send it to the chat to initiate the interaction. For
    example:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image52.png)

6.  Replace the **“\[TO REPLACE\]”** with +++rear camera issue+++ and
    assign it to me.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image53.png)

7.  The confirmation dialog if you notice has more metadata that what
    you sent, thanks to the new instructions.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image54.png)

8.  Proceed to add the item by **confirming** the dialog.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image55.png)

9.  The agent responds with the **created item**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image42.png)

10. Next, you will test the new analytical capability of your agent.
    Open a new chat by selecting the **New chat** button on the top
    right corner of your agent.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image56.png)

11. Next, copy the prompt below and paste it to the message box and hit
    enter to send it.

    +++Classify repair items based on title into three distinct categories:
    Routine Maintenance, Critical, and Low Priority. Then, generate a chart
    displaying the percentage representation of each category.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image57.png)

12. You should get some response similar to below screen. It may vary
    sometimes.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image58.png)

13. Open the link
    +++https://dev.teams.microsoft.com+++/

14. Select **Apps** from the left pane.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image59.png)

15. You will find the **RepairServiceAgent** under Apps.

16. Scroll to the right, click on the **3 dots** and select **Delete**.
    This needs to be done in order to provision another agent. Since you
    will be creating another agent in the next lab, this step needs to
    be done.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%208/media/image60.png)

## Summary:

In this lab, you have:

- Used **TypeSpec** to describe APIs and bind them to Copilot actions.

- Configure **Adaptive Cards** to display repair records in a rich
  visual layout.

- Build a complete scenario where users can interact naturally with
  Copilot to manage repair data.

This lab demonstrated how Declarative Agents leverage the **Copilot
platform’s orchestration, foundation models, and security controls** to
deliver a familiar and consistent user experience while integrating with
custom business data and workflows.
