---
name: webapp-auditor
description: Comprehensive web application auditing, fixing, testing, and recompilation. Use this skill when a user requests a complete website audit, security review, vulnerability check, code review, bug fixing, test coverage improvement, or a full review and rebuild of a web project.
---

# Web Application Auditor

This skill provides a structured, step-by-step workflow for performing a complete audit of a web application, fixing identified issues, ensuring robust test coverage, and recompiling the project.

## Workflow

When invoked to audit a web application, follow these sequential phases. **Crucially, you MUST pause and communicate with the user after Phase 1 to ensure alignment before making any changes to the codebase.**

### Phase 1: Deep Analysis & Audit

1. **Project Discovery**: Identify the tech stack by examining root files (`package.json`, `requirements.txt`, `Dockerfile`, `docker-compose.yml`, etc.). Determine the build system, test runner, and primary languages.
2. **Dependency Audit**: Run package manager audit tools to find known vulnerabilities in dependencies (e.g., `npm audit`, `pip-audit`, `safety`).
3. **Static Code Analysis**: Review the codebase for syntax errors, deprecated functions, code smells, and anti-patterns. Use available linters if configured (e.g., `npm run lint`, `flake8`, `ruff`).
4. **Security & Vulnerability Scan**: Check for common security vulnerabilities (OWASP Top 10, injection flaws, XSS, misconfigured CORS, hardcoded secrets/API keys).
5. **Performance & Architecture Review**: Identify bottlenecks, inefficient database queries, memory leaks, or architectural flaws. Look for refactoring opportunities that could drastically improve performance or maintainability.
6. **Test Coverage Assessment**: Evaluate the current test suite. Identify gaps in unit, integration, and end-to-end tests. If no tests exist, note this as a critical gap.
7. **Reporting**: Compile a comprehensive report of all findings using the template below. **Present this to the user and WAIT for their approval before proceeding to Phase 2.**

#### Audit Report Template
Always use this exact structure for the Phase 1 report:

```markdown
# Web Application Audit Report: [Project Name]

## Executive Summary
[1-2 paragraphs summarizing the overall health of the application, major risks, and the primary tech stack detected.]

## Findings by Severity

### Critical (Immediate Action Required)
*Security vulnerabilities, breaking bugs, or severe data loss risks.*
- **[Component/File]**: [Description of issue] - [Proposed Fix]

### High (Address Soon)
*Major performance bottlenecks, architectural flaws, or significant test gaps.*
- **[Component/File]**: [Description of issue] - [Proposed Fix]

### Medium (Technical Debt)
*Code smells, deprecated functions, or minor inefficiencies.*
- **[Component/File]**: [Description of issue] - [Proposed Fix]

### Low (Enhancements)
*Formatting, minor optimizations, or nice-to-have refactors.*
- **[Component/File]**: [Description of issue] - [Proposed Fix]

## Next Steps
[Ask the user which severity levels or specific items they want to authorize fixing in Phase 2.]
```

### Phase 2: Strategic Remediation

1. **Prioritize Fixes**: Based on user feedback from Phase 1, address authorized issues. Always start with Critical security vulnerabilities and breaking errors.
2. **Implement Fixes**: Modify the code to resolve the identified issues. Ensure fixes adhere to the project's coding standards and improve the overall logic. Group related fixes into logical commits if using git.
3. **Iterative Verification**: Double-check that each change resolves the issue without introducing regressions. Do not apply all fixes at once blindly; verify as you go.

### Phase 3: Test Suite Fortification

1. **Evaluate Current State**: 
   - **If tests exist**: Run the suite. Update any tests broken by Phase 2 fixes.
   - **If no tests exist**: Create a foundational test setup (e.g., configure Jest/Vitest for JS, Pytest for Python) and write initial tests for core business logic.
2. **Write New Tests**: Create new tests to cover the vulnerabilities fixed in Phase 2, edge cases, and any newly added logic. Ensure the tests are meaningful, not just chasing coverage percentages.
3. **Run Tests**: Execute the entire test suite and ensure a 100% pass rate.

### Phase 4: Recompilation and Verification

1. **Build Process**: Run the project's build or compilation commands (e.g., `npm run build`, `tsc`, `docker-compose build`, `pip install -r requirements.txt`).
2. **Resolve Build Errors**: If the build fails, deeply diagnose and fix the compilation errors, then retry until successful.
3. **Final Verification**: Start the application in a local or staging environment (e.g., `npm run dev`, `python manage.py runserver`). Verify that the server starts without crashing, responds with HTTP 200 on the main routes, and shows no critical console errors.
4. **Final Delivery**: Compile the totality of the work into a final summary report for the user, detailing exactly what was changed, what tests were added, and confirming the build status.
