# Founder's Guide to AI-Powered Development Workflow

**A simple, step-by-step guide for non-technical founders to ship production-ready React Native apps using AI and Test-Driven Development**

---

## 🎯 What Is This?

This is a **6-step workflow system** that helps you (a non-technical founder) work with AI agents to build high-quality mobile features for your React Native/Expo app. 

**You don't need to know how to code.** Just describe what you want in plain English, and the AI will guide you through a structured process to build it right.

---

## 🚀 Quick Start (5 Minutes)

### Prerequisites

Before you start, make sure you have:
- ✅ A GitHub Copilot account
- ✅ Access to these chatmodes (you're in the right place!)
- ✅ A basic idea of what feature you want to build

### Your First Feature in 5 Steps

Let's say you want to build a "dashboard with customizable modules." Here's what you do:

#### Step 1: Describe Your Idea (Plain English)

Just write what you want:

```
"I want a dashboard where users can add and remove feature modules 
using + icons. Modules should be tiles that users can position anywhere."
```

**That's it!** The AI will take it from here.

#### Step 2: Use the Enhancement Mode

Switch to **Step 2: Request Enhancement** chatmode and paste your description.

The AI will transform your plain English into a detailed technical spec:
- Which React Native components to use
- How state management will work
- What the database needs
- How it works on iOS and Android
- And more!

**You review** to make sure it matches your vision. If not, ask for changes!

#### Step 3: Create the Build Plan

Switch to **Step 3: Build Plan** chatmode and give it the enhanced spec.

The AI will create a detailed implementation plan with phases and tasks:
- Phase 1: Setup
- Phase 2: Database
- Phase 3: State management
- Phase 4: UI components
- And so on...

**You get** a clear roadmap of what will be built.

#### Step 4: Write Tests First (TDD Red Phase)

Switch to **Step 4: TDD Red** chatmode and give it the plan.

The AI will write **comprehensive tests** for everything BEFORE any code exists:
- What should happen when you tap the + icon?
- What should happen when you add a module?
- What should happen when you delete a module?
- What should happen offline?

All these tests will **FAIL** at first (because the code doesn't exist yet). This is expected and good! It's called the "Red Phase" of Test-Driven Development.

**Why this matters**: Tests ensure quality. When tests pass later, you know the feature works correctly.

#### Step 5: Build the Feature (TDD Green Phase)

Switch to **Step 5: Build & Iterate** chatmode and give it the failing tests.

The AI will:
1. Write **minimal code** to make tests pass one by one (Green Phase)
2. **Refactor** the code to be clean and optimized (Refactor Phase)
3. Keep running tests to ensure nothing breaks

**You get**: Working, tested, production-ready code!

#### Step 6: Final Quality Review

Switch to **Step 6: Review & Enhance** chatmode and give it the working code.

The AI will review:
- Code quality (Is it clean and maintainable?)
- Performance (Does it run smoothly at 60 FPS?)
- Accessibility (Can everyone use it?)
- Security (Is data protected?)
- Mobile standards (Does it work on iOS and Android?)

**You get**: A quality report with a verdict:
- ✅ **APPROVED**: Ready to ship!
- ⚠️ **NEEDS MINOR FIXES**: Almost there, small tweaks needed
- ❌ **NEEDS MAJOR FIXES**: Go back to Step 5 and address issues

---

## 📖 Complete Workflow Example

Let's walk through a real example: **Building a Dashboard Feature**

### Starting Point

**You**: "I want users to have a customizable dashboard where they can add modules using + buttons."

### Step 2: Enhancement 🎨

**Chatmode**: Step 2 - Request Enhancement

**Input**: Your plain English description

**AI Output**: 
```markdown
# Modular Dashboard Feature

## Technical Specification

### Components Needed:
- DashboardScreen (main screen)
- ModuleCard (individual module tile)
- ModuleSelectionModal (to pick modules)
- FloatingActionButton (the + button)

### State Management:
- Zustand store for dashboard state
- TanStack Query for fetching available modules from database

### Database (Supabase):
- `modules` table: Available module types
- `user_modules` table: User's active modules with positions

### Mobile Features:
- FlashList for smooth scrolling (100+ modules)
- Haptic feedback when adding modules
- Works offline with cached data
- Pull-to-refresh to sync

### Platform Support:
- iOS 13.0+
- Android API 21+
- Safe area handling for notches
```

**You**: Review and confirm it matches your vision. Ask for changes if needed.

### Step 3: Build Plan 📋

**Chatmode**: Step 3 - Build Plan

**Input**: The enhanced specification from Step 2

**AI Output**: 
```markdown
# Implementation Plan

## Phase 1: Setup (Tasks 1-4)
- Create project structure
- Define TypeScript types
- Setup test configuration

## Phase 2: Database (Tasks 5-8)
- Create Supabase tables
- Setup Row Level Security policies
- Generate TypeScript types from schema

## Phase 3: State Management - RED (Tasks 9-12)
- Write tests for Zustand store
- All tests should FAIL (no code yet)

## Phase 4: State Management - GREEN (Tasks 13-16)
- Implement Zustand store
- Make tests PASS

## Phase 5: API Integration - RED (Tasks 17-21)
- Write tests for TanStack Query hooks
- All tests should FAIL

## Phase 6: API Integration - GREEN (Tasks 22-26)
- Implement hooks
- Make tests PASS

## Phase 7-14: Continue with UI, E2E tests, etc.
```

**You**: You now know exactly what will be built and in what order.

### Step 4: TDD Red Phase ❌

**Chatmode**: Step 4 - TDD Red

**Input**: The implementation plan from Step 3

**AI Output**: Creates test files:

```typescript
// stores/__tests__/useDashboardStore.test.ts
describe('useDashboardStore', () => {
  it('should initialize with empty modules', () => {
    // Test will FAIL - store doesn't exist yet ❌
  });

  it('should add module to dashboard', () => {
    // Test will FAIL - addModule doesn't exist yet ❌
  });

  it('should remove module from dashboard', () => {
    // Test will FAIL - removeModule doesn't exist yet ❌
  });
  
  // ... 30+ more tests
});

// Total: 47 tests, all FAILING ❌
```

**Why it matters**: These tests define exactly what the feature should do. When they all pass, you know it's done correctly.

**You**: AI confirms all tests fail for the right reason (missing code, not bugs).

### Step 5: TDD Green & Refactor ✅

**Chatmode**: Step 5 - Build & Iterate

**Input**: The failing tests from Step 4

**AI Process**:

**GREEN PHASE** (Make tests pass):
```typescript
// Iteration 1
// Write minimal code to pass first test
export const useDashboardStore = create((set) => ({
  modules: [], // ✅ First test passes!
}));

// Iteration 2
// Add addModule to pass next test
export const useDashboardStore = create((set) => ({
  modules: [],
  addModule: (module) => set((state) => ({ 
    modules: [...state.modules, module] 
  })), // ✅ Second test passes!
}));

// Continue until ALL 47 tests pass ✅
```

**REFACTOR PHASE** (Improve code quality):
```typescript
// Refactor 1: Add proper TypeScript types
interface DashboardStore {
  modules: UserModule[]; // Better type than any[]
  addModule: (module: UserModule) => void;
}

// Refactor 2: Extract helper function
const getNextPosition = (modules: Module[]) => {
  // Complex logic extracted to separate function
};

// Refactor 3: Add React.memo for performance
export const ModuleCard = React.memo(({ module, onPress }) => {
  // Component won't re-render unnecessarily
});

// After each refactor: Run tests → Must stay GREEN ✅
```

**AI Output**:
```markdown
# Implementation Complete

## Tests Status
- All 47 tests passing ✅
- Coverage: 92%

## Code Quality
- Clean and organized ✅
- Properly typed (TypeScript) ✅
- Optimized for mobile performance ✅
- Works offline ✅
- Accessible ✅

## Platform Testing
- iOS: Works perfectly ✅
- Android: Works perfectly ✅
```

**You**: Your feature is now built and tested!

### Step 6: Quality Review 🔍

**Chatmode**: Step 6 - Review & Enhance

**Input**: The working code from Step 5

**AI Output**:
```markdown
# Review Report - Modular Dashboard

## Executive Summary
**Overall Verdict**: ✅ APPROVED FOR PRODUCTION

## Code Quality Review
- TypeScript: ✅ PASS (no errors, strict mode)
- Organization: ✅ PASS (clean structure)
- Error Handling: ✅ PASS (comprehensive)

## Performance Review
- List Performance: ✅ PASS (60 FPS with FlashList)
- Component Optimization: ✅ PASS (React.memo used)
- Bundle Size: ✅ PASS (+45KB only)

## Mobile Review
- iOS: ✅ Works perfectly
- Android: ✅ Works perfectly
- Offline: ✅ Full support
- UX: ✅ Haptics, pull-to-refresh, skeletons

## Accessibility Review
- Screen Readers: ✅ PASS (VoiceOver, TalkBack)
- Touch Targets: ✅ PASS (all 44x44pt minimum)
- Color Contrast: ✅ PASS (5.2:1 ratio)
- WCAG 2.1 AA: ✅ CERTIFIED

## Security Review
- Data Validation: ✅ PASS (Zod schemas)
- RLS Policies: ✅ PASS (users see only their data)
- No exposed secrets: ✅ PASS

## Testing Review
- Coverage: 94% (excellent!)
- All tests passing: ✅
- E2E tests: ✅ iOS and Android

## Final Verdict
🎉 READY TO SHIP! 🚀

No critical issues. Feature is production-ready.
```

**You**: Your feature is approved and safe to ship to users!

---

## 🎓 Understanding Each Step

### Step 2: Request Enhancement
**Purpose**: Turn your vague idea into a precise technical plan

**What you do**: Describe what you want in plain English

**What AI does**: Adds all the technical details:
- Which components to use
- How data flows
- Mobile-specific considerations
- Platform differences (iOS vs Android)

**When to use**: Always start here with every new feature

### Step 3: Build Plan
**Purpose**: Create a roadmap for implementation

**What you do**: Give the enhanced spec to the AI

**What AI does**: Breaks it into phases and tasks:
- Setup → Database → State → API → UI → Tests → Polish

**When to use**: After Step 2, before building anything

### Step 4: TDD Red Phase
**Purpose**: Write tests BEFORE code (quality insurance)

**What you do**: Give the build plan to the AI

**What AI does**: Writes comprehensive tests that FAIL:
- Unit tests (business logic)
- Component tests (UI)
- Integration tests (workflows)
- E2E tests (full user journeys)

**When to use**: After Step 3, before Step 5

**Why it matters**: Tests define "done correctly." If tests pass, feature works.

### Step 5: Build & Iterate
**Purpose**: Build the feature using TDD (Test-Driven Development)

**What you do**: Give the failing tests to the AI

**What AI does**:
1. **GREEN**: Write code to make tests pass (one test at a time)
2. **REFACTOR**: Clean up code while keeping tests green
3. Loop until perfect

**When to use**: After Step 4, with failing tests

**Result**: Working, tested, clean code

### Step 6: Review & Enhance
**Purpose**: Final quality check before shipping

**What you do**: Give the working code to the AI

**What AI does**: Reviews everything:
- Code quality
- Performance (60 FPS?)
- Accessibility (everyone can use it?)
- Security (data safe?)
- Mobile standards (iOS and Android work?)

**When to use**: After Step 5, before shipping

**Result**: Approval to ship or list of fixes needed

---

## 🎯 When to Use Each Step

### Always Use This Order

```
Your Idea
    ↓
Step 2: Enhancement (plain English → technical spec)
    ↓
Step 3: Build Plan (spec → roadmap)
    ↓
Step 4: TDD Red (roadmap → failing tests)
    ↓
Step 5: Build & Iterate (tests → working code)
    ↓
Step 6: Review (code → quality check)
    ↓
Ship to Users! 🚀
```

### Can I Skip Steps?

**Short answer**: No, don't skip steps.

**Long answer**:
- **Skip Step 2?** ❌ You'll miss mobile-specific details
- **Skip Step 3?** ❌ You'll have no roadmap
- **Skip Step 4?** ❌ You'll have no quality assurance (NEVER skip tests!)
- **Skip Step 5?** ❌ Nothing will be built
- **Skip Step 6?** ❌ You might ship bugs or performance issues

**All steps are important.** They ensure quality.

### When to Loop Back

Sometimes you need to go backwards:

**Scenario 1**: Step 6 finds issues
- Loop back to Step 5 (Build & Iterate)
- Fix the issues
- Return to Step 6 for re-review

**Scenario 2**: Founder changes mind during Step 3
- Loop back to Step 2
- Update the specification
- Continue forward from there

**Scenario 3**: Tests reveal wrong assumptions in Step 4
- Loop back to Step 2 or Step 3
- Clarify requirements
- Update tests

---

## 💡 Tips for Success

### For Step 2 (Enhancement)

**Do**:
- ✅ Be specific about what you want
- ✅ Mention if it's similar to another app
- ✅ Describe the user experience
- ✅ Ask questions if you don't understand the output

**Don't**:
- ❌ Use technical jargon (unless you know it)
- ❌ Rush through this step
- ❌ Accept a spec you don't understand

**Example**:
```
Good: "I want a chat feature like WhatsApp where users can send 
text messages and see when messages are read."

Bad: "Make a chat thing."
```

### For Step 3 (Build Plan)

**Do**:
- ✅ Review the phases - do they make sense?
- ✅ Ask about timeline if needed
- ✅ Clarify any confusing tasks

**Don't**:
- ❌ Skip reading the plan
- ❌ Start building before the plan is clear

### For Step 4 (TDD Red)

**Do**:
- ✅ Trust the process (failing tests are good!)
- ✅ Confirm tests cover all your requirements
- ✅ Ask about test coverage

**Don't**:
- ❌ Panic when tests fail (that's the point!)
- ❌ Skip this step (it's critical for quality)

### For Step 5 (Build & Iterate)

**Do**:
- ✅ Let the AI work through GREEN → REFACTOR cycles
- ✅ Check in periodically
- ✅ Test manually on your device when done

**Don't**:
- ❌ Rush the refactoring phase
- ❌ Skip mobile testing (test on iOS AND Android)

### For Step 6 (Review)

**Do**:
- ✅ Read the review report carefully
- ✅ Address all critical issues
- ✅ Consider minor improvements

**Don't**:
- ❌ Ship with critical issues unresolved
- ❌ Skip accessibility fixes
- ❌ Ignore security warnings

---

## 🛠 Troubleshooting

### Problem: AI output is too technical

**Solution**: 
```
Ask: "Can you explain this in simpler terms for a non-technical founder?"
```

### Problem: Feature doesn't match my vision

**Solution**:
```
Go back to Step 2 and clarify:
"Actually, I wanted users to drag modules to rearrange them, 
not just add and remove them."
```

### Problem: Tests are failing in Step 4

**Solution**:
```
This is EXPECTED! Tests should fail in Step 4.
They'll pass in Step 5 when code is built.
```

### Problem: Tests are still failing after Step 5

**Solution**:
```
This is NOT good. Tell the AI:
"Some tests are still failing. Here are the failing test names: [paste names]
Please fix the code to make them pass."
```

### Problem: Step 6 review finds critical issues

**Solution**:
```
Go back to Step 5 and ask:
"The review found these critical issues: [paste issues]
Please fix them and ensure all tests still pass."
```

### Problem: Feature works on iOS but not Android

**Solution**:
```
Tell Step 5 AI:
"Feature works on iOS but fails on Android with this error: [paste error]
Please add platform-specific code to handle Android."
```

### Problem: App is slow or laggy

**Solution**:
```
Tell Step 6 AI:
"The feature is working but feels slow. Can you review performance 
and suggest optimizations?"
```

---

## 📚 Cheat Sheet

Quick reference for each step:

| Step | Chatmode | Input | Output | Success Check |
|------|----------|-------|--------|---------------|
| **2** | enhance-request | Plain English idea | Technical specification | "Do I understand and agree with the spec?" |
| **3** | build-plan | Enhanced spec | Implementation plan with phases | "Does the plan make sense?" |
| **4** | tdd-red | Build plan | Failing test files | "Are tests failing? Good!" |
| **5** | build-iterate | Failing tests | Working code + passing tests | "Do all tests pass?" |
| **6** | review-enhance | Working code | Quality report + verdict | "Did it get approved?" |

### Quick Decision Tree

```
┌─────────────────────┐
│   Have new idea?    │
│                     │
└──────────┬──────────┘
           │
           ↓
    ┌──────────────┐
    │  Use Step 2  │ → Get technical spec
    └──────┬───────┘
           │
           ↓
    ┌──────────────┐
    │  Use Step 3  │ → Get build plan
    └──────┬───────┘
           │
           ↓
    ┌──────────────┐
    │  Use Step 4  │ → Write tests (will fail)
    └──────┬───────┘
           │
           ↓
    ┌──────────────┐
    │  Use Step 5  │ → Build code (tests pass)
    └──────┬───────┘
           │
           ↓
    ┌──────────────┐
    │  Use Step 6  │ → Quality review
    └──────┬───────┘
           │
    ┌──────┴──────┐
    │             │
    ↓             ↓
┌────────┐    ┌──────────┐
│Approved│    │  Issues  │
└───┬────┘    └────┬─────┘
    │              │
    ↓              ↓
 Ship! 🚀    Fix (Step 5)
                   │
                   ↓
              Re-review (Step 6)
```

---

## 🎉 Success Stories (Examples)

### Example 1: Dashboard Feature
- **Started with**: "I want a customizable dashboard"
- **Went through**: All 6 steps
- **Result**: Production-ready in 2 days with 94% test coverage
- **User feedback**: "Love the smooth UX!"

### Example 2: Chat Feature
- **Started with**: "Users should be able to message each other"
- **Challenge**: Step 6 found offline sync issues
- **Solution**: Looped back to Step 5, added proper offline queue
- **Result**: Shipped with full offline support

### Example 3: Profile Screen
- **Started with**: "Profile with photo upload"
- **Challenge**: Accessibility issues in Step 6
- **Solution**: Fixed in Step 5, added proper labels
- **Result**: WCAG 2.1 AA certified

---

## 🚀 Ready to Build?

### Your Action Plan

1. **Start small**: Pick one simple feature to build first
2. **Follow the steps**: Use the workflow exactly as designed
3. **Don't skip tests**: Step 4 is critical for quality
4. **Test on devices**: Both iOS and Android
5. **Ship with confidence**: After Step 6 approval

### Remember

- 🎯 **You don't need to code** - Just describe what you want
- ✅ **Trust the process** - The 6 steps ensure quality
- 🧪 **Tests are your friend** - They guarantee correctness
- 📱 **Mobile-first** - Everything is optimized for iOS and Android
- 🚀 **Ship fast** - But ship quality, not bugs

---

## 📞 Getting Help

### If you're stuck

1. **Read this guide again** - The answer is often here
2. **Ask the AI** - It can clarify any step
3. **Check the troubleshooting section** - Common issues covered
4. **Start over** - Sometimes it's easier to restart from Step 2

### Common Questions

**Q: How long does the full workflow take?**
A: For a simple feature: 2-4 hours. Complex features: 1-2 days.

**Q: Do I need to understand the code?**
A: No! But understanding the specs and plans helps.

**Q: Can I modify the code after Step 5?**
A: Yes, but run tests again and re-run Step 6 review.

**Q: What if I want to change the feature mid-way?**
A: Go back to Step 2, update the spec, and continue forward.

**Q: Is this only for React Native?**
A: This workflow is optimized for React Native/Expo, but the TDD principles apply to any framework.

---

## 🎓 Next Steps

Now that you understand the workflow:

1. ✅ **Pick your first feature** - Something simple to start
2. ✅ **Open Step 2 chatmode** - Start with enhancement
3. ✅ **Follow the steps** - One at a time, don't skip
4. ✅ **Review the output** - After Step 6
5. ✅ **Ship it!** - When approved

**You've got this!** 🚀

The 6-step workflow takes the complexity out of mobile development and ensures you ship quality features every time.

---

**Happy Building!** 🎉

*Built with ❤️ for non-technical founders who want to ship quality mobile apps*
