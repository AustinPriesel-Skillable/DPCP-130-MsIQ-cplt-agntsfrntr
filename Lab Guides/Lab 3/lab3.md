# Lab 3-Build the Zava Retail workforce upskilling Learning Agent with Microsoft 365 Copilot

**Estimated Duration:** 30 minutes

## Lab objectives

In this lab, you will explore how to build a Workforce Upskilling Agent using Microsoft 365 Copilot Agent Builder. You will learn how to configure the agent aligned to workforce transformation goals, ground it in organizational context using Work IQ principles, and enrich it with enterprise knowledge sources. By the end of this lab, you will be able to:
- Build a custom Workforce Upskilling Agent using Microsoft 365 Copilot
  Agent Builder

- Configure agent instructions aligned to retail workforce
  transformation goals

- Ground the agent in organizational context using Work IQ principles
- Add enterprise knowledge sources to improve agent relevance
- Diagnose employee skill gaps using operational behavior signals
- Generate personalized learning plans for multiple workforce personas
- Use the agent to simulate coaching conversations and leadership
  role-play

- Produce workforce readiness briefings for executive stakeholders


## Scenario

You are Jordan Mercer, Chief Operating Officer of Zava Retail — a mid-sized retail chain specializing in consumer electronics and home goods, operating across four regional store clusters in the Midwest. Zava Retail is eighteen months into a digital transformation initiative:
- A new Retail Management System (RMS) is being rolled out company-wide
- AI-powered inventory forecasting is active in two regional store
  clusters

- Customer behavior analytics tools are being adopted by store
  supervisors

- ERP migration completes next quarter


Technology adoption is accelerating faster than employee readiness. To address this challenge, you will build and deploy a Workforce Upskilling Agent that helps identify skill gaps, personalize employee learning journeys, and improve workforce readiness across operations.

### Key Personas

1. Jordan Mercer (COO – Primary Persona): Leads digital transformation strategy and oversees workforce capability planning.

1. Alex Chen (Store Operations Supervisor)- Frequently overrides AI inventory alerts without reviewing them.

1. Maria Santos (Supply Chain Analyst)- Leaving in 60 days with undocumented critical supplier knowledge.

1. Derek Okonkwo (Operations Coordinator)- Low RMS adoption despite extensive legacy systems experience.


## Exercise 1: Creating the Workforce Upskilling Agent

Before the agent can support workforce development, you must first build and configure it inside Microsoft 365 Copilot.

### Task 1: Open Agent Builder

1. Navigate to +++https://m365copilot.com/+++ to open Microsoft 365 copilot page. Sign in with your credentials.

    - Username - +++@lab.CloudPortalCredential(User1).Username+++
    - TAP Token - +++@lab.CloudPortalCredential(User1).AccessToken+++
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image100.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image101.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image102.png)


1. From the left navigation panel, click **More agents**, then click **Create Agent**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp1.png)

1. The **New Agent** page will be opened. Now click **Skip**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp2.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp3.png)


### Task 2: Define and Configure Agent

1. Paste the following details to define and configure the agent:

    **Agent Name**: +++Zava Retail Workforce Coach+++

    **Agent description**:

    `Supports workforce capability development by diagnosing skill gaps, generating personalized learning plans, and assisting leaders with workforce readiness decisions during digital transformation`
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/p5.png)

1. Paste the below given prompt in the field and then click on the **Execute** button.
  
    +++You are Zava Retail’s Workforce Coach. Your purpose is to help leaders identify workforce capability gaps, generate personalized learning plans, support coaching simulations, and recommend interventions during digital transformation. Focus on: - RMS adoption - AI inventory forecasting literacy - Customer analytics interpretation - Supply chain risk management - Change adoption coaching Always tailor recommendations based on: - Employee role - Operational urgency - Experience level - Retail store cluster context+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/p6.png)

1. In the Knowledge Sources, upload or connect the below mentioned organizational resources. Select **Upload from device** icon to upload the files. The required files for this lab are available at **C:\Lab Files\Lab 3 - Lab files**

    - RMS onboarding guide
    - AI inventory forecasting SOP
    - Store operations handbook
    - Supply chain transition playbook
    - ERP migration training documentation

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp4.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image306.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp5.png)


1. Click **Create** and then, select **Start Chat**.

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp6.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp7.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp8.png)


## Exercise 2: Grounding the Agent in Organizational Context

Once the agent is built, provide the transformation context of Zava Retail.

### Task 1: Initialize Agent Context

1. Paste the following prompt in the chat panel of Zava Retail Workforce Coach agent and click on the **Send** button.
  
    ```
    I am the COO of Zava Retail, a mid-sized retail chain specializing
    in consumer electronics and home goods, with 4 regional store clusters
    and approximately 600 employees across store operations, supply chain,
    customer experience, and merchandising.
    
    We are currently migrating to a new Retail Management System (RMS)
    and deploying AI-powered inventory forecasting and customer analytics
    tools.  

    Our key upskilling priorities are:  
    1. RMS system adoption
    2. AI inventory and analytics supervisory skills
    3. Supply chain risk management for mid-career analysts
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/pp9.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image311.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image312.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image313.png)

    >[!Note] AI-generated responses are non-deterministic and may vary across environments, sessions, and prompts.


### Task 2: Validate Agent Understanding

1. To test the agent, enter the following prompt and click on the **Send** button.
  
    +++What are the most critical workforce skill domains I should prioritize during this retail digital transformation?+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image314.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image315.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image316.png)

    >[!Note] AI-generated responses are non-deterministic and may vary across environments, sessions, and prompts.


## Exercise 3: Diagnosing Workforce Skill Gaps

### Task 1: Diagnose Alex Chen

1. Paste the following prompt and click on the **Send** button to diagnose workforce skills gaps:

    ```
    I have a Store Operations Supervisor named Alex who is consistently
    overriding AI-powered inventory replenishment alerts without reviewing
    them — approximately 3 times per week over the past month. Based on this behavioral signal, what skill gaps should I hypothesize, and what targeted learning plan should I create? 
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image317.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image318.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image319.png)


### Task 2: Diagnose Maria Santos

1. Paste the following prompt and click on the **Send** button to diagnose workforce skills gaps:

    +++One of our supply chain analysts, Maria, is leaving in 60 days. She owns four sole-source supplier relationships with no documented handover process. What urgent learning and knowledge transfer plan should I implement?+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image320.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image321.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image322.png)


### Task 3: Diagnose Derek Okonkwo

1. Paste the following prompt to diagnose workforce skills gaps:

    +++Our RMS went live 6 months ago. Derek is at 31% system utilization — lowest on his team. He has 11 years of legacy system experience. What resistance patterns and skill gaps should I address?+++
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image323.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image324.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image325.png)


## Exercise 4: Generating Personalized Learning Plans

### Task 1: Generate Alex’s 6-Week Plan

1. To generate plan for Alex, paste the following prompt and click on the **Send** button.
  
    ```
    Generate a structured 6-week learning plan for Alex with: 
    - Learning objectives
    - Weekly activities 
    - Resources 
    - Checkpoints
    - Success metrics
    ```
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image326.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image327.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image328.png)


### Task 2: Maria’s 60-Day Transition Plan

1. To generate plan for Maria, paste the following prompt:

    +++Generate a 60-day knowledge transfer and upskilling plan for Maria’s transition scenario. Include parallel tracks for: 1. Knowledge transfer 2. Analyst upskilling+++

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image329.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image330.png)


### Task 3: Derek’s RMS Adoption Plan

1. To generate plan for Derek, paste the following prompt and select **Send** button.

    `Create an 8-week adoption-focused learning plan for Derek that positions RMS mastery as a career growth opportunity.`

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image331.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image332.png)


## Exercise 5: Workforce Readiness Briefing

### Task 1: Generate Executive Briefing

1. To test the workforce readiness and generate a briefing plan, paste the below prompt, and click on the **Send** button.

    +++Generate a workforce readiness briefing for Zava Retail covering: 1. Current risk summary 2. Intervention status 3. What I need from Store Managers 4. 30-day watch list+++
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image333.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image334.png)


### Task 2: Tailor for VP of HR

1. To test the workforce readiness and generate a summary for the VP, paste the below prompt and click on the **Send** button.

    +++Condense this into a 5-bullet summary for my VP of HR focused only on HR action items.+++
  
    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image335.png)

1. Review the output:

    ![](https://raw.githubusercontent.com/technofocus-pte/MsIQ-cplt-agntsfrntr/refs/heads/main/Lab%20Guides/Lab%203/media/image336.png)


## Summary

In this lab, you built a custom Workforce Upskilling Agent in Microsoft 365 Copilot designed to support retail workforce transformation. You configured the agent’s behavior to align with workforce development goals, grounded it in organizational context for more relevant and accurate responses, and used operational signals to diagnose workforce skill gaps. The lab also guided you through generating personalized learning plans tailored to employee needs, refining agent responses through prompt engineering for improved effectiveness, and producing workforce readiness briefings to support decision-making and training strategy.
