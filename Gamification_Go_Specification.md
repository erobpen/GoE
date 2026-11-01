# Gamification Go — Platform requirements

Status: current product requirements, with open decisions recorded below.  
Updated: 2026-11-01.  
Source: Roberto's explanation in this chat on 2026-11-01.

## 1. Authority and product identity

The product is **Gamification Go**, for education. The GitHub repository remains GoE. EduQuest is the former working name and is no longer the product name.

This document supersedes both the former product vision in EduQuest_SAFe_Product_Vision.md and the original goe.odt proposal. Those earlier documents must not supply conflicting requirements. A requirement that is absent here is not automatically approved merely because it appeared in an older proposal; bring any potentially useful older detail back for a decision.

Use this document for agreed behavior. Items explicitly marked **Open** are undecided and must not be implemented as settled rules. No application or game implementation is authorized by this documentation update.

## 2. Purpose and product boundaries

Enable education through a reusable game platform: content creators prepare educational content, teachers assign finished content to classrooms, parents manage their children, and students learn through gameplay.

Prodigy Math Game is a conceptual inspiration for the isometric educational game. Detailed game design will be discussed separately.

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

A member can hold multiple roles. A teacher who also wants to author content uses the content creator role for authoring; teacher status alone does not confer the content creation workflow.

**Open:** How roles are added or changed after onboarding, and how a parent-managed child profile authenticates. Do not assume that each child must own a Google or Facebook account.

## 5. Student member view

The student website is deliberately small. It provides:

- A button to launch the web game.
- Messages from friends, where the required approvals exist.
- Classrooms and classroom invitations relevant to that student.
- Character creation and pet selection after login.

There is generic starter content so a student can begin playing without a classroom. Mathematics in English was given as the initial example; the exact starter syllabus remains **Open**.

Character creation is simple initially. More customization and a possible business model connected to it are future topics, not initial payment requirements. Pet appearance and behavior are also to be designed later.

Do not add the older proposal's broad student analytics dashboard, AI adaptation, or additional student website modules as agreed initial scope.

## 6. Parent member view and approvals

A parent sees their linked children and can invite children and create profiles for them. The exact invite, linking, identity, and child-login flows are **Open**.

For an underage child, the parent manages the account and approvals:

- Approve requests from other friends before the child can chat with those friends.
- Approve teacher invitations before the child joins those classrooms.
- Receive classroom approval requests automatically when a teacher invites the child. Automatic delivery means a request is sent to the parent; it does not mean automatic approval.
- See learning statistics, including course progress, completion, success, and performance.

A pending or unapproved friend-chat request must not enable that chat. A pending or unapproved classroom invitation must not enroll an underage child. These requirements must be enforced by the service, not only by hiding controls.

The owner mentioned exceptions to approval rules but has not specified them. No exception is approved yet. Classroom enrollment must not be treated as blanket approval for unrelated friend chat.

**Open:** Underage threshold and supported age groups; how guardian authority is established; what a child can do before a guardian is linked; exceptions; whether and how teacher-to-child messages are covered by classroom approval; and revocation behavior. The precise definitions and display of performance statistics also need design.

## 7. Teacher member view

A teacher:

1. Creates a classroom.
2. Browses finished, published educational content.
3. Filters content by subject, more specific subject / topic, and language.
4. Inspects available ratings, information about prior use, and the number of game levels.
5. Selects existing content for the classroom.
6. Invites students; underage invitations require the parent's approval.
7. Communicates with parents and students through messages.

Subjects can include mathematics, geography, chemistry, physics, and others. Languages can include English, Serbian, Croatian, German, Spanish, Chinese, and others. The catalog is not conceptually restricted to a single subject or language; the initial starter content can be narrow.

Teachers select completed content rather than building questions, uploading videos, or configuring monsters in the teacher workflow. Authoring belongs to the separate content creator role.

**Open:** Rating eligibility and scale, usage metrics, whether content must be previewable before assignment, and the detailed permissions for classroom messaging. Do not invent a rating formula or an approval exception.

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

A correct answer must be represented explicitly rather than inferred from its position. The owner used A as one example of the correct answer and referred to other lettered choices as distractors. The number of choices (for example, four versus five) remains **Open**.

The user-friendly import must validate required data, question-to-level mapping, minimum counts for every level, answer-choice references, and point values. It must identify the rows / fields needing correction. The exact column names and allowed point values are **Open**.

Question weights and the level's passing threshold must be settled together so an author cannot accidentally publish a level whose required score cannot be reached. The validation formula depends on the still-open encounter and scoring rules.

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

Uploaded questions are stored as draft content. A draft is not available for teacher selection. Publishing makes the prepared package available for reuse through the platform.

The intended publication workflow includes:

- Retaining the questions as platform-stored content.
- Making a platform-controlled copy of the submitted YouTube videos.
- Hosting those copies as unlisted videos on the platform's dedicated YouTube channel.
- Using those platform copies for the published package.
- Terms covering platform ownership / shared rights as described by the owner, and reuse by other platform users.

This is a product requirement to design, not a claim that a YouTube link alone provides permission or a supported copying mechanism. The rights terms, creator permission, source acquisition, and upload mechanism must be resolved before implementing publication. No video copying, uploading, or acceptance of legal terms is authorized by this documentation task.

**Open:** Exact rights arrangement and terms; how creators supply authorized source video files or another permitted acquisition method; what happens if a copy fails; editing, replacement, versioning, and withdrawal of published packages; and whether additional moderation is needed.

Do not silently publish a package with unfinished required video processing. Teachers must receive usable published content; the precise publication states will be designed with that workflow.

Creators may receive compensation in the future if monetization is introduced. The payout rules are not yet defined.

## 10. Game and learning loop

The first game is web-based, with two levels, an isometric view, and a constrained path through each map. It is not an open world.

The student's character moves along the path. Monsters are placed randomly along that path so the student must encounter all configured monsters. Random placement must not permit bypassing required encounters.

At the start of a level, show its core lesson video. The precise watch / skip behavior is **Open**.

On encountering a monster:

1. Switch from the map to a battle view.
2. Put the student's character on the left and the monster on the right.
3. Fight through correctly answering educational questions.
4. Defeat the monster by completing the required correct answers.
5. Award points, with a possible character item reward.
6. Return to map progression.

There is no agreed second, question-free RPG combat phase. The earlier shield-then-standard-combat design is superseded. Shields, fixed mage/ranger classes, counterattacks, health, pets' battle abilities, and item drop formulas are not current requirements.

To advance, the student must encounter the level's monsters and meet a required points threshold. Clearing the path or defeating monsters does not by itself waive the score requirement.

**Open:** Questions drawn per monster, allocation and reuse of the extra question pool, handling of wrong answers, scoring on retry, monster defeat versus failed encounters, how a student who falls short can recover, the threshold formula, and item rewards. The examples of three or five points do not establish a fixed maximum or pass mark. Prevent accidental dead ends once the recovery rules are agreed.

Video slot 2 offers optional further learning. Slot 3 supports struggling students. Their exact in-game use is to be specified later, with the slot-1 fallback preserved.

## 11. Free access and future business model

The owner explicitly requested that the platform be **free of charge forever**, while also discussing possible future monetization, creator compensation, and character customization as a business opportunity.

For the current scope, no subscription, advertisement requirement, payment gate, institutional charge, premium content fee, commission, or microtransaction is approved. Payment and business-model design are deferred.

**Open:** Which elements must remain free forever and what, if anything, may be monetized later. Do not infer a paid tier or a creator payout formula from the former documents. Fundraising information on the public landing page is separate from a paid-access model.

## 12. Delivery scope and technology

The next implementation phase must be agreed after the open questions are answered. The website and member workflows are described here; the web game will be built later.

The two-level game configuration and its authoring data constraints are proof-of-concept requirements. The exact implementation sequence and which complete flows must ship together are **Open**. Do not defer parent approvals to an unspecified later release if a release enables the underage social or classroom actions they govern.

The current explanation does not select a technology stack. Unity, Unreal, React Native, Kubernetes, microservices, cloud provider, database, LLM-generated questions, automated translation, and adaptive AI paths in the former documents are not binding choices.

Preserve the separation of public website, role-specific member workflows, reusable educational packages, classrooms, and game runtime in the design. Choose implementation technologies separately. Multi-subject and multilingual content discovery does not imply that automatic translation is required.

## 13. Decisions needed before implementation

| ID | Decision |
| --- | --- |
| D1 | Question choices, encounter question count / selection, wrong-answer behavior, retry scoring, passing threshold, and recovery after a low score. |
| D2 | Age threshold, parent / child linking and login, consent exceptions, and classroom / teacher messaging permissions. |
| D3 | Video duration cap, required watching, extension and remedial triggers, authorized video acquisition, and publication rights. |
| D4 | What “free forever” covers and the boundary of any later monetization. |
| D5 | First delivery scope: landing page and member workflows first; game timing; starter subject / syllabus and initial sign-in providers. |
| D6 | Spreadsheet import format / Google Sheets method, level selection, ratings / usage definitions, and published-content revision policy. |

Resolve the product and consent rules before implementing the flows that depend on them. Resolve import-format and catalog details before implementing those forms. No unresolved detail should silently inherit a conflicting rule from an older proposal.

## 14. Alignment with the former documents

| Former proposal | Current requirement |
| --- | --- |
| EduQuest branding | Gamification Go, for education. |
| Teacher and content creator combined | Separate roles; one member may hold both. |
| Public and authenticated access unspecified | Public landing page and demo; authenticated gameplay only. |
| Broad student dashboard and AI adaptation | Small member view, game launch, messages, classes, character and pet creation. |
| Parent controls in a later phase | Parent management and approvals are part of the applicable member flows. |
| Per-level monster configuration | One count of 3–10 applied to all selected levels. |
| Minimum question count not clearly per-level | At least 2 × monsters for every level; 12 total in the two-level, three-monster example. |
| Knowledge shields followed by ordinary RPG combat | Educational questions directly resolve monster encounters; no separate standard-combat phase. |
| Teacher validation / AI authoring as mandatory path | Creator imports and validates questions and videos; teacher selects published packages. |
| Shared content and platform video copies unclear or deferred | Explicit publish-before-use workflow and intended platform-controlled unlisted copies, with rights and acquisition still open. |
| Subscriptions, ads, licensing, and premium services assumed | Free access requirement; payment model deferred and scope of “forever” to be clarified. |
| Stack and AI services prescribed | Technology choices and optional AI capabilities require separate decisions. |
