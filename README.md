# Awesome-Reactive-Programming

# Top Reactive Programming Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Observable Streams, Transparent Reactivity & Explicit State Machines*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Reactive Programming**. These tools help applications model asynchronous data flows, state changes, and side effects as composable streams or observable values — enabling declarative handling of events, UI updates, and complex async logic without callback hell or manual subscription management.

**Examples** include RxJS, Bacon.js, Kefir, Most.js, Cycle.js, MobX, Redux, XState, Effector, and ReactiveX (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, observable composition, and transparent reactivity models — ideal for frontend developers building complex async UIs, engineers modeling state transitions, and teams prioritizing predictable data flow.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **Redux DevTools (Browser Extension)** — While Redux is open-source, the browser extension ecosystem around it is maintained as a separate distribution. The core debugging capability (time-travel, action replay, state inspection) is free and open-source, but commercial integration with platforms like Sentry and LogRocket adds hosted error tracking and session replay alongside state debugging.

- **XState Commercial (Stately)** — XState core is MIT-licensed, but **Stately** provides a managed visual editor, deployment platform, and AI-assisted state machine generation as a commercial service.

- **MobX-State-Tree Commercial Support** — MST is MIT-licensed, but commercial support and consulting are available through the maintainers for enterprises needing guaranteed response times and architecture guidance.

## Open-Source GitHub Projects

- **[RxJS](https://github.com/ReactiveX/rxjs)**  
  **The most widely adopted reactive programming library for JavaScript** — Apache 2.0 licensed, **31,000+ GitHub stars** [citation:13]. **The Reactive Extensions for JavaScript** — a rewrite of the original RxJS with better performance, better modularity, and better debuggable call stacks [citation:4]. **Core type is the Observable**, with satellite types (Observer, Schedulers, Subjects) and operators inspired by Array methods (map, filter, reduce, every) [citation:16]. **Uses a pipe-based functional composition model** — `range(1, 200).pipe(filter(x => x % 2 === 1), map(x => x + x))` [citation:4]. **Distinguishes between cold and hot streams** (unicast and multicast respectively) for the same Observable abstraction [citation:13]. **Error handling**: an error stops the stream, and errors thrown inside the pipeline are automatically caught and forwarded as error events [citation:13]. **The default choice for Angular applications** and the most mature reactive library in the JS ecosystem.

- **[Bacon.js](https://github.com/baconjs/bacon.js)**  
  **The functional reactive programming library for TypeScript and JavaScript** — MIT licensed, **6,400+ GitHub stars** [citation:13]. **Only supports hot streams (multicast)** — unlike RxJS, there are no cold streams [citation:13]. **Subscriptions always execute asynchronously** — a deliberate semantic choice [citation:13]. **Error behavior differs from RxJS**: errors do not terminate the stream by default; you must explicitly use `endOnError` to end on first error [citation:5]. **Operators do not catch thrown errors** — `map` doesn't wrap exceptions; you must use `Bacon.try()` or `flatMap` to convert errors into Error events [citation:5]. **Provides glitch avoidance information** — an important characteristic for state consistency [citation:13]. **EventStream and Property semantics**: streams cannot emit initial events to new subscribers; properties represent current values [citation:5]. **Best for developers wanting precise FRP semantics** with hot-stream-only multicast behavior.

- **[Kefir.js](https://github.com/kefirjs/kefir)**  
  **A reactive programming library inspired by Bacon.js and RxJS with focus on high performance and low memory usage** — MIT licensed, **1,800+ GitHub stars** [citation:13][citation:6]. **Ships with Flow type definitions** for type-safe stream composition [citation:6]. **Actively maintained through 2023** with the last commit in March 2023 [citation:13]. **Best for projects wanting Bacon.js-style semantics with better performance characteristics** and Flow integration.

- **[Most.js](https://github.com/mostjs/core)**  
  **High-performance reactive event stream programming** — MIT licensed, **3,400+ GitHub stars** for v1, **406 stars** for v2 (@most/core) [citation:13]. **`@most/core` features a battle-tested, high-performance architecture** in a leaner, functions-only, curried API in a tree-shakeable package [citation:19]. **Last commit activity on core was March 2024** — the ecosystem is less actively maintained than RxJS or Bacon.js [citation:7]. **Best for performance-sensitive applications** where tree-shakeable bundles and curried APIs matter.

- **[Cycle.js](https://github.com/cyclejs/cyclejs)**  
  **A functional and reactive JavaScript framework for predictable code** — MIT licensed [citation:8]. **Built around the idea of a single `main()` function** that receives drivers and returns sinks — pure functional composition of side effects. **Supports multiple stream libraries**: `@cycle/rxjs-run` for RxJS, `@cycle/most-run` for Most.js [citation:8]. **Cycle Unified and Cycle Diversity** releases represent its evolution [citation:20]. **Best for developers wanting a fully reactive architectural pattern** where every side effect is an observable stream.

- **[MobX](https://github.com/mobxjs/mobx)**  
  **Simple, scalable state management through transparent functional reactive programming** — MIT licensed, **28,000+ GitHub stars**. **Signal-based, battle-tested library** that makes state management simple by transparently applying FRP [citation:9]. **"Anything that can be derived from the application state, should be. Automatically."** — the core philosophy [citation:9]. **Observable state, computed values, and reactions** automatically track dependencies and update UI granularly. **No manual optimization needed** — the reactivity system builds a dependency tree at runtime, guaranteeing computations run only when strictly needed [citation:9]. **Framework-agnostic** — state management works outside any UI framework, making code decoupled, portable, and testable [citation:9]. **Best for teams wanting reactive state without explicit selectors or subscriptions.**

- **[Redux](https://github.com/reduxjs/redux)**  
  **A JS library for predictable global state management** — MIT licensed [citation:10]. **Strict unidirectional data flow** with actions, reducers, and a single store. **Time-travel debugging** via Redux DevTools [citation:2]. **Requires middleware for async** — redux-thunk for simple calls, redux-saga for complex flows [citation:2]. **Can cause global re-renders** unless using React.memo or createSelector [citation:2]. **Medium learning curve with Redux Toolkit**; high boilerplate without it [citation:2]. **Best for large teams needing auditability and strict state predictability** — the most debuggable state architecture.

- **[XState](https://github.com/statelyai/xstate)**  
  **State machines and statecharts for complex application logic** — MIT licensed, **27,000+ GitHub stars**. **Defines states and allowed transitions** — invalid transitions are impossible by design [citation:2]. **Explicit, visualizable state transitions** for wizards, modals, and device control [citation:2]. **High learning curve** but eliminates invalid states entirely [citation:2]. **Stately Agent** extends XState to LLM agents — the machine owns control flow, the model only picks legal events [citation:11]. **Best for workflows where state transitions must be explicit, testable, and visualizable.**

- **[Effector](https://github.com/effector/effector)**  
  **Event-driven reactive system** — MIT licensed. **Uses stores (state), events (triggers), and effects (async operations)** [citation:2]. **Framework-agnostic and composable** — works anywhere [citation:2]. **First-class `createEffect` for async with built-in pending/error states** [citation:2]. **Granular updates** — components subscribe to specific state slices, avoiding unnecessary re-renders [citation:2]. **Medium-high learning curve** due to its unique approach [citation:2]. **Best for framework-agnostic reactive systems** needing fine-grained control over state updates and side effects [citation:14].

### Additional Strong Open-Source Options

- **ReactiveX** — The umbrella organization behind RxJS, RxSwift, RxPY, RxCpp, RxDart, RxPHP, and other language-specific Reactive Extensions implementations [citation:3].
- **ReactiveUI** — Advanced composable functional reactive MVVM framework for all .NET platforms. 8,500+ GitHub stars [citation:3].
- **Monix** — Asynchronous, reactive programming for Scala and Scala.js. 1,900+ GitHub stars [citation:3].
- **DynamicData** — Reactive collections based on Rx.NET. 1,900+ GitHub stars [citation:3].
- **samber/ro** — Streams and reactive programming paradigm for Go with declarative, composable APIs. 660+ GitHub stars [citation:3].

**Frameworks for building custom systems**: Combine **RxJS** for the most mature observable composition with operators and schedulers, **Bacon.js** or **Kefir** for precise FRP semantics with hot-stream-only multicast, **Most.js** for tree-shakeable high-performance streams, **MobX** for transparent reactive state without explicit selectors, **XState** for explicit state machines in complex workflows, and **Effector** for framework-agnostic event-driven systems — to build a reactive architecture tailored to your async complexity, framework ecosystem, and performance requirements.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Reactive programming tools differ significantly in stream semantics, error handling, and framework coupling. **RxJS distinguishes cold vs hot streams; Bacon.js only supports hot streams** [citation:13]. **Bacon.js errors do not terminate streams by default** — you must use `endOnError`; RxJS errors stop the stream and thrown errors are auto-caught [citation:13][citation:5]. **Bacon.js operators do not catch thrown errors** — use `Bacon.try()` [citation:5]. **Redux causes global re-renders** unless optimized with selectors or memoization [citation:2]. **XState has a high learning curve** but eliminates invalid states by design [citation:2]. **Most.js v2 is less actively maintained** — last core commit March 2024 [citation:7]. **MobX and Valtio use proxy-based reactivity** — the React Compiler silently over-memoizes proxy-based libraries, suppressing required re-renders (verify compatibility before adopting with the compiler).
- Self-hosted open-source solutions require proper subscription lifecycle management, memory leak prevention (unsubscribe on component unmount), and awareness of scheduler behavior for concurrency.

---

**Made for frontend developers, reactive systems architects, and engineers building async data flows and state machines.**
Let's make reactive programming more open, predictable, and stream-composable.
