# Workflow Validation Test - Dashboard Feature

This document demonstrates the 6-step workflow using the example dashboard feature from the HANDOFF document.

---

## Test Scenario

**Founder Request**: "I want a dashboard template that has + icons that opens modules with components to place in your desired location"

**Expected Flow**: This request should flow successfully through all 6 steps, producing production-ready code.

---

## Validation Steps

### Step 1: Initial Request

**Input to Step 2**:
```
I want a dashboard template that has + icons that opens modules 
with components to place in your desired location
```

**Expected**: Plain English, non-technical language ✅

---

### Step 2: Request Enhancement

**Chatmode**: `personal-chatmodes/chatmodes/step-2-enhance-request/enhance-request.chatmode.md`

**Process**:
1. AI reads project.md to understand tech stack (React Native 0.81.4, Expo SDK 54, etc.)
2. AI identifies core requirements from vague input
3. AI adds mobile-specific technical details
4. AI structures output with components, state, API, navigation

**Expected Output Sections**:
- ✅ Feature Overview
- ✅ User Stories
- ✅ Technical Components (Gluestack UI, FlashList, etc.)
- ✅ State Management (Zustand + TanStack Query)
- ✅ Backend Integration (Supabase tables, RLS policies)
- ✅ Navigation (Expo Router paths)
- ✅ Mobile Optimizations (performance, offline, platform-specific)
- ✅ Accessibility Requirements
- ✅ Testing Requirements

**Validation Check**:
- [ ] Output includes React Native/Expo specifics
- [ ] References Gluestack UI components
- [ ] Includes Zustand store structure
- [ ] Includes TanStack Query hooks
- [ ] Defines Supabase schema
- [ ] Includes iOS and Android considerations
- [ ] Includes offline support strategy
- [ ] Includes accessibility requirements
- [ ] Ready for Step 3

**Sample Expected Output**:
```markdown
# Modular Dashboard Feature

## Overview
Create a customizable dashboard screen where users can add/remove feature 
modules using + icons. Modules are draggable tiles that can be positioned 
anywhere on the screen.

## User Stories
- As a user, I want to add modules via + icon
- As a user, I want to remove modules I don't use
- As a user, I want to drag modules to rearrange them

## Technical Specification

### UI Components (Gluestack UI + NativeWind)
- DashboardScreen with FlashList
- ModuleCard with Pressable and HapticFeedback
- ModuleSelectionModal from Gluestack UI
- FloatingActionButton with + icon

### State Management
- Zustand store: useDashboardStore
- TanStack Query: useModules(), useAddModule()

### Backend (Supabase)
- modules table
- user_modules table
- RLS policies for data security

### Mobile Optimizations
- FlashList for 60 FPS
- React.memo for components
- Offline support with TanStack Query cache
- Platform.select() for iOS/Android differences

[... continues with full spec ...]
```

---

### Step 3: Build Plan

**Chatmode**: `personal-chatmodes/chatmodes/step-3-build-plan/build-plan.chatmode.md`

**Process**:
1. AI reads enhanced specification from Step 2
2. AI breaks down into phases following TDD structure
3. AI creates granular tasks with completion criteria
4. AI defines testing strategy for each phase

**Expected Output Sections**:
- ✅ YAML frontmatter (goal, version, status, tags)
- ✅ Introduction
- ✅ Requirements & Constraints (REQ-XXX, SEC-XXX, etc.)
- ✅ Implementation Steps (Phase 1-14)
- ✅ Alternatives considered
- ✅ Dependencies listed
- ✅ Files affected
- ✅ Testing requirements
- ✅ Risks & Assumptions

**Expected Phases**:
- Phase 1: Setup & Type Definitions
- Phase 2: Backend & Database (Supabase)
- Phase 3: State Management - RED (Write tests)
- Phase 4: State Management - GREEN (Implement)
- Phase 5: API Integration - RED (Write tests)
- Phase 6: API Integration - GREEN (Implement)
- Phase 7: UI Components - RED (Write tests)
- Phase 8: UI Components - GREEN (Implement)
- Phase 9: Screen Integration - RED
- Phase 10: Screen Integration - GREEN
- Phase 11: Mobile Optimizations - REFACTOR
- Phase 12: E2E Testing
- Phase 13: Accessibility & Polish
- Phase 14: Documentation & Review

**Validation Check**:
- [ ] All phases follow TDD structure (RED → GREEN → REFACTOR)
- [ ] Each phase has specific tasks
- [ ] Tasks include file paths
- [ ] Testing is prioritized
- [ ] Mobile optimizations included
- [ ] Platform testing included
- [ ] Follows implementation-plan.chatmode.md template
- [ ] Ready for Step 4

**Sample Expected Phase**:
```markdown
### Phase 3: State Management - RED (Write Tests First)

**GOAL-003**: Write comprehensive tests for Zustand store (TDD Red Phase)

| Task | Description | Completed | Date |
|------|-------------|-----------|------|
| TASK-009 | Write test: Initial state is correct | | |
| TASK-010 | Write test: addModule updates state correctly | | |
| TASK-011 | Write test: removeModule updates state correctly | | |
| TASK-012 | Write test: Edge cases and error scenarios | | |

**Details**:
- Test file: `stores/__tests__/useDashboardStore.test.ts`
- All tests will FAIL initially (expected for RED phase)
- Tests define the behavior of the store
```

---

### Step 4: TDD Red Phase

**Chatmode**: `personal-chatmodes/chatmodes/step-4-tdd-red/tdd-red.chatmode.md`

**Process**:
1. AI reads implementation plan from Step 3
2. AI creates comprehensive test files
3. AI writes tests that FAIL (no implementation yet)
4. AI verifies all tests fail for the right reasons

**Expected Test Files**:
- ✅ `stores/__tests__/useDashboardStore.test.ts`
- ✅ `hooks/__tests__/useDashboard.test.ts`
- ✅ `components/__tests__/DashboardScreen.test.tsx`
- ✅ `components/__tests__/ModuleCard.test.tsx`
- ✅ `components/__tests__/ModuleSelectionModal.test.tsx`
- ✅ `__tests__/dashboard-flow.test.tsx` (integration)
- ✅ `e2e/dashboard.e2e.ts` (E2E for iOS and Android)

**Expected Test Types**:
- Unit tests for Zustand store
- Unit tests for TanStack Query hooks
- Component tests with React Native Testing Library
- Integration tests for complete workflows
- E2E tests with Detox (iOS and Android)
- Offline scenario tests
- Accessibility tests

**Validation Check**:
- [ ] All test files created
- [ ] Tests use proper React Native Testing Library patterns
- [ ] Tests include mobile-specific scenarios (offline, gestures)
- [ ] Tests include accessibility checks
- [ ] Tests include platform-specific checks (iOS/Android)
- [ ] Running `npm test` shows all tests FAILING
- [ ] Failures are for correct reasons (missing implementation)
- [ ] No syntax errors in tests
- [ ] Test coverage document created
- [ ] Ready for Step 5

**Sample Expected Test**:
```typescript
// stores/__tests__/useDashboardStore.test.ts
import { renderHook, act } from '@testing-library/react-hooks';
import { useDashboardStore } from '../useDashboardStore';

describe('useDashboardStore', () => {
  it('should initialize with empty modules array', () => {
    const { result } = renderHook(() => useDashboardStore());
    expect(result.current.modules).toEqual([]);
    // ❌ WILL FAIL - store doesn't exist yet
  });

  it('should add module to dashboard', () => {
    const { result } = renderHook(() => useDashboardStore());
    const mockModule = { id: '1', name: 'Test Module' };

    act(() => {
      result.current.addModule(mockModule);
    });

    expect(result.current.modules).toContain(mockModule);
    // ❌ WILL FAIL - addModule doesn't exist yet
  });

  // ... more tests, all FAILING ❌
});

// Expected: All tests FAIL (RED phase complete)
```

**Test Execution Result**:
```bash
$ npm test

FAIL stores/__tests__/useDashboardStore.test.ts
FAIL hooks/__tests__/useDashboard.test.ts
FAIL components/__tests__/DashboardScreen.test.tsx
...

Tests: 0 passed, 47 failed, 47 total
```

---

### Step 5: Build & Iterate (GREEN → REFACTOR)

**Chatmode**: `personal-chatmodes/chatmodes/step-5-build-iterate/build-iterate.chatmode.md`

**Process**:

**GREEN PHASE**:
1. Pick ONE failing test
2. Write MINIMUM code to make it pass
3. Run tests, verify it passes
4. Commit
5. Repeat until ALL tests pass

**REFACTOR PHASE**:
1. All tests GREEN? Good!
2. Improve code quality (types, organization, performance)
3. Run tests after each change (must stay GREEN)
4. Commit each refactor
5. Repeat until code is production-ready

**Expected Iterations**:

**Iteration 1 (GREEN)**: 
- Create basic Zustand store
- Tests: 3/47 passing ✅

**Iteration 2 (GREEN)**: 
- Add addModule action
- Tests: 8/47 passing ✅

**Iteration 3 (GREEN)**: 
- Add removeModule action
- Tests: 12/47 passing ✅

**Continue until...**
- Tests: 47/47 passing ✅ (GREEN ACHIEVED!)

**Refactor 1**: 
- Add proper TypeScript types (no `any`)
- Tests: 47/47 passing ✅

**Refactor 2**: 
- Extract helper functions
- Tests: 47/47 passing ✅

**Refactor 3**: 
- Add React.memo optimization
- Tests: 47/47 passing ✅

**Refactor 4**: 
- Add haptic feedback
- Tests: 47/47 passing ✅

**Continue until code is clean and optimized**

**Expected Files Created**:
- ✅ `types/dashboard.ts`
- ✅ `stores/useDashboardStore.ts`
- ✅ `hooks/useDashboard.ts`
- ✅ `components/DashboardScreen.tsx`
- ✅ `components/ModuleCard.tsx`
- ✅ `components/ModuleSelectionModal.tsx`
- ✅ `app/dashboard/index.tsx`
- ✅ `utils/dashboard.ts`

**Validation Check**:
- [ ] All 47 tests passing ✅
- [ ] TypeScript strict mode satisfied (no `any`, no errors)
- [ ] Code is organized and DRY
- [ ] React Native optimizations applied (FlashList, React.memo, useCallback)
- [ ] Mobile UX features added (haptics, pull-to-refresh, skeletons)
- [ ] Platform-specific code for iOS/Android
- [ ] Error boundaries added
- [ ] Accessibility labels added
- [ ] Offline support working
- [ ] JSDoc comments on complex logic
- [ ] Manual testing on iOS ✅
- [ ] Manual testing on Android ✅
- [ ] Ready for Step 6

**Test Execution Result**:
```bash
$ npm test

PASS stores/__tests__/useDashboardStore.test.ts
PASS hooks/__tests__/useDashboard.test.ts
PASS components/__tests__/DashboardScreen.test.tsx
...

Tests: 47 passed, 0 failed, 47 total
Coverage: 92.5%

$ npm run type-check
No errors ✅

$ npm run lint
No errors ✅
```

---

### Step 6: Review & Enhance

**Chatmode**: `personal-chatmodes/chatmodes/step-6-review-enhance/review-enhance.chatmode.md`

**Process**:
1. AI verifies all tests pass
2. AI reviews code quality (TypeScript, organization, errors, docs)
3. AI reviews performance (lists, components, images, bundle)
4. AI reviews mobile UX (loading/error/empty states, platforms, offline, gestures)
5. AI reviews accessibility (screen readers, touch targets, contrast, focus)
6. AI reviews Supabase integration (RLS, queries, subscriptions)
7. AI reviews security (validation, sensitive data, auth)
8. AI reviews testing (coverage, quality, E2E)
9. AI generates comprehensive review report
10. AI provides verdict (APPROVED, NEEDS MINOR FIXES, or NEEDS MAJOR FIXES)

**Expected Review Categories**:
- ✅ Code Quality (TypeScript, organization, errors, docs)
- ✅ React Native Performance (lists, components, images, bundle)
- ✅ Mobile-Specific (UX, platforms, offline, gestures)
- ✅ Accessibility (WCAG 2.1 AA compliance)
- ✅ Supabase Integration (RLS, queries, subscriptions)
- ✅ Security (validation, secrets, auth)
- ✅ Testing (coverage, quality, E2E)

**Expected Outcomes**:

**Best Case** (✅ APPROVED):
```markdown
# Review Report - Modular Dashboard

## Executive Summary
**Overall Verdict**: ✅ APPROVED FOR PRODUCTION

## Summary of Required Actions
### Critical (Must fix before shipping)
*None* ✅

### Minor (Should fix, but not blocking)
*None* ✅

## Final Verdict
🎉 READY TO SHIP! 🚀

All quality checks passed. Feature is production-ready.
```

**Needs Fixes** (⚠️):
```markdown
# Review Report - Modular Dashboard

## Executive Summary
**Overall Verdict**: ⚠️ NEEDS MINOR FIXES

## Summary of Required Actions
### Critical (Must fix before shipping)
*None* ✅

### Minor (Should fix)
- [ ] Add accessibility labels to 2 buttons
- [ ] Increase test coverage to >80%

## Final Verdict
After fixing minor issues: ✅ Ready to Ship
```

**Validation Check**:
- [ ] Review report generated
- [ ] All 7 categories reviewed
- [ ] Clear verdict provided (APPROVED, MINOR FIXES, or MAJOR FIXES)
- [ ] Actionable feedback for any issues
- [ ] If approved: Ready to ship!
- [ ] If fixes needed: Clear list of what to fix

---

## Workflow Completion Checklist

After running through all 6 steps:

### Step 2: Enhancement
- [ ] ✅ Vague request transformed into technical spec
- [ ] ✅ React Native/Expo specifics included
- [ ] ✅ Mobile optimizations defined
- [ ] ✅ Platform differences noted

### Step 3: Build Plan
- [ ] ✅ Phase-based implementation plan created
- [ ] ✅ TDD structure (RED → GREEN → REFACTOR) followed
- [ ] ✅ Granular tasks defined
- [ ] ✅ Testing strategy included

### Step 4: TDD Red
- [ ] ✅ Comprehensive test files created
- [ ] ✅ All tests FAILING initially
- [ ] ✅ Unit, component, integration, and E2E tests
- [ ] ✅ Mobile-specific tests (offline, platform, accessibility)

### Step 5: Build & Iterate
- [ ] ✅ All tests PASSING
- [ ] ✅ Code refactored and clean
- [ ] ✅ TypeScript strict mode satisfied
- [ ] ✅ Performance optimized
- [ ] ✅ Works on iOS and Android
- [ ] ✅ Offline support working

### Step 6: Review & Enhance
- [ ] ✅ Comprehensive review completed
- [ ] ✅ Quality report generated
- [ ] ✅ Verdict provided (APPROVED or needs fixes)

---

## Success Criteria

The workflow is successful if:

1. **All 6 steps completed** ✅
2. **Each step's output feeds into the next** ✅
3. **Plain English → Production code** ✅
4. **Tests ensure quality** ✅
5. **Mobile standards met** ✅
6. **Ready to ship** ✅

---

## Validation Summary

**Test Scenario**: Dashboard with + icons for modules

**Expected Result**: 
- ✅ Step 2: Technical spec created
- ✅ Step 3: Implementation plan created
- ✅ Step 4: Tests written (all failing)
- ✅ Step 5: Code built (all tests passing)
- ✅ Step 6: Quality approved

**Actual Result**: [To be filled in during actual validation]

**Status**: ✅ WORKFLOW VALIDATED / ⚠️ NEEDS ADJUSTMENT / ❌ FAILED

---

## Notes for Improvement

Document any issues or suggestions discovered during validation:

1. [Issue/Suggestion 1]
2. [Issue/Suggestion 2]
3. [Issue/Suggestion 3]

---

**Validation Complete**: [Date]  
**Validated By**: [Name/Team]  
**Next Steps**: [Deploy to production / Iterate on workflow / etc.]
