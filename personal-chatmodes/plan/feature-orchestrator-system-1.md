---
goal: Implement 6-Step Founder-Friendly Development Workflow System
version: 2.0
date_created: 2025-10-24
last_updated: 2025-10-24
owner: Non-Technical Founder
status: 'Planned'
tags: ['feature', 'workflow', 'simple', 'founder-friendly', 'react-native']
---

# 6-Step Development Workflow System

![Status: Planned](https://img.shields.io/badge/status-Planned-blue)

## Introduction

**For Non-Technical Founders**: This creates a simple 6-step workflow where you describe what you want, and AI guides you through building it properly for your React Native/Expo app.

### Your Simple 6-Step Flow

```
Step 1: YOUR REQUEST
"I want a dashboard with + icons that opens modules"
        ↓
Step 2: REQUEST ENHANCEMENT
AI clarifies and improves your idea with proper technical terms
        ↓
Step 3: BUILD PLAN
AI creates a step-by-step implementation plan
        ↓
Step 4: CREATE TESTS FIRST (TDD - Red Phase)
AI writes tests that will fail (because code doesn't exist yet)
        ↓
Step 5: BUILD & ITERATE (Green → Refactor)
AI writes code to pass tests, then improves it
• Write minimum code to pass tests (Green)
• Improve and clean up code (Refactor)
• Repeat until all tests pass
        ↓
Step 6: REVIEW & ENHANCE
AI reviews everything for quality, security, performance
```

**Real Example:**

```
You: "Dashboard with + icons for modules"
  ↓
Step 2: "Modular dashboard with Pressable components, modal selection, 
         Zustand state, FlashList for performance..."
  ↓
Step 3: Implementation plan with phases and tasks
  ↓
Step 4: Test files created (they fail - that's good!)
  ↓
Step 5: Code written → Tests pass → Code improved → All tests pass
  ↓
Step 6: Everything reviewed, enhanced, ready to ship ✅
```

## 1. Requirements & Constraints

### What You Get (Simple Version)

- **REQ-001**: Each step is clear and tells you what happens next
- **REQ-002**: Every mode understands your React Native/Expo/Supabase tech stack
- **REQ-003**: TDD cycle (Red-Green-Refactor) is built into Step 5
- **REQ-004**: You can skip steps if you want (but don't skip tests!)
- **REQ-005**: Each step gives you clear, structured output
- **REQ-006**: Everything is tailored to mobile app development

### Your Tech Stack (From project.md)

Every mode knows you're building with:

- **Frontend**: React Native 0.81.4 + Expo SDK 54
- **Language**: TypeScript (strict mode)
- **UI**: Gluestack UI + NativeWind
- **State**: TanStack Query + Zustand
- **Backend**: Supabase
- **Testing**: Jest + React Native Testing Library + Detox
- **Mobile**: iOS & Android support

### Simple Rules

- **RULE-001**: Start at Step 1 (your request), end at Step 6 (review)
- **RULE-002**: Don't skip Step 4 (tests first!) - this is TDD magic
- **RULE-003**: Step 5 loops (write code → test → improve) until tests pass
- **RULE-004**: If Step 6 finds issues → Quick fix → Step 6 again
- **RULE-005**: Each mode tells you exactly what to do next

## 2. Implementation Steps

### Phase 1: Create Step 2 - Request Enhancement Mode

**GOAL**: Build the mode that makes your vague ideas crystal clear

| Task | Description | Completed | Date |
|------|-------------|-----------|------|
| TASK-001 | Create `step-2-enhance-request.chatmode.md` for clarifying user requests | | |
| TASK-002 | Add React Native/Expo/Supabase vocabulary translation | | |
| TASK-003 | Add mobile-specific enhancements (offline, platform, performance) | | |
| TASK-004 | Output format: Enhanced request + key features + tech decisions | | |

### Phase 2: Create Step 3 - Build Plan Mode

**GOAL**: Build the mode that creates structured implementation plans

| Task | Description | Completed | Date |
|------|-------------|-----------|------|
| TASK-005 | Create `step-3-build-plan.chatmode.md` (simplified planner) | | |
| TASK-006 | Accept enhanced request from Step 2 as input | | |
| TASK-007 | Output clear phases with specific tasks | | |
| TASK-008 | Include React Native patterns, components, state management | | |

### Phase 3: Create Step 4 - TDD Red Phase Mode

**GOAL**: Build the mode that writes tests FIRST (this is the magic!)

| Task | Description | Completed | Date |
|------|-------------|-----------|------|
| TASK-009 | Create `step-4-tdd-red.chatmode.md` for test creation | | |
| TASK-010 | Accept build plan from Step 3 as input | | |
| TASK-011 | Generate Jest unit tests for React Native components | | |
| TASK-012 | Generate React Native Testing Library integration tests | | |
| TASK-013 | Generate Detox E2E tests for critical flows | | |
| TASK-014 | Add mobile-specific tests (offline, platform, gestures) | | |
| TASK-015 | Verify all tests FAIL (Red phase - tests before code!) | | |

### Phase 4: Create Step 5 - Build & Iterate Mode (Green + Refactor)

**GOAL**: Build the mode that creates code and improves it through TDD cycle

| Task | Description | Completed | Date |
|------|-------------|-----------|------|
| TASK-016 | Create `step-5-build-iterate.chatmode.md` with TDD integration | | |
| TASK-017 | Accept tests from Step 4 as input | | |
| TASK-018 | **GREEN Phase**: Write minimum code to pass tests | | |
| TASK-019 | Run tests, verify they pass | | |
| TASK-020 | **REFACTOR Phase**: Improve code quality without breaking tests | | |
| TASK-021 | Loop: GREEN → REFACTOR until all tests pass and code is clean | | |
| TASK-022 | Use React Native/Expo best practices throughout | | |

### Phase 5: Create Step 6 - Review & Enhance Mode

**GOAL**: Build the final quality check mode

| Task | Description | Completed | Date |
|------|-------------|-----------|------|
| TASK-023 | Create `step-6-review-enhance.chatmode.md` (simplified review) | | |
| TASK-024 | Check React Native performance (FlashList, memoization) | | |
| TASK-025 | Check mobile-specific concerns (offline, platform, accessibility) | | |
| TASK-026 | Check Supabase integration (RLS, queries, auth) | | |
| TASK-027 | If issues found → Quick fix → Re-review | | |
| TASK-028 | If all good → Output "✅ Ready to Ship" summary | | |

### Phase 6: Documentation & Quick Start

**GOAL**: Make it easy for you to use

| Task | Description | Completed | Date |
|------|-------------|-----------|------|
| TASK-029 | Create simple workflow diagram (6 boxes with arrows) | | |
| TASK-030 | Create "Quick Start for Founders" guide | | |
| TASK-031 | Add example: Dashboard feature start to finish | | |
| TASK-032 | Add cheat sheet: When to use each step | | |

## 3. Why These 6 Steps? (Alternatives We Rejected)

- **ALT-001**: "Just one AI that does everything"
  - **Why not**: Too complex, hard to control, can't track progress
  - **Why 6 steps**: Clear, trackable, you know exactly where you are

- **ALT-002**: "Skip the tests, just build it"
  - **Why not**: Bugs, broken features, impossible to maintain
  - **Why TDD**: Tests first = fewer bugs + confidence when changing code

- **ALT-003**: "Build first, test later"
  - **Why not**: Hard to test after, usually skipped, tests miss edge cases
  - **Why TDD first**: Forces good design, comprehensive testing, quality built-in

- **ALT-004**: "AI decides everything automatically"
  - **Why not**: You lose control, can't learn, hard to debug
  - **Why human-in-loop**: You approve each step, learn the process, stay in control

## 4. Dependencies

### File Dependencies

- **DEP-001**: Existing planner mode (`chatmodes/planner/implementation-plan.chatmode.md`)
- **DEP-002**: Existing execution mode (`chatmodes/main_coder/execution_chatmode.txt`)
- **DEP-003**: Existing debug mode (`chatmodes/bugreview/debug_chatmode.txt`)
- **DEP-004**: Existing review mode (`chatmodes/bugreview/review_chatmode.txt`)
- **DEP-005**: Project context file (`project.md`)
- **DEP-006**: Chatmode examples from `https://github.com/github/awesome-copilot/tree/main/chatmodes`

### Tool Dependencies

- **DEP-007**: VS Code with GitHub Copilot Chat extension
- **DEP-008**: Markdown rendering for chatmode files
- **DEP-009**: YAML/JSON parsing for configuration files

### Knowledge Dependencies

- **DEP-010**: Understanding of React Native/Expo development workflow
- **DEP-011**: Understanding of TDD principles and practices
- **DEP-012**: Understanding of requirements engineering
- **DEP-013**: Familiarity with existing chatmode format and conventions

## 5. Files to Create (Your 6 Modes)

### The 6 Chat Mode Files

- **FILE-001**: `chatmodes/step-2-enhance-request.chatmode.md`
  - What it does: Takes your vague idea and makes it crystal clear
  - Knows about: React Native, Expo, Supabase, mobile best practices
  - Output: Enhanced request with technical details

- **FILE-002**: `chatmodes/step-3-build-plan.chatmode.md`
  - What it does: Creates step-by-step implementation plan
  - Knows about: Component structure, state management, navigation
  - Output: Phased plan with specific tasks

- **FILE-003**: `chatmodes/step-4-tdd-red.chatmode.md`
  - What it does: Writes tests BEFORE code (Red phase of TDD)
  - Knows about: Jest, React Native Testing Library, Detox, mobile testing
  - Output: Test files that fail (because code doesn't exist yet)

- **FILE-004**: `chatmodes/step-5-build-iterate.chatmode.md`
  - What it does: Writes code to pass tests, then improves it (Green + Refactor)
  - Knows about: React Native components, hooks, performance, offline support
  - Output: Working, tested, clean code

- **FILE-005**: `chatmodes/step-6-review-enhance.chatmode.md`
  - What it does: Final quality check before shipping
  - Knows about: Performance, security, accessibility, mobile patterns
  - Output: Quality report + enhancements or "✅ Ship it!"

- **FILE-006**: `docs/founder-workflow-guide.md`
  - What it does: Simple guide for you to follow
  - Contains: Examples, cheat sheet, troubleshooting
  - Output: Confidence using the system

## 6. How to Know It Works (Testing)

### Test the Complete Flow

- **TEST-001**: The Dashboard Example (Your Real Use Case!)
  - Step 1: You say "I want a dashboard with + icons that opens modules"
  - Step 2: AI enhances it with React Native terms
  - Step 3: AI creates implementation plan
  - Step 4: AI writes tests (they fail - good!)
  - Step 5: AI writes code → tests pass → AI improves code
  - Step 6: AI reviews → "✅ Ready to ship"
  - **Success**: You have a working, tested dashboard feature

### Test Each Step Works

- **TEST-002**: Step 2 makes vague ideas clear
  - Input: "I need a list of properties"
  - Output: "FlashList component with PropertyCard, Zustand state, offline support..."

- **TEST-003**: Step 4 creates proper tests
  - Input: Build plan for property list
  - Output: Jest tests, RTL tests, Detox E2E tests (all failing)

- **TEST-004**: Step 5 follows Red-Green-Refactor
  - Phase 1: Tests fail (Red) ✅
  - Phase 2: Write code, tests pass (Green) ✅
  - Phase 3: Improve code, tests still pass (Refactor) ✅

- **TEST-005**: Step 6 catches issues
  - Scenario: Code with performance problem
  - Output: "Found: FlatList with 500 items. Fix: Use FlashList instead."

## 7. What Could Go Wrong (And How to Fix It)

### Potential Issues

- **ISSUE-001**: "I don't want to go through 6 steps every time"
  - Solution: Skip steps for simple changes (but always keep Step 4 - tests!)
  - Example: Bug fix → Skip to Step 5 → Step 6

- **ISSUE-002**: "The AI is giving me too much detail"
  - Solution: Each mode has "Summary for Founder" section with just what you need
  - You control: Ask for "simple version" anytime

- **ISSUE-003**: "I changed my mind halfway through"
  - Solution: Go back to any step, modes are flexible
  - Example: At Step 5, decide to change plan → Back to Step 3

- **ISSUE-004**: "Tests are failing and I don't know why"
  - Solution: Step 5 is built for this! It iterates until tests pass
  - Trust the process: Red (fail) → Green (pass) → Refactor (improve)

### What You Should Know

- **You're in control**: You approve each step before moving forward
- **Nothing is automatic**: You invoke each mode when ready
- **You can skip steps**: But Step 4 (tests) is highly recommended!
- **Modes are project-aware**: Every mode knows your React Native/Expo stack
- **It's iterative**: Especially Step 5 - it loops until perfect

## 8. What to Read First

### For Non-Technical Founders (You!)

- **Start here**: This plan (you're reading it!)
- **Your tech stack**: [project.md](../project.md) - What your app is built with
- **TDD explained simply**: [martinfowler.com/bliki/TestDrivenDevelopment.html](https://martinfowler.com/bliki/TestDrivenDevelopment.html)
- **After modes are built**: `docs/founder-workflow-guide.md` - Your cheat sheet

### For Your Developer/AI (Technical)

- [Existing Execution Mode](../chatmodes/main_coder/execution_chatmode.txt) - Code quality standards
- [Existing Review Mode](../chatmodes/bugreview/review_chatmode.txt) - Quality assurance process
- [Chatmode Format](https://github.com/github/awesome-copilot/tree/main/chatmodes) - How to create modes

### Why This Matters

**TDD (Test-Driven Development)** is the secret:

1. Write tests first (they fail) = Red
2. Write minimum code to pass = Green  
3. Improve the code = Refactor
4. Result: Quality built-in, not bolted-on

**Your React Native Stack** makes mobile apps:

- Works on iOS and Android from one codebase
- Fast, native performance
- Modern UI components
- Offline support built-in

---

## How to Build This (For Your Developer/AI)

### Build Order (Do These in Sequence)

1. **Phase 1**: Create Step 2 mode (enhance requests) - Start here!
2. **Phase 2**: Create Step 3 mode (build plans)
3. **Phase 3**: Create Step 4 mode (TDD Red phase) - The most important!
4. **Phase 4**: Create Step 5 mode (Build & Iterate with Green/Refactor)
5. **Phase 5**: Create Step 6 mode (Review & Enhance)
6. **Phase 6**: Create founder guide and test with real example

### Success = This Works

Test with your real example:

**You say:** "I want a dashboard template that has + icons that opens modules with components to place in your desired location"

**Then:**

- Step 2: AI clarifies with React Native/Expo terms
- Step 3: AI creates phased implementation plan
- Step 4: AI writes Jest/RTL/Detox tests (they fail)
- Step 5: AI writes code → tests pass → AI refactors
- Step 6: AI reviews for mobile performance/security
- **Result**: ✅ Working dashboard with tests, ready to ship

### Key Requirements for Builder

1. **Every mode must know project.md** (React Native, Expo, Supabase, TypeScript)
2. **Step 4 is critical** (TDD Red phase - write tests first!)
3. **Step 5 must loop** (Green → Refactor until perfect)
4. **Keep it simple** (Non-technical founder should understand flow)
5. **Each mode outputs clear "Next Step" instruction**
