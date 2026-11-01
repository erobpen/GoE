# Gamification Go — Platform requirements

Status: current product requirements, with open decisions recorded below.  
Updated: 2026-11-01.  
Source: the product owner's explanations on 2026-11-01, including subsequent clarifications about permissions, scoring, publishing, business model, branding, and floating-island game design.

## 1. Authority and product identity

The product is **Gamification Go**, for education. The GitHub repository remains GoE. EduQuest is the former working name and is no longer the product name.

This document supersedes both the former product vision in EduQuest_SAFe_Product_Vision.md and the original goe.odt proposal. Those earlier documents must not supply conflicting requirements. A requirement that is absent here is not automatically approved merely because it appeared in an older proposal; bring any potentially useful older detail back for a decision.

Use this document for agreed behavior. Items explicitly marked **Open** are undecided and must not be implemented as settled rules. This update records requirements only. Implementation and final technology choices will be discussed separately.

## 2. Purpose and product boundaries

Enable education through a reusable game platform: content creators prepare educational content, teachers assign finished content to classrooms, parents manage their children, and students learn through gameplay.

Prodigy Math Game is a conceptual inspiration for the educational gameplay. The world uses compact floating islands, an isometric 3D view, block-like terrain, and a colorful storybook atmosphere; see sections 10 and 15.

The product has three connected parts:

- A public website / landing page.
- A signed-in member website with views appropriate to the member's roles.
- A web-based game, to be built later and launched from the member website.

The first available game is a proof of concept with two levels. A future catalog may include more levels (for example, 70) and multiple games. Those are expansion possibilities, not commitments for the proof of concept.

## 3. Public landing page and access

Anyone can visit the landing page without logging in. It explains the platform's purpose and includes marketing, promotion, development-funding information, and a game demonstration video.

The public visitor can watch the demonstration but cannot play the game. An authenticated member is required to launch and play it. This applies to direct game entry as well as the Play button; a public game link must not provide an anonymous playable session.

The landing page offers registration and login. Third-party sign-in is required in principle, with Google and Facebook mentioned as examples. The exact provider list is **Open**; the examples do not prescribe every provider or exclude other account methods.

## 4. Onboarding and multiple roles

After signing in, ask how the member plans to use the platform:

- For themselves as a student / player.
- For their children as a parent.
- As a teacher.
- As a content creator.

A member can hold multiple roles, including teacher and content creator together. Content made by a teacher must still go through the creator workflow and be published before classroom use.

Parents create and manage linked child accounts through an experience inspired by Google Family Link. This is a product experience reference, not a requirement to integrate with Family Link or to require every child to own a Google account.

**Open:** How roles are added or changed after onboarding; guardian verification; the exact child sign-in / recovery method; and country-specific age / supervision rules. See section 6 for the age-policy reference.

## 5. Student member view

The student website remains focused. It provides:

- A button to launch the web game.
- Friend requests, approved friend connections, and text messages.
- Classrooms, pending classroom invitations / requests, and assigned learning not yet completed.
- A classroom information board with announcements and student questions to the teacher.
- The student's own results and learning progress.
- Simple character creation / selection and customizable familiar / pet selection.

The first character types are **wizard** and **archer**. Their battles use ranged actions; there is no close combat with monsters.

The preferred direction is to create the character and familiar in the member browser interface so the avatar is already available before launching the game, if practical. **Open:** The final placement and exact customization options. Initial customization is simple; expanded customization comes later.

Generic starter content lets a student begin without joining a classroom. The platform team will seed content rather than expect a new community to provide everything. Existing English, mathematics, geography, and question materials may already be available; they have not been located, inspected, or imported in this task. The final starter subjects / syllabus and usable source materials remain to be confirmed.

Text communication is in scope. In-platform voice is only a possible later addition. This does not require a Discord integration.

A broader AI-adaptive student dashboard is not approved merely because the original proposal included it.

## 6. Parent member view, friendships, and approvals

A parent creates / links child accounts and sees:

- Each child's classrooms and pending invitations.
- Progress and performance for each classroom.
- Completion, learning success, and play-time statistics.
- Friend and classroom approval requests.
- Requests by a child to leave a classroom.

Exact statistical definitions and account-linking / identity checks remain **Open**.

### 6.1 Friend requests between children

For supervised / underage student A sending a friend request to student B, when they have not attended the same classroom, require all three:

1. Approval by A's parent / guardian.
2. Approval by B's parent / guardian.
3. Acceptance by B.

A's sending action expresses A's intent; it does not replace either guardian approval or B's acceptance. Friendship and friend chat are not enabled while any required approval is missing.

The exception is a pair of students who have attended the same classroom with the required enrollment approvals. They may send and accept a friend request between themselves, without collecting fresh parental friend approvals. The recipient still has to accept; shared classroom membership does not automatically make them friends.

A pending classroom invitation is not evidence of shared attendance. No general “we know each other” bypass is approved. The stated exception is the shared classroom.

**Open:** Exact evidence of attendance versus approved enrollment; whether all historical shared classes qualify indefinitely; guardian changes, revocation, blocking, and mixed-age friendships. These details must not silently expand the exception.

### 6.2 Classroom enrollment and departure

When a teacher invites an underage student, send the parent an approval request automatically. This is automatic delivery, not automatic approval.

Enrollment requires **both student acceptance and parent approval**. Neither action alone activates membership. The order of those actions is not prescribed.

An enrolled underage student cannot immediately remove themselves from the classroom. They can request to leave, and their parent must approve the departure. This later clarification supersedes the earlier “cannot leave” wording.

The parent view must clearly explain that approving a classroom permits communication with its teacher and fellow students under the classroom rules. The parent should know and assess whose invitation they approve.

**Open:** Teacher removal / closure controls, guardian-initiated departure, adult student behavior, and what happens to assignments and statistics after departure. Detailed classroom management will be discussed later.

### 6.3 Classroom communication and completion

Within the approved classroom, students can communicate and ask the teacher questions through the classroom board. The teacher may contact enrolled children directly on the basis of that classroom's approval.

After the classroom finishes, that classroom alone no longer permits direct teacher-to-child messages. Continued direct contact requires a separately accepted friend connection with the child's parent's approval; that connection is optional, not a condition of taking the class.

**Open:** Exact adult-to-child friend-request approval flow, completion / archiving events, message history access, and the effect of leaving a class early. There is no blanket permission for a teacher to message arbitrary children outside approved classrooms or separately approved connections.

### 6.4 Age / supervision reference

Use a Family Link-like parent-managed account experience. Do not interpret “underage” as a finalized universal age of 18.

As checked on 2026-11-01, Google's own-account management minimum varies by country: its published requirements include Croatia 16+, Serbia 15+, and Spain 14+, with 13 applying to countries not separately listed. These are Google's account rules, not automatically Gamification Go's age policy or a legal determination. [Google Account age requirements](https://support.google.com/accounts/answer/1350409?hl=en).

Google also describes parent-created child accounts and supervised teen accounts; its FAQ says supervised teens below 18 need parent approval to stop supervision. [Google Family Link FAQ](https://families.google/familylink/faq/).

**Open:** Gamification Go's actual supported countries, age / supervision matrix, age assurance, and transition out of supervision. These must be set for this service before the dependent account and messaging flows are implemented.

## 7. Teacher member view

A teacher sees and maintains their created classrooms. The teacher:

1. Creates a classroom.
2. Selects finished, published educational content for it.
3. Selects students and sends invitations.
4. Waits for the required student acceptance and parent approvals.
5. Maintains classroom information, announcements, and a question / discussion board.
6. Communicates with students and parents under the rules in section 6.
7. Reviews classroom and student learning statistics.
8. Sets the required level-passing score for their classroom assignment.

The catalog supports filters for subject, more specific topic, and language. Before selection, show available ratings, prior-use information, and the number of game levels. Subjects and languages are not conceptually restricted to a single pilot; the starter catalog can be small.

The teacher selects existing published content. Authoring questions, video uploads, and game-package configuration belong to the separate creator role.

Classroom setup is editable. Editing a classroom or its assignment does not by itself grant authority to alter someone else's published content. A teacher who authors their own package must publish it through the creator role.

The teacher can set a required score as a percentage, such as 40%, 50%, 60%, 70%, or 100%, or as an absolute points target. Validate the target against what students can actually earn in the configured level. The teacher, **not the content creator**, sets the classroom passing target. See section 10.

The purpose is to complement regular school / teaching work.

**Open:** Catalog rating rules and usage metrics; effects of editing active assignments or targets; default thresholds for independent play; and detailed classroom management.

## 8. Content creator workflow

A creator produces an educational content package, such as a mathematics topic in English, for a selected game.

The creator:

1. Chooses a game. Initially there is only one choice.
2. Chooses how many available game levels the package uses. Initially the game has two levels.
3. Chooses one monster count, from **3 through 10**, that applies equally to every selected level.
4. Supplies subject / topic and language information needed for catalog discovery.
5. Imports questions through a user-friendly, predefined form or table.
6. Imports a separate table of YouTube links, mapped to levels and video purposes.
7. Resolves validation problems.
8. Publishes the package before teachers can use it.

The initial configuration must not support different monster counts for different levels. Future games may offer more levels, but creators should be able to select a smaller package rather than being forced to use every available level.

**Open:** Whether level selection is a count of sequential levels or a choice of specific maps. Do not assume all future maps must be included.

### 8.1 Question quantity

The minimum is **two questions per monster, per level**.

For a package with L selected levels and M monsters per level:

- Each level must have at least 2 × M questions.
- The package total must be at least L × 2 × M questions.
- Extra questions are allowed.
- Questions for one level do not compensate for missing questions in another.

Example: two levels with three monsters per level need at least six questions for each level, or **12 questions in total**. This resolves the earlier verbal six-question example by following the later explicit per-level clarification.

### 8.2 Question import data

The import needs enough information to identify the level, question text, answer choices, correct answer, and question point value / weight.

Excel and Google Sheets were named as desired ways to supply tabular questions. The exact supported file types and whether Google Sheets means a direct connection, exported spreadsheet, or paste/import are **Open**.

For the proof of concept, questions use four choices, **A, B, C, D**, with the correct choice represented explicitly. Do not assume A is always correct. Additional question formats are a future expansion.

The user-friendly import must validate required data, question-to-level mapping, minimum counts for every level, answer-choice references, and point values. It must identify the rows / fields needing correction. The exact column names and allowed point values are **Open**.

Question weights belong to the imported content; the teacher selects the classroom passing threshold. Validate content for usable reward / question data, then validate each teacher target against the maximum attainable score from the configured encounters. The full uploaded question pool is not itself the score maximum: only two questions per monster are used in an encounter. Exact weighting and scoring on failed attempts remain open.

### 8.3 Video import data

Creators upload links, not just an unstructured list. Use a separate, user-friendly table identifying the level and the video's role.

Each selected level needs at least one YouTube video and supports at most three role slots:

| Slot | Purpose | Requirement |
| --- | --- | --- |
| 1 | Core lesson / introduction to the topic and level | Required |
| 2 | Optional extension for students who want to learn more | Optional |
| 3 | More detailed explanation / support for struggling students | Optional |

Public or unlisted source videos may be used if the platform can access them and the publishing requirements are satisfied.

If slot 2 or slot 3 is missing, reuse slot 1 at that location / trigger. With only one supplied video, the same video serves all three purposes.

Validate that each required level has its video entry and that supplied links identify usable YouTube videos. The access and availability checks must be defined when the integration is designed.

The owner prefers concise lessons and discussed approximately 15–30 minutes as an upper range, with shorter videos allowed. A hard duration limit was not settled. Do not replace this with “any length allowed” or invent a precise YouTube platform limit.

**Open:** Exact hard duration limit; whether introductory playback must be completed or can be skipped; extension-video location / trigger; what counts as struggling and triggers slot 3; and any additional playback behavior. These details will be supplied later.

## 9. Drafts, publishing, and platform copies

Draft questions and video-link tables are stored but unavailable for teacher selection. Publishing makes the package available for reuse by other platform users.

At publication the creator must accept publishing terms covering the agreed product policy:

- Creators retain ownership of their original content.
- The platform receives a copy and a perpetual, free-to-use license for reuse and hosting through the platform.
- Questions are retained in the platform database.
- Video copies are hosted as unlisted videos on the platform's dedicated YouTube channel.
- After publication, the creator cannot delete the published platform copy.
- The platform may remove prohibited / insulting content under its moderation policy; applicable YouTube policy may also cause removal.

This clarifies the earlier ambiguous “platform ownership” wording: preserve creator ownership together with the intended continuing platform usage rights. The exact legal terms are not drafted or accepted by this specification. “Cannot delete” is the creator's ordinary published-content control, not an assertion that removal is impossible in every circumstance.

Do not rely solely on a creator's original YouTube link, since later removal of the original must not automatically remove the platform copy. A usable link alone does not establish an authorized copying mechanism. Source acquisition and re-upload implementation remain to be designed.

Do not publish a package to teachers while required video processing is unfinished or failed. Publication states and recovery must be specified.

If the platform becomes commercially successful, the owner intends to share revenue with creators and reward the best / most-used educational content. No payout percentage, eligibility formula, or payment implementation is set yet.

**Open:** Exact rights and acceptance text; creator authorization checks; original-file delivery or another permitted acquisition workflow; moderation and takedown process; published-content revision / versioning; and commercial payout rules. No copying, uploading videos, accepting terms, or payments are authorized by this documentation task.

## 10. Game, encounters, scoring, and world

### 10.1 Browser-first floating islands

The game must run directly in a web browser without installing a game client, engine, browser extension, or other extra software. Ordinary browser asset loading is expected. Local storage / cookies and persistence behavior are to be discussed separately.

The first game has two compact proof-of-concept levels. Each level is a floating island surrounded by void, with a roughly square / block-based terrain footprint, a path across it, and attractive selected assets.

Use a 3D isometric view, potentially with limited camera rotation to reveal the terrain. Islands can have different elevations and vertical layers. Limited deviation from the main path is allowed, but this is not a large open world.

Constrain movement with visible natural geography: forests, lakes, rivers, cliffs, and bridges. A monster can guard a bridge or another real bottleneck. Do not explain inaccessible areas only with arbitrary invisible barriers.

Block-like terrain can evoke the modular look of Minecraft, but the player **cannot dig, mine, or modify terrain**. This is an exploration / learning game, not a terrain-editing sandbox.

Use a fable / storybook atmosphere and lively fantasy colors, with Simon the Sorcerer named as a visual mood reference. W-AI's approved plum, gold, and parchment palette remains the shared identity foundation; see section 15. Exact environment colors, layout, assets, and rendering style will be reviewed later.

The owner already has selected game assets and previous Unity experience. The asset files, locations, licenses, and browser suitability have not been supplied or checked in this task. Reuse the selected assets after inspection rather than choose replacements without discussion.

A longer first load is acceptable, followed by lightweight, responsive play. No download-size, load-time, frame-rate, or memory budget has been finalized.

### 10.2 Encounter and video loop

At the start of a level, show the core lesson video. Exact watch / skip rules are open. The optional extension and struggling-student videos retain the slot-1 fallback from section 8.

The student's wizard or archer moves through the island. Monsters are distributed randomly along suitable paths and terrain locations. Some monsters block progress; others may be bypassed if the map allows and enough points have been collected. The earlier requirement to encounter every monster is superseded.

On an encounter:

1. Switch from the island map to a battle view.
2. Put the player on the left and the monster on the right.
3. Resolve the encounter through two educational questions.
4. Two correct answers defeat the monster and produce the configured points, with a possible item reward.
5. Return to island progression.

Wizard and archer actions are ranged. There is no close combat or separate question-free standard RPG combat phase. Health, counterattacks, shields, familiar combat powers, item drop rules, and visual spell effects still need detailed design.

A failed encounter leaves the monster undefeated. The student may try another available path or fight that monster again. A defeated monster cannot be fought again in that level run.

**Open:** What happens immediately on a wrong answer, whether both answers must be correct in a single attempt, partial points on failed attempts, progress reset rules between attempts, and the exact visual battle sequence. Do not allow the score model to depend on farming an already defeated monster.

### 10.3 Question pools and retries

Each encounter uses two questions randomly selected from that level's uploaded pool. Extra questions increase variety. For example, ten monsters require at least 20 questions per level, but the creator may upload 50.

With three monsters and only six uploaded questions, all six are intended to be used across those encounters. Reattempts draw randomly from the same level pool and may repeat questions; they do not require a new uploaded pool.

**Open:** Exact randomization / no-repeat behavior across first attempts, failed attempts, and a full run. Implement the minimum-pool coverage and retry repetition intentionally rather than assume unrestricted random draws satisfy both.

### 10.4 Teacher-set gate

The classroom teacher sets a passing target for the assigned content, expressed as a percentage or points. The creator does not choose that classroom target.

Open the next-level gate when the target is met. An animation / message can announce that enough points have been earned. The exit must still be reachable through the island's physical routes.

A lower target may let the student leave without defeating every monster. A 100% target requires earning the level's maximum; in the simple three-monster example this means defeating all three.

Validate teacher targets against the maximum actually collectible from the configured level / encounters. Reject a target above that maximum. More questions in a pool do not create more encounters or additional refights against defeated monsters.

Example with equal one-point questions: three monsters × two questions provide six available points. A teacher's five-point target can be met by a successful encounter that takes the total to six; exact equality is not required.

**Open:** Whether points are credited per answer or only on defeat; how imported unequal question weights produce a stable attainable maximum under random selection; percentage rounding; allowed minimum / zero targets; independent-play defaults; and how already-awarded partial points are handled on retry. These details must be settled before scoring code is written.

## 11. Free access and future business model

Core access is intended to remain free forever through an **ad-supported model**, analogous to the owner's YouTube comparison. Future ads are intended to include child accounts, subject to the service's applicable child-account and advertising rules; ad targeting and implementation are not specified or approved by this document.

A possible monthly subscription removes ads. It is not a requirement to subscribe in order to access the core learning experience.

Future optional purchases may include character clothing / items, customization, and spell appearance. Whether any purchasable spell affects gameplay rather than appearance remains **Open**.

Parents may later allocate purchased money / credits to their children for in-game spending. Children may also earn credits through achievements, such as the example of a school grade of five. The verification and reward rules are not defined. A marketplace is a possibility, not a selected launch requirement.

The owner also mentioned possible collaboration with governments / local governments and support for many languages.

Ads, subscriptions, credit purchases / allocations, marketplace behavior, and creator payouts are **future work**, not proof-of-concept payment features. No prices, real-money transfer rules, cash withdrawal, trading system, or payout formula are approved. Free learning must remain available.

The intended creator revenue sharing is recorded in section 9. Its commercial rules will be defined later.

## 12. Delivery scope and technology

The next implementation phase must be agreed after the open questions are answered. The website and member workflows are described here; the web game will be built later.

The two-level game configuration and its authoring data constraints are proof-of-concept requirements. The exact implementation sequence and which complete flows must ship together are **Open**. Do not defer parent approvals to an unspecified later release if a release enables the underage social or classroom actions they govern.

The technology stack is not selected. The owner prefers a lightweight browser game, is not committing to Unity, and suggested Godot as a candidate to discuss. Do not treat Godot or any other engine as selected or assume browser-export suitability without evaluating the chosen assets and runtime. Unity, Unreal, React Native, Kubernetes, microservices, cloud provider, database, and AI capabilities in the former proposal are not binding choices.

Preserve the separation of public website, role-specific member workflows, reusable educational packages, classrooms, and game runtime in the design. Choose implementation technologies separately. Multi-subject and multilingual content discovery does not imply that automatic translation is required.

## 13. Decisions still open before dependent implementation

| ID | Decision |
| --- | --- |
| D1 | Detailed wrong-answer and retry scoring; unequal question weights, attainable maximum, percentage rounding, randomization / coverage, and independent-play passing defaults. Teacher control of classroom targets and two-question encounters are settled. |
| D2 | Country-specific age / supervision matrix, child login and guardian verification, historical-class eligibility, revocation / departure behavior, and exact post-class adult-to-child friendship flow. Core three-approval and classmate-exception rules are settled. |
| D3 | Video duration cap, watching / triggers, authorized video acquisition, final perpetual-license / acceptance text, moderation / takedown, and published-content versioning. Creator ownership, platform copy, and no creator deletion after publication are settled product intentions. |
| D4 | Future ad/subscription implementation, cosmetic / spell purchase boundaries, parent-funded and earned credits, and creator payout rules. Free ad-supported learning and optional ad removal are settled business direction. |
| D5 | Implementation sequence, initial auth providers, starter content inventory, selected asset inspection, engine evaluation, camera controls, browser performance budgets, and storage / cookie behavior. |
| D6 | Import format / Google Sheets method, level selection, ratings / usage definitions, edits to active classroom assignments, and additional classroom-management details. |

Resolve the product and consent rules before implementing the flows that depend on them. Resolve import-format and catalog details before implementing those forms. No unresolved detail should silently inherit a conflicting rule from an older proposal.

## 14. Alignment with the former documents

| Former proposal | Current requirement |
| --- | --- |
| EduQuest branding | Gamification Go, for education. |
| Teacher and content creator combined | Separate roles; one member may hold both. |
| Public and authenticated access unspecified | Public landing page and demo; authenticated gameplay only. |
| Broad AI-adaptive student dashboard | Focused member view with own results, game launch, messages, classes / boards, character and familiar creation. |
| Parent controls in a later phase | Parent management and approvals are part of the applicable member flows. |
| Per-level monster configuration | One count of 3–10 applied to all selected levels. |
| Minimum question count not clearly per-level | At least 2 × monsters for every level; 12 total in the two-level, three-monster example. |
| Knowledge shields followed by ordinary RPG combat | Educational questions directly resolve monster encounters; no separate standard-combat phase. |
| Teacher validation / AI authoring as mandatory path | Creator imports and validates questions and videos; teacher selects published packages. |
| Shared content and platform video copies unclear or deferred | Publish-before-use, creator ownership with perpetual platform reuse rights, unlisted platform copies, no creator deletion of published copies; acquisition and legal wording still open. |
| Monetization assumptions inherited from the former proposal | Owner-confirmed future ad-supported free learning, optional ad-removal subscription, possible cosmetic / credit purchases, and creator revenue sharing; details deferred. |
| Stack and AI services prescribed | Technology choices and optional AI capabilities require separate decisions. |

## 15. Visual identity and owner mark

Use the approved **Cinematic Plum** palette from the W-AI website as the identity foundation for the game and platform. Color values were read from the referenced website project's `website/app/brand-theme.css` on 2026-11-01.

| Role | Color |
| --- | --- |
| Background / deep plum | `#17121E` |
| Surface / plum | `#251B2F` |
| Accent / warm gold | `#C8AB73` |
| Text / parchment | `#F2EBDD` |
| Ink on light areas | `#2D2133` |
| Muted lavender | `#BFB2C7` |
| Borders | `#493B51` |

Source reference: [W-AI website](https://www.withwai.com/) and the chat “Update AI consulting website” supplied by the owner. Use these as design references, not instructions to change that website.

The game's islands should still have the lively fable / classic fantasy atmosphere described in section 10. Palette adoption does not prescribe a flat recoloring of every environmental asset.

Reuse the existing W-AI logo as the owner's mark: [w-ai-logo.svg](w-ai-logo.svg). The file is copied unchanged from the referenced website's `public/brand/w-ai-logo-primary.svg`. Use the mark discreetly in an appropriate location. Placement will be reviewed with the interface.

Do not add a personal biography, portrait, personal endorsement, or personal attribution to the product interface. Logo use does not rename Gamification Go to W-AI.

## 16. Seed content and creator guidance

Launch with platform-provided educational content rather than depend on immediate outside contributions. Inspect the owner's existing English, mathematics, geography, YouTube lesson, and question materials when their locations are supplied; availability and readiness are not verified yet.

Plan a tutorial for creators covering how to prepare and publish educational content: make a lesson video, host it on YouTube, fill the question and video tables, validate the package, and publish with the agreed rights. AI-assisted video/content preparation may be explained as an option, not as a mandatory dependency or an authorization for paid generation.

The exact tutorial format, initial courses, and production / publication workflow will be agreed separately.
