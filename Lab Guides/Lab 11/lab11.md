# Lab 11 - Modernize Customer Support at Zava Retail with an AI-Powered Product Knowledge Agent using Azure AI Search and Foundry Models

**Estimated duration** – 60 minutes

## Scenario:

Zava Retail is a fast-growing omnichannel retailer specializing in home
appliances and consumer electronics, operating both physical stores and
a rapidly expanding e-commerce platform across multiple regions. As
product complexity increases—especially for items like washing machines,
refrigerators, and smart home devices—customers frequently reach out for
support related to product specifications, installation guidance,
warranty coverage, and troubleshooting.

Currently, Zava Retail’s customer support model relies heavily on:

- Static FAQ pages on the website

- High call volumes handled by centralized support teams

- Manual lookup of product manuals by agents

This approach is creating **operational bottlenecks**:

- Call center volumes are increasing, leading to long wait times

- Support agents spend significant time searching across scattered
  documents

- Customers receive inconsistent answers depending on the agent’s
  experience

- Digital self-service channels fail to handle nuanced or
  product-specific queries

To address these challenges, Zava Retail’s Digital Innovation team has
initiated a **Customer Support Modernization program** to introduce
AI-driven self-service capabilities.

As part of this initiative, the team plans to deploy an **AI-powered
Product Knowledge Agent** integrated into their website and support
channels. This agent will:

- Leverage **Azure AI Search** to index product manuals, warranty
  policies, and troubleshooting guides stored in internal repositories

- Use **retrieval-augmented generation (RAG)** to fetch precise,
  context-aware information

- Provide **natural, conversational responses** to customer queries

- Include **direct references to source documents** for transparency and
  trust

- Integrate **custom or bring-your-own models from Microsoft Foundry**
  to tailor responses to Zava Retail’s tone, product catalog, and
  support policies

This solution is expected to:

- Reduce call center volume by enabling effective self-service

- Improve first-contact resolution rates

- Ensure consistent and accurate responses across channels

- Enhance overall customer satisfaction and brand trust

- Enable scalable, 24/7 support without proportional increases in
  staffing

In this lab, you will act as Elena Rodriguez, an AI Engineer at Zava
Retail, and simulate the company’s implementation by building and
configuring an intelligent product support agent using Azure AI
Search, Azure OpenAI, and Microsoft Copilot Studio, while also
integrating a custom model from Microsoft Foundry to align with
enterprise-grade AI deployment practices.

**Key Personas**

**1. Sarah Mitchell – Customer Support Director**

- Owns customer experience metrics (CSAT, resolution time, call
  deflection)

- Concerned about rising support costs and inconsistent service quality

- Needs a scalable solution to handle increasing product-related queries

- Success metric: Reduce call center volume by 30% while improving CSAT

**2. David Chen – Digital Platform Lead**

- Responsible for Zava Retail’s web and digital customer experience

- Tasked with integrating AI-driven capabilities into website and
  support channels

- Needs seamless integration with existing systems

- Success metric: Enable 24/7 intelligent self-service across channels

**3. Elena Rodriguez – AI Engineer**

- Designs and implements AI-powered solutions using Azure services

- Builds the knowledge pipeline, embeddings, and agent orchestration

- Works with Azure AI Search, Foundry models, and Copilot Studio

- Success metric: Deliver accurate, context-aware responses using RAG

**4. Michael O’Connor – Support Agent**

- Handles customer queries via call center and chat

- Spends time searching across manuals and internal systems

- Needs faster, reliable access to product knowledge

- Success metric: Reduce average handling time and improve first-contact
  resolution

**5. James Walker – Customer**

- Purchases appliances and electronics from Zava Retail

- Needs quick answers on warranty, installation, and troubleshooting

- Prefers self-service over contacting support

- Success metric: Get accurate answers instantly without waiting

**Objective**

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

In this exercise, we will first create an Azure AI Search resource,
which will be used to search through the documents.

1.  Open a browser, navigate to
    +++https://portal.azure.com+++ and
    login using the **Username** and **TAP** credentials from
    the **Resources** tab.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image1.png)

2.  From the Home page of the Azure portal, select **Foundry.**

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image2.png)

3.  In the **AI Foundry page**, select **AI Search** from the left pane
    and then select **+ Create**.

    ![A screenshot of a search engine AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image3.png)

4.  Enter the below details and select **Review + create**.

    - Subscription – @lab.CloudSubscription.Name

    - Resource group – @lab.CloudResourceGroup(ResourceGroup1).Name

    - Service name – +++documentstore@lab.labinstance.id+++

    - Location – @lab.CloudResourceGroup(ResourceGroup1).Location

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image4.png)

5.  Once the validation passes, select **Create**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image5.png)

6.  The deployment takes a few minutes. Select **Go to resource** once
    the search service is created.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image6.png)

7.  From the **Overview** page, copy the Url value and save it in a
    notepad to be used in a future exercise.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image7.png)

8.  Select **Keys** under **Settings** from the left pane. Copy
    the **Primary admin key** and save it in a notepad for using it in
    the upcoming exercises.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image8.png)

9.  Select **Identity** under **Settings** from the left pane.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image9.png)

10. Toggle the Status to **On** under **System assigned** and then click
    on **Save**.

    ![A screenshot of a computer screen AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image10.png)

11. Select **Yes** in the **Enable system assigned managed
    identity** confirmation dialog. This setting will enable the search
    service to be listed under the managed identity resources, which can
    then be assigned roles as required.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image11.png)

## Exercise 2: Create a Storage account

This exercise is to create a storage account with Blob storage and
upload the documents required supporting the retail customers in it.

1.  From the Home page of the Azure portal, +++https://portal.azure.com/+++, select **Storage accounts**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image12.png)

2.  Select **+ Create** to create a new Storage account.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image13.png)

3.  Enter the below details, accept the default values in the other
    fields and click on **Review + create**.

    - Subscription – @lab.CloudSubscription.Name

    - Resource group – @lab.CloudResourceGroup(ResourceGroup1).Name

    - Region – @lab.CloudResourceGroup(ResourceGroup1).Location

    - Storage account name – +++docstore@lab.labinstance.id+++

    - Preferred storage type – Select **Azure Blob Storage or Azure Data
      Lake Storage Gen 2**

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image14.png)

4.  Once the validation passes, click on **Create**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image15.png)

5.  Once the resource creation succeeds, click on **Go to resource**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image16.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image17.png)

6.  Select **Containers** under **Data storage**. Select **+ Add
    container**, enter the name as +++documents+++ and click
    on **Create** to create the container.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image18.png)

7.  Select the created container **documents** to upload the leave
    policy document into it.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image19.png)

8.  Click on **Upload** and then select **Browse for files**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image20.png)

9.  Select the **documents** from **C:\LabFiles\AISearch** folder and
    then click on **Upload**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image21.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image22.png)

10. Navigate to the **docstore@lab.labinstance.id** Storage account
    (Select **Storageaccounts** from the **Home page** of the Azure
    portal and select the resource that starts with **docstore**) and
    select **Access Control (IAM)** from the left pane. Select **Add -\>
    Add role assignment**.

![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image23.png)

11. Search for +++Storage Blob Data Reader+++, select it and click
    on **Next**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image24.png)

12. Click on **+Select members**, search for and select your **user
    id** +++@lab.CloudPortalCredential(User1).Username+++, select
    your **user id** that gets listed and then click on **Select**. This
    adds the Storage Blob Data Reader role to your user id.

    ![A screenshot of a group of people AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image25.png)

13. Select **Managed identity** and then select **+ Select members**.
    Select **Search service** under **Managed identity** and select
    the **docuemntstorexxxx** search service that gets listed.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image26.png)

14. Click on **Select** to select the search service.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image27.png)

15. Back in the Add role assignment screen, click on **Review +
    assign**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image28.png)

16. Select **Review + assign** again in the next screen.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image29.png)

17. Proceed to the next step once you receive a success message on role
    addition.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image30.png)

In this exercise, we have created a Storage account and added the
documents and required Role permissions to it.

## Exercise 3: Create an Azure OpenAI Service and deploy a model

The AI Search service will have to vectorize the data uploaded, in order
to perform the search over the documents. To vectorize the data, an
embedding model needs to be deployed. In this exercise, you will create
an Azure OpenAI Service and deploy the text-embedding model in it.

1.  From the Azure portal Home page, search for select +++Azure
    OpenAI+++.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image31.png)

2.  Select **+ Create -> Azure OpenAI**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image32.png)

3.  Enter the below details and select **Next**.

    - Subscription – @lab.CloudSubscription.Name

    - Resource group – @lab.CloudResourceGroup(ResourceGroup1).Name

    - Region – @lab.CloudResourceGroup(ResourceGroup1).Location
      
    - Name – +++openaiservice@lab.labinstance.id+++

    - Pricing tier – Select **Standard**

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image33.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image34.png)

4.  Select **Next** in the next 2 screens select **Create** in
    the **Review + submit** screen.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image35.png)

5.  Click on **Go to resource** once the service is created.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image36.png)

6.  Select **Access control (IAM)** from the left pane, select **Add -\>
    Add role assignment**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image37.png)

7.  Search for +++Cognitive Services OpenAI User+++, select the role
    and click on **Next**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image38.png)

8.  Select **+ Select members**, search for your **user
    id** +++@lab.CloudPortalCredential(User1).Username+++, select it
    and click on **Select**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image39.png)

9.  Back in the **Add role assignment** screen, select **Managed
    identity**. Then select **+ Select members**. In the **Select
    managed identities** screen, select **Search
    service** under **Managed identity** and select the resource that
    starts with **documentstore** service.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image40.png)

10. Once selected, click on **Select**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image41.png)

11. Select Review + assign in the next 2 screens.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image42.png)

12. Wait for a **success** message on the role additions before
    proceeding with the next tasks.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image43.png)

13. From the **Overview** page of the Azure OpenAI Service resource,
    select **Go to Foundry portal** to open the Azure OpenAI Service
    there and deploy a model.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image44.png)

14. Select **Deployments** from the left pane. Select **+ Deploy
    model** -\> **Deploy base model**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image45.png)

15. Search for +++text-embedding+++,
    select **text-embedding-3-large** and then select **Confirm**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image46.png)

16. Select **Deploy** in the Deploy text-embedding-3-large.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image47.png)

17. The model gets deployed and the screen is loaded with the deployment
    details.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image48.png)

## Exercise 4: Create a vector index

The AI Search resource needs a Vector index to perform the vector
search. You will vectorize the uploaded data in this exercise.

1.  From the Azure portal, go to the AI Search service resource that
    starts with **documentstore**. Select **Import data**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image149.png)

2.  Select the **Azure Blob Storage** option.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image50.png)

3.  Select the **RAG** option in the **What scenarios are you targeting?** screen.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image51.png)

4.  Enter the below details, accept the other values as default and
    click **Next**.

    - Subscription – @lab.CloudSubscription.Name

    - Storage account- Select the account that starts with **docstore**

    - Blob-container – Select **documents**

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image52.png)

5.  In the Vectorize your text screen, the subscription is
    pre-populated. Enter the below details and click **Next**.

    - Azure OpenAI resource – Select **openaiservice@Lab.LabInstance.ID**

    - Model deployment – Select **text-embedding-3-large**

    - Authentication type – Select **System assigned identity**

    - Select the checkbox to acknowledge the cost alert of Azure OpenAI.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image53.png)

6.  Select Next in the **Vectorize and enrich your images** screen since
    we are not dealing with images here and select **Next** in
    the **Advanced settings** screen as well.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image54.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image55.png)

7.  Select **Create** in the **Review + create** screen.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image56.png)

8.  Click on **Close** in the success dialog box.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image157.png)

**Exercise 5: Create a retail assistant agent**

In this exercise, you will create a retail assistant agent in Copilot
Studio.

1.  Login to
    +++https://copilotstudio.microsoft.com+++/ using
    your login credentials from the Resources tab and select **Get
    Started** to start the **Copilot Studio trial**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image1.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image58.png)

2.  Ensure that the **Configure** tab is selected in the Agent creation
    pane that is open now. Enter the below details and select Create.

    - Name - +++Retail assistant+++

    - Description - `You are a Retail assistant agent for customers HR
      who will answer questions related to the store products`

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image59.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image60.png)

3.  Once the agent is created, in the Test pane, enter +++What is the
    warranty period for Washing machine?+++ and click **Send.**

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image61.png)

4.  It gives a generalized reply as in the screenshot below.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image62.png)

## Exercise 6: Add the Azure AI Search as a knowledge source

In this exercise, you will add the Azure AI Search that you created from
the Azure portal, as a knowledge source to the Retail assistance agent
in Copilot Studio.

1.  From the **Overview** page of the agent, select **+ Add knowledge**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image63.png)

2.  Select **Azure AI Search** from the list of knowledge sources
    available.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image64.png)

3.  Click on the **drop down** next to **Not connected** in the next
    screen and select **Create new connection**.

    ![A screenshot of a search engine AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image65.png)

4.  Enter the **Endpoint url** and the **Admin key** values which we
    saved to a notepad in a previous exercise and then click
    on **Create** to create the connection.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image66.png)

5.  Once the connection is established, the available index is listed
    and already selected. Click on **Add to agent**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image67.png)

6.  The AI Search service is added as a knowledge source to the agent
    and is in **Ready** state now.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image68.png)

7.  Now, let us test the agent with the same question we have tried
    before.

8.  In the Test pane, enter +++ What is the warranty period for Washing
    machine?+++ and click **Send.**

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image69.png)

9.  You can see that the response from the agent now is from the
    document uploaded in the AI Search service.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image70.png)

## Exercise 7: Deploy a Model in Azure AI Foundry

In this exercise, you will deploy a model in the Azure AI Foundry to use
it in the Copilot Studio (in the next exercise).

1.  Open the Microsoft Foundry Azure OpenAI resource created earlier.

2.  From the left pane, select **Deployments**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image71.png)

3.  Select the drop down next to the **+ Deploy model** and
    select **Deploy base model**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image72.png)

4.  Select **gpt-4o** and select **Confirm**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image73.png)

5.  In the Deploy gpt-4o dialog, enter the **Deployment name** as
    +++ModelforMCS+++, accept the other defaults and
    select **Deploy.**

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image74.png)

6.  Copy the Target URI and key values to a notepad to be used during
    the connection creation from the Copilot Studio.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image75.png)

Now that the model is deployed, you can use it in Copilot Studio’s agent
prompt.

## Exercise 8: Create a prompt in the Copilot Studio and use the model created in Azure AI Foundry

In this exercise, you will learn how to bring the deployed model from
Azure AI Foundry in the Copilot Studio. Here, we are using a base model
that is deployed. We can also create a fine tuned model as per the
business requirements and then use it in Copilot Studio.

1.  From the Copilot Studio agent, select **Tools** from the top menu
    bar.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image76.png)

2.  Select **+ New tool** to add a new tool to the agent

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image77.png)

3.  Select Prompt since we are going to add a new prompt.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image78.png)

4.  In the Custom prompt screen, select the drop down next to
    the **model** name.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image79.png)

5.  Select + against **Azure AI Foundry Models** to add the model
    deployed in Azure AI Foundry and select **Connect a new model**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image80.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image81.png)

6.  Enter the below details and click on Connect.

    - Model deployment name - +++ModelforMCS+++

    - Base model name - +++gpt-4o+++

    - Azure model endpoint URL – Enter the target url saved earlier

    - API Key – Enter the model API key saved earlier.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image82.png)

    ![A screen shot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image83.png)

7.  Once connected, select **Close**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image84.png)

8.  You can see that the model ModelforMCS is selected now

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image85.png)

9.  Rename the prompt to +++WM Types+++. Enter +++What are the different
    types of Washing Machines?+++ and select **Test**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image86.png)

10. Select **Save** to save the prompt.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image87.png)

11. Select the **Add and configure** option to add the prompt to the
    agent.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image88.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%2011/media/image89.png)

With this feature, we can fine-tune the model in Microsoft Foundry and
use it in Copilot Studio with ease. We can bring in the vast ecosystem
of the models in the Azure AI Foundry easily into the Copilot Studio.

## Summary

In this lab, you created a knowledge-driven AI support agent by integrating Azure AI Search, Azure OpenAI, and Microsoft Copilot Studio. You started by uploading and indexing product documents, then enabled vector-based search using an embedding model to support accurate information retrieval.

You connected this knowledge base to a Copilot Studio agent, allowing it to answer customer queries with relevant, document-backed responses. Finally, you integrated a model from Azure AI Foundry and used it within a custom prompt to extend the agent’s capabilities.

This lab demonstrates how to build and connect the core components required for a RAG-based, enterprise-ready support solution.
