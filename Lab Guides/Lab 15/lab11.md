# Lab 15 - Modernize Customer Support at Zava Retail with an AI-Powered Product Knowledge Agent using Azure AI Search and Foundry Models

**Estimated duration** - 60 minutes

## Scenario:

Zava Retail is a fast-growing omnichannel retailer specializing in home appliances and consumer electronics, operating both physical stores and a rapidly expanding e-commerce platform across multiple regions. As product complexity increases-especially for items like washing machines, refrigerators, and smart home devices-customers frequently reach out for support related to product specifications, installation guidance, warranty coverage, and troubleshooting.

Currently, Zava Retail's customer support model relies heavily on:
- Static FAQ pages on the website
- High call volumes handled by centralized support teams
- Manual lookup of product manuals by agents


This approach is creating **operational bottlenecks**:
- Call center volumes are increasing, leading to long wait times
- Support agents spend significant time searching across scattered
  documents

- Customers receive inconsistent answers depending on the agent's
  experience

- Digital self-service channels fail to handle nuanced or
  product-specific queries


To address these challenges, Zava Retail's Digital Innovation team has initiated a **Customer Support Modernization program** to introduce AI-driven self-service capabilities.

As part of this initiative, the team plans to deploy an **AI-powered Product Knowledge Agent** integrated into their website and support channels. This agent will:
- Leverage **Azure AI Search** to index product manuals, warranty
  policies, and troubleshooting guides stored in internal repositories

- Use **retrieval-augmented generation (RAG)** to fetch precise,
  context-aware information

- Provide **natural, conversational responses** to customer queries
- Include **direct references to source documents** for transparency and
  trust

- Integrate **custom or bring-your-own models from Microsoft Foundry**
  to tailor responses to Zava Retail's tone, product catalog, and support policies


This solution is expected to:
- Reduce call center volume by enabling effective self-service
- Improve first-contact resolution rates
- Ensure consistent and accurate responses across channels
- Enhance overall customer satisfaction and brand trust
- Enable scalable, 24/7 support without proportional increases in
  staffing


In this lab, you will act as Elena Rodriguez, an AI Engineer at Zava Retail, and simulate the company's implementation by building and configuring an intelligent product support agent using Azure AI Search, Azure OpenAI, and Microsoft Copilot Studio, while also integrating a custom model from Microsoft Foundry to align with enterprise-grade AI deployment practices.

### Key Personas

### 1. Sarah Mitchell - Customer Support Director

- Owns customer experience metrics (CSAT, resolution time, call
  deflection)

- Concerned about rising support costs and inconsistent service quality
- Needs a scalable solution to handle increasing product-related queries
- Success metric: Reduce call center volume by 30% while improving CSAT


### 2. David Chen - Digital Platform Lead

- Responsible for Zava Retail's web and digital customer experience
- Tasked with integrating AI-driven capabilities into website and
  support channels

- Needs seamless integration with existing systems
- Success metric: Enable 24/7 intelligent self-service across channels


### 3. Elena Rodriguez - AI Engineer

- Designs and implements AI-powered solutions using Azure services
- Builds the knowledge pipeline, embeddings, and agent orchestration
- Works with Azure AI Search, Foundry models, and Copilot Studio
- Success metric: Deliver accurate, context-aware responses using RAG


### 4. Michael O'Connor - Support Agent

- Handles customer queries via call center and chat
- Spends time searching across manuals and internal systems
- Needs faster, reliable access to product knowledge
- Success metric: Reduce average handling time and improve first-contact
  resolution


### 5. James Walker - Customer

- Purchases appliances and electronics from Zava Retail
- Needs quick answers on warranty, installation, and troubleshooting
- Prefers self-service over contacting support
- Success metric: Get accurate answers instantly without waiting


### Objective

In this lab, you will:
- Provision and configure an **Azure AI Search** service
- Create and configure an **Azure Storage account** to host knowledge
  documents

- Upload and manage product-related documents (manuals, FAQs, policies)
  in Blob Storage

- Configure **managed identities and role-based access control (RBAC)**
  for secure service integration

- Provision an **Azure OpenAI resource** and deploy an embedding model
- Generate embeddings and create a **vector index** in Azure AI Search
  for semantic retrieval

- Implement a **Retrieval-Augmented Generation (RAG)** pipeline using
  indexed data

- Create and configure an agent in **Microsoft Copilot Studio**
- Integrate Azure AI Search as a **knowledge source** for the agent
- Deploy a **foundation model in Microsoft Foundry** and connect it to
  Copilot Studio

- Create and test **custom prompts** using the integrated model
- Validate end-to-end functionality of the AI-powered product support
  agent


## Exercise 1: Create an Azure AI Search resource

In this exercise, we will first create an Azure AI Search resource, which will be used to search through the documents.

1. Open a browser, navigate to +++https://portal.azure.com+++ and login using the **Username** and **TAP** credentials from the **Resources** tab.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image1.png)

1. From the Home page of the Azure portal, select **Foundry.**

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image2.png)

1. In the **Microsoft Foundry| AI Search page**, select **AI Search** from the left pane and then select **+ Create**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v1.png)

1. Enter the below details and select **Review + create**.

    - Subscription - @lab.CloudSubscription.Name
    - Resource group - @lab.CloudResourceGroup(ResourceGroup1).Name
    - Service name - +++documentstore@lab.LabInstance.Id+++
    - Location - @lab.CloudResourceGroup(ResourceGroup1).Location

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v2.png)


1. Once the validation passes, select **Create**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v3.png)

1. The deployment takes a few minutes. Select **Go to resource** once the search service is created.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v4.png)

1. From the **Overview** page, copy the Url value and save it in a notepad to be used in a future exercise.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v5.png)

1. Select **Keys** under **Security + networking** from the left pane. Copy the **Primary admin key** and save it in a notepad for using it in the upcoming exercises.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v6.png)

1. Select **Identity** under **Security + networking** from the left pane.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v7.png)

1. Toggle the Status to **On** under **System assigned** and then click on **Save**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v8.png)
  
1. Select **Yes** in the **Enable system assigned managed identity** confirmation dialog. This setting will enable the search service to be listed under the managed identity resources, which can then be assigned roles as required.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v9.png)


## Exercise 2: Create a Storage account

This exercise is to create a storage account with Blob storage and upload the documents required supporting the retail customers in it.

1. From the Home page of the Azure portal, select **Storage accounts**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image12.png)

1. Select **+ Create** to create a new Storage account.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v10.png)

1. Enter the below details, accept the default values in the other fields and click on **Review + create**.

    - Subscription - @lab.CloudSubscription.Name
    - Resource group - @lab.CloudResourceGroup(ResourceGroup1).Name
    - Region - @lab.CloudResourceGroup(ResourceGroup1).Location
    - Storage account name - +++docstore@lab.LabInstance.Id+++
    - Preferred storage type - Select **Azure Blob Storage or Azure Data
    Lake Storage**

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v11.png)


1. Once the validation passes, click on **Create**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v12.png)
  
1. Once the resource creation succeeds, click on **Go to resource**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v13.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v14.png)

1. Select **Containers** under **Data storage**. Select **+ Add container**, enter the name as +++documents+++ and click on **Create** to create the container.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image18.png)

1. Select the created container **documents** to upload the leave policy document into it.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image19.png)

1. Click on **Upload** and then select **Browse for files**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image20.png)

1. Select the **documents** from **C:\LabFiles\AISearch** folder and then click on **Upload**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image21.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image22.png)

1. Navigate to the **docstore@lab.LabInstance.Id** Storage account (Select **Storageaccounts** from the **Home page** of the Azure portal and select the resource that starts with **docstore**) and select **Access Control (IAM)** from the left pane. Select **Add -\> Add role assignment**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image23.png)

1. Search for +++Storage Blob Data Reader+++, select it and click on **Next**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image24.png)

1. Click on **+Select members**, search for and select your **user id** +++@lab.CloudPortalCredential(User1).Username+++, select your **user id** that gets listed and then click on **Select**. This adds the Storage Blob Data Reader role to your user id.

    ![A screenshot of a group of people AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image25.png)

1. Select **Managed identity** and then select **+ Select members**. Select **Search service(Foundry IQ)** under **Managed identity** and select the **docuemntstore@lab.LabInstance.Id** search service that gets listed.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v15.png)
  
1. Click on **Select** to select the search service.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v16.png)

1. Back in the Add role assignment screen, click on **Review + assign**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image28.png)

1. Select **Review + assign** again in the next screen.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v17.png)

1. Proceed to the next step once you receive a success message on role addition.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image30.png)

    In this exercise, we have created a Storage account and added the documents and required Role permissions to it.


## Exercise 3: Create an Azure OpenAI Service and deploy a model

The AI Search service will have to vectorize the data uploaded, in order to perform the search over the documents. To vectorize the data, an embedding model needs to be deployed. In this exercise, you will create an Azure OpenAI Service and deploy the text-embedding model in it.

1. From the Azure portal Home page, search for select +++Azure
    OpenAI+++.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v18.png)
  
1. Select **+ Create -> Azure OpenAI**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image32.png)

1. Enter the below details and select **Next**.

    - Subscription - @lab.CloudSubscription.Name
    - Resource group - @lab.CloudResourceGroup(ResourceGroup1).Name
    - Region - @lab.CloudResourceGroup(ResourceGroup1).Location
    - Name - +++openaiservice@lab.LabInstance.Id+++
    - Pricing tier - Select **Standard S0**

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image33.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image34.png)


1. Select **Next** in the next 2 screens, and then select **Create** in the **Review + submit** screen.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v19.png)

1. Click on **Go to resource** once the service is created.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v20.png)

1. Select **Access control (IAM)** from the left pane, select **Add -\> Add role assignment**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image37.png)

1. Search for +++Cognitive Services OpenAI User+++, select the role and click on **Next**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image38.png)

1. Select **+ Select members**, search for your **user id** +++@lab.CloudPortalCredential(User1).Username+++, select it and click on **Select**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image39.png)

1. Back in the **Add role assignment** screen, select **Managed identity**. Then select **+ Select members**. In the **Select managed identities** screen, select **Search service(Foundry IQ)** under **Managed identity** and select the resource that starts with **documentstore** service.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v21.png)

1. Once selected, click on **Select**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v22.png)

1. Select **Review + assign** in the next 2 screens.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v23.png)

1. Wait for a **success** message on the role additions before proceeding with the next tasks.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image43.png)

1. From the **Overview** page of the Azure OpenAI Service resource, select **Go to Foundry portal** to open the Azure OpenAI Service there and deploy a model.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image44.png)

1. Close the **Create a project** window.
1. **Turn off** New Foundry toggle button and the select **continue without feedback**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v24.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v25.png)
  
1. Select your Azure Openai service resource

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v26.png)

1. Select **Deployments** from the left pane. Select **+ Deploy model** -\> **Deploy base model**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v27.png)
  
1. Search for +++text-embedding+++, select **text-embedding-3-large** and then select **Confirm**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v28.png)
  
1. Select **Deploy** in the Deploy text-embedding-3-large.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image47.png)

1. The model gets deployed and the screen is loaded with the deployment details.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v29.png)


## Exercise 4: Create a vector index

The AI Search resource needs a Vector index to perform the vector search. You will vectorize the uploaded data in this exercise.

1. From the Azure portal, go to the AI Search service resource that starts with **documentstore**. Select **Import data**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v30.png)

1. Select the **Azure Blob Storage** option.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v31.png)
  
1. Select the **RAG** option in the **What scenarios are you targeting?** screen.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v32.png)
  
1. Enter the below details, accept the other values as default and click **Next**.

    - Subscription - @lab.CloudSubscription.Name
    - Storage account- Select the account that starts with **docstore**
    - Blob-container - Select **documents**

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image52.png)


1. In the Vectorize your text screen, the subscription is pre-populated. Enter the below details and click **Next**.

    - Kind: Select **Foundry resource(Microsoft Foundry/Azure OpenAI)**
    - Microsoft Foundry service/project: Select **openaiservice@lab.LabInstance.Id**
    - Model deployment - Select **text-embedding-3-large**
    - Authentication type - Select **System assigned identity**
    - Select the checkbox to acknowledge the cost alert of Azure OpenAI.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee1.png)


1. Select Next in the **Vectorize and enrich your images** screen since we are not dealing with images here and select **Next** in the **Advanced settings** screen as well.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image54.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image55.png)

1. Select **Create** in the **Review + create** screen.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image56.png)

1. Click on **Close** in the success dialog box.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v33.png)


## Exercise 5: Create a retail assistant agent

In this exercise, you will create a retail assistant agent in Copilot Studio.

1. Login to +++https://copilotstudio.microsoft.com+++/ using your login credentials from the **Resources tab**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image1.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image58.png)

1. Select **Agents** and then select **Create blank agent**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v34.png)

1. Enter +++Retail assistant+++ as your agent name and then click **Create** button to create new agent in Copilot Studio.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v35.png)

1. Select **Edit** and enter +++You are a Retail assistant agent for customers HR who will answer questions related to the store products+++ as your description. Click **Save** to save the changes.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v36.png)
  
1. Once the agent is created, in the Test pane, enter +++What is the warranty period for Washing machine ?+++ and click **Send**.`

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v37.png)
  
1. It gives a generalized reply as in the screenshot below.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v38.png)


## Exercise 6: Add the Azure AI Search as a knowledge source

In this exercise, you will add the Azure AI Search that you created from the Azure portal, as a knowledge source to the Retail assistance agent in Copilot Studio.

1. From the **Overview** page of the agent, select **+ Add knowledge**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v39.png)

1. Select **Azure AI Search** from the list of knowledge sources available.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image64.png)

1. Click on the **drop down** next to **Not connected** in the next screen and select **Create new connection**.

    ![A screenshot of a search engine AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image65.png)

1. Enter the **Endpoint url** and the **Admin key** values which we saved to a notepad in a previous exercise and then click on **Create** to create the connection.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image66.png)

1. Once the connection is established, the available index is listed and already selected. Click on **Add to agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image67.png)

1. The AI Search service is added as a knowledge source to the agent and is in **Ready** state now.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image68.png)

1. Now, let us test the agent with the same question we have tried before.

1. In the Test pane, enter +++What is the warranty period for Washing machine?+++ and click **Send**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v40.png)
  
1. You can see that the response from the agent now is from the document uploaded in the AI Search service.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v41.png)


## Exercise 7: Deploy a Model in Microsoft Foundry

In this exercise, you will deploy a model in the Microsoft Foundry to use it in the Copilot Studio (in the next exercise).

1. Open the Microsoft Foundry Azure OpenAI resource created earlier.

1. From the left pane, select **Deployments**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v46.png)
  
1. Select the drop down next to the **+ Deploy model** and select **Deploy base model**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v42.png)
  
1. Select **o3** and select **Confirm**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee2.png)
  
1. In the Deploy o3 dialog, enter the **Deployment name** as +++ModelforMCS+++, accept the other defaults and select **Deploy.**

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee3.png)

1. Copy the Target URI and key values to a notepad to be used during the connection creation from the Copilot Studio.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee4.png)

    Now that the model is deployed, you can use it in Copilot Studio's agent prompt.


## Exercise 8: Create a prompt in the Copilot Studio and use the model created in Microsoft Foundry

In this exercise, you will learn how to bring the deployed model from Microsoft Foundry in the Copilot Studio. Here, we are using a base model that is deployed. We can also create a fine tuned model as per the business requirements and then use it in Copilot Studio.

1. From the Copilot Studio agent, select **Tools** from the top menu bar. Click **+ Add a tool**

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v47.png)
  
1. Select **Prompt** since we are going to add a new prompt.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee5.png)

1. In the Custom prompt screen, select the drop down next to the **model** name.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v49.png)
  
1. Select **+** against **Azure AI Foundry Models** to add the model deployed in Azure AI Foundry and select **Connect a new model**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v50.png)
  
    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image81.png)

1. Enter the below details and click on **Connect**.

    - Model deployment name - +++ModelforMCS+++
    - Base model name - +++o3+++
    - Azure model endpoint URL - Enter the target url saved earlier
    - API Key - Enter the model API key saved earlier.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee6.png)


1. Once connected, select **Close**.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image84.png)

1. You can see that the model ModelforMCS is selected now

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v52.png)

1. Rename the prompt to +++WM Types+++. Enter +++What are the different types of Washing Machines?+++ and select **Send**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee7.png)
  
1. Select **Keep it**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee8.png)
  
1. Select Test to test the prompts.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/ee9.png)
  
1. Scroll down and select **Save** to save the prompt.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v54.png)

1. Select the **Add and configure** option to add the prompt to the agent.

    ![A screenshot of a computer AI-generated content may be incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/image88.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2015/media/v55.png)

    With this feature, we can fine-tune the model in Microsoft Foundry and use it in Copilot Studio with ease. We can bring in the vast ecosystem of the models in the Microsoft Foundry easily into the Copilot Studio.


## Summary

In this lab, you created a knowledge-driven AI support agent by integrating Azure AI Search, Azure OpenAI, and Microsoft Copilot Studio. You started by uploading and indexing product documents, then enabled vector-based search using an embedding model to support accurate information retrieval.

You connected this knowledge base to a Copilot Studio agent, allowing it to answer customer queries with relevant, document-backed responses. Finally, you integrated a model from Microsoft Foundry and used it within a custom prompt to extend the agent's capabilities.

This lab demonstrates how to build and connect the core components required for a RAG-based, enterprise-ready support solution.
