---
name: webapp-auditor
description: Comprehensive web application auditing, fixing, testing, and recompilation. Use this skill when a user requests a complete website audit, vulnerability check, bug fixing, test coverage improvement, or a full review and rebuild of a web project.
---

# Web Application Auditor

This skill provides a structured, step-by-step workflow for performing a complete audit of a web application, fixing identified issues, ensuring robust test coverage, and recompiling the project.

## Core Philosophy

A complete audit and fix cycle should not be a black box. It requires breaking down the project into root issues, analyzing them deeply, and iterating over logic to ensure the best outcomes. Do not blindly apply fixes without understanding the architectural implications. Challenge assumptions and look for moonshot optimizations where applicable.

## Workflow

When invoked to audit a web application, follow these sequential phases. **Crucially, pause and communicate with the user after Phase 1 to ensure alignment before making sweeping changes.**

### Phase 1: Deep Analysis & Audit
1. **Static Code Analysis**: Review the codebase for syntax errors, deprecated functions, code smells, and anti-patterns.
2. **Vulnerability Scan**: Check for common security vulnerabilities (e.g., OWASP Top 10, injection flaws, XSS, insecure dependencies, misconfigured CORS).
3. **Performance & Architecture Review**: Identify bottlenecks, inefficient database queries, memory leaks, or architectural flaws. Look for "moonshot" refactoring opportunities that could drastically improve performance or maintainability.
4. **Test Coverage Assessment**: Evaluate the current test suite. Identify gaps in unit, integration, and end-to-end tests.
5. **Reporting**: Compile a comprehensive, well-reasoned report of all findings. Present this to the user in digestible pieces. **Wait for user feedback and approval before proceeding to Phase 2.**

### Phase 2: Strategic Remediation
1. **Prioritize Fixes**: Address critical security vulnerabilities and breaking errors first. Group related fixes to maintain system stability.
2. **Implement Fixes**: Modify the code to resolve the identified issues. Ensure fixes adhere to the project's coding standards and improve the overall logic.
3. **Iterative Verification**: Double-check that each change resolves the issue without introducing regressions.

### Phase 3: Test Suite Fortification
1. **Update Existing Tests**: Modify existing tests if they are broken or outdated due to the recent fixes.
2. **Write New Tests**: Create new tests to cover the previously identified vulnerabilities, edge cases, and any newly added logic. Ensure the test suite is robust and meaningful, not just chasing coverage percentages.
3. **Run Tests**: Execute the entire test suite and ensure a 100% pass rate.

### Phase 4: Recompilation and Verification
1. **Build Process**: Run the project's build or compilation commands (e.g., `npm run build`, `tsc`, `docker-compose build`, `pip install -r requirements.txt`).
2. **Resolve Build Errors**: If the build fails, deeply diagnose and fix the compilation errors, then retry.
3. **Final Render/Run**: Start the application in a local or staging environment to verify that it renders correctly, functions as expected, and that the fixes have been successfully integrated.
4. **Final Delivery**: Compile the totality of the work into a final summary report for the user.

## Best Practices
- **Step-by-Step Execution**: Break concepts into root issues. Work in digestible pieces.
- **Challenge the Status Quo**: If the current architecture is fundamentally flawed, suggest alternative solutions rather than just patching bad code.
- **Deep Research**: Prefer deeply researched and well-reasoned assistance to quick outputs. Iterate over your logic.
