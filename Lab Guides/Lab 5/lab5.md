# Streamline Zava Retail Calendar Management with Microsoft 365 Copilot Cowork

#### Estimate duration: 60 mins

## Scenario

Zava Retail is a growing SMB omnichannel retailer with 12 physical
stores and a successful online business. To support its continued
growth, the company is preparing to open two new stores in neighbouring
cities during the next quarter — its first regional expansion.

The expansion requires close coordination across Store Operations,
Procurement, IT, Marketing, and HR to ensure both stores are ready to
open on schedule.

As the Expansion Program Lead, Alex Morgan is responsible for
coordinating all project activities and keeping stakeholders aligned.
With multiple departments requesting meetings, the calendar has become
increasingly difficult to manage.

Current challenges include:

- Conflicting meeting requests from different departments

- Back-to-back meetings with little preparation time

- No protected focus time for strategic planning and project
  documentation

- Meetings scheduled without agendas

- Difficulty finding suitable meeting times for key stakeholders

To help keep the expansion on track, Zava Retail has adopted Microsoft
365 Copilot Cowork. Alex will use Cowork as an AI-powered executive
assistant to manage the calendar, resolve scheduling conflicts,
intelligently coordinate meetings, and protect time for high-value
strategic work.

## Objectives

During this lab, you will use **Microsoft 365 Copilot Cowork** to:

 **Detect and resolve calendar conflicts** — identify overlapping
meetings and back-to-back scheduling, and act on AI-recommended fixes.

 **Schedule meetings intelligently** — book meetings around attendee
availability, preferences, and context from prior emails.

 **Protect focus time** — apply standing rules like minimum notice
periods and protected focus blocks.

 **Stay in control of AI-driven changes** — review and approve every
action before it's applied.

## Key Personas

- **Alex Morgan – Expansion Program Lead (Learner):** Coordinates the
  entire store expansion program and relies on Copilot Cowork to
  organize meetings, reduce calendar overload, and protect focus time.

- **Rachel Singh – Operations Director:** Executive sponsor for the
  expansion who requires meetings to be scheduled at least 48 hours in
  advance with a clear agenda.

- **Tom Bradley – Store Operations Manager:** Frequently schedules
  operational meetings at short notice, often without an agenda, making
  calendar management more challenging.

- **Lisa Chen – Procurement & Supply Chain Manager:** Works closely with
  Alex to coordinate supplier onboarding and inventory deliveries. Their
  weekly project sync must be scheduled while respecting both calendars
  and meeting constraints.

## Exercise 1: Access Cowork Agent

In this exercise, you need to sign in to Microsoft 365 Copilot as Alex
Morgan and turn on the Cowork agent. This exercise gets your environment
ready for the rest of the lab.

1.  Open a **web browser** and navigate to +++https://m365.cloud.microsoft/chat/+++.

2.  Sign in with your Microsoft 365 Copilot account credentials.

    - Username - <+++@lab.CloudPortalCredential>(User1).Username+++

    - TAP Token - <+++@lab.CloudPortalCredential(User1).AccessToken>+++

    ![](./media/image1.png)
    
    ![](./media/image2.png)

3.  When prompted to stay signed in, select **Yes**.
    ![](./media/image3.png)

4.  From the left navigation menu, enable **Cowork.**

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image4.png)

5.  Cowork is now active and ready to use as your calendar assistant for
    the rest of this lab.

    ![](./media/image5.png)

## Exercise 2: Populate Your Calendar with Sample Expansion Meetings

Before Cowork can help you manage conflicts and priorities, your
calendar needs some real meetings to work with. In this exercise, you'll
use a single prompt to generate a week's worth of expansion-related
meetings — including a few that are deliberately missing agendas, so you
can see how Cowork flags that gap later in the lab.

### Task 1 – Create Sample Meetings Using Copilot Cowork

In this task, you enter a one-shot prompt that asks Cowork to create
eight realistic expansion meetings on your calendar, including two with
no agenda so you can test agenda-detection later.

1.  Enter the following prompt in the Cowork prompt field, then select
    **Send**:

    ```

    Act as my calendar assistant. I am Alex Morgan, Expansion Program

    Lead at Zava Retail. We are coordinating the opening of two new

    stores next quarter. Please create the following 8 meetings in my

    calendar for next week.

    Important: For meetings 7 and 8, leave the description and body

    completely empty — no agenda text at all.

    1. "Store Expansion Kickoff — Operations Review"

    Monday, 10:00–11:00 AM

    Organiser: Tom Bradley (Store Operations Manager)

    2. "New Store IT Infrastructure Briefing"

    Monday, 10:30–11:30 AM

    Organiser: IT Team

    3. "Supplier Onboarding Planning — City Store 1"

    Tuesday, 9:00–10:00 AM

    Organiser: Lisa Chen (Procurement & Supply Chain Manager)

    4. "Inventory & Delivery Schedule Review"

    Tuesday, 10:00–11:00 AM

    Organiser: Lisa Chen (Procurement & Supply Chain Manager)

    5. "Marketing Campaign Kickoff — Grand Opening"

    Tuesday, 11:00 AM–12:00 PM

    Organiser: Marketing Team

    6. "HR Recruitment Drive — Store Staffing Update"

    Wednesday, 8:00–9:00 AM

    Organiser: HR Team

    7. "Store Operations Weekly Check-in"

    Thursday, 2:00–3:00 PM

    Organiser: Tom Bradley (Store Operations Manager)

    (NO description, NO agenda — leave body completely blank)

    8. "Expansion Progress Review — Leadership Update"

    Friday, 11:00 AM–12:00 PM

    Organiser: Rachel Singh (Operations Director)

    (NO description, NO agenda — leave body completely blank)

    Please create all 8 meetings and confirm when done.
    ```

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image6.png)

2.  Cowork will ask for your approval before creating each event
    individually. Select **Send** to approve each meeting creation
    request.
    
    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image7.png)

    **Note:** All eight meetings will be created one at a time, and you'll
    receive a separate approval prompt for each. Review each request before
    approving — this is your chance to confirm exactly what Cowork is about
    to add to your calendar.

    ![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image8.png)

### Task 2: Verify the Meeting

Confirm that all eight meetings actually landed on your calendar by
checking the Teams calendar view.

1.  Open the **App Launcher** from the left navigation bar and select
    **Teams**.
    
    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image9.png)

2. In Teams, select **Calendar** from the left navigation to view all
eight newly created meetings.

    ![A screenshot of a calendar AI-generated content may be incorrect.](./media/image10.png)

## Exercise 3: Detect and Resolve Calendar Conflicts

Use Copilot Cowork to identify overlapping meetings and unbroken meeting
runs on your calendar, then apply AI-recommended resolutions with your
approval. By the end of this exercise, you'll have resolved two
scheduling conflicts, drafted the related reschedule communications, and
reviewed a calendar health summary for the week.

### Task 1 – Scan the Calendar and Prioritize Conflicts

Ask Cowork to review the next five business days, flag every overlap and
back-to-back run, and propose fixes — while protecting the two meetings
Lisa Chen has already confirmed.

1.  Select **New Task**.

    ![](./media/image11.png)

2.  Enter the following prompt and select **Send**:

    ```

    I am Alex Morgan, Expansion Program Lead at Zava Retail. We are

    currently coordinating the opening of two new stores in neighbouring

    cities next quarter.

    Scan my calendar for the next 5 business days and do the following:

    1. List every scheduling conflict where two or more meetings overlap

    2. Identify any back-to-back runs of 3 or more consecutive meetings

    with no break between them

    3. For each conflict or back-to-back run, propose a resolution:

    — Which meeting should be moved and why

    — The best alternative time slot that avoids other meetings

    — A polite and professional reschedule message I can send to

    the organiser

    Priority: Keep the Supplier Onboarding Planning and Inventory &

    Delivery Schedule Review meetings in their current slots if possible,

    as Lisa Chen has confirmed her availability for those times.

    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image12.png)

3.  Cowork returns a full conflict report, including the Monday overlap
    and the Tuesday back-to-back run, with suggested resolutions for
    each.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image13.png)

    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image14.png)

    ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image15.png)

    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image16.png)

    ![A
    screenshot of a email AI-generated content may be
    incorrect.](./media/image17.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image18.png)

### Task 2 – Resolve the Monday Conflict

Act on Cowork's recommendation for the overlapping Monday meetings: move
the IT briefing and draft a reschedule note, without disturbing the
higher-priority Operations Review.

1.  With the conflicts identified, ask Cowork to resolve the Monday
    overlap between the Store Expansion Kickoff and the IT
    Infrastructure Briefing. Enter the following prompt and select
    **Send**:

    ```

    For the Monday conflict between the Store Expansion Kickoff —

    Operations Review and the New Store IT Infrastructure Briefing,

    please do the following:

    1. Move the IT Infrastructure Briefing to the next available

    morning slot this week that does not clash with any other

    expansion meetings

    2. Draft a professional reschedule message to the IT Team explaining

    the conflict and proposing the new time

    3. Keep the tone collaborative — mention that the Store Expansion

    Kickoff with Tom Bradley takes priority as it covers operational

    readiness for both new store locations

    ```

    ![](./media/image19.png)

2. Select **Update** to approve the rescheduled IT Infrastructure
Briefing.

    ![A screenshot of a chat AI-generated content may be
    incorrect.](./media/image20.png)

3. Cowork confirms the new time and shares the drafted reschedule
message.

    ![](./media/image21.png)![A screenshot of a chat AI-generated content
    may be incorrect.](./media/image22.png)

### Task 3 – Resolve the Tuesday Back-to-Back Run

Fix the three-meeting Tuesday run by adding prep breaks, keeping Lisa
Chen's confirmed slot untouched, and shifting the Marketing kickoff if
needed.

1.  In the same thread, ask Cowork to fix the Tuesday back-to-back run.
    Enter the following prompt and select **Send**:

    ```

    For the three back-to-back meetings on Tuesday — Supplier

    Onboarding Planning, Inventory & Delivery Schedule Review, and

    Marketing Campaign Kickoff — please do the following:

    1. Keep the Supplier Onboarding Planning at 9:00 AM as Lisa Chen

    has confirmed her availability

    2. Add a 15-minute preparation break between each meeting

    3. Suggest which meeting is the best candidate to move to a

    later slot if a break cannot be inserted without causing

    further conflicts

    4. Draft a brief note to the Marketing Team explaining that

    their Campaign Kickoff may need to shift by 30 minutes to

    allow preparation time between sessions

    ```

    ![](./media/image23.png)

2.  Cowork proposes the adjusted schedule and a draft note to the
    Marketing Team..

    ![](./media/image24.png)
    
    ![](./media/image25.png)
    
    ![](./media/image26.png)

3.  Confirm the changes by entering the following prompt:

    ```

    Please apply these schedule changes to the calendar. Then create the
    email as a draft in Outlook — don't send it — so I can review it
    first.

    ```

4.  Select **Update** to apply the changes to the calendar.

    ![](./media/image27.png)
    
    ![](./media/image28.png)

5. Cowork confirms the calendar has been updated and the email has been
saved as a draft.

    ![A screenshot of a computer AI-generated content may
    be incorrect.](./media/image29.png)

    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image30.png)

6. To review the draft email, open the **App Launcher** and select
**Outlook** (or use the direct draft link Cowork provides).

    ![](./media/image31.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image32.png)  
7. Review the draft email.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image33.png)

8. Navigate back to Teams and refresh the window to view the changes.

    ![A screenshot of a calendar AI-generated content may be
    incorrect.](./media/image34.png)

### Task 4 – Get a Calendar Health Summary

Wrap up the exercise with an at-a-glance summary of meeting load for the
week, plus a recommendation for when to block time for the Master
Expansion Plan.

1.  Request a summary of the week's calendar health:

    ```

    Now give me a Calendar Health summary for this week's expansion

    meetings. Include:

    1. Total number of meetings and total meeting hours this week

    2. Any days that are overloaded with meetings

    3. Days that have good availability for focused strategic work

    4. One recommendation for when I should block time to work on

    the Master Expansion Plan document — considering all the

    meetings we have just resolved

    Keep the summary concise and actionable.

    ```

    ![](./media/image35.png)

2.  Cowork returns a concise summary of meeting load, overloaded days,
    and a recommended time to block for focused work.

    ![A screenshot of a calendar AI-generated content may be
    incorrect.](./media/image36.png)

    ![A screenshot of a email AI-generated
    content may be incorrect.](./media/image37.png)

## Exercise 4: Schedule Meetings Intelligently Using Email Context

Real scheduling requests rarely come with a full brief attached — often
the context lives in an email thread. In this exercise, you'll send
yourself a sample email about supplier onboarding, then ask Cowork to
use that context to intelligently schedule a recurring sync with Lisa
Chen, complete with a Teams link and a draft agenda.

### Task 1 – Send a Sample Context Email

Send yourself a short email about supplier onboarding so Cowork has real
context to draw on when it drafts the meeting agenda.

1.  Navigate to **C:\Lab Files\Cowork** folder and open the
    coworkSampleEmail file get the sample email for this lab.

2.  Send a sample email about supplier onboarding to the current user
    using your personal email address.

3.  Verify the email has arrived in your inbox.

    ![A screenshot of a
        computer AI-generated content may be
        incorrect.](./media/image38.png)

### Task 2 – Schedule the Weekly Project Sync

Ask Cowork to book a 30-minute sync with Lisa Chen, applying scheduling
constraints and pulling talking points straight from the email you just
sent.

1.  Select New task.

    ![](./media/image39.png)

2.  Enter the following prompt and select **Send**:

    ```

    Schedule a 30-minute 'Weekly Project Sync' with Lisa Chen next week.
    Constraints: not Monday, not within 30 minutes of either of our
    existing meetings, prefer mornings, and add a Teams link and a draft
    agenda with 3 talking points based on our recent email thread about
    supplier onboarding.

    ```

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image40.png)

3.  Cowork reviews the supplier onboarding email you sent to build the
    agenda talking points. 
    
    ![A screenshot of a chat AI-generated content
    may be incorrect.](./media/image41.png)

4.  When prompted, confirm that Cowork should send the meeting invite.

    ![](./media/image42.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image43.png)

5.  Open the Teams calendar to verify the Weekly Project Sync was
    created.

    ![](./media/image44.png)

    ![](./media/image45.png)

6.  Check the personal email address you used earlier — you should
    receive a meeting request for the newly scheduled sync..

    ![A screenshot of a mail AI-generated content may be
    incorrect.](./media/image46.png)

## Exercise 5: Apply Executive Calendar Management Rules

In this exercise, you'll move from one-off fixes to standing rules — the
kind of protections a real executive assistant would maintain
automatically. You'll set up a minimum-notice rule and a protected daily
focus block, test the notice rule against a real short-notice request,
and finish with an executive summary confirming everything is on track.

### Task 1 – Define Standing Calendar Rules

Set up two ongoing rules: flag any meeting requested with less than 48
hours' notice, and protect a 90-minute daily focus block for the Master
Expansion Plan.

1.  Select **New task**.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image47.png)

2.  Enter the following prompt in the prompt field and click the Send
    button to execute the prompt:

    ```

    I want to apply two standing rules to my calendar going forward: (1)
    Any meeting requested with less than 48 hours' notice should be
    flagged, and I should be prompted before accepting — this is Rachel
    Singh's requirement as Operations Director. (2) Protect a daily
    90-minute focus block each morning this week for the Master Expansion
    Plan document — no meetings should be scheduled over it without my
    explicit approval. Show me what this looks like on my calendar before
    making any changes.

    ```

    ![](./media/image48.png)

3.  Cowork walks you through how it plans to apply both rules before
    touching your calendar.

    **Note:** Cowork's responses are AI-generated, so exact wording may vary
    from what's shown here.

    ![](./media/image49.png)

    ![A screenshot of a chat AI-generated content may be
    incorrect.](./media/image50.png)

4.  Review each clarifying prompt Cowork presents as it works through
    the setup.

    ![](./media/image51.png)

5.  Cowork will show you how the focus blocks look on your calendar
    across the week. Click **Send**.
    
    ![A screenshot of a computer
    AI-generated content may be incorrect.](./media/image52.png)
    
    ![A
    screenshot of a computer AI-generated content may be
    incorrect.](./media/image53.png)

6.  Select **Schedule** to confirm the recurring focus block
    task.
    
    ![](./media/image54.png)

7.  Cowork confirms both standing rules — the 48-hour notice flag and
    the protected focus blocks — are now
    active.
    
    ![](./media/image55.png)
    
    ![](./media/image56.png)

### Task 2 – Test the 48-Hour Notice Rule

Simulate a real short-notice request from Tom Bradley to confirm the new
notice rule actually triggers as expected.

1.  Enter the following prompt to test the rule you just created, then
    select **Send**:

    ```

    Tom Bradley just messaged asking for a 30-minute call tomorrow morning
    to discuss a staffing issue at City Store 1 — no agenda given. Can you
    find time?

    ```

    ![](./media/image57.png)

2.  Cowork flags the request as short-notice and asks for your
    permission before proceeding.
    
    ![](./media/image58.png)

3.  Review and approve the proposed meeting slot when
    prompted.
    
    ![](./media/image59.png)

    ![](./media/image60.png)

### Task 3 – Get an Executive Summary

As Expansion Program Lead, Alex needs a final status check before facing
Rachel Singh on Friday. Ask Cowork to confirm focus time is protected,
flag any meetings still missing an agenda, and verify Alex is on track
for the Leadership Update.

1.  Enter the following prompt in the prompt field and click the
    **Send** button to execute the prompt:

    ```

    Give me an executive summary of my calendar for the rest of this week:
    confirm my focus blocks are protected, flag any meetings that still
    don't have an agenda, and tell me if I'm on track to have
    uninterrupted time to finish the Master Expansion Plan before Friday's
    Leadership Update with Rachel Singh.

    ```

    ![](./media/image61.png)

2.  Cowork returns an executive summary confirming your protected focus
    time, any meetings still missing an agenda, and whether you're on
    track for Friday's Leadership
    Update.
    
    ![](./media/image62.png)
    
    ![](./media/image63.png)

## Summary

In this lab, you used Microsoft 365 Copilot Cowork as an AI-powered
executive assistant to manage Alex Morgan's calendar during a store
expansion program — detecting and resolving scheduling conflicts,
scheduling a meeting using email context, and setting up standing rules
to protect focus time, all with your approval at each step.

By the end of this lab, you should be able to:

- Detect and resolve calendar conflicts using natural-language prompts

- Schedule meetings that respect business constraints and stakeholder
  context

- Set up standing rules to protect focus time and enforce notice
  requirements

- Review and approve AI-generated calendar and email actions before
  they're applied
