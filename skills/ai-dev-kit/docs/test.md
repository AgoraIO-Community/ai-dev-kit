---
description: Test that progressive disclosure docs work correctly
---

Verify that the progressive disclosure documentation in this repo gives AI agents the right context at the right level — L0+L1 for common tasks, L2 only when depth is needed.

## How It Works

For each test question, launch a fresh sub-agent with access to this repo. The sub-agent should navigate the docs naturally (starting from AGENTS.md or L0). After it answers, check which files it actually read to determine whether the PD loading pattern worked.

## Rules

- Each test question must be answered by a **fresh sub-agent** (no carried-over context)
- Do NOT tell the sub-agent which docs to read — let it navigate naturally
- After each answer, record which files the sub-agent read (from its tool use)
- A test **passes** if the agent got a correct answer AND loaded the right level:
  - L0+L1 only for routine questions (setup, build, test, conventions)
  - L0+L1+specific L2 for deep questions (architecture details, edge cases)
- A test **fails** if:
  - The agent loaded L2 unnecessarily (wasted context)
  - The agent gave a wrong or incomplete answer (doc gap)
  - The agent couldn't find the answer at all (missing coverage)

## Workflow

### 1. Generate test questions

Create questions in these categories by reading the repo's actual codebase and recent git history:

**Setup & Build** — can an agent set up and build this project from docs alone?
- How do I install dependencies and build this project?
- What environment variables are required?
- What's the minimum system requirement?

**Test & Run** — can an agent run and test the project?
- How do I run the test suite?
- How do I start the project locally?

**Conventions** — does the agent know the project's patterns?
- What naming conventions does this project use?
- How should I handle errors in this codebase?

**Development** — can an agent implement a feature?
- Read `git log --oneline --since="3 months ago"` to find 2-3 recent features
- For each, write a question like: "How would I add a similar feature to [area]?"
- These should require understanding architecture, not just setup

**Deep Dive** — questions that should require L2
- Pick a complex subsystem and ask about its internals
- Ask about an edge case or non-obvious behavior
- These should only be answerable with L2 detail

If `$ARGUMENTS` specifies a focus area, weight questions toward that area.

### 2. Run tests

For each question:

1. Launch a fresh sub-agent with access to the repo
2. Ask the question
3. Record: the answer, which files were read, whether the answer was correct
4. Classify: L0+L1 sufficient, or L2 needed

### 3. Analyze results

For each test, determine:

| Result | Meaning | Action |
| --- | --- | --- |
| Correct answer, right level loaded | PD docs working | None |
| Correct answer, L2 loaded unnecessarily | L1 summary too thin | Expand the relevant L1 section |
| Wrong/incomplete answer, L2 exists but wasn't found | Bad cross-references | Fix `## Related Deep Dives` links in L1 |
| Wrong/incomplete answer, no L2 exists | Missing deep dive | Create the L2 file |
| Agent couldn't find answer at all | Missing L1 coverage | Add to the relevant L1 file |

### 4. Write results

Save results to `docs/ai/test-results.md`:

```markdown
# PD Documentation Test Results

Tested: [date]
Agent: [which agent/model]
Repo: [repo name]

## Summary

- Total questions: N
- Passed: N (correct answer, right level)
- L1 gaps: N (needed L2 but L1 should have sufficed)
- L2 gaps: N (needed L2 that doesn't exist)
- Cross-ref issues: N (L2 exists but wasn't found)

## Results

### Setup & Build

| # | Question | Answer Correct? | Files Read | Level Loaded | Result |
|---|----------|-----------------|------------|--------------|--------|
| 1 | How do I build? | Yes | L0, 01_setup | L0+L1 | Pass |

### Test & Run
...

### Conventions
...

### Development
...

### Deep Dive
...

## Recommended Fixes

- [ ] Expand 01_setup.md section on [topic] (questions N, N failed)
- [ ] Add deep dive: [topic].md (question N needed detail not in L1)
- [ ] Fix Related Deep Dives link in 02_architecture.md (question N)
```

### 5. Fix and retest

If any tests failed, fix the docs and rerun the failing questions only. Update test-results.md with the retest.
