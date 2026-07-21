# AI Future Ready product plan

## 1. Product vision

AI Future Ready helps students in grades 6–10 learn how to use artificial intelligence effectively, critically, creatively, and safely.

The product is not an unrestricted chatbot or a shortcut for completing schoolwork. It is a structured learning environment where students practice working with AI, evaluate its answers, recognize its limitations, protect their privacy, and reflect on when AI should or should not be used.

## 2. Product goals

The product should enable students to:

- Explain, at an age-appropriate level, what generative AI is and how it works.
- Recognize that AI output can be incomplete, biased, misleading, or incorrect.
- Write clear prompts that include a goal, useful context, constraints, and an expected output format.
- Improve a prompt after reviewing an unsatisfactory result.
- Verify important AI-generated claims using reliable sources.
- Protect personal, private, and confidential information.
- Use AI to support learning and creativity without replacing their own thinking.
- Make responsible decisions about when AI use is appropriate.

The product should enable educators to:

- Assign structured AI-literacy activities.
- See student progress and areas where additional instruction is needed.
- Review curriculum before assigning it.
- Discuss AI use through shared language, scenarios, and learning objectives.

## 3. Target users

### 3.1 Students

Students in grades 6–10 are the primary users. Content and interaction design should support two initial grade bands:

- Grades 6–8: concrete explanations, guided practice, shorter activities, and familiar examples.
- Grades 9–10: deeper evaluation, more independent practice, complex scenarios, and stronger emphasis on evidence and responsible academic use.

### 3.2 Educators

Teachers, librarians, instructional technology staff, and school program leaders assign lessons and monitor learning.

### 3.3 Administrators

Authorized curriculum or platform administrators publish content, manage access, and review safety reports.

### 3.4 Guardians

Guardian functionality is not part of the initial MVP unless required by the account and consent model. The data model should not prevent adding it later.

## 4. Product principles

- Learning comes before engagement metrics.
- AI should coach student thinking, not complete the thinking for them.
- Human-reviewed curriculum is the source of truth.
- Student safety and privacy are system requirements.
- The product must be useful even when the AI provider is unavailable.
- Feedback should be supportive, specific, and age appropriate.
- Important assessments should use deterministic scoring.
- Accessibility is part of feature completion, not a later enhancement.
- Avoid public rankings, popularity mechanics, and shame-based incentives.
- Clearly distinguish AI-generated material from authored curriculum.

## 5. Initial curriculum

The initial learning path contains six modules. Each module may present different examples and difficulty levels for the two grade bands.

### Module 1: What AI is

- Recognize common uses of AI.
- Understand that generative AI predicts responses from patterns in data.
- Distinguish AI from a search engine, database, or human expert.
- Identify tasks AI handles well and tasks where it may struggle.

### Module 2: Prompt fundamentals

- State a clear goal.
- Add relevant context.
- Add useful constraints.
- Request an appropriate output format.
- Revise a prompt based on the result.

### Module 3: Check before you trust

- Recognize hallucinations and unsupported claims.
- Separate facts, opinions, and generated suggestions.
- Ask for sources without assuming cited sources are real.
- Verify important claims using trustworthy references.

### Module 4: Privacy and safety

- Identify personal, sensitive, and confidential information.
- Decide what should never be placed in an AI prompt.
- Respond appropriately to unsafe or uncomfortable output.
- Know how to report a problem to a trusted adult or educator.

### Module 5: Bias, fairness, and responsibility

- Recognize that AI output may reflect bias.
- Compare answers from different perspectives.
- Understand that people remain responsible for decisions made with AI.
- Identify situations where using AI may be unfair or inappropriate.

### Module 6: AI as a learning partner

- Use AI to brainstorm, explain, quiz, revise, and explore.
- Preserve the student's own voice and reasoning.
- Disclose AI assistance when an assignment requires it.
- Create a personal checklist for responsible AI use.

## 6. Learning experience model

Each lesson should follow a consistent cycle:

1. **Discover:** introduce one concept with a short explanation or story.
2. **Observe:** show a realistic example and explain what happened.
3. **Practice:** let the student make a decision, edit a prompt, or evaluate a response.
4. **Reflect:** ask the student to explain why a choice was effective or safe.
5. **Check:** use a short deterministic assessment to confirm understanding.
6. **Apply:** provide an optional challenge that uses the skill in a new context.

Every lesson must define:

- Grade band
- Learning objective
- Prerequisites
- Estimated duration
- Activity type
- Completion criteria
- Assessment criteria
- Accessibility requirements
- Curriculum version

## 7. MVP scope

### 7.1 Student experience

- Account access based on the approved identity and consent model.
- Grade-band onboarding.
- Student dashboard showing the current learning path and progress.
- Module and lesson navigation.
- Lessons containing authored text, examples, and interactive checks.
- Prompt Builder for assembling a prompt from goal, context, constraints, and format.
- Response Detective activities for identifying weak, unsupported, biased, or unsafe AI answers.
- Scenario-based safety activities.
- Short quizzes with deterministic scoring and explanations.
- Saved lesson completion, quiz attempts, and mastery progress.
- Private achievements that recognize learning milestones.
- A clear mechanism for reporting unsafe or inaccurate content.

### 7.2 Educator experience

- Educator account and role-protected workspace.
- Create or manage a classroom.
- Invite or enroll students using the approved school workflow.
- Browse published curriculum.
- Assign lessons or modules with optional due dates.
- View completion and skill-level summaries.
- View an individual student's assignment history when authorized.
- Receive reports without exposing raw student AI conversations by default.

### 7.3 Administrator experience

- Role-protected administration area.
- Create and edit draft curriculum.
- Preview lessons for each grade band.
- Publish a new curriculum version.
- Archive content without invalidating historical attempts.
- Review content and safety reports.
- Audit privileged curriculum and access-management actions.

### 7.4 Platform capabilities

- Secure authentication and server-side authorization.
- Role and ownership policies.
- Versioned curriculum and assessments.
- Progress and mastery tracking.
- Server-side AI provider abstraction.
- AI input and output safety checks.
- Typed validation at every external boundary.
- Operational logging that excludes sensitive student content.
- Health and readiness checks.
- Responsive and accessible interfaces.

## 8. Explicitly outside the MVP

- An unrestricted general-purpose chatbot.
- Student-to-student messaging or a public social feed.
- Public profiles, follower counts, public leaderboards, or popularity metrics.
- AI-generated final grades or disciplinary recommendations.
- Advertising, behavioral profiling, or sale of student data.
- Native mobile applications.
- Parent or guardian dashboards unless required by the consent model.
- Real-time collaborative editing.
- Marketplace or user-submitted public lessons.
- Broad learning-management-system integrations.
- Voice cloning, face recognition, or generated impersonation activities.

## 9. Key user journeys

### 9.1 Student completes a first lesson

1. The student signs in through the approved account flow.
2. The student selects or confirms a grade band.
3. The dashboard recommends the first available lesson.
4. The student completes the explanation and guided activity.
5. The student submits a short knowledge check.
6. The system records the attempt and updates progress.
7. The student sees feedback and the next recommended activity.

### 9.2 Student practices a prompt

1. The student receives a learning goal and scenario.
2. The Prompt Builder guides the student through prompt components.
3. The server validates and safety-checks the submitted prompt.
4. The AI provider returns a bounded response or a safe fallback is shown.
5. The student evaluates the response against a checklist.
6. The student revises the prompt and compares the result.
7. Completion records the practiced skill, not the raw conversation by default.

### 9.3 Educator assigns a module

1. The educator opens an authorized classroom.
2. The educator previews a published module and grade-band variant.
3. The educator creates an assignment and optional due date.
4. Enrolled students see the assignment on their dashboards.
5. The educator sees completion and mastery summaries.

### 9.4 Administrator publishes curriculum

1. An administrator creates or updates a draft.
2. The content is validated for structure and required metadata.
3. An authorized reviewer previews and approves it.
4. Publishing creates an immutable curriculum version.
5. New activity uses the published version while historical attempts retain their original references.

## 10. Core domain areas

The initial domain model should support these concepts without prematurely fixing the database schema:

- User
- Role and permission
- Student profile and grade band
- Educator profile
- Classroom and membership
- Learning path
- Module
- Lesson and lesson version
- Activity
- Quiz and question
- Assignment
- Lesson progress
- Quiz attempt
- Skill and mastery state
- Achievement
- AI activity session metadata
- Content report
- Audit event

The exact schema, relationships, deletion behavior, and retention rules will be designed after the database and identity decisions are approved.

## 11. Architecture direction

The application will be a TypeScript-first Next.js monolith using the App Router.

High-level boundaries:

- Pages and layouts compose feature UI.
- Route handlers and server actions form trusted application boundaries.
- Services own business workflows and domain decisions.
- Repositories isolate non-trivial database operations.
- Provider adapters isolate external AI services.
- Validation schemas protect every external boundary.
- Authorization policies centralize role, membership, and ownership checks.
- Authored curriculum remains independent of live AI availability.

Proposed feature areas:

```text
features/
  auth/
  users/
  curriculum/
  lessons/
  quizzes/
  ai-lab/
  progress/
  classrooms/
  achievements/
  safety/
```

## 12. Architecture decisions required before scaffolding

Each material decision should be recorded in `docs/decisions` with context, options, the selected approach, and consequences.

Required decisions:

1. Supported Node.js and Next.js versions.
2. Package manager and dependency-version policy.
3. Relational database and data-access library.
4. Hosting and database deployment environment.
5. Authentication, session, student account, and educator verification model.
6. Consent and age-assurance requirements for the first deployment region.
7. Curriculum authoring and storage model: database, version-controlled files, or hybrid.
8. AI provider interface, initial provider, model-selection policy, and fallback behavior.
9. Prompt and response moderation approach.
10. Student prompt, output, analytics, and audit retention policies.
11. Unit, integration, accessibility, and browser testing tools.
12. Logging, error reporting, metrics, and alerting services.
13. Transactional email provider if invitations or account recovery require email.
14. Deployment environments, continuous integration, and release workflow.

PostgreSQL is the current database recommendation because classrooms, assignments, curriculum versions, attempts, and progress have relational constraints. It remains a proposal until documented and approved.

## 13. Safety and privacy requirements

Before persistent student accounts or live AI activities are released:

- Define which personal data is required and why.
- Define the lawful consent and account model for the initial deployment region.
- Define retention and deletion periods for every student-data category.
- Ensure raw prompts and AI responses are not retained by default.
- Review the selected AI provider's data-processing and retention controls.
- Implement server-side prompt and response safety checks.
- Provide age-appropriate blocked-content and provider-failure experiences.
- Provide content reporting and authorized review workflows.
- Prevent student data from appearing in logs, analytics, or error-reporting payloads.
- Complete threat modeling for authentication, classroom membership, progress access, curriculum publishing, and AI endpoints.
- Document account deletion and data-export processes.

Legal and policy review is required before production use with minors. Engineering controls support that review but do not replace it.

## 14. Accessibility requirements

The initial release targets WCAG 2.2 AA.

Required practices include:

- Keyboard access for every interaction.
- Semantic structure and meaningful focus order.
- Visible focus indicators.
- Sufficient text and non-text contrast.
- Text alternatives for meaningful images.
- Captions or transcripts for instructional media.
- No reliance on color alone for meaning.
- Reduced-motion support.
- Clear language and recovery guidance.
- Responsive support for narrow mobile screens, tablets, and desktops.
- Accessibility checks in automated tests plus manual review of critical journeys.

## 15. Measurement plan

Product measurement should answer whether students are learning, not merely whether they remain on the site.

Initial learning measures:

- Lesson completion by module and grade band.
- First-attempt and eventual quiz mastery.
- Improvement between initial and revised prompts in structured activities.
- Ability to identify unsupported or unsafe AI output.
- Retention checks completed after a delay.
- Educator-assigned activity completion.

Operational measures:

- Page and API reliability.
- AI-provider latency and failure rate.
- Safe-fallback frequency.
- Accessibility defects.
- Content reports and resolution time.
- Estimated AI cost per completed activity.

Do not collect event data simply because it may be useful later. Every event must have a defined purpose, allowed fields, retention period, and access policy.

## 16. Delivery plan

### Phase 0: Standards and decisions

Deliverables:

- Engineering standards
- Product plan
- Architecture decision template
- Initial architecture decisions
- MVP acceptance criteria
- Risk register

Exit criteria:

- Product scope and non-goals are agreed.
- Safety, privacy, and consent questions have owners.
- Technical foundation decisions are documented.

### Phase 1: Application foundation

Deliverables:

- Next.js TypeScript application
- Formatting, linting, and strict type checking
- Test foundations
- Environment validation
- Database foundation and migrations
- Continuous integration
- Health and readiness routes
- Basic public and authenticated application shells

Exit criteria:

- Quality checks and production build pass.
- The application starts from documented setup steps.
- Health checks work in the target environment.
- No application feature depends on a live AI provider yet.

### Phase 2: Identity and access

Deliverables:

- Approved authentication and session flow
- Student, educator, and administrator roles
- Centralized authorization policies
- Grade-band onboarding
- Account and session security tests
- Required consent or enrollment workflow

Exit criteria:

- Protected routes enforce access on the server.
- Role, ownership, and denied-access tests pass.
- No sensitive identity tokens are accessible to browser JavaScript.

### Phase 3: Curriculum and lessons

Deliverables:

- Versioned curriculum model
- Draft, preview, publish, and archive workflows
- Student learning path and lesson experience
- Authored activities that do not require live AI
- Lesson completion and progress tracking

Exit criteria:

- An administrator can publish a reviewed lesson.
- A student can complete it and retain progress.
- Historical attempts retain their curriculum version.

### Phase 4: Assessment and mastery

Deliverables:

- Quizzes and deterministic scoring
- Attempt history
- Skill and mastery calculation
- Feedback and retry rules
- Student progress views

Exit criteria:

- Scoring and progress invariants have unit tests.
- Students receive useful feedback without answer leakage.
- Duplicate submissions do not duplicate progress or rewards.

### Phase 5: Guided AI lab

Deliverables:

- Provider-neutral server-side AI interface
- Prompt Builder activities
- Response Detective activities
- Input and output safety pipeline
- Bounded timeouts, retries, and usage limits
- Safe failure states
- AI operational metrics without disallowed content

Exit criteria:

- Provider credentials and prompts remain server-side.
- Unsafe, malformed, delayed, and unavailable-provider cases are tested.
- Core curriculum remains usable during provider failure.
- Retention behavior matches the approved policy.

### Phase 6: Classrooms and assignments

Deliverables:

- Classroom membership
- Student enrollment workflow
- Assignments and due dates
- Educator progress summaries
- Individual progress access controls

Exit criteria:

- Educators can access only their authorized classrooms and students.
- Students can access only their own assignments and progress.
- Educator reporting does not expose raw AI conversations by default.

### Phase 7: Production hardening and pilot

Deliverables:

- Security and privacy review
- Accessibility audit and remediation
- Threat-model follow-up
- Observability and alerts
- Backup and recovery validation
- Data export and deletion workflows
- Load and cost testing
- Pilot curriculum review
- Operational runbooks

Exit criteria:

- Critical student and educator journeys meet accessibility requirements.
- Safety, security, privacy, and operational launch checks are complete.
- A limited pilot can be supported and monitored safely.

## 17. Testing strategy

- Unit-test scoring, mastery, access policies, curriculum rules, and safety decisions.
- Integration-test route handlers, services, repositories, and database constraints.
- Contract-test AI provider adapters using recorded or synthetic fixtures, never live student data.
- Browser-test critical student, educator, and administrator journeys.
- Test denied access for every protected role and ownership boundary.
- Test provider timeouts, malformed output, unsafe content, and safe fallback behavior.
- Automate accessibility checks and manually test the most important workflows.
- Keep test data synthetic and deterministic.

## 18. Initial release acceptance criteria

The MVP is ready for a controlled pilot when:

- Students can securely access the correct grade-band learning path.
- Students can complete all six initial modules and retain progress.
- Quizzes provide deterministic scoring and useful feedback.
- Guided AI activities use server-side safety controls and fail safely.
- Educators can assign content and view authorized progress summaries.
- Administrators can publish versioned, reviewed curriculum.
- The product remains usable when the AI provider is unavailable.
- Student data collection, retention, deletion, and access rules are documented and implemented.
- Critical journeys meet the agreed accessibility target.
- Required quality, security, privacy, and operational checks pass.
- Pilot support, reporting, and incident-response ownership are defined.

## 19. Open product questions

These questions should be resolved before their related implementation phase:

- Will the first release serve individual learners, schools, or a single partner program?
- Which country or region governs the first deployment?
- Who creates student accounts, and what consent or school authorization is required?
- Are students expected to use school-managed identity providers?
- Are educator-created classrooms required for the first pilot?
- Will curriculum be created by the internal team, external educators, or both?
- Which subjects should supply examples: general study skills, science, language arts, social studies, coding, or a selected subset?
- Should students receive any free-form AI interaction, or only scenario-bound guided activities?
- Which languages must the initial curriculum and interface support?
- What information may educators view about student practice?
- What evidence will define a successful pilot?

## 20. Immediate next steps

1. Review and approve this product plan.
2. Identify the first deployment audience and region.
3. Resolve the MVP account, consent, and role model.
4. Record the foundation architecture decisions.
5. Write measurable acceptance criteria for the first curriculum module.
6. Create low-fidelity flows for the student lesson and educator assignment journeys.
7. Scaffold the application only after the required decisions are approved.
