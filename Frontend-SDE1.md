Frontend SDE 1 Roadmap
---

Here is your comprehensive study guide, the top machine coding questions you will face, and the ultimate cross-platform capstone project to build.

## Essential Frontend System Design & Machine Coding Topics

To crack these interviews, your preparation must focus on **Vanilla JS/TS fundamentals** and **React/React Native architectures**.

### 1. Advanced JS/TS Fundamentals (The Core)

* **Execution Context & Event Loop:** Deeply understand Microtasks (Promises) vs. Macrotasks (setTimeout) and how UI rendering fits into the loop.
* **Polyfills & Core JS:** Be able to write polyfills from scratch for `Promise.all()`, `Array.prototype.reduce()`, `Function.prototype.bind()`, and `debounce() / throttle()`.
* **Memory Management:** Understand closures, memory leaks (detached DOM nodes, un-cleared intervals), and garbage collection.

### 2. React (Web) Core Mechanics

* **Reconciliation & Fiber Architecture:** Understand how React diffs the Virtual DOM and how the Fiber tree enables interruptible rendering.
* **Performance Optimization:** Strategic use of `React.memo`, `useMemo`, and `useCallback` to prevent re-renders. Understand windowing/virtualization (using libraries like `react-window`) for infinite scrolling lists.
* **State Management Architectures:** Context API vs. Redux vs. Zustand. Know when to use local component state vs. global state.

### 3. React Native (Mobile) Nuances

* **The Bridge vs. JSI (JavaScript Interface):** Understand how old React Native communicated asynchronously via the Bridge, and how the New Architecture uses JSI for synchronous C++ execution.
* **Mobile-Specific Performance:** UI Thread vs. JS Thread. Mastering the `Animated` API and `Reanimated 2/3` to keep animations on the UI thread to prevent dropped frames.
* **Cross-Platform Architecture:** Monorepo setup (Yarn Workspaces/Turborepo) sharing Redux state, hooks, and API layers across React (Next.js) and React Native.

### 4. DOM, Network & Web Vitals (For Web SDE-2)

* **Web Vitals:** LCP (Largest Contentful Paint), CLS (Cumulative Layout Shift), FID (First Input Delay).
* **Network Optimization:** Prefetching, preloading, HTTP/2 multiplexing, and Service Workers for offline caching.

---

## Top Machine Coding Questions (Web & Mobile)

At companies like Flipkart or Slice, the Machine Coding round is an eliminatory 90-120 minute session. You must produce a working, modular application using plain HTML/CSS/JS or React without a heavy boilerplate.

**1. Build an Image Carousel / Slider**

* **Topics:** DOM Manipulation, Event Listeners, Animation.
* **Tricky Part:** Infinite looping (going from the last image smoothly back to the first without a jarring jump), auto-play that pauses on hover, and lazy loading off-screen images.

**2. Design a Nested File Explorer (Tree View)**

* **Topics:** Recursive Component Rendering, State Management.
* **Tricky Part:** Managing the open/closed state of deeply nested folders efficiently. Optimizing rendering so expanding one folder doesn't re-render the entire tree.

**3. Build a Progressive Auto-Suggest Search Bar**

* **Topics:** Debouncing, Network Requests, Caching.
* **Tricky Part:** Race conditions. If the user types "A" (Request 1 takes 500ms) then "AP" (Request 2 takes 100ms), Request 2 resolves first. You must ignore Request 1 when it eventually resolves to prevent overriding the UI with stale data. Caching past searches using a Trie data structure or Map.

**4. Create a Pagination System (or Infinite Scroll)**

* **Topics:** Intersection Observer API, Data fetching, Windowing.
* **Tricky Part:** For infinite scroll, managing DOM bloat. If the user scrolls through 10,000 items, the browser will crash. You must implement "virtualization"—only rendering the 20 items currently visible on screen and replacing the rest with empty padding nodes.

**5. Build a Tic-Tac-Toe Game (Extendable to NxN)**

* **Topics:** 2D Arrays, Game State, Event Delegation.
* **Tricky Part:** The $O(1)$ win-check algorithm. Instead of scanning the whole board every turn, maintain counters for rows, columns, and diagonals to determine the winner instantly.

**6. Design a Multi-Step Checkout Form**

* **Topics:** Controlled vs. Uncontrolled Components, Form Validation, State Persistence.
* **Tricky Part:** Persisting data if the user refreshes midway (using `localStorage` or `sessionStorage`), and handling complex validation rules (e.g., Credit card Luhn algorithm validation) dynamically.

**7. Build a Calendar / Date Picker Component**

* **Topics:** Date Math, Grid Layouts.
* **Tricky Part:** Calculating leap years, determining the day of the week for the 1st of the month to pad empty grid cells correctly, and handling timezone shifts.

---

## Capstone Project: Cross-Platform FinTech Dashboard (React + React Native Monorepo)

To target companies like Slice (FinTech) or Flipkart (E-commerce), your portfolio should demonstrate the ability to manage complex business logic that runs seamlessly on both Web and Mobile.

**Project Idea:** "SpendSense" - An offline-first personal finance tracker and analytical dashboard.

### Core Features & Technical Differentiators:

1. **Monorepo Architecture (Turborepo or Yarn Workspaces):**
* Create a `packages/core` folder containing all Redux/Zustand state, API fetching logic (React Query), and utility functions.
* Create `apps/web` (Next.js/React) and `apps/mobile` (React Native/Expo). Both consume `@spendsense/core` so your business logic is written exactly once.


2. **Offline-First & Optimistic Updates:**
* When the user adds an expense on mobile while on a subway (no internet), save it to a local SQLite database (Mobile) or IndexedDB (Web) using WatermelonDB or Redux Persist.
* Queue the API request. When the network reconnects, synchronize it to the backend.


3. **High-Performance Virtualized Lists:**
* Render a transaction history of 10,000+ items. Use `FlashList` (by Shopify) in React Native and `react-window` in React Web to ensure the list scrolls at a buttery 60FPS without blowing up memory.


4. **Heavy Animations on the UI Thread:**
* Implement an interactive budget slider or drag-and-drop category sorter in React Native using **Reanimated 3**. Ensure no bridge traffic occurs during the animation.


5. **Complex Data Visualization:**
* Build interactive expenditure charts (Pie/Line charts). Use `D3.js` math in the shared core, rendering it to SVG on Web and using `react-native-svg` on mobile.

