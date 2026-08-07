# Lab 6 - Build an Enterprise Marketing Operations Agent with Microsoft 365 Copilot

Estimated duration: 40 minutes

# Scenario

Zava Retail is a growing SMB omnichannel retailer with 12 physical
stores and a successful online business. Its marketing team runs
frequent, multi-channel campaigns — seasonal sales, product launches,
loyalty promotions — but has no consistent, repeatable way to plan them.

Every campaign brief looks different depending on who wrote it. Creative
assets for email, social, SMS, and in-store signage are produced
separately by different people, often inconsistent in tone and
messaging. Executives receive campaign summaries in varying formats,
which slows down approvals. And when a campaign needs to be adapted —
for loyalty members, for a premium audience, or for different store
regions — the team frequently starts over instead of building on the
original plan.

As Marketing Operations Lead, Priya Nair is responsible for how
campaigns move from idea to execution to executive sign-off. With a
Summer Clearance campaign due for leadership approval by the end of the
week, Priya needs a faster, more consistent way to plan the campaign,
produce channel-ready assets, adapt it for different audiences and
regions, and package it for executive review.

To solve this, Zava Retail has adopted Microsoft 365 Copilot Chat. Priya
will build a reusable custom agent — the Zava Retail Marketing
Operations Advisor — that plans campaigns to a consistent enterprise
structure, generates creative assets, adapts content for different
audiences and channels, and prepares executive-ready summaries.

# Objectives

During this lab, you will use Microsoft 365 Copilot Chat to:

- Create a custom Copilot agent — build a dedicated marketing operations
  assistant from scratch with a defined name and purpose.

- Configure enterprise-grade instructions — enforce a consistent,
  complete campaign structure and enable image generation and web
  search.

- Generate a structured campaign brief and creative assets — produce a
  complete campaign plan and a promotional banner from a single prompt.

- Adapt campaigns for different audiences, channels, and regions —
  refine content while preserving the original objective and KPIs.

- Prepare and validate an executive approval package — produce
  leadership-ready materials and confirm the agent works reliably for
  the whole team.

# Key Personas

- **Priya Nair – Marketing Operations Lead (Learner):** Owns campaign
  planning and execution at Zava Retail and builds the Copilot agent to
  standardize campaign briefs, creative assets, and executive reporting.

- **David Kim – VP of Marketing:** Executive sponsor for the Summer
  Clearance campaign who requires every campaign brief to include an
  executive summary, KPIs, and clearly flagged risks and assumptions
  before he will approve it.

- **Sam Osei – Creative Director:** Leads the creative team and needs
  channel-ready first-draft copy and imagery across email, social, SMS,
  and in-store signage so designers and copywriters aren't starting from
  a blank page.

- **Regional Store Directors – North, South, Urban, Rural:** Require the
  same campaign to be adapted to local context — timing, product
  emphasis, and preferred channels — without changing the underlying
  campaign objective.

# Exercise 1: Create and Configure the Marketing Operations Agent

In this exercise, you will sign in to Microsoft 365 Copilot Chat as
Priya Nair and create a new custom agent from scratch. This exercise
gets your environment ready for the rest of the lab.

## Task 1 – Sign In to Microsoft 365 Copilot Chat

1.  Open a web browser and navigate to +++https://m365.cloud.microsoft/chat/+++.

2.  Sign in with your Microsoft 365 Copilot account credentials.

    - Username - @lab.CloudPortalCredential(User1).Username

    - TAP Token - @lab.CloudPortalCredential(User1).AccessToken

    ![](./media/image1.png)

    ![](./media/image2.png)

3.  When prompted to stay signed in, select Yes.

    ![](./media/image3.png)

## Task 2 – Create the Agent

1.  From the left navigation menu, select **New agent**.

    ![](./media/image4.png)

2.  Select **skip to configure**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image5.png)

3.  Enter the agent's identity:

    - Name: Campaign Planning Assistant

    - Description: Enterprise AI assistant for planning and executing
      retail marketing campaigns.

    - Instruction: Enter the following instruction:

    ```
    You are the Campaign Planning Assistant, an enterprise AI
    assistant that supports the Zava Retail marketing team in planning,
    creating and preparing multi-channel marketing campaigns for the executive
    approval.
    
    ROLE AND SCOPE
    - Act as a marketing operations strategist and creative producer.
    - Support campaign planning, audience segmentation, channel adaptation,
      regional localization, and executive reporting for retail marketing
      initiatives.
    - Stay within marketing, brand, and campaign operations topics. Politely
      decline requests unrelated to marketing operations.
    
    RESPONSE REQUIREMENTS
    Every campaign-related response must include the following sections,
    clearly labelled:
    1. Campaign Objective
    2. Target Audience
    3. Key Messaging
    4. Channels
    5. Timeline
    6. KPIs (Key Performance Indicators)
    7. Risks and Assumptions
    8. Executive Summary (3-5 sentences, written for a VP-level audience)
    9. Creative Assets (descriptions and, where requested, generated images)
    
    STYLE AND TONE
    - Professional, concise, and action-oriented.
    - Default to Zava Retail's brand voice: confident, customer-first,
      optimistic, and inclusive.
    - Avoid unsubstantiated claims; flag assumptions explicitly.
    
    BRAND GUARDRAILS
    - Do not fabricate pricing, legal disclaimers, or discount terms beyond
      what the user specifies.
    - Do not generate content that disparages competitors by name.
    - Always mark placeholder data (e.g., dates, budgets) clearly as
      [PLACEHOLDER] if not provided by the user.
    
    WHEN ASKED TO ADAPT CONTENT
    - Preserve the original campaign objective and core value proposition
      unless explicitly told to change them.
    - Clearly state what was changed and why when adapting for a new
      audience, channel, or region.
    
    WHEN ASKED FOR EXECUTIVE MATERIALS
    - Prioritize brevity, business impact, and risk visibility.
    - Use structured, scannable formatting (headers, bullet points, short
      paragraphs).
    ```

    ![](./media/image6.png)

## Task 3 – Add knowledge Source

1.  Move to the Knowledge section and upload the files present at

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image7.png)

## Task 4 – Enable Capabilities

1.  Scroll down and navigate to the **Capabilities** section. Make sure
    the **Create images** capability is enabled.

    ![](./media/image8.png)

2.  Click **Create** to publish the agent.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image9.png)

3.  Select **Go to agent**.

    ![](./media/image10.png)

    Now the agent is ready to use.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image11.png)

# Exercise 2: Build the Summer Clearance Campaign Brief

David Kim has asked Priya for a complete campaign plan for the Summer
Clearance event before he'll consider it for approval. In this exercise,
you will test whether a single prompt produces a complete, structured
campaign brief.

## Task 1 – Generate the Campaign Brief

1.  Open a chat with the Zava Retail Marketing Operations Advisor.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image11.png)

2.  Enter the following prompt, then select **Send**:

    ```
    Create a complete Summer Clearance campaign (up to 50% off apparel)
    with the full 9-section structure, and generate (render, don't just
    describe) a hero banner image for the Creative Assets section that
    reflects the offer and Zava Retail's brand voice.
    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image12.png)

3.  Confirm the Creative Assets section includes a promotional banner
    concept, and that an image has been generated if Image Generation is
    enabled.

    ![A screenshot of a advertisement AI-generated content may be
    incorrect.](./media/image13.png)

    **Note:** Generated outputs are non-deterministic and may vary across users,
    sessions, and environments.

4.  Review the response and confirm it includes all nine required
    sections: Campaign Objective, Target Audience, Key Messaging,
    Channels, Timeline, KPIs, Risks and Assumptions, Executive Summary,
    and Creative Assets.

    ![A screenshot of a campaign objective AI-generated content may be
    incorrect.](./media/image14.png)

    ![A close-up of a website AI-generated
    content may be incorrect.](./media/image15.png)

    ![A screenshot of a email AI-generated content may be
    incorrect.](./media/image16.png)

    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image17.png)

    ![A screenshot of a white page AI-generated content may be
    incorrect.](./media/image18.png)
    ![A screenshot of a computer screen
    AI-generated content may be incorrect.](./media/image19.png)
    ![A screenshot of a computer screen AI-generated content may be
    incorrect.](./media/image20.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image21.png)
    ![A screenshot of a web page
    AI-generated content may be incorrect.](./media/image22.png)

    **Note:** Generated outputs are non-deterministic and may vary across users,
    sessions, and environments.

# Exercise 3: Generate Multi-channel Campaign Assets

Sam Osei's creative team needs a running start across every channel, not
just the core brief. In this exercise, you will ask the agent to
translate the Summer Clearance campaign into channel-ready assets for
seven distinct formats in a single request.

## Task 1 – Generate Channel Assets

1.  In the same conversation as Exercise 2 (to preserve campaign
    context), enter the following prompt, then select Send:

    ```
    Generate assets for this campaign across the following channels: Email,
    Teams announcement, LinkedIn, Instagram, Facebook, SMS, and in-store
    digital signage. For each channel, provide the copy, tone adjustments,
    and any format-specific notes (e.g., character limits, image aspect
    ratio).
    
    ```
    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image23.png)

2.  Review each of the seven channel outputs and confirm they are
    adapted to the channel.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image24.png)

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image25.png)

    ![A screenshot of a web page AI-generated content may be
    incorrect.](./media/image26.png)

    ![](./media/image27.png)![A screenshot of a email campaign AI-generated content may be
    incorrect.](./media/image28.png)

## Task 2 – Generate a Promotional Image

1.  Enter the following prompt, then select Send:

    ```
    Generate a promotional image for the Instagram post that matches the
    Summer Clearance campaign's messaging and Zava Retail's brand voice.
    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image29.png)

2.  Confirm that an image is generated and visually consistent with the
    campaign messaging.

    ![](./media/image30.png)

# Exercise 4: Refine the Campaign for Loyalty Members

David Kim has a follow-up request: loyalty program members shouldn't
receive the same “everything must go” clearance messaging as everyone
else — they should feel like they're getting early, exclusive access. In
this exercise, you will refine the existing campaign without starting
over.

## Task 1 – Refine for Audience and Brand Tone

1.  In the same conversation, enter the following prompt, then select
    Send:

    ```
    Refine this campaign for loyalty program members, with a more premium
    brand feel. Preserve the original campaign objective and KPIs, but
    adjust messaging, tone, and offer framing accordingly.
    ```
    ![](./media/image31.png)

2.  Review the response and confirm it explicitly states:

    - What changed (e.g., messaging shifted from “clearance” to “exclusive
      loyalty access”)

    - What was preserved (objective, KPIs, timeline)

3.  Confirm the tone reads as more premium — word choice, pacing, and
    framing should feel distinct from the original mass-market version.

    ![](./media/image32.png)

    ![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image33.png)

    ![](./media/image34.png)

# Exercise 5: Adapt the Campaign for Regional Stores

Zava Retail's regional store directors have flagged that a single
national message doesn't land the same way in every market. In this
exercise, you will generate four regional versions of the same campaign.

## Task 1 – Generate Regional Variants

1.  In the same conversation, enter the following prompt, then select
    Send:

    ```
    Create four regional versions of this campaign for: North stores, South
    stores, Urban stores, and Rural stores. Highlight any differences in
    messaging, product mix emphasis, or channel priority for each version,
    while keeping the core campaign objective identical.
    ```

    ![](./media/image35.png)

2.  Review each of the four versions and confirm:

    - Each has a distinct regional angle (e.g., Urban emphasizes foot
      traffic and digital signage; Rural emphasizes SMS and local relevance)

    - All four versions stay consistent with the original campaign objective
      and KPIs

    - There are no contradictory claims between versions

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image36.png)

    ![A screenshot of a web page
    AI-generated content may be incorrect.](./media/image37.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image38.png)

    ![A screenshot of a white screen
    AI-generated content may be incorrect.](./media/image39.png)

# Exercise 7: Prepare the Executive Approval Package

David Kim has one rule for Friday's leadership review: every campaign
pitch must be scannable in under two minutes. In this exercise, you will
generate a complete executive approval package from the campaign you've
built.

## Task 1 – Generate the Executive Approval Package

3.  In the same conversation, enter the following prompt, then select
    Send:

    ```
    Prepare an executive approval package for this campaign, including:
    - Executive summary
    - Expected business impact
    - Campaign risks
    - Assumptions
    - Success metrics
    - Approval checklist
    ```

  ![A screenshot of a computer AI-generated content may be
  incorrect.](./media/image40.png)

4.  Review the response, it must cover the following points:

    - Executive Summary: 3–5 sentence overview for a VP-level decision-maker

    - Expected Business Impact: quantified or directional impact (revenue,
      traffic, engagement)

    - Campaign Risks: realistic risks (e.g., inventory shortfall, message
      fatigue, timing conflicts)

    - Assumptions: explicitly flagged placeholders (budget, dates, inventory
      levels)

    - Success Metrics: tied back to the KPIs from Exercise 3

    - Approval Checklist: actionable items (e.g., Legal review, Brand
      review, Budget sign-off, Channel scheduling confirmed)

    ![A screenshot of a white and black page AI-generated content may be
    incorrect.](./media/image41.png)

    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image42.png)

    ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image43.png)

# Summary

In this lab, you used Microsoft 365 Copilot Chat to build a custom
marketing operations agent for Zava Retail — configuring enterprise
instructions that enforce a consistent campaign structure, generating a
full campaign brief and multi-channel creative assets, refining the
campaign for a premium loyalty audience, adapting it across four store
regions, and packaging it for executive approval, before publishing it
for the wider marketing team.

By the end of this lab, you should be able to:

- Create a custom Microsoft 365 Copilot Chat agent and configure
  enterprise-grade instructions

- Generate a structured campaign brief and creative assets, including
  generated images

- Refine and adapt a campaign for different audiences, channels, and
  regions while preserving the original objective and KPIs

- Prepare a leadership-ready executive approval package
