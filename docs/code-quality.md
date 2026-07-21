# AI Future Ready engineering standards

> Every contributor, including AI-assisted contributors, must follow these standards unless the team deliberately updates this document.

AI Future Ready is a TypeScript-first Next.js monolith that helps students in grades 6–10 learn how to use AI effectively, critically, and safely. Product decisions must prioritize student safety, accessibility, privacy, and learning outcomes over engagement alone.

## 1. Project principles

- Use TypeScript for application code with strict type checking enabled.
- Do not add JavaScript source files unless a tool requires JavaScript configuration.
- Use the Next.js App Router.
- Keep business logic out of pages, React components, and route handlers.
- Keep feature-specific code inside `features/<feature-name>`.
- Keep reusable UI primitives inside `components` and shared utilities inside `lib`.
- Keep server-only code inside `server`, or in files that are explicitly marked as server-only.
- Keep database schemas, migrations, and database helpers inside `db`.
- Keep curriculum source files and content tooling inside `content` when content is version controlled.
- Keep documentation inside `docs`.
- Prefer Server Components. Add Client Components only when browser APIs, local interactivity, or client-side state require them.
- Do not import server-only modules into Client Components.
- Do not hardcode production URLs, secrets, credentials, API keys, model identifiers, or callback URLs.
- Pin important runtime and infrastructure dependencies to reviewed versions.
- Build the smallest complete feature that meets the learning objective; avoid speculative abstractions.

## 2. Source documentation

- Add comments when they explain intent, constraints, safety decisions, or non-obvious behavior.
- Do not add comments that merely repeat what the code already states.
- Exported public utilities, services, and domain operations should have concise JSDoc when their contract is not obvious from their name and types.
- Safety-critical behavior, authorization rules, data-retention decisions, and AI prompt constraints must document the reason for the rule.
- Use architecture decision records in `docs/decisions` for choices that materially constrain the system.

Example:

```ts
/**
 * Evaluates a quiz attempt and returns mastery changes without persisting them.
 *
 * @param attempt - The validated answers submitted by a student.
 * @returns The score and resulting mastery changes.
 */
export function evaluateQuizAttempt(attempt: QuizAttemptInput): QuizResult {
  // Implementation omitted.
}
```

## 3. Naming conventions

| Type | Convention | Example |
| --- | --- | --- |
| React components | `PascalCase.tsx` | `LessonCard.tsx` |
| Hooks | `useCamelCase.ts` | `useLessonProgress.ts` |
| Utilities | `camelCase.ts` | `calculateMastery.ts` |
| Server services | `camelCase.service.ts` | `lessonProgress.service.ts` |
| Repositories | `camelCase.repository.ts` | `quizAttempt.repository.ts` |
| Schemas | `camelCase.schema.ts` | `quizAttempt.schema.ts` |
| Tests | `<subject>.test.ts` or `<subject>.test.tsx` | `calculateMastery.test.ts` |
| End-to-end tests | `<journey>.spec.ts` | `completeLesson.spec.ts` |
| Types and interfaces | `PascalCase` | `LessonProgress` |
| Constants | `UPPER_SNAKE_CASE` | `SUPPORTED_GRADE_LEVELS` |
| Database tables | `snake_case`, plural | `quiz_attempts` |
| Route segments | `kebab-case` | `learning-paths` |

Avoid `I` prefixes for interfaces. Names should describe the domain concept rather than its TypeScript construct.

## 4. Intended project structure

```text
AI-Future-Ready/
  app/
    (public)/
    (auth)/
    (student)/
    (educator)/
    (admin)/
    api/
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
  components/
    ui/
  lib/
  server/
  db/
  content/
  tests/
  docs/
    decisions/
```

Rules:

- Pages render UI and compose feature components.
- Route handlers authenticate, authorize, validate input, call services, and format responses.
- Services contain business workflows and domain logic.
- Repositories contain database queries when a query is more than a direct, isolated operation.
- Components must not access database clients or private server utilities directly.
- Features may depend on shared code, but shared code must not depend on feature implementations.
- Cross-feature operations should be coordinated by a service rather than by importing internal UI code.
- Avoid catch-all `utils` folders. Put utilities near their domain or give shared modules a specific responsibility.

## 5. TypeScript and validation

- Do not use `any`. Use `unknown` at untrusted boundaries and narrow it safely.
- Avoid type assertions unless the invariant is documented and cannot be expressed more safely.
- Validate all external input at runtime, including forms, route parameters, request bodies, environment variables, imported curriculum, webhooks, and AI output.
- Derive TypeScript types from validation schemas when practical to prevent duplicated contracts.
- Represent finite domain states with unions or enums instead of free-form strings.
- Handle nullable and optional values explicitly.
- Never trust data simply because it originated from another part of the application.

## 6. API conventions

Use a consistent response envelope for application API routes.

Successful response:

```json
{
  "success": true,
  "data": {}
}
```

Error response:

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Check the highlighted fields and try again."
  }
}
```

Paginated response:

```json
{
  "success": true,
  "data": [],
  "pagination": {
    "page": 1,
    "pageSize": 20,
    "totalItems": 100,
    "totalPages": 5
  }
}
```

Additional rules:

- Use stable, machine-readable error codes and age-appropriate user-facing messages.
- Do not expose stack traces, database errors, provider responses, internal prompts, or secrets.
- Use appropriate HTTP methods and status codes.
- Make mutation endpoints safe against duplicate submissions when the operation warrants it.
- Add pagination before a collection can grow without a small, enforced upper bound.
- Version externally consumed APIs when backward compatibility becomes a requirement.

## 7. Authentication and authorization

- Prefer secure, `httpOnly`, same-site cookies for sessions.
- Do not store session tokens or sensitive identity data in browser local storage.
- Every protected server operation must authenticate the user.
- Every role-specific operation must enforce permissions on the server.
- Centralize role and ownership checks in reusable authorization policies.
- Never rely on hidden UI controls as authorization.
- Students, educators, guardians, and administrators must receive only the minimum permissions required for their role.
- Access to classrooms, assignments, student progress, and account management requires explicit membership or ownership checks.
- Privileged curriculum publishing and administrative actions must be auditable.

The initial role and consent model must be recorded in an architecture decision before authentication is implemented.

## 8. Student safety and privacy

Students in the target grade range may be minors. Treat safety and privacy as system requirements, not optional moderation features.

- Collect the minimum personal data required to provide the product.
- Do not ask students to enter full names, addresses, phone numbers, school credentials, private documents, or other sensitive information into AI activities.
- Provide visible, age-appropriate reminders not to share personal or confidential information.
- Do not store raw student prompts or AI conversations by default. Any retention must have a documented purpose, retention period, access policy, and deletion path.
- Do not use student content to train models unless a separately reviewed policy and valid consent mechanism explicitly permit it.
- Apply server-side safety checks to open-ended AI input and output.
- Provide safe, age-appropriate responses when content is blocked; never reveal moderation internals.
- Provide a clear route for students and educators to report unsafe, inaccurate, or inappropriate material.
- Do not use manipulative engagement patterns, public popularity metrics, or competitive ranking that can expose or shame students.
- Avoid collecting precise location, unnecessary device identifiers, or advertising profiles.
- Ensure account deletion and data-export requirements are addressed before collecting persistent student data.
- Review applicable child privacy, education privacy, and consent requirements for each deployment region before launch.

## 9. AI integration standards

- AI providers may only be called from server-side modules.
- Keep provider-specific code behind an internal interface so providers and models can change without rewriting product features.
- Treat model output as untrusted external input and validate structured responses before use.
- Keep system prompts and safety policies in version-controlled server-side files.
- Never expose system prompts, provider credentials, moderation details, or hidden evaluation data to the client.
- Set explicit timeouts, token limits, and bounded retry behavior for provider calls.
- Fail safely when an AI provider is unavailable; core lessons and previously saved progress should remain usable where possible.
- Record operational metadata needed for reliability and cost monitoring, but exclude student prompt content unless approved by the retention policy.
- Display AI-generated content as AI-generated and remind students that it can be incomplete, biased, or incorrect.
- Do not present AI output as an authoritative grade, disciplinary decision, diagnosis, legal conclusion, or safety determination.
- Human-authored curriculum and deterministic assessment rules take precedence over model-generated content.
- Prompts, models, and evaluation criteria must be versioned when changes could affect learning outcomes.

## 10. Curriculum and learning integrity

- Each lesson must have a stated grade band, learning objective, estimated duration, and completion criteria.
- Curriculum content must be reviewed by a human before publication.
- Separate draft and published curriculum states.
- Published learning content must be versioned so historical attempts remain interpretable.
- Use deterministic scoring for graded quizzes unless a reviewed rubric explicitly requires assisted evaluation.
- AI feedback should coach reasoning and revision rather than provide answers that bypass the learning activity.
- Activities should teach students to verify claims, identify uncertainty, check sources, recognize bias, and protect privacy.
- Progress and mastery calculations belong in tested domain functions, not UI components.
- Accessibility and age appropriateness are acceptance criteria for every learning activity.

## 11. Accessibility and user experience

- Target WCAG 2.2 AA for student, educator, and administrative experiences.
- All functionality must be usable with a keyboard.
- Use semantic HTML before adding ARIA attributes.
- Maintain visible focus states and sufficient color contrast.
- Provide text alternatives for meaningful images and transcripts or captions for instructional media.
- Do not rely on color alone to communicate status, correctness, or progress.
- Respect reduced-motion preferences.
- Write concise, supportive language appropriate for the selected grade band.
- Error messages must explain how the student can recover without blame or shame.
- Test key student journeys at narrow mobile widths as well as desktop widths.

## 12. Environment variables and secrets

- Never commit `.env` files containing real values.
- Commit `.env.example` with safe placeholders.
- Document every environment variable used by the application.
- Validate environment variables at application startup.
- Separate server-only variables from variables intentionally exposed with `NEXT_PUBLIC_`.
- Optional integrations must fail gracefully when their configuration is absent.
- Rotate any secret immediately if it appears in source code, logs, screenshots, test fixtures, or Git history.

The exact foundation variables will be added after the database, authentication, deployment, and AI-provider decisions are recorded.

## 13. Database and data integrity

- The database choice and data-access library must be recorded in an architecture decision before implementation.
- Use migrations for every schema change.
- Review generated migrations before applying them.
- Use transactions for operations that update multiple records as one business action.
- Enforce important invariants with database constraints as well as application validation.
- Store timestamps in UTC and convert them only at presentation boundaries.
- Use explicit retention and deletion behavior for student-created data.
- Avoid destructive migrations without a documented rollout and recovery plan.
- Seed data must be synthetic and must not contain real student information.

## 14. Error handling, logging, and observability

- Use typed application errors for expected failure cases.
- Convert internal errors into safe responses at the system boundary.
- Do not log secrets, session tokens, personal student data, raw prompts, or AI responses.
- Use structured logs with request or trace identifiers.
- Capture enough context to diagnose failures without identifying a student unnecessarily.
- Track AI latency, failure rate, token usage, and estimated cost without storing disallowed content.
- Define health and readiness checks for deployed environments.
- Alert on sustained authentication failures, elevated server errors, and AI safety pipeline failures.

## 15. Testing and quality gates

Every delivery phase has a testing checkpoint before work moves forward.

Minimum pull-request checks:

- Formatting passes.
- Lint passes without ignored errors.
- TypeScript checking passes.
- Unit and integration tests pass.
- The production build succeeds.
- Database migrations are reviewed when present.
- Changed student-facing flows pass relevant accessibility checks.

Feature expectations:

- Domain logic receives focused unit tests.
- Server operations receive happy-path, validation, and authorization tests.
- Every role-restricted feature includes a denied-access test.
- AI integrations test schema failures, provider timeouts, unsafe content, and safe fallback behavior without making live provider calls.
- Critical student journeys receive browser-level tests.
- Bug fixes include a regression test when practical.
- Tests must not depend on production services or real student data.

## 16. Dependencies and third-party services

- Prefer platform capabilities and existing dependencies before adding a package.
- Evaluate maintenance status, license, bundle impact, security history, and necessity before adding a dependency.
- Keep provider SDK usage behind project-owned boundaries.
- Do not introduce a third-party analytics, advertising, AI, or monitoring service until its student-data behavior has been reviewed.
- Commit the lockfile and use reproducible installs in continuous integration.
- Review automated dependency updates before merging them.

## 17. Git and review conventions

Use Conventional Commits:

```text
feat(lessons): add interactive lesson completion
fix(progress): prevent duplicate mastery awards
docs(standards): clarify student data retention
test(ai-lab): cover unsafe prompt fallback
```

Additional rules:

- Keep commits focused and independently understandable.
- Do not mix unrelated formatting or refactoring into feature commits.
- Do not commit generated artifacts unless the project deliberately tracks them.
- Never commit secrets, personal data, production exports, or real student content.
- Pull requests must describe the user impact, testing performed, safety or privacy implications, and any follow-up work.
- Changes to authentication, authorization, student data, curriculum publication, AI safety, or retention require explicit review.

## 18. Definition of done

A feature is complete only when:

- Its acceptance criteria and learning objective are satisfied.
- Authorization, validation, error handling, and empty states are implemented.
- Student safety and privacy implications have been reviewed.
- The experience is accessible and responsive for its supported devices.
- Required tests and quality gates pass.
- Operational behavior and failure modes are understood.
- Documentation and environment examples are updated when affected.
- No unrelated changes, secrets, or personal data are included.
