# SidelineReel Product Manager Assessment — Ajaia
**Candidate Submission Document by Ravinder Kumar, Sr. Product Manager** 
**Video Walkthrough & Defense:** 
**Portfolio / Public Work:** [https://github.com/ravinder024/SidelineReel-Ajaia]

---

## Executive Summary
SidelineReel's superpower is not raw video editing or live streaming infrastructure; it is **frictionless emotional fulfillment for families**—automating the capture of their child’s athletic journey and delivering that pride directly to their phones. 

A thorough review of Materials 1 through 5 reveals a critical inflection point:
1. **The Loudest Signal is an Existential Trap:** Ridgeline’s $180k renewal threat demands live streaming, but live streaming is a commodity utility with crippling unit economics (cellular uplinks, bandwidth bills, camera operator dependencies) that diverts the company away from its proprietary AI moat.
2. **The Stated vs. Revealed Preference Trap:** 58% of surveyed parents ask for "more editing tools and music," yet in reality, only 6% open the editor and under 1% ever finish an edit. Conversely, **90% tap "Share" on automated recaps**. Building more editing tools is solving for a phantom user. Instead, additional automated templates will help improve share rate as well surveyed parents preference for editing tools with music will reduce as well.
3. **The Silent Retention Killer:** 30% of reels are never opened. Analytics and support tickets prove why: **misattributed jersey tags (e.g., #14 vs #4, #1 vs #11)** and late-night delivery timestamps. Incorrect person's thumbnail for videos, when a parent opens a reel and sees someone else’s child, trust in the core AI engine is destroyed, directly undermining the renewal value Carla Reyes (Ridgeline) cited: *"SidelineReel's highlight reels are a big part of why half our parents renewed this year."*

**Our Decision:** Build the **High-Confidence OCR & Jersey Verification Engine with Coach Rapid-Review (Human-in-the-Loop) and Optimal-Hour or near to real-time Dispatch**. We fix the leaking foundation of the core product before layering on expensive adjacency distractions.

---

## Task 1: The Roadmap Call (Prioritization & Strategy)

### 1.1 Evaluated Roadmap Candidates & Evidence-Based Ranking

| Rank | Candidate Feature | Strategic Value & Evidence Grounding | Effort / Risk | Decision |
| :--- | :--- | :--- | :--- | :--- |
| **#1** | **High-Confidence OCR Disambiguation & Coach Rapid-Review Queue** | **Directly resolves 3 support tickets** (Ridgeline, Brightwater, Cobblestone) and fixes the **30% unopened reel leak** (Material 5). Eliminates wrong-kid reels that embarrass clubs and frustrate parents. Protects the core value prop Carla credited for 50% parent renewals. | Medium effort (3-5 wks) / Low Risk | **BUILD NEXT (Top Priority)** |
| **#2** | **Smart Sunday Morning Scheduled Dispatch** | Solves the second half of Material 5 (late-night delivery). Moves notification delivery from 11:30 PM post-processing to Sunday 9:00 AM family breakfast window, projected to lift overall open rates from 70% to >88%. | Low (1 wk) / Minimal Risk | **BUILD CONCURRENTLY with #1** |
| **#3** | **Turnkey "Live-to-Reel" Camera Partner Integration (The Ridgeline Bridge)** | Directly addresses Carla & Jamal's $180k renewal threat **without building a proprietary live-streaming tech stack**. Partner with Veo/Hudl/GameChanger or RTMP ingest to ingest existing live streams while SidelineReel retains the high-margin reel synthesis AI. | Medium-High (6-10 wks) / Medium Risk | **STAGE FOR NEXT CYCLE (Commitment to Carla)** |
| **#4** | **League & Multi-Sport Custom Branding (Team Logo & App Watermark)** | Addresses 2 support tickets (all-sports icon confusion, camera roll watermark drop). Improves word-of-mouth branding when 90% of parents share reels to social media. | Low 1 wk / Minimal Risk | **FAST-FOLLOW BACKLOG** |
| **#5** | **Advanced In-App Reel Editor (Music & Manual Trimming)** | Classic stated vs. revealed preference trap. 58% claimed they wanted it, but **<1% of editor sessions ever finish an edit**. Building this burns engineering capital on an active anti-pattern. | High (8+ wks) / High Distraction Risk | **DO NOT BUILD** |
| **#6** | **Additional templates for Reels (More options to automated Reels)** | Indirectly reduces the demand for #5. If users have more options to automated reels, then less users will opt for manual editing, increasing the likelihood of **improving overall share rate**. | Medium (2-3 wks) / Low Distraction Risk | **BUILD AFTER #1 and #2** |
| **7** | **Full Native Real-Time Live Streaming Platform** | Carla's board ask. High bandwidth cost, severe cellular latency/failure rates at youth fields, operational support nightmare. Complete distraction from Ajaia’s core AI moat. | Massive (6+ months) / Fatal Business Risk | **DO NOT BUILD (Direct Pushback)** |

---

### 1.2 What We Will NOT Build Next and Why

#### What We Will NOT Build #1: Native In-House Live Streaming Infrastructure
*   **The Pressure:** Jamal Whitfield (VP of Sales) warned that Ridgeline is a $180k ARR account up for renewal in 6 weeks, and Carla Reyes says her board wants live streaming for grandparents and college scouts.
*   **Why We Say NO to Building Native Streaming:**
    1.  **Unit Economics Destruction:** Live streaming HD video from hundreds of remote grass fields with spotty 5G uplinks requires massive egress bandwidth costs, dedicated hardware ingestion, and real-time streaming servers. It converts SidelineReel from a high-margin AI software business into a low-margin live video utility.
    2.  **Scouts and Grandparents Don't Watch 90 Minutes of Raw 4K:** College scouts and busy grandparents rarely sit through full 90-minute youth soccer stalemates in real time. They want the curated 45-second reel of Maya #14's touches, passes, and goals—which is exactly what SidelineReel already automates best.
    3.  **The Commercial Counter-Offer to Save Ridgeline:** We do not say "no" to Carla; we say "yes to your outcome, no to building commodity plumbing." We offer Ridgeline a **Partner Live-Link Bridge**: SidelineReel allows coaches to paste a YouTube Live, GameChanger, or Veo live stream URL directly into the team hub for parents/scouts during match hours. Once the match finishes, SidelineReel ingests the recording automatically to deliver the reels. We commit this integration on the roadmap before Carla’s signups open in 6 weeks.

#### What We Will NOT Build #2: Advanced Reel Editor (Music Trimming & Manual Cuts)
*   **The Trap:** 58% of survey respondents explicitly requested "more editing controls and music."
*   **The Behavioral Truth:** The telemetry is undeniable. Only 6% of parents ever opened the editor, and **less than 1% finished an edit**. Parents *think* they want to be video editors; in reality, they are time-poor parents who love SidelineReel precisely because they don't have to edit anything. 90% of auto-recaps are shared as-is. Building editing tools caters to vocal survey sentiment while degrading the automated "magic" of the core product.

---

## Task 2: The Engineering Spec (PRD)

### Feature Name
**High-Confidence OCR & Jersey Verification Engine with Coach Quick-Review (Human-in-the-Loop)**

### 2.1 Problem Statement & Target Outcome
*   **Problem:** Computer vision currently mistakes visually similar jersey numbers (#14 vs #4, #1 vs #11, swapped digits) due to jersey folds, motion blur, and occlusions. Approximately 30% of reels are never opened, driven in part by wrong-kid video thumbnails and midnight dispatch notifications.
*   **Target Outcomes:**
    1.  **Drop misattribution error rate to below 1%** for all delivered reels.
    2.  **Lift overall Family Reel Open Rate from 70% to >88%** across all participating clubs.
    3.  **Keep Coach Review Time under 30 seconds per match** (median review effort &le; 2 ambiguous clips).

---

### 2.2 In Scope vs. Out of Scope

#### In Scope (Release 1.0)
*   **Dual-Digit Disambiguation Heuristic:** Computer vision confidence scoring specifically tuned for 1- vs 2-digit collisions (#1 vs #11, #4 vs #14).
*   **Confidence Thresholding Pipeline:** Clips with &ge; 85% confidence are auto-approved. Clips between 50%–84% confidence or with conflicting digit reads are routed to the Coach Quick-Review Queue. Clips &lt; 50% are discarded or tagged as "General Team Highlight."
*   **Coach Rapid-Review Queue (Mobile & Web):** A lightweight 1-tap review interface showing the 3-second play loop, the detected digit clash, and candidate roster players with photo and position.
*   **Smart Delivery Scheduling:** Moving auto-recap dispatch from immediate post-processing (often 11:00 PM – 2:00 AM) to a configurable parent-friendly window (default: Sunday 9:00 AM local time).
*   **Watermark Persistence Fix:** Ensuring club logo watermark renders reliably across all iOS/Android camera roll export pipelines (resolving the coach support ticket).

#### Out of Scope (Explicitly Deferred)
*   Native in-app video editing timeline, multi-track audio trimming, and custom music uploads.
*   Proprietary live-streaming video ingestion and real-time broadcasting.
*   Facial recognition biometric identification (strict adherence to youth COPPA and student privacy protections; identification relies strictly on jersey numbers, positions, and roster data).

---

### 2.3 Where a Human Stays in the Loop (HITL Architecture)
AI does 95% of the heavy lifting; the human coach provides 5% judgment where ambiguity exists:
1.  **Threshold Gate:** The AI evaluates bounding box OCR confidence across all frames of a detected play. If confidence is &ge; 85%, the clip bypasses the queue and automatically lands in the player’s personal reel.
2.  **The 30-Second Coach Queue:** If confidence drops below 85% (due to jersey wrinkles, goalkeeper jersey differences, or cluster collisions), the clip appears in the coach's post-match summary with pre-ranked roster candidates (e.g., *"Maya #14 (94% positional match) vs Chloe #4 (12% match)"*).
3.  **One-Tap Resolution:** The coach taps one button: `[Confirm Maya #14]`, `[Reassign to Chloe #4]`, or `[Discard Clip]`.
4.  **Auto-Dispatch Safeguard:** If a coach does not review flagged clips within 12 hours, the system suppresses the ambiguous clips from individual reels and includes them only in the general Team Recap, guaranteeing no parent receives a reel with the wrong child.

---

### 2.4 Acceptance Criteria

Feature: Automated Jersey Tagging & Coach Review Queue

1. Scenario: High confidence OCR auto-attribution
   Given game footage is uploaded with clear jersey visibility
    When the CV pipeline detects jersey number 9 with confidence >= 85%
    Then the clip is automatically attributed to roster player #9 Sophia K.
    And no coach review prompt is generated for this clip.

 2. Scenario: Low confidence digit ambiguity routed to Coach Queue
    Given game footage where jersey fold obscures digit #14 (read as #4 or #14 with 62% confidence)
    When processing completes
    Then the clip is flagged as "Ambiguous" and placed in the Coach Rapid-Review Queue
    And the clip is NOT added to Maya #14's or Chloe #4's reel until resolved.

 3. Scenario: Coach resolves ambiguity in under 2 taps
    Given a coach opens the Review Queue with 2 pending flagged clips
    When the coach taps "Confirm Maya #14"
    Then the clip is assigned 100% verified status for Maya #14
    And the thumbnail for Maya's reel is generated from this confirmed frame.

  4. Scenario: Scheduled Sunday Morning Delivery
    Given match footage processed on Saturday at 8:30 PM
    When the coach approves or skips the review queue
    Then the auto-recap notification is held until Sunday 9:00 AM local club time
    And parent push notifications trigger at 9:00 AM with the verified thumbnail.
---

### 2.5 Failure Modes & Mitigation Telemetry


| Failure Mode | Root Cause | Real-Time Catch / Guardrail |
| :--- | :--- | :--- |
| **Failure Mode 1: "Silent False Positive"** (AI has 88% false confidence and misattributes #4 as #14 without flagging the coach). | Player is moving directly toward the camera lens at high velocity; perspective distortion flattens digit "1". | **Roster & Position Context Filter:** The algorithm cross-references player position tracking (heatmaps). If player #4 is a Center Back and the play occurred deep in the opponent's 6-yard box, the AI flags a "Positional Anomaly" and forces the clip into Coach Review regardless of raw OCR score. |
| **Failure Mode 2: "Coach Review Abandonment"** (Coaches ignore the review queue, delaying reel delivery to families). | Coach fatigue after Saturday tournaments; coaches ignore app notifications. | **Fail-Safe Fallback Timer:** If the review queue is unopened after 12 hours (or by Sunday 8:00 AM), the pipeline automatically ships all high-confidence reels (>85%) on schedule. Unverified ambiguous clips are safely relegated to the unassigned team recap reel. |

---


## Task 3: Working Prototype Documentation

The interactive prototype has been fully implemented in `index.html`. It is a zero-dependency, self-contained, clickable web application demonstrating the end-to-end user experience.

The working prototype can accessed using **Github** [[https://github.com/ravinder024/SidelineReel-Ajaia/]

### Features
1. **Screen 1: Computer Vision Ingestion & Disambiguation Engine**
   - Simulates video ingest for Ridgeline U14 vs Westside.
   - Live telemetry counters (frames processed, plays isolated, high confidence vs ambiguous flags).
   - Real-time bounding box visualization catching the `#14 vs #4` jersey fold and `#1 vs #11` goalie occlusion.
2. **Screen 2: Coach Rapid-Review Queue (Human-in-the-Loop)**
   - Recreates the exact support ticket scenarios from Ridgeline and Cobblestone.
   - Side-by-side roster candidate cards showing player photos, jersey numbers, and contextual positional confidence.
   - Interactive 1-click confirmation (`Confirm Maya #14`), updating confidence badges from 62% to 100% verified.
3. **Screen 3: Family Reel Preview & Scheduled Sunday Morning Dispatch**
   - Notification timing control solving the midnight drop issue.
   - Interactive mobile parent simulator showing Maya Gonzalez's verified highlight reel, complete with one-tap SMS/group sharing.
   - Comparative analytics dashboard contrasting the old vanity metric against the new True North retention metric.

---

### Task 4: AI Workflow Reflection

*   **Where AI was used:**
    - AI was utilized to analyze the raw support ticket logs and survey data to identify frequency patterns (clustering digit mix-ups: #14/#4 and #1/#11).
    - AI helped draft initial Gherkin acceptance criteria edge cases and structured the single-file prototype codebase in Tailwind CSS and JavaScript.
*   **What was deliberately kept human:**
    - **Strategic trade-offs and client boundary holding:** The decision to say NO to Carla Reyes' demand for native live streaming and to Jamal's sales panic was an entirely human judgment call based on unit economics, business model defense, and company focus.
    - **Discarding survey bias:** The conscious decision to ignore the 58% survey request for an in-app reel editor required human PM judgment to recognize stated preference bias versus actual behavioral usage data.
*   **One specific thing an AI tool got wrong or was rejected:**
    - An initial AI roadmap suggestion proposed building a *"Lite Live Streaming MVP"* using WebRTC to appease Carla. I **explicitly rejected this**. An MVP live stream that stutters or drops frames at a soccer park would destroy Ridgeline's renewal faster than having no live streaming at all. Instead, I crafted a commercial bridge: allowing coaches to embed third-party live links (YouTube/Veo) while SidelineReel doubles down on automated highlight creation.

---

## Task 5: Video Defense & Pitch Script (5–8 Minutes)

The video can be accessed via this URL- 




