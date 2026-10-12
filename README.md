Act as a Senior Software Architect, QA Automation Architect, and GitHub Copilot Agent Skills specialist.

I want you to create a reusable custom agent and Agent Skill for generating industry-standard acceptance tests for my existing CRUD application.

The solution must follow established acceptance-testing practices, BDD principles where appropriate, risk-based testing, requirements traceability, and maintainable test automation practices.

1. Inspect the existing repository

Before creating files, inspect the repository and determine:

* Application architecture, programming language, and framework.
* API controllers, route attributes, and endpoint mappings.
* HTTP methods, route parameters, query parameters, request DTOs, and response DTOs.
* Business logic, services, repositories, and database operations.
* Authentication, authorization, validation, and exception handling.
* Existing unit, integration, API, and acceptance-test projects.
* Existing test frameworks, naming conventions, fixtures, and CI/CD configuration.
* Existing GitHub Copilot custom agents and skills, if any.

Do not assume a framework or application feature exists without evidence.

Do not modify existing application code during initial discovery.

2. Create the custom agent

Create a repository-level custom agent at:

.github/agents/acceptance-test-agent.agent.md

The agent must:

* Act as a senior acceptance-test engineer.
* Analyze application requirements and existing API behavior.
* Invoke or follow the acceptance-testing skill when relevant.
* Coordinate the testing workflow from endpoint analysis through test reporting.
* Ask for clarification when business expectations are ambiguous.
* Require review before destructive operations or changes outside the approved scope.
* Never claim tests passed unless execution evidence exists.

Use the custom-agent format supported by the current GitHub Copilot environment.

3. Create the reusable Agent Skill

Create the skill at:

.github/skills/acceptance-test-engineer/SKILL.md

Use the Agent Skills format supported by GitHub Copilot, including valid YAML frontmatter with a clear name and description.

The skill must define the following workflow.

Phase 1: Endpoint discovery and analysis

Discover all API endpoints from the actual application code and route configuration.

Build an endpoint inventory containing:

* Endpoint ID.
* HTTP method and route.
* Controller or handler.
* Business purpose.
* Request and response contracts.
* Expected HTTP status codes where documented.
* Validation rules.
* Authentication and authorization requirements.
* Service, repository, and database dependencies.
* Source file references.

Map endpoints to CRUD resources and identify undocumented or ambiguous behavior.

Phase 2: Requirements and acceptance criteria

Derive acceptance criteria from approved requirements, user stories, API specifications, and verified business rules.

Use Given/When/Then scenarios where appropriate.

Do not treat implementation behavior as proof that the behavior is correct. Identify discrepancies between implementation and documented requirements.

Phase 3: Test design

Generate appropriate scenarios using established testing techniques:

* Positive and negative testing.
* Equivalence partitioning.
* Boundary value analysis.
* Decision tables for complex rules.
* State-transition testing where applicable.
* Authentication and authorization testing.
* Data validation and persistence testing.
* Error handling and exception scenarios.
* Concurrency and idempotency where applicable.
* Integration and regression testing.

For CRUD APIs, consider creation, retrieval, updates, deletion, nonexistent resources, invalid inputs, duplicate records, data integrity, and referential constraints where relevant.

Do not generate tests for unsupported features without identifying them as assumptions or clarification items.

Phase 4: Test automation

Inspect the existing test framework before generating code.

Use the project’s established testing libraries and conventions. For .NET applications, evaluate the existing use of xUnit, NUnit, MSTest, HttpClient, integration-test fixtures, and ASP.NET Core test infrastructure rather than selecting a new framework without justification.

Tests must be deterministic, maintainable, isolated, and focused on observable business outcomes.

Use realistic test data, reliable cleanup, meaningful assertions, and appropriate dependency boundaries.

Avoid arbitrary sleeps, brittle implementation-specific assertions, shared mutable state, and unnecessary mocking.

Do not weaken assertions to make tests pass.

Phase 5: Requirements traceability

Map each requirement and acceptance criterion to one or more test cases.

Each test case should include:

* Unique test ID.
* Requirement or acceptance-criterion ID.
* Scenario title.
* Business purpose.
* Preconditions.
* Test data.
* Execution steps.
* Expected result.
* Priority and risk rationale.
* Automation status.
* Actual result and evidence when executed.

Identify acceptance criteria without tests and tests without a documented requirement or justified risk-based purpose.

Phase 6: Execution and reporting

Run only approved tests in an authorized environment.

Capture failures, relevant logs, assertion details, and available evidence.

Classify results accurately as:

* PASS
* FAIL
* BLOCKED
* NOT RUN
* INCONCLUSIVE

Distinguish application defects from test defects, configuration problems, environment failures, and insufficient evidence.

Never fabricate execution results or claim complete coverage without evidence.

Produce a concise report covering test results, requirement coverage, unresolved defects, gaps, and release risks.

4. Deliverables

Create or update the following files as appropriate:

.github/agents/acceptance-test-agent.agent.md

.github/skills/acceptance-test-engineer/SKILL.md

docs/acceptance-testing/endpoint-inventory.md

docs/acceptance-testing/crud-behavior-matrix.md

docs/acceptance-testing/api-contract-gaps.md

docs/acceptance-testing/acceptance-test-plan.md

Use existing documentation conventions if the repository already has an appropriate structure.

Create additional reference files only when they provide clear value. Do not generate unnecessary boilerplate.

5. Industry-standard quality requirements

Use these practices:

* ISTQB-aligned acceptance-testing principles.
* BDD and Gherkin where they improve business readability.
* Risk-based test prioritization.
* Requirements-to-test traceability.
* Maintainable test automation and clear separation of test levels.
* Appropriate security and data-integrity validation.
* CI/CD integration compatible with the existing repository.
* Explicit quality gates and transparent test reporting.

Treat these as testing principles, not a claim of formal certification or compliance.

6. Safety and implementation rules

* Begin with repository analysis.
* Do not access production systems or create real transactions.
* Do not expose secrets, tokens, certificates, or sensitive test data.
* Do not modify production code merely to satisfy generated tests.
* Do not execute destructive database operations without explicit approval.
* Do not overwrite existing agent, skill, or test files without reviewing them.
* Separate verified facts, assumptions, and unanswered questions.
* Prefer the smallest useful implementation that follows existing conventions.

7. Execution plan

Work in this order:

1. Analyze the repository and report findings.
2. Propose the agent and skill structure.
3. Create the custom agent and skill.
4. Validate their file formats and configuration.
5. Analyze CRUD endpoints and produce the initial documentation.
6. Present a summary of files created or changed and any remaining gaps.

Do not generate or execute acceptance tests until the endpoint analysis and expected business behavior have been reviewed.

First inspect the repository and explain the proposed implementation. Then proceed with the safe, in-scope changes, requesting approval before any destructive or production-impacting action.