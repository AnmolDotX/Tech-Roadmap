# 📱 Full-Stack (React/Next.js) → Mobile Engineer (React Native + Swift)

> **Goal:** SDE-1 / SDE-2 mobile roles at product companies like **Swiggy** and **Urban Company (UC)**, or any company paying **₹24 LPA+ base** in India
> **Starting point:** full-stack engineer (React, Next.js)
> **Machine:** MacBook Air M4, **no iPhone** (iOS simulator + Android emulator only)
> **Infra constraint:** projects must run **locally**, or deploy on **Vercel**, **Play Store** or a basic **Hostinger VPS**. No AWS or heavy cloud.
> **Time:** ~24 weeks at 12–15 hrs/week, with applications starting around week 16–18
---

## 3. 🧭 Strategy: What to Learn in What Order

```
React Native (TypeScript + Expo)  ← PRIMARY (weeks 1-10, then keep building)
      │
      ├── Swift / SwiftUI / iOS native  ← SECONDARY (weeks 11-14)
      │      └── write Swift native modules for RN
      │
      └── Kotlin / Android literacy     ← LIGHT but important (weeks 15-16)
             └── write Kotlin native modules for RN
```

### Why this order (and the honest trade-offs)

| Choice | Pros | Cons |
|---|---|---|
| **React Native first** | Reuses React/TS skills, one codebase, fastest path to a shipped app and a hireable portfolio | Employers still expect native-layer knowledge for complex features |
| **Swift second** | Opens native iOS roles, strengthens RN native-module skills, impressive in interviews | No iPhone: you can't ship or fully test on a device. Fewer Indian users on iOS than Android. |
| **Kotlin/Android literacy** | Android dominates in India, RN postings often mention Android native, KMP is a bonus at some companies | Extra learning load. Keep it focused. |

### Market overview: mobile approaches

| Approach | Who uses it | Strengths | Weaknesses |
|---|---|---|---|
| **Native (Swift/SwiftUI, Kotlin/Compose)** | Large consumer apps, core flows needing top performance | Best platform fit and performance, first access to new OS features | Two codebases, two teams |
| **React Native** | Many startups and product teams, shared logic with web teams | One codebase, JS/TS talent pool, OTA updates, large ecosystem | Native bridge/module work, upgrade pain, device-specific bugs |
| **Flutter** | Startups and agencies, strong UI consistency | Fast UI, one codebase | Dart ecosystem, fewer shared skills with web |
| **Kotlin Multiplatform (KMP)** | Teams sharing business logic between native apps | Native UIs with shared core | Younger ecosystem, still needs Swift + Kotlin skills |
| **PWA/Capacitor/Ionic** | Simple apps, internal tools | Web skills reuse | Limited native feel and performance |

**State of React Native in 2026 (from community write-ups; verify in official docs):** the **New Architecture is the only architecture** (since RN 0.82), **Hermes V1** is the default engine (0.84), iOS builds can use **precompiled** core binaries, and **React Compiler** is stable in new Expo templates. This means you should learn the New Architecture (Fabric, TurboModules, JSI) from the start, not the legacy bridge.

---

## 4. 💻 MacBook Air M4 Setup & the "No iPhone" Plan

### Hardware reality check

| Concern | What to do |
|---|---|
| **Disk space** | Xcode plus simulators, Android Studio plus emulator images and build caches can eat 100GB+. Keep ≥ 80–100GB free. Delete old simulators and DerivedData regularly. |
| **RAM** | 16GB works if you're disciplined: run **one simulator/emulator at a time**, close Chrome tabs, avoid running Docker + Xcode + Android Studio together. |
| **Thermals (fanless Air)** | Long native builds throttle. Prefer incremental builds, `npx expo run:*` dev builds, and avoid repeatedly clean-building. |
| **Apple Silicon** | iOS simulator runs natively. Use **arm64** Android emulator images. Both run well on M-series. |

### One-time setup checklist
- [ ] Install **Xcode** (Mac App Store), open it once, accept license, install iOS Simulator runtimes
- [ ] Install **Xcode Command Line Tools**, **Homebrew**, **Node** (via `fnm`/`nvm`), **Watchman**, a supported **JDK** (check current RN docs for the required version)
- [ ] Install **Android Studio**, SDK, platform-tools and an **arm64 emulator** (Pixel image)
- [ ] Install **VS Code/Cursor** + ESLint, Prettier, React Native tools
- [ ] Create an **Expo** app and run it on **both** the iOS Simulator and Android emulator
- [ ] Install **Flipper replacement:** use **React Native DevTools** (bundled with RN) and the platform profilers (Xcode Instruments, Android Studio Profiler)

### What you CAN do without an iPhone

| Capability | Status |
|---|---|
| Develop, run and debug RN + SwiftUI apps in the **iOS Simulator** | ✅ |
| UI/layout testing across device sizes, dark mode, dynamic type, accessibility inspector | ✅ |
| Networking, storage, navigation, animations (approximate), deep links | ✅ |
| Simulated push payloads and simulated locations | ✅ (limited) |
| StoreKit/in-app purchase flows via local test configs | ✅ (check Xcode docs) |
| Unit/integration/E2E tests (Jest, RNTL, Maestro on simulator/emulator) | ✅ |
| Instruments profiling on simulator (relative numbers only) | ⚠️ not representative of device |

### What you CAN'T (or can't fully) do without an iPhone

| Capability | Workaround |
|---|---|
| Real-device performance, thermal behavior, real-world scrolling feel | Profile on **Android real device or emulator**, note the limitation in your README |
| Real push notification tokens (APNs), camera/Bluetooth/NFC hardware, real haptics | Build the feature, demo the Android version, test iOS with mocks or borrow a friend's iPhone once for a final check |
| Shipping to the App Store/TestFlight | Requires the paid **Apple Developer Program** (about $99/year). Optional. Skip until you're ready. |
| Device-only bugs | Be honest in interviews: say what you validated on simulator vs Android hardware |

### Android hardware tip
If you own **any Android phone**, enable developer mode and run builds over USB. It gives you real-device testing for free and is the most valuable single upgrade to your setup. Borrow one if needed.

### Public proof strategy without iOS shipping
- **Android:** installable **APK on GitHub Releases** (no store needed) + optional **Play Store**
- **Web demo:** Expo web export deployed on **Vercel** so recruiters can try the app in a browser
- **Screen recordings:** 60–90 second videos of both iOS Simulator and Android emulator in each README
- **Expo Snack** links for small components

---

## 5. ☁️ Low-Cloud Infra Plan

| Need | Use | Cost/effort notes |
|---|---|---|
| Landing page, privacy policy, web demo | **Vercel** (Next.js landing page + Expo web export) | Free tier is typically enough. A **privacy policy URL** is required for Play Store listings. |
| Backend for apps | **Local server first**: Node (Hono/Express/Fastify), Go, or FastAPI + **SQLite** (or Postgres in Docker) | Runs on your Mac. No cloud needed. |
| Backend deployed for real demos | **Hostinger VPS**: Docker or plain binary + **Caddy/Nginx** + SQLite/Postgres + a free TLS cert | One small VPS can host several demo backends. Keep secrets out of git. |
| Android distribution | **GitHub Releases APK** (simplest), or **Google Play** | Play: one-time developer fee of about **US$25**. For **personal accounts created after 13 Nov 2023**, Google requires a **closed test with at least 12 testers opted in for 14 continuous days** before you can apply for production access. Organization accounts are exempt. Budget roughly **3 weeks** for a first launch and **start the clock early** (see timeline). |
| iOS distribution | **Skip for now** or later pay for the Apple Developer Program | Not needed to get hired. |
| Builds | **Local builds** (`npx expo run:android` / `run:ios`, or `eas build --local`) | Avoids paying for or waiting on cloud build queues. EAS cloud builds have free-tier limits. Check current plan details. |
| Crash/analytics | **Sentry** free tier or Firebase Crashlytics, PostHog free tier | Optional. Adds "production mindset" signal. |
| Maps | Avoid keys with billing: use **MapLibre** with free/demo tile sources and respect their usage policies. Or mock maps with static images. | Google Maps SDK needs a billing-enabled key on Android. |
| Push notifications | Start with **local notifications** (no server). Remote push through FCM/APNs is optional later. | Real APNs needs the paid Apple program and a real device. |
| Free data | Public APIs (TMDB, Open-Meteo, PokeAPI), or your own seeded JSON/SQLite | Always include a **local mock server** so the app works offline in demos. |

> **Rule:** every project must start with `git clone && npm i && npm run dev` working with a **local** backend or mock, with the VPS/Vercel deploy as optional polish.

---

## 6. 🗓️ Timeline at a Glance

```
Weeks 1-2    M0  Setup, mobile fundamentals, TS/React refresher
Weeks 3-6    M1  React Native core (Expo)                       → Project 1 (ship by wk 6)
Week 6-7           Create Play Console account, start closed test (14-day clock) using Project 1
Weeks 7-12   M2  Production RN: architecture, perf, native APIs → Project 2
Weeks 11-14  M3  Swift & iOS native                              → Project 3 (Swift)
Weeks 15-16  M4  Kotlin/Android literacy + native modules       → Expo module in Swift + Kotlin
Weeks 15-22  M5  Release engineering, quality, security         → Project 4 (UC-style)
Weeks 16-18       START APPLYING (Projects 1-3 are done)
Weeks 17-24  M6  DSA, machine coding, mobile system design, mock interviews
```

DSA: **3–5 problems/week from week 1 to the end.** Do not postpone it.

---

## 7. 📚 Learning Modules

Each module: **Learn → Market overview → Deliverable**.

---

### M0 · Weeks 1–2 · Setup & Mobile Fundamentals

**Learn**
- [ ] Complete Section 4 setup and run a hello-world on both simulators
- [ ] Mobile concepts: app lifecycle (foreground/background/killed), permissions, threading (UI vs background), memory limits, battery, screen densities, safe areas, gestures
- [ ] How RN works: JS runtime (Hermes), **New Architecture** (Fabric renderer, TurboModules, JSI) at a conceptual level
- [ ] TypeScript refresher: generics, discriminated unions, utility types, strict mode
- [ ] React refresher for mobile: hooks, effects cleanup, memoization, concurrent features, **React Compiler** basics

**Market overview**

| Area | Popular options |
|---|---|
| RN tooling | **Expo** (dev builds, EAS, Expo Router), bare RN CLI |
| Debugging | React Native DevTools, Xcode/Android Studio debuggers, Reactotron (some teams) |
| Language | TypeScript (nearly universal in RN job posts) |

**Deliverable:** a hello-world app running on iOS Simulator + Android emulator, committed to GitHub with a README.

---

### M1 · Weeks 3–6 · React Native Core

**Learn**
- [ ] Core components, **Flexbox layout**, platform differences, responsive design, safe areas, keyboard handling
- [ ] **Lists:** `FlatList`, `SectionList`, **FlashList**, windowing, key extraction, pagination and infinite scroll
- [ ] **Navigation:** **Expo Router** and **React Navigation** (stack, tabs, modals, deep links, auth flows)
- [ ] **Forms and validation:** React Hook Form + Zod
- [ ] **State management:** local state, Context, **Zustand**, Redux Toolkit (you'll see Redux in many postings), **TanStack Query** for server state
- [ ] **Networking:** fetch/Axios, error/loading states, retries, cancellation, offline handling
- [ ] **Storage:** **MMKV**, AsyncStorage, **expo-sqlite** (+ Drizzle or similar), SecureStore for secrets
- [ ] **Animations and gestures:** Animated basics, **Reanimated**, **Gesture Handler**
- [ ] Styling: StyleSheet, NativeWind (Tailwind-style), Tamagui/Unistyles overview
- [ ] Accessibility (screen readers, touch target sizes) and dark mode

**Market overview**

| Need | RN options | Native iOS | Native Android |
|---|---|---|---|
| UI | RN components + Flexbox | SwiftUI / UIKit | Jetpack Compose / Views |
| Navigation | Expo Router, React Navigation | NavigationStack / UIKit | Navigation Compose |
| State | Zustand, Redux Toolkit, Jotai, TanStack Query | Observation / Combine | ViewModel + StateFlow |
| Local DB | SQLite, WatermelonDB, Realm-type, MMKV | SwiftData / Core Data | Room |
| Animations | Reanimated, Lottie | SwiftUI animations | Compose animations |

**Deliverable → Project 1** (Section 8).

---

### M2 · Weeks 7–12 · Production React Native

**Learn**
- [ ] **Architecture:** feature-based folders, layering (UI → hooks → services → data), dependency injection patterns, MVVM-style separation, clean boundaries
- [ ] **New Architecture in depth:** Fabric, TurboModules, JSI, Codegen; what changed and why
- [ ] **Performance:** unnecessary re-renders, memoization (and when React Compiler helps), list performance, image optimization, startup time, bundle size, Hermes bytecode, avoiding bridge-like chatter
- [ ] **Native capabilities:** location, camera/media picker, files, notifications (local first), biometrics, background tasks, deep links/universal links
- [ ] **Offline-first patterns:** local cache, optimistic updates, request queues, conflict handling
- [ ] **Real-time:** WebSockets/SSE to a local server; reconnection and backoff
- [ ] **Testing:** **Jest**, **React Native Testing Library**, mocking native modules, **Maestro** (or Detox) E2E on simulator/emulator. TDD style as one Swiggy RN posting explicitly asks.
- [ ] **Code quality:** ESLint, Prettier, strict TS, Husky/lint-staged, conventional commits
- [ ] **Monorepo basics:** pnpm workspaces to share types between app, web and backend

**Market overview**

| Area | Popular options |
|---|---|
| Networking/data | TanStack Query, RTK Query, Apollo (GraphQL), tRPC (TS full-stack) |
| E2E testing | **Maestro**, Detox, Appium (enterprise), BrowserStack/Sauce device clouds |
| Perf tools | React Native DevTools, Xcode Instruments, Android Studio Profiler, Perfetto |
| Backend-for-mobile choices | Node (Hono/Fastify/NestJS), Go, FastAPI, Firebase/Supabase (BaaS) |

**Go/Python/JS note for you:** your backend language is a free choice here. Use **TypeScript backend** for shared types with the app, or the Go/Python you may already be learning. Mobile interviewers care that you understand API contract design for mobile (pagination, payload size, caching, versioning), not which language serves it.

**Deliverable → Project 2** (Section 8).

---

### M3 · Weeks 11–14 · Swift & iOS Native

**Learn**
- [ ] **Swift language:** optionals, structs vs classes, enums with associated values, protocols, generics, closures, error handling, **async/await**, actors, **Swift Concurrency**
- [ ] **SwiftUI:** views, state (`@State`, `@Binding`, `@Observable`), navigation, lists, layout, animations
- [ ] **UIKit overview:** view controllers, lifecycle, Auto Layout (many large apps still have UIKit codebases)
- [ ] **Architecture:** MVVM, Clean Architecture, dependency injection (initializer injection, protocols)
- [ ] **Data:** `URLSession`, `Codable`, **SwiftData/Core Data**, Keychain
- [ ] **Concurrency:** Combine basics vs async/await
- [ ] **Tooling:** Xcode, Swift Package Manager, Instruments, XCTest/Swift Testing, UI tests
- [ ] **Bridge to RN:** write a **native module in Swift** using the **Expo Modules API** (and understand TurboModules)

**Market overview**

| Topic | Swift/iOS | React Native | Kotlin/Android |
|---|---|---|---|
| UI | SwiftUI/UIKit | RN components | Compose/Views |
| Async | async/await, Combine | Promises, async/await | Coroutines, Flow |
| DI | Swinject-type / manual | manual / context | Hilt/Koin |
| Testing | XCTest, Swift Testing | Jest, RNTL | JUnit, Espresso |

**Trade-off to be able to explain:** native gives best platform integration and performance; RN gives shared code and speed of iteration. For a feed-heavy consumer app, the usual compromise is RN for most screens and native for performance- or platform-critical surfaces.

**Deliverable → Project 3** (Section 8).

---

### M4 · Weeks 15–16 · Kotlin/Android Literacy (focused)

You don't need to become an Android specialist. Aim for **reading and modifying** native Android code and writing small modules.

- [ ] Kotlin basics: null safety, data classes, sealed classes, extension functions, coroutines overview
- [ ] Android fundamentals: Activities/Fragments, lifecycle, permissions, services overview, Gradle basics, manifest
- [ ] **Jetpack Compose** overview (to understand modern Android UI)
- [ ] Write the **Kotlin side** of your Expo native module
- [ ] Read how RN's Android build works (Gradle, autolinking), and debug a build error on purpose
- [ ] Optional: look at **Kotlin Multiplatform** (Swiggy lists it as a plus on a native iOS role)

**Market overview:** Android uses Kotlin/Compose/Hilt/Room/Retrofit/Coroutines; KMP shares business logic across Android and iOS; Flutter is an alternative cross-platform choice you should be able to compare (Dart, widget-based UI, own rendering engine).

**Deliverable:** the same Expo native module published with **both Swift and Kotlin implementations** (Project 3).

---

### M5 · Weeks 15–22 · Release Engineering, Quality, Security & Observability

**Learn**
- [ ] **Release process:** versioning, build variants, signing (Android keystore, iOS signing concepts), AAB vs APK, release notes, staged rollouts
- [ ] **Play Console:** listing, content rating, data safety form, privacy policy, internal → closed → production tracks
- [ ] **CI/CD:** GitHub Actions (lint, typecheck, test, build), Fastlane (overview), EAS Build/Submit (overview and local usage)
- [ ] **OTA updates:** Expo **EAS Update** or self-hosted alternatives. Know what can and can't be updated over the air.
- [ ] **Monitoring:** Sentry/Crashlytics, source maps, breadcrumbs, release health
- [ ] **Analytics and experimentation:** event design, funnels (PostHog or similar), feature flags, A/B testing concepts
- [ ] **Security:** secure storage, token handling, certificate pinning concept, obfuscation basics, jailbreak/root detection concept, OWASP MASVS overview
- [ ] **Performance budget:** startup time, TTI, frame drops, memory, app size. Measure before/after.
- [ ] **Accessibility and i18n/RTL:** real checklists, not afterthoughts
- [ ] **Deep links, app links, universal links, share extensions** overview

**Market overview**

| Area | Popular options |
|---|---|
| Crash reporting | Sentry, Firebase Crashlytics, Bugsnag |
| Analytics | PostHog, Mixpanel, Amplitude, Firebase Analytics, Segment |
| CI/CD | GitHub Actions, Bitrise, Codemagic, Fastlane, EAS |
| Feature flags | LaunchDarkly, GrowthBook, Unleash, Firebase Remote Config |
| OTA | EAS Update, self-hosted CodePush-style alternatives (check current options) |

**Deliverable:** CI pipeline running lint + typecheck + tests on every PR, a signed release build, and a Play closed-test (or GitHub Release APK) for Project 1.

---

### M6 · Weeks 17–24 · Interview Preparation (DSA, Machine Coding, Mobile System Design)

See Section 9. Run it in parallel with M4–M5 from week 17.

---

## 8. 🛠️ Portfolio Projects

Build **4 projects**. Each needs: README with screen recordings (iOS Simulator + Android), architecture diagram, setup in under 5 minutes, tests, performance notes and a "what I'd improve" section. Every project works **locally** with a mock backend.

### Project 1 · Offline-First Expense/Budget Tracker (Weeks 3–6)
- **Stack:** Expo + TypeScript, Expo Router, **expo-sqlite**, MMKV, Zustand/TanStack Query, charts, local notifications (reminders), dark mode
- **No backend required.** Optional: tiny sync API on VPS.
- **Distribution:** GitHub Release APK + Expo web export on **Vercel** + a Next.js privacy-policy page. Start the **Play closed test** here so production access clears by the time you finish Project 2.
- **Shows:** fundamentals, offline-first, local persistence, shipping

### Project 2 · "Mini-Swiggy" Food Ordering App (Weeks 7–12)
- **Features:** restaurant list with search/filters, menu, cart, checkout (mocked payment), order history, **live order status** (simulated delivery progress), address selection, favorites
- **Stack:** Expo + TS, **FlashList**, TanStack Query, Zustand, **Reanimated** micro-interactions, **MapLibre** (or static map mock) for tracking
- **Backend:** local **Node/Hono (or Go/FastAPI) + SQLite**, seeded data, **WebSocket/SSE** for order status. Docker Compose for one-command start. Optional deploy to Hostinger VPS.
- **Engineering signal:** tests (Jest + RNTL + Maestro flows for "search → add → checkout"), performance case study (before/after FPS and startup), accessibility pass
- **Shows:** consumer-app patterns Swiggy cares about: lists, search, cart state, real-time updates, performance

### Project 3 · Native Depth: SwiftUI App + Swift/Kotlin Expo Module (Weeks 11–16)
- **3a. SwiftUI app** (runs in the iOS Simulator): e.g., a habit tracker or focus timer with **SwiftData**, MVVM, a home-screen **widget** (simulator-testable), unit tests
- **3b. Expo native module** with **both Swift and Kotlin** implementations (e.g., a secure-storage wrapper, a haptics/sound helper, or a lightweight device-info utility). Publish to npm with docs and an example app. Open the repo to issues.
- **Shows:** you can cross the bridge, which is exactly the "RN + native" profile postings describe

### Project 4 · "Urban-Company-Style" Home Services Booking (Weeks 15–22)
- **Two apps in one monorepo:** a **customer app** (browse services, choose slot, address, book, track, rate) and a **provider app** (accept/decline jobs, status updates). Shared packages for types and UI.
- **Features:** slot-picker calendar, booking state machine, optimistic UI, offline queue for actions, deep links, local notifications, rating flow, i18n (English + Hindi)
- **Backend:** TypeScript or Go service + SQLite/Postgres, local-first, with VPS deployment as a bonus. Booking-state diagrams in the README.
- **Shows:** multi-role product thinking, state machines, monorepo skills, UC-relevant domain

### Optional extras
- **Performance teardown** blog post: measure and fix a slow list, long startup or heavy re-render
- **RN upgrade write-up:** upgrade a project across versions and document breakages
- **Open-source contributions:** target 1–3 merged PRs

| Repo/area | Why |
|---|---|
| **expo/expo** | Docs and module issues, TypeScript/Swift/Kotlin exposure |
| **Shopify/flash-list** | Performance-focused list library |
| **software-mansion** (Reanimated, Gesture Handler) | Animation/gesture internals |
| **react-native-community** libraries | Many "good first issue" tasks |
| **facebook/react-native** | Docs/typing fixes for visibility |
| **Maestro, MapLibre RN** | Testing and mapping ecosystems |

Ladder: docs fix → tests → bug fix → small feature. Check each repo's contribution guide.

---

## 9. 🎤 Interview Prep

### Typical process (from public interview guides; expect variation)
1. Recruiter/hiring-manager screen
2. **DSA coding round(s)**
3. **Machine-coding / practical round** (build a small UI feature in 60–90 minutes)
4. **Technical deep-dive** on mobile (RN or native internals, your projects)
5. **System design / LLD**, often with mobile flavor
6. Behavioral/hiring manager round

One guide for Swiggy describes about **5 rounds over 4–6 weeks** and stresses ambiguity handling and API-contract collaboration with backend teams.

### DSA (continuous)
- Arrays/strings, hash maps, two pointers, sliding window, stacks/queues, trees/graphs, binary search, basic DP, heaps
- Target a steady 3–5 problems/week, with timed mock sessions from week 17

### Machine coding drills (practice 1–2 per week)
- Cart with quantity updates and totals · autocomplete search with debounce · infinite scroll feed · star rating · OTP input · toast/queue manager · image carousel · stopwatch · todo with persistence · nested comment thread

### RN deep-dive questions
1. How does the **New Architecture** differ from the old bridge? What are Fabric, TurboModules and JSI?
2. Why can a `FlatList` feel janky and how do you fix it? When would you use FlashList?
3. How do you avoid unnecessary re-renders? What does React Compiler change?
4. How do you structure a large RN codebase?
5. How would you implement offline-first with sync conflicts?
6. How do you handle deep links and auth state restoration?
7. How would you write and test a native module?
8. What belongs in JS vs native code?

### Native/platform questions (to expect, at least conceptually)
- App lifecycle states, memory warnings, background execution limits
- Threading: main thread rules, why UI work must not block it
- Swift: value vs reference types, ARC/retain cycles, optionals, `async/await`
- Android: Activity lifecycle, permissions, process death

### Mobile system design prompts
- Design the **Swiggy home feed** (pagination, caching, image loading, A/B experiments)
- Design **live order tracking** (location updates, battery, reconnection, push vs socket)
- Design an **offline-first notes/booking app** with sync
- Design **image loading and caching** for a feed
- Design **analytics SDK/event pipeline** for an app
- Design a **feature-flag/remote-config** system for mobile

### Behavioral
- Prepare 5 stories: ownership, conflict, failure, impact, learning a new tech fast (your pivot is a good one)

---

## 10. 🧭 Job Search Playbook

- **Start applying in weeks 16–18**, once Projects 1–3 are polished. Refresh the portfolio as Project 4 completes.
- **Titles to search:** React Native Developer/Engineer, Mobile Engineer, SDE-1/2 Mobile, SDE-2 (React Native/Android), Frontend Engineer (Mobile), iOS Engineer (if you lean native)
- **Where to apply:** company careers pages (Swiggy, Urban Company and similar product companies), LinkedIn, Wellfound, referrals. Many companies post RN roles directly on their careers pages. Recruiters at UC have posted hiring calls publicly on LinkedIn.
- **Referrals** beat cold applications. Share your app demos and one technical post with relevant engineers.
- **Resume:** lead with 3 projects with metrics (startup time, FPS, bundle size, test coverage), then your full-stack history framed as an advantage ("I understand the whole stack and API design").
- **GitHub profile:** pinned repos, GIFs/videos, release APKs, clean READMEs, tests.
- **Level selection:** apply to SDE-1 and SDE-2 roles that match your experience. Let interviews decide.
- **Negotiation:** ask for the **base vs variable vs ESOP breakdown**, compare **in-hand** and **total compensation**, and use competing processes as leverage. Use several salary sources because they disagree.
- **Safety net:** introduce a small mobile or RN project at your current job if possible (internal app, PWA to RN migration). Real work experience is the strongest credential.

---

## 11. ✅ Master Checklist

**Setup**
- [ ] Xcode + Android Studio + simulators working · [ ] Expo app on both platforms · [ ] Real Android phone available (own or borrowed)

**React Native**
- [ ] Components/layout · [ ] Navigation · [ ] Forms · [ ] State + server state · [ ] Storage/offline · [ ] Animations/gestures · [ ] New Architecture concepts · [ ] Performance · [ ] Testing (Jest, RNTL, Maestro)

**Native**
- [ ] Swift fundamentals · [ ] SwiftUI app · [ ] Swift native module · [ ] Kotlin basics · [ ] Kotlin native module

**Production**
- [ ] CI/CD pipeline · [ ] Signed builds · [ ] Play closed test · [ ] Crash reporting · [ ] Security basics · [ ] Accessibility pass

**Portfolio**
- [ ] Project 1 shipped · [ ] Project 2 (Mini-Swiggy) · [ ] Project 3 (Swift + module) · [ ] Project 4 (UC-style) · [ ] 1–3 OSS PRs · [ ] 2 blog posts

**Interview**
- [ ] DSA 100+ problems · [ ] 15+ machine-coding drills · [ ] 5 mobile system designs · [ ] Mock interviews · [ ] Applications sent from week ~16–18

**Monthly review:** every 4 weeks, check this list, re-read current job postings and adjust. RN, Expo and OS requirements change often, so verify tool versions against official docs.

---
