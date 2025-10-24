# 🚀 HANDOFF TO EXECUTION MODE

**Date**: 2025-10-24  
**From**: Planning Mode  
**To**: Execution Mode (Coding Agent)  
**Implementation Plan**: `feature-orchestrator-system-1.md`

---

## 📋 What You're Building

Create a **6-step founder-friendly development workflow system** consisting of 6 chatmode files that guide a non-technical founder from idea to production-ready code using Test-Driven Development.

## ✅ Critical Requirements from chatmodeflow.md

### MUST Follow These Rules

1. **Follow GitHub Copilot Chatmode Guidelines**
   - Structure: `https://github.com/github/awesome-copilot/tree/main/chatmodes`
   - Use YAML frontmatter + markdown body
   - Include `description` and `tools` in frontmatter

2. **Reference Template Structure**
   - Use `chatmodes/planner/implementation-plan.chatmode.md` as structural reference
   - Maintain consistency with existing modes (execution, debug, review)

3. **Tailor to project.md Tech Stack**
   - **CRITICAL**: Every mode MUST reference and understand `project.md`
   - Tech Stack: React Native 0.81.4, Expo SDK 54, TypeScript, Gluestack UI, NativeWind, TanStack Query, Zustand, Supabase, Jest, Detox
   - Each mode must provide React Native/Expo/mobile-specific guidance

4. **Clear Objectives for Each Mode**
   - Each chatmode must have clear objectives
   - Each must have specific guidelines for AI agent
   - Each must have appropriate tools list

5. **TDD & Debug Modes are CRITICAL**
   - TDD mode (Step 4) must be very precise
   - Must ensure high code quality
   - Must be effective for problem-solving

## 🎯 The 6 Modes to Create

### Mode 1: Step 2 - Request Enhancement

**File**: `personal-chatmodes/chatmodes/step-2-enhance-request/enhance-request.chatmode.md`

**Purpose**: Transform vague founder requests into clear, technical specifications

**Key Requirements**:

- Input: Founder's plain English request
- Process: Enhance with React Native/Expo/Supabase terminology
- Output: Technical specification with components, state management, navigation, mobile considerations
- Must understand: Gluestack UI components, NativeWind styling, Expo Router, platform differences (iOS/Android)

**Example**:

```
Input: "Dashboard with + icons for modules"
Output: "Create a modular dashboard screen using:
- FlashList for performance with 100+ items
- Pressable components with HapticFeedback for + icons
- Modal from Gluestack UI for module selection
- Zustand store for dashboard state management
- Expo Router for navigation to module details
- Platform-specific safe area handling
- Offline-first with TanStack Query cache"
```

---

### Mode 2: Step 3 - Build Plan

**File**: `personal-chatmodes/chatmodes/step-3-build-plan/build-plan.chatmode.md`

**Purpose**: Create structured implementation plan from enhanced request

**Key Requirements**:

- Input: Enhanced technical specification from Step 2
- Process: Break down into phases with specific tasks
- Output: Implementation plan following `implementation-plan.chatmode.md` template
- Must include: Component structure, state management setup, API integration, testing strategy
- Must reference: Existing project patterns, file structure, naming conventions

**Example Output Structure**:

```
Phase 1: Setup & State Management
- Create Zustand store for dashboard state
- Define TypeScript types for modules
- Setup TanStack Query hooks for Supabase

Phase 2: UI Components
- Create DashboardScreen component
- Create ModuleCard component with + icon
- Create ModuleSelectionModal

Phase 3: Integration
- Connect to Supabase RLS policies
- Add offline support
- Test on iOS and Android
```

---

### Mode 3: Step 4 - TDD Red Phase (MOST CRITICAL!)

**File**: `personal-chatmodes/chatmodes/step-4-tdd-red/tdd-red.chatmode.md`

**Purpose**: Write comprehensive tests BEFORE any implementation code (Red Phase of TDD)

**CRITICAL Requirements from chatmodeflow.md**:

- ⚠️ "TTD and Debug modes need to be very precise in their instructions to ensure high code quality and effective problem-solving"
- Must be extremely detailed and methodical
- Must enforce test-first discipline
- Must cover all test types

**Key Requirements**:

- Input: Build plan from Step 3
- Process: Generate test files for ALL components, hooks, and features
- Output: Test suites that FAIL (because code doesn't exist yet)
- Must create:
  - **Unit Tests**: Jest tests for business logic, hooks, utilities
  - **Component Tests**: React Native Testing Library for UI components
  - **Integration Tests**: Feature workflows (create module, add to dashboard, etc.)
  - **E2E Tests**: Detox tests for critical user journeys
  - **Mobile-Specific Tests**: Platform checks, offline behavior, permission handling

**Test Coverage Requirements**:

- Happy path scenarios
- Edge cases (empty states, loading, errors)
- Mobile-specific (screen sizes, keyboard, gestures)
- Offline scenarios
- Platform differences (iOS vs Android)

**Example Output**:

```typescript
// DashboardScreen.test.tsx
describe('DashboardScreen', () => {
  it('should render dashboard with module cards', () => {
    // Test will FAIL - component doesn't exist yet
  });
  
  it('should open modal when + icon pressed', () => {
    // Test will FAIL - functionality doesn't exist yet
  });
  
  it('should work offline with cached data', () => {
    // Test will FAIL - offline support doesn't exist yet
  });
});
```

**Verification**: Mode must confirm ALL tests fail appropriately (Red phase complete)

---

### Mode 4: Step 5 - Build & Iterate (Green + Refactor)

**File**: `personal-chatmodes/chatmodes/step-5-build-iterate/build-iterate.chatmode.md`

**Purpose**: Implement code using Red-Green-Refactor TDD cycle

**Key Requirements**:

- Input: Test suites from Step 4 (all failing)
- Process: Implement in iterations following TDD cycle
- Output: Working, tested, clean code

**TDD Cycle Implementation**:

**GREEN PHASE (TASK-018, TASK-019)**:

1. Run tests → Confirm they fail (Red)
2. Write MINIMUM code to make ONE test pass
3. Run tests → Verify that test now passes
4. Repeat for next test
5. Continue until ALL tests pass (Green achieved)

**REFACTOR PHASE (TASK-020, TASK-021)**:

1. All tests passing? Good! Now improve the code
2. Extract components, improve naming, remove duplication
3. Run tests after EACH refactor → Must stay green
4. Apply React Native best practices:
   - Use React.memo for expensive components
   - Use useCallback for functions passed as props
   - Use FlashList instead of FlatList
   - Implement proper error boundaries
   - Add proper TypeScript types
5. Continue refactoring until code is clean and maintainable
6. Final test run → All tests must still pass

**ITERATE**: Loop Green → Refactor until code is production-ready

**React Native/Expo Specific Standards**:

- Use Gluestack UI components
- Follow NativeWind styling patterns
- Implement Expo Router navigation correctly
- Add Platform.select() for platform-specific code
- Ensure offline-first with TanStack Query
- Test on both iOS and Android
- Handle SafeArea properly
- Implement proper loading and error states

**Example Iteration**:

```
Iteration 1 (GREEN):
- Write basic DashboardScreen component
- Tests: 3/10 passing ✅

Iteration 2 (GREEN):
- Add + icon Pressable
- Tests: 6/10 passing ✅

Iteration 3 (GREEN):
- Add Modal functionality
- Tests: 10/10 passing ✅ (GREEN ACHIEVED!)

Iteration 4 (REFACTOR):
- Extract ModuleCard component
- Tests: 10/10 passing ✅

Iteration 5 (REFACTOR):
- Add React.memo optimization
- Improve TypeScript types
- Tests: 10/10 passing ✅

DONE: All tests passing + clean code ✅
```

---

### Mode 5: Step 6 - Review & Enhance

**File**: `personal-chatmodes/chatmodes/step-6-review-enhance/review-enhance.chatmode.md`

**Purpose**: Final quality assurance before shipping

**Key Requirements**:

- Input: Working code from Step 5 (all tests passing)
- Process: Comprehensive review across multiple dimensions
- Output: Quality report + enhancements OR "✅ Ready to Ship"

**Review Checklist**:

**React Native Performance**:

- FlashList used for large lists?
- Components memoized appropriately?
- No inline functions in render?
- Images optimized?
- Bundle size impact acceptable?

**Mobile-Specific**:

- Works on iOS and Android?
- Offline functionality works?
- Safe area handled properly?
- Keyboard behavior correct?
- Gestures work as expected?
- Permissions handled gracefully?

**Supabase Integration**:

- Row Level Security (RLS) policies correct?
- Queries optimized?
- Real-time subscriptions cleaned up?
- Error handling comprehensive?

**Code Quality**:

- TypeScript strict mode satisfied?
- No `any` types?
- Proper error boundaries?
- Accessibility labels present?
- Code is maintainable?

**Testing**:

- All tests passing?
- Coverage meets standards (>80%)?
- E2E tests cover critical paths?

**Security**:

- User input validated?
- No secrets in code?
- Secure storage used for sensitive data?

**Output Format**:

```
## Review Summary

✅ APPROVED / ⚠️ NEEDS MINOR FIXES / ❌ NEEDS MAJOR FIXES

### Strengths
- All tests passing (100% coverage)
- Excellent React Native performance patterns
- Proper offline support

### Issues Found
⚠️ Minor: Add accessibility labels to + icons
⚠️ Minor: Extract magic numbers to constants

### Recommended Enhancements
💡 Consider adding haptic feedback on + icon press
💡 Consider skeleton loading state

### Verdict
After fixing minor issues: ✅ Ready to Ship
```

If issues found → Quick fix → Re-run Step 6

---

### Mode 6: Founder Workflow Guide

**File**: `personal-chatmodes/docs/founder-workflow-guide.md`

**Purpose**: Simple guide for non-technical founders to use the system

**Contents**:

- Quick start guide
- Example workflow with dashboard feature
- When to use each step
- When you can skip steps (but don't skip tests!)
- Common troubleshooting
- Cheat sheet

---

## 🎨 Chatmode File Structure Template

Each chatmode MUST follow this structure:

```markdown
---
description: '[Clear one-sentence description of what this mode does]'
tools: ['codebase', 'usages', 'vscodeAPI', 'think', 'problems', 'changes', 'testFailure', 'terminalSelection', 'terminalLastCommand', 'openSimpleBrowser', 'fetch', 'findTestFiles', 'searchResults', 'githubRepo', 'extensions', 'edit/editFiles', 'runNotebooks', 'search', 'new', 'runCommands', 'runTasks']
---

# [Mode Name]

## Primary Directive

[What is this mode's core purpose?]

## Core Identity

- **Experience Level**: [What level of expertise does this mode embody?]
- **Focus**: [What is the primary focus?]
- **Philosophy**: [What guiding principles?]

## Input Format

[What does this mode expect as input?]

## Process

[Step-by-step what this mode does]

### Step 1: [Name]
[Details...]

### Step 2: [Name]
[Details...]

## Output Format

[Exactly what this mode produces]

### Example Output
```

[Show concrete example]

```

## Project Context (CRITICAL)

This mode operates on a React Native/Expo project with:
- React Native 0.81.4 + Expo SDK 54
- TypeScript (strict mode)
- UI: Gluestack UI + NativeWind
- State: TanStack Query + Zustand
- Backend: Supabase
- Testing: Jest + React Native Testing Library + Detox

[Mode-specific guidance for this stack]

## Mobile Development Standards

[Mobile-specific best practices for this mode]

## Success Criteria

[How to know this mode completed successfully]

## Next Steps

[Clear instruction on what to do next]
```

---

## 📁 Directory Structure to Create

```
personal-chatmodes/
├── chatmodes/
│   ├── step-2-enhance-request/
│   │   └── enhance-request.chatmode.md
│   ├── step-3-build-plan/
│   │   └── build-plan.chatmode.md
│   ├── step-4-tdd-red/
│   │   └── tdd-red.chatmode.md
│   ├── step-5-build-iterate/
│   │   └── build-iterate.chatmode.md
│   └── step-6-review-enhance/
│       └── review-enhance.chatmode.md
└── docs/
    └── founder-workflow-guide.md
```

---

## ✅ Acceptance Criteria

Your implementation is complete when:

1. **All 6 files created** with proper chatmode format
2. **Each mode references project.md** and understands the tech stack
3. **Step 4 (TDD Red) is extremely detailed** per chatmodeflow.md requirement
4. **Step 5 implements full TDD cycle** (Green → Refactor loop)
5. **All modes work together** with clear handoff formats
6. **Founder guide is simple** and actionable
7. **Test with example**: Dashboard feature flows through all 6 steps successfully

---

## 🧪 Validation Test

After building all modes, validate with this scenario:

**Founder Request**: "I want a dashboard template that has + icons that opens modules with components to place in your desired location"

**Expected Flow**:

1. ✅ Step 2: Enhances to React Native technical spec
2. ✅ Step 3: Creates implementation plan with phases
3. ✅ Step 4: Generates Jest/RTL/Detox tests (all failing)
4. ✅ Step 5: Implements code → All tests pass → Refactored clean
5. ✅ Step 6: Reviews → Minor enhancements → "✅ Ready to Ship"

---

## 📝 Development Guidelines

Follow your existing execution mode standards:

1. **Production-grade quality**: Code you'd stake your reputation on
2. **TypeScript strict mode**: No `any`, explicit return types
3. **Comprehensive error handling**: Try-catch, user-friendly messages
4. **React Native best practices**: FlashList, memoization, platform checks
5. **Mobile performance**: 60 FPS, startup time, memory management
6. **Accessibility**: Screen reader support, touch targets, contrast
7. **Security**: Input validation, RLS policies, secure storage

---

## 🚨 Critical Reminders

1. **DON'T skip Step 4 tests** - TDD is the foundation of quality
2. **Step 5 MUST loop** - Green → Refactor until perfect
3. **Every mode MUST know project.md** - Not generic, specific to React Native/Expo
4. **TDD mode is CRITICAL** - Per chatmodeflow.md, be very precise
5. **Founder-friendly** - Simple language, clear next steps

---

## 📚 Reference Files

- **Implementation Plan**: `plan/feature-orchestrator-system-1.md`
- **Project Context**: `project.md`
- **Template Reference**: `chatmodes/planner/implementation-plan.chatmode.md`
- **Execution Standards**: `chatmodes/main_coder/execution_chatmode.txt`
- **Review Standards**: `chatmodes/bugreview/review_chatmode.txt`
- **Requirements**: `chatmodeflow.md`

---

## 🎯 Ready to Execute

You have everything you need to build this system. Follow the plan phase-by-phase, create each chatmode with care, and test the complete flow.

**Start with Phase 1** (Step 2 - Request Enhancement mode) and work sequentially through Phase 6.

Good luck! 🚀
