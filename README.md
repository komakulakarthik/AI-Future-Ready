# AI Future Ready

AI Future Ready is a learning platform that helps students in grades 6–10 understand and use artificial intelligence effectively, critically, creatively, and safely.

The product is designed as a structured learning environment—not an unrestricted chatbot or a shortcut for completing schoolwork. Students learn how to write useful prompts, evaluate AI-generated answers, verify claims, recognize bias, protect their privacy, and decide when AI is appropriate to use.

## Project status

The project is currently in the product-planning and architecture phase. Application scaffolding and implementation will begin after the foundational product, safety, privacy, and technical decisions are approved.

The application will be built as a TypeScript-first Next.js monolith using the App Router.

## Who it serves

- **Students in grades 6–8:** guided activities, concrete examples, and shorter learning exercises.
- **Students in grades 9–10:** deeper evaluation, independent practice, and more complex responsible-use scenarios.
- **Educators:** curriculum assignment and student progress visibility.
- **Administrators:** curriculum publishing, access management, and safety review.

## Initial learning path

The first curriculum is organized into six modules:

1. **What AI is** — capabilities, limitations, and common uses.
2. **Prompt fundamentals** — goals, context, constraints, and output formats.
3. **Check before you trust** — hallucinations, sources, and claim verification.
4. **Privacy and safety** — protecting personal information and reporting unsafe content.
5. **Bias, fairness, and responsibility** — perspectives, accountability, and appropriate use.
6. **AI as a learning partner** — brainstorming, explaining, revising, and learning without replacing independent thought.

## Product principles

- Learning outcomes come before engagement metrics.
- AI should coach student thinking, not complete the thinking for them.
- Human-reviewed curriculum is the source of truth.
- Student safety and privacy are system requirements.
- Important assessments use deterministic scoring.
- Core learning remains available when an AI provider is unavailable.
- Accessibility and age appropriateness are part of feature completion.
- AI-generated material is clearly distinguished from authored curriculum.

## Planned MVP

The initial release is expected to include:

- Grade-band onboarding and student learning paths.
- Interactive lessons and scenario-based activities.
- A guided Prompt Builder.
- Response Detective exercises for evaluating AI output.
- Quizzes, mastery, and progress tracking.
- Educator classrooms and assignments.
- Versioned, human-reviewed curriculum publishing.
- Server-side AI integration with input and output safety controls.
- Private achievements and age-appropriate feedback.
- Reporting for unsafe or inaccurate content.

An unrestricted chatbot, public social features, public leaderboards, advertising, and AI-generated final grades are explicitly outside the MVP.

## Documentation

- [Product plan](plan.md) — vision, scope, curriculum, architecture direction, delivery phases, and launch criteria.
- [Engineering standards](docs/code-quality.md) — code organization, quality gates, accessibility, AI safety, and student-data requirements.

Architecture decisions will be recorded in `docs/decisions` before the corresponding implementation begins.

## Development

The application has not been scaffolded yet. Setup, development, testing, and deployment instructions will be added when the technical foundation is created.

## Contributing

All contributors, including AI-assisted contributors, must follow the engineering standards and protect student privacy. Changes involving authentication, authorization, student data, curriculum publication, AI safety, or data retention require explicit review.

Use [Conventional Commits](https://www.conventionalcommits.org/) for commit messages.

## License

A license has not yet been selected. Until one is added, the repository should be treated as all rights reserved.
