### Hi there 👋
Working on things.  [mrbuilder](https://mr-builder.github.io) and stuff.  

#### Here are a few folks who think I'm cool:
- [Zaid A](https://github.com/beatzball)

<!--
**jspears/jspears** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

My git aliases look like

```
[alias]
        undo = checkout origin/main
        last = log -1 HEAD
        ignore = "!f() { for f in \"$@\"; do echo \"$f\" >> .git/info/exclude; done; }; f"
        unignore = "!f() { for f in \"$@\"; do sed -i \"\" \"\\\\|^${f}$|d\" .git/info/exclude; done; }; f"
        ls = branch  --sort=committerdate
        alias = config --global alias.
        main = switch main
        wip = commit -nam 'wip'
        back = "!f() { ~/bin/git-back.sh $@ | xargs git switch; }; f"
        unwip = "!f() { ~/bin/git-unwip.sh \"$@\"; }; f"


```

# INVENTION DISCLOSURE LIST

**Justin Spears** | GitHub: jspears | npm: speajus**Owned Organizations:** bobamo · inquorum-app · kubitical · mr-builder · pbinj · skibididrizz · speajus · subschema · tenence · ts-wift**Also contributed to:** electrode-io (WalmartLabs)**Prepared:** February 27, 2026 | CONFIDENTIAL | v5.0

## Executive Summary

This document discloses **26 inventions and original works** authored by Justin Spears, spanning over 18 years of independent software development (2008–2026). These inventions cover dependency injection frameworks, build tooling, form rendering engines, mobile deployment infrastructure, database schema tooling, document rendering, CLI utilities, and developer productivity tools.

Of particular IP significance are:

- **Proxy-Based Dependency Injection family** (INV-010 PBJ/PBinJ, INV-011 Diblob) — a novel approach to dependency injection using JavaScript Proxy objects, enabling type-safe, zero-boilerplate service containers with automatic lifecycle management.
- **Tenence platform** (INV-012) — a commercial multi-tenant SaaS platform leveraging automatic PostgreSQL Row-Level Security for tenant isolation, built on proprietary technology.
- **TypeSpec-to-Drizzle compiler** (INV-013 skibididrizz/drizzle) — a compiler that generates Drizzle ORM schemas from TypeSpec API definitions, bridging API-first design with database schema management.

Of the 26 inventions documented, **20 are fully detailed** with public references, and **3 are pending** further documentation (INV-015 Inquorum, INV-016 Kubitical, INV-017 ts-wift involve private repositories or early-stage work). Two inventions — **Tenence** (INV-012) and **Inquorum** (INV-015) — represent potential commercial ventures with proprietary elements and are **not open-source**.

All works were created independently and outside the scope of any employment relationship, except where noted (see INV-009).

## Invention Summary Index

| ID | Title | Org | Status |
| --- | --- | --- | --- |
| INV-001 | MrBuilder — Mono-Repo Build Orchestrator | mr-builder | Documented |
| INV-002 | Subschema — Schema-Driven React Forms Engine | subschema | Documented |
| INV-003 | Nojector — Node Parameter Injection | jspears (personal) | Documented |
| INV-004 | MERS — Mongoose Express Rest Service | jspears (personal) | Documented |
| INV-005 | Bobamo — Mongoose + Backbone + Bootstrap Scaffolding | bobamo | Documented |
| INV-006 | postcss-react-native — PostCSS for React Native | speajus | Documented |
| INV-007 | Emeth — CSS Modules Theme System | jspears (personal) | Documented |
| INV-008 | TypeScript Type-Level Utilities | jspears (gists) | Documented — Blog Post Series |
| INV-009 | Electrode OTA Server — Over-the-Air Update Platform | electrode-io / WalmartLabs | Documented — ⚠️ Created during WalmartLabs employment (employer-owned IP) |
| INV-010 | PBJ / PBinJ — Proxy-Based Injection | pbinj | Documented |
| INV-011 | Diblob — Proxy-Key Dependency Injection | speajus | Documented |
| INV-012 | Tenence — Multi-Tenant SaaS Platform | tenence | Documented ⚠️ COMMERCIAL |
| INV-013 | skibididrizz/drizzle — TypeSpec-to-Drizzle Compiler | skibididrizz | Documented |
| INV-014 | Cartoonize — Photo-to-Cartoon Converter | jspears (personal) | Documented |
| INV-015 | Inquorum — Non-Profit Board Governance Platform | inquorum-app | Pending — ⚠️ COMMERCIAL, NOT OPEN SOURCE |
| INV-016 | Kubitical — Graphical Kubernetes Management | kubitical | Pending |
| INV-017 | ts-wift — Swift-to-TypeScript Transpiler | ts-wift | Pending |
| INV-018 | rlsify — PostgreSQL Row-Level Security Tooling | jspears (personal) | Documented |
| INV-019 | Gazel — Bazel GUI | jspears (personal) | Documented |
| INV-020 | @speajus/markdown-to-pdf — Markdown to PDF Without a Browser | speajus | Documented |
| INV-021 | mermaid-to-svg — Mermaid Charts Without a Browser | speajus | Documented |
| INV-022 | vitest-markdown — Run TypeScript Examples in Markdown | jspears (personal) | Documented |
| INV-023 | ts-arg — TypeScript Decorator-Based Argument Parser | jspears (personal) | Documented |
| INV-024 | worktree — Git Worktree ZSH Plugins | jspears (personal) | Documented |
| INV-025 | scrolldata — React Virtual Table | jspears (personal) | Documented |
| INV-026 | Deno JWT Libraries | speajus | Documented |

## Detailed Invention Disclosures

### INV-001: MrBuilder — Mono-Repo Build Orchestrator

**Organization:** mr-builder | **Language:** JavaScript / Webpack | **Status:** Documented — Open Source

**Summary**MrBuilder is a monorepo build orchestration tool that manages complex multi-package JavaScript projects through a plugin-based Webpack configuration system. It provides a unified build pipeline with 50+ composable Webpack plugins, enabling zero-config builds for monorepo packages while maintaining full customizability. The project evolved through multiple major versions (v3 as `mrbuilder-*`, v4 as `@mrbuilder/*`).

**Problem Addressed**Managing builds across dozens of packages in a JavaScript monorepo required extensive per-package Webpack configuration, leading to configuration drift, duplication, and maintenance burden. Existing monorepo tools (Lerna, Nx) focused on task orchestration but not on unifying build configuration itself.

**Novel / Inventive Aspects**

- Plugin-based Webpack configuration composition — each build concern (Babel, CSS, TypeScript, etc.) is an independent plugin that can be declaratively combined
- Automatic dependency graph resolution for build ordering across monorepo packages
- Zero-config defaults with escape-hatch customization per package
- 50+ reusable Webpack plugins covering the full JavaScript build pipeline
- Unified CLI that orchestrates builds across heterogeneous package types (libraries, apps, servers)

**References**

- GitHub: [https://github.com/jspears/mrbuilder](https://github.com/jspears/mrbuilder)
- npm: `mrbuilder-*` (v3), `@mrbuilder/*` (v4) — 50+ published packages

### INV-002: Subschema — Schema-Driven React Forms Engine

**Organization:** subschema | **Language:** React / JavaScript | **Status:** Documented — Open Source

**Summary**Subschema is a schema-driven React forms framework that generates complex, interactive forms from JSON schema definitions. It features a large ecosystem of 60+ packages covering field types, validation, conditional rendering, value management, and React Native support. The framework uses a dependency injection system for extensibility.

**Problem Addressed**Building complex forms in React — with conditional fields, nested structures, dynamic validation, and cross-field dependencies — required extensive hand-written code. No framework offered schema-driven form generation with a pluggable architecture supporting arbitrary field types and behaviors.

**Novel / Inventive Aspects**

- JSON-schema-to-React-form compilation with full conditional logic support
- Internal dependency injection system (`subschema-injection`) allowing runtime registration of custom field types, validators, and templates
- Value management layer (`subschema-valuemanager`) providing observable state with path-based access
- Schema-driven conditional field rendering based on sibling field values
- Cross-platform support via `subschema-native` for React Native
- 60+ composable packages enabling fine-grained framework customization

**References**

- GitHub: [https://github.com/jspears/subschema](https://github.com/jspears/subschema)
- npm: `subschema`, `subschema-loader`, `subschema-injection`, `subschema-valuemanager`, `subschema-native`, and 55+ additional packages

### INV-003: Nojector — Node Parameter Injection

**Organization:** jspears (personal) | **Language:** JavaScript | **Status:** Documented — Open Source

**Summary**Nojector is a lightweight dependency injection library for Node.js that uses function parameter names to automatically resolve and inject dependencies. It provides a simple, convention-based approach to DI without decorators or explicit registration.

**Problem Addressed**Early Node.js applications lacked a lightweight DI mechanism. Existing solutions required verbose configuration or class decorators. Developers needed a way to automatically wire dependencies using natural function signatures.

**Novel / Inventive Aspects**

- Parameter-name-based dependency resolution — function argument names are used as service identifiers
- Automatic dependency graph construction from function signatures
- Minimal API surface — no decorators, no configuration files
- Predecessor to the Proxy-based DI approach later developed in PBJ (INV-010)

**References**

- GitHub: [https://github.com/jspears/nojector](https://github.com/jspears/nojector)
- npm: `nojector`

### INV-004: MERS — Mongoose Express Rest Service

**Organization:** jspears (personal) | **Language:** Node.js / Express | **Status:** Documented — Open Source

**Summary**MERS (Mongoose Express Rest Service) automatically generates RESTful API endpoints from Mongoose schema definitions. It introspects Mongoose models and creates full CRUD routes with filtering, pagination, and population of referenced documents — eliminating boilerplate REST API code.

**Problem Addressed**Developers using Mongoose had to manually write Express routes for each model, duplicating logic for CRUD operations, query filtering, pagination, and relationship population. This led to significant boilerplate and inconsistency across endpoints.

**Novel / Inventive Aspects**

- Automatic REST endpoint generation from Mongoose schema introspection
- Query string-to-Mongoose-query translation for filtering and population
- Schema-aware pagination and sorting
- Automatic handling of Mongoose population (joins) via query parameters
- Convention-over-configuration approach to REST API design

**References**

- GitHub: [https://github.com/jspears/mers](https://github.com/jspears/mers)
- npm: `mers`

### INV-005: Bobamo — Mongoose + Backbone + Bootstrap Scaffolding

**Organization:** bobamo | **Language:** JavaScript | **Status:** Documented — Open Source

**Summary**Bobamo is a full-stack application scaffolding tool that generates Backbone.js + Bootstrap frontends backed by Mongoose/MongoDB data models. It provides an end-to-end application generator with automatic CRUD interfaces, form generation, and data binding from schema definitions.

**Problem Addressed**Building CRUD-heavy web applications required assembling and wiring together multiple framework layers (ORM, REST API, frontend MVC, UI framework) manually. No tool provided automatic full-stack scaffolding from a single schema definition.

**Novel / Inventive Aspects**

- Single-schema full-stack generation — Mongoose models drive both API and UI generation
- Automatic Backbone view and model generation from database schema
- Integrated Bootstrap UI component scaffolding
- Schema-driven form generation with validation
- Precursor to modern full-stack meta-frameworks

**References**

- GitHub: [https://github.com/jspears/bobamo](https://github.com/jspears/bobamo)
- npm: `bobamo`

### INV-006: postcss-react-native — PostCSS for React Native

**Organization:** speajus | **Language:** JavaScript / PostCSS | **Status:** Documented — Open Source

**Summary**postcss-react-native is a PostCSS plugin that transforms standard CSS into React Native StyleSheet-compatible JavaScript objects. It enables developers to write standard CSS (or use CSS preprocessors) and compile the output to React Native's styling format.

**Problem Addressed**React Native uses a JavaScript-based styling system (StyleSheet) that differs significantly from standard CSS. Developers could not reuse existing CSS knowledge, tooling, or stylesheets when building React Native applications. Sharing styles between web and native was impractical.

**Novel / Inventive Aspects**

- CSS-to-React-Native-StyleSheet compilation via PostCSS plugin pipeline
- Support for CSS features not natively available in React Native (media queries, pseudo-selectors mapped to component state)
- Enables existing PostCSS plugins (autoprefixer, variables, nesting) to be used in React Native workflows
- Bridging web CSS tooling with React Native's styling system

**References**

- GitHub: [https://github.com/jspears/postcss-react-native](https://github.com/jspears/postcss-react-native)
- npm: `postcss-react-native`

### INV-007: Emeth — CSS Modules Theme System

**Organization:** jspears (personal) | **Language:** JavaScript / CSS | **Status:** Documented — Open Source

**Summary**Emeth is a theming system built on top of CSS Modules that provides runtime theme switching, theme composition, and scoped theme variables. It extends CSS Modules' local scoping with a theme layer that enables dynamic style customization without CSS-in-JS overhead.

**Problem Addressed**CSS Modules provided excellent style scoping but lacked a built-in theming mechanism. Developers needed to choose between CSS Modules (with no theming) or CSS-in-JS libraries (with runtime overhead). There was no lightweight solution for theme composition with CSS Modules.

**Novel / Inventive Aspects**

- Theme composition layer on top of CSS Modules — themes are defined as CSS Module overrides
- Runtime theme switching without CSS-in-JS runtime overhead
- Theme inheritance and composition (base theme + variant themes)
- Webpack loader integration for build-time theme resolution

**References**

- GitHub: [https://github.com/jspears/emeth](https://github.com/jspears/emeth)
- npm: `emeth`

### INV-008: TypeScript Type-Level Utilities

**Organization:** jspears (gists) | **Language:** TypeScript | **Status:** Documented — Blog Post Series

**Summary**A collection of advanced TypeScript type-level utilities that push the boundaries of TypeScript's type system for compile-time computation. These include type-level arithmetic, string manipulation, conditional type patterns, and recursive type constructs used across multiple projects. These utilities were created as demonstrations for a blog post series exploring the limits of TypeScript's type system.

**Problem Addressed**TypeScript's type system is Turing-complete but lacks built-in utilities for common type-level operations. Developers building type-safe libraries needed reusable patterns for conditional types, mapped types, template literal types, and recursive type constructs.

**Novel / Inventive Aspects**

- Type-level arithmetic operations using recursive conditional types
- Advanced template literal type manipulation for string-typed APIs
- Reusable conditional type patterns for library authors
- Type-safe builder patterns using mapped and conditional types
- Foundational type utilities used in PBJ (INV-010) and Diblob (INV-011) for type-safe DI

**References**

- GitHub Gists: [https://gist.github.com/jspears](https://gist.github.com/jspears)

### INV-009: Electrode OTA Server — Over-the-Air Update Platform

**Organization:** electrode-io / WalmartLabs | **Language:** Node.js | **Status:** Documented — ⚠️ Created during WalmartLabs employment (employer-owned IP)

**Summary**The Electrode OTA Server is an over-the-air update platform for React Native and Cordova applications, enabling hot deployment of JavaScript bundles without app store review cycles. Originally developed as part of WalmartLabs' Electrode platform, it provides a self-hosted alternative to Microsoft's CodePush service with enhanced deployment management.

**Problem Addressed**Mobile app updates through app stores involve multi-day review cycles, preventing rapid bug fixes and feature delivery. Microsoft's CodePush was a hosted service with limited customization. Organizations needed a self-hosted OTA solution with enterprise-grade deployment controls.

**Novel / Inventive Aspects**

- Self-hosted OTA update server compatible with the CodePush client SDK
- Differential update generation — only changed bundles are transmitted to devices
- Deployment management with rollback, staged rollouts, and deployment keys
- Plugin architecture for custom storage backends (S3, Azure, local filesystem)
- Multi-app and multi-deployment support for enterprise environments
- Originally contributed to the open-source Electrode platform at WalmartLabs

**References**

- GitHub: [https://github.com/electrode-io/electrode-ota-server](https://github.com/electrode-io/electrode-ota-server) (original), [https://github.com/jspears/electrode-ota-server](https://github.com/jspears/electrode-ota-server) (fork)
- npm: `electrode-ota-server`, `electrode-ota-*`

**Note:** This invention was created during employment at WalmartLabs. Intellectual property rights may be owned by the employer. It is disclosed here for completeness.

### INV-010: PBJ / PBinJ — Proxy-Based Injection

**Organization:** pbinj | **Language:** TypeScript | **Status:** Documented — Open Source

**Summary**PBJ (PBinJ — Proxy-Based Injection) is a dependency injection framework for JavaScript and TypeScript that uses ES6 Proxy objects as service identifiers and lazy resolution handles. Unlike traditional DI containers that use string tokens or class references, PBJ's proxies act as both the service identifier and a transparent stand-in for the resolved service, enabling fully type-safe DI with zero boilerplate.

**Problem Addressed**Existing JavaScript/TypeScript DI frameworks required either string-based tokens (losing type safety), decorator-heavy class registration (coupling to framework), or manual factory functions (losing automation). None leveraged Proxy objects to create transparent, type-safe service handles that could be used as both identifiers and resolved values.

**Novel / Inventive Aspects**

- **Proxy-as-identifier pattern** — ES6 Proxy objects serve dual purpose as service tokens and lazy-resolved service handles
- Type-safe dependency resolution without decorators, string tokens, or explicit registration
- Automatic lifecycle management (singleton, transient, scoped) via Proxy trap interception
- Transparent proxy forwarding — consumers use the proxy as if it were the real service, with no `.get()` or `.resolve()` calls
- Ecosystem of extensions: `@pbinj/pbj-guards` (validation), `@pbinj/pbj-prometheus` (metrics), `@pbinj/pbj-visualization` (dependency graph visualization)
- Zero-dependency core with pluggable middleware architecture

**References**

- GitHub: [https://github.com/pbinj/pbj](https://github.com/pbinj/pbj)
- npm: `@pbinj/pbj`, `@pbinj/pbj-guards`, `@pbinj/pbj-prometheus`, `@pbinj/pbj-metrics`, `@pbinj/pbj-visualization`

### INV-011: Diblob — Proxy-Key Dependency Injection

**Organization:** speajus | **Language:** TypeScript | **Status:** Documented — Open Source

**Summary**Diblob is a next-generation dependency injection framework that evolves the Proxy-based DI concept from PBJ (INV-010). In Diblob, the proxy object (the "blob") is itself the container key, enabling a more ergonomic API where importing a blob automatically imports its dependency graph. The framework includes extensions for logging, configuration, OAuth, MCP integration, testing, visualization, and async context propagation.

**Problem Addressed**Even with PBJ's proxy-based approach, DI containers still required explicit container references for service registration and resolution. Developers needed a pattern where dependency graph wiring was implicit in module imports — importing a service blob should automatically bring its dependencies into scope.

**Novel / Inventive Aspects**

- **Blob-as-key pattern** — the proxy object is both the dependency graph node and the resolution key, eliminating separate container registration
- Import-driven dependency graph construction — importing a blob module wires its dependencies automatically
- Rich extension ecosystem: logging (`diblob-logger`), configuration (`diblob-config`), OAuth (`diblob-oauth`), MCP protocol (`diblob-mcp`), testing utilities (`diblob-testing`), dependency visualization (`diblob-visualizer`), async context propagation (`diblob-async-context`)
- Evolution of PBJ's proxy-based DI with improved ergonomics and module-system integration

**References**

- GitHub: [https://github.com/speajus/diblob](https://github.com/speajus/diblob)
- npm: `@speajus/diblob`, `@speajus/diblob-logger`, `@speajus/diblob-config`, `@speajus/diblob-oauth`, `@speajus/diblob-mcp`, `@speajus/diblob-testing`, `@speajus/diblob-visualizer`, `@speajus/diblob-async-context`

### INV-012: Tenence — Multi-Tenant SaaS Platform

**Organization:** tenence | **Language:** TypeScript / PostgreSQL | **Status:** Documented — ⚠️ COMMERCIAL, NOT OPEN SOURCE

**Summary**Tenence is a commercial multi-tenant SaaS platform that provides automatic tenant isolation using PostgreSQL Row-Level Security (RLS). It enables developers to build multi-tenant applications without manually implementing data isolation logic — the platform automatically generates and enforces RLS policies based on schema definitions, ensuring tenant data is cryptographically separated at the database level.

**Problem Addressed**Building multi-tenant SaaS applications requires complex data isolation logic to prevent cross-tenant data leakage. Traditional approaches (separate databases, schema-per-tenant, application-level filtering) either don't scale, waste resources, or are error-prone. No platform provided automatic, schema-driven tenant isolation using PostgreSQL's built-in RLS.

**Novel / Inventive Aspects**

- **Automatic RLS policy generation** from schema definitions — developers define their data model and Tenence generates the security policies
- Schema-driven tenant isolation without application-level filtering code
- Integration with Drizzle ORM for type-safe multi-tenant queries
- Built on rlsify (INV-018) for programmatic RLS policy management
- Leverages skibididrizz (INV-013) for TypeSpec-to-Drizzle schema compilation
- Commercial platform with proprietary tenant management, billing, and provisioning layers

**References**

- GitHub Organization: [https://github.com/tenence](https://github.com/tenence)
- Website: [https://tenence.dev](https://tenence.dev) (GitHub Pages)
- **Note:** This is a commercial venture. Source code is proprietary and not publicly available.

### INV-013: skibididrizz/drizzle — TypeSpec-to-Drizzle Compiler

**Organization:** skibididrizz | **Language:** TypeScript | **Status:** Documented — Open Source

**Summary**skibididrizz/drizzle is a compiler that generates Drizzle ORM schema definitions from TypeSpec API specifications. It bridges the gap between API-first design (TypeSpec) and database schema management (Drizzle ORM), enabling a single source of truth for both API types and database schemas.

**Problem Addressed**Teams using API-first design with TypeSpec had no way to automatically derive database schemas from their API definitions. Maintaining separate API type definitions and Drizzle ORM schemas led to drift, duplication, and type mismatches between the API layer and database layer.

**Novel / Inventive Aspects**

- **TypeSpec-to-Drizzle compilation** — generates Drizzle ORM table definitions from TypeSpec model declarations
- Single source of truth for API types and database schema
- Automatic type mapping between TypeSpec primitives and PostgreSQL/Drizzle column types
- Support for relationships, indexes, and constraints derived from TypeSpec decorators
- Common utilities package (`@skibididrizz/common`) and test helpers (`@skibididrizz/common-test`)

**References**

- GitHub: [https://github.com/speajus/skibididrizz](https://github.com/speajus/skibididrizz)
- npm: `@skibididrizz/drizzle`, `@skibididrizz/common`, `@skibididrizz/common-test`

### INV-014: Cartoonize — Photo-to-Cartoon Converter

**Organization:** jspears (personal) | **Language:** Python | **Status:** Documented — Open Source

**Summary**Cartoonize is an image processing tool that converts photographs into cartoon-style images using computer vision techniques. It applies edge detection, color quantization, and bilateral filtering to produce stylized cartoon effects from photographic input.

**Problem Addressed**Creating cartoon-style images from photographs required manual editing in graphics software or complex custom image processing pipelines. A simple, automated tool for batch photo-to-cartoon conversion was not readily available.

**Novel / Inventive Aspects**

- Automated cartoon effect pipeline combining edge detection, color quantization, and bilateral filtering
- Configurable stylization parameters for different cartoon aesthetics
- Batch processing support for multiple images

**References**

- GitHub: [https://github.com/jspears/cartoonize](https://github.com/jspears/cartoonize)

### INV-015: Inquorum — Non-Profit Board Governance Platform

**Organization:** inquorum-app | **Language:** TBD | **Status:** Pending — ⚠️ COMMERCIAL, NOT OPEN SOURCE

**Summary**Inquorum provides management software to small non-profit boards to facilitate governance. It is a commercial venture and is not open source.

**Problem Addressed**Small non-profit boards lack affordable, purpose-built software for governance tasks like meeting management, voting, document management, and compliance tracking. They often rely on generic tools (email, spreadsheets) that don't enforce governance best practices.

**Novel / Inventive Aspects**

- Purpose-built governance workflow for non-profit boards
- Meeting management, voting, and compliance tracking
- Designed for small organizations with limited technical resources

**References**

- GitHub Organization: [https://github.com/inquorum-app](https://github.com/inquorum-app)
- **Note:** This is a commercial venture. Source code is proprietary and not publicly available.

### INV-016: Kubitical — Graphical Kubernetes Management

**Organization:** kubitical | **Language:** TBD | **Status:** Pending

**Summary**Kubitical provides graphical tools for managing Kubernetes clusters, providing visual interfaces for cluster operations, resource management, and monitoring.

**Problem Addressed**Kubernetes management through kubectl CLI is complex and error-prone, especially for teams without deep K8s expertise. Existing dashboards are either too simple or too complex.

**Novel / Inventive Aspects**

- Visual K8s cluster management
- Graphical resource browser and editor
- Accessible K8s operations for teams without CLI expertise

**References**

- GitHub Organization: [https://github.com/kubitical](https://github.com/kubitical)

### INV-017: ts-wift — Swift-to-TypeScript Transpiler

**Organization:** ts-wift | **Language:** Swift / TypeScript | **Status:** Pending

**Summary**ts-wift is a transpiler from Swift to TypeScript + React, enabling SwiftUI applications to be cross-compiled to web applications. It translates SwiftUI view declarations into React component trees.

**Problem Addressed**SwiftUI applications are locked to Apple platforms. There is no automated way to bring SwiftUI apps to the web. Developers must rewrite their UI layer entirely when targeting web browsers.

**Novel / Inventive Aspects**

- Swift-to-TypeScript transpilation
- SwiftUI-to-React component mapping
- Cross-compilation of native Apple UI to web applications
- Enables code sharing between iOS/macOS and web platforms

**References**

- GitHub Organization: [https://github.com/ts-wift](https://github.com/ts-wift)

### INV-018: rlsify — PostgreSQL Row-Level Security Tooling

**Organization:** jspears (personal) | **Language:** TypeScript / PostgreSQL | **Status:** Documented — Open Source

**Summary**rlsify is tooling for generating and managing PostgreSQL Row-Level Security (RLS) policies programmatically. It provides a TypeScript API for defining RLS policies from schema definitions and applying them to PostgreSQL databases. It serves as foundational technology in the Tenence platform (INV-012).

**Problem Addressed**Manually writing and maintaining PostgreSQL RLS policies is error-prone and doesn't scale with schema changes. As database schemas evolve, RLS policies must be updated in lockstep — a process that is tedious, easy to get wrong, and can lead to data leakage if policies fall out of sync with the schema.

**Novel / Inventive Aspects**

- Programmatic RLS policy generation from schema definitions
- Integration with Drizzle ORM for type-safe policy management
- Automatic policy synchronization with schema migrations
- Foundational to Tenence's (INV-012) automatic tenant isolation layer
- TypeScript-native API for defining security policies as code

**References**

- GitHub: [https://github.com/jspears/rlsify](https://github.com/jspears/rlsify)
- npm: `rlsify`

### INV-019: Gazel — Bazel GUI

**Organization:** jspears (personal) | **Language:** TypeScript / JavaScript | **Status:** Documented — Open Source

**Summary**Gazel is a graphical user interface for Google's Bazel build system, providing visual build target management and dependency visualization. It makes Bazel accessible to developers who are unfamiliar with its CLI-driven workflow.

**Problem Addressed**Bazel's CLI-only interface makes it difficult to discover, navigate, and manage build targets in large monorepos. Teams adopting Bazel face a steep learning curve, and understanding dependency relationships between targets requires manual query commands.

**Novel / Inventive Aspects**

- Visual build target browser with search and filtering
- Dependency graph visualization for understanding target relationships
- GUI-driven build execution and target selection
- Accessible Bazel management for teams unfamiliar with CLI workflows
- Interactive exploration of BUILD files and target definitions

**References**

- GitHub: [https://github.com/jspears/gazel](https://github.com/jspears/gazel)
- npm: `gazel`

### INV-020: @speajus/markdown-to-pdf — Markdown to PDF Without a Browser

**Organization:** speajus | **Language:** TypeScript | **Status:** Documented — Open Source

**Summary**A tool that converts Markdown documents to PDF format without requiring a headless browser, using direct PDF generation. It provides a lightweight alternative to Puppeteer-based solutions for server-side and CI/CD document generation.

**Problem Addressed**Existing Markdown-to-PDF tools relied on headless Chrome or Puppeteer, adding heavy dependencies (~300MB+), slow rendering times, and complex installation requirements. Server-side and CI/CD environments needed a lightweight, browser-free solution.

**Novel / Inventive Aspects**

- Browser-free PDF generation from Markdown using direct PDF rendering
- Lightweight alternative to Puppeteer-based solutions (no Chromium dependency)
- Suitable for server-side document generation and CI/CD pipelines
- Support for common Markdown extensions (tables, code highlighting, images)

**References**

- GitHub: [https://github.com/speajus/markdown-to-pdf](https://github.com/speajus/markdown-to-pdf)
- npm: `@speajus/markdown-to-pdf`

### INV-021: mermaid-to-svg — Mermaid Charts Without a Browser

**Organization:** speajus | **Language:** TypeScript | **Status:** Documented — Open Source

**Summary**Converts Mermaid diagram definitions to SVG format without requiring a headless browser. Mermaid's standard rendering requires a DOM environment, making server-side rendering heavyweight. This tool provides browser-free rendering suitable for CI/CD and document generation pipelines.

**Problem Addressed**Mermaid diagram rendering typically requires a browser environment (DOM) because it uses D3.js and browser APIs for SVG generation. This makes server-side rendering, CI/CD integration, and automated documentation pipelines impractical without heavy browser dependencies.

**Novel / Inventive Aspects**

- Browser-free Mermaid-to-SVG rendering without DOM dependencies
- Suitable for CI/CD pipelines and server-side document generation
- Lightweight alternative to Puppeteer/Playwright-based Mermaid rendering
- Can be integrated into documentation build pipelines

**References**

- GitHub: [https://github.com/speajus/mermaid-to-svg](https://github.com/speajus/mermaid-to-svg)
- npm: `mermaid-to-svg`

### INV-022: vitest-markdown — Run TypeScript Examples in Markdown

**Organization:** jspears (personal) | **Language:** TypeScript / Vitest | **Status:** Documented — Open Source

**Summary**A Vitest plugin that extracts and executes TypeScript code examples from Markdown files as tests, ensuring documentation examples stay correct and up-to-date. It treats documentation as a test suite, catching broken examples before they reach users.

**Problem Addressed**Code examples in documentation frequently become outdated and broken because they aren't tested as part of the CI pipeline. Developers manually copy examples into test files, which quickly fall out of sync with the documentation. There was no automated way to verify that Markdown code blocks actually compile and run correctly.

**Novel / Inventive Aspects**

- Automatic extraction and execution of Markdown code blocks as Vitest tests
- Documentation-as-tests approach — Markdown files become part of the test suite
- Support for TypeScript code blocks with full type checking
- Integration with Vitest's test runner, reporters, and watch mode
- Configurable code block selection (by language tag, metadata)

**References**

- GitHub: [https://github.com/jspears/vitest-markdown](https://github.com/jspears/vitest-markdown)
- npm: `vitest-markdown`

### INV-023: ts-arg — TypeScript Decorator-Based Argument Parser

**Organization:** jspears (personal) | **Language:** TypeScript | **Status:** Documented — Open Source

**Summary**A CLI argument parser that uses TypeScript decorators to define commands, options, and arguments with full type safety. It provides a declarative, class-based approach to CLI definition where the type system enforces correctness of argument parsing.

**Problem Addressed**CLI argument parsers in the Node.js ecosystem (commander, yargs, meow) lacked TypeScript-native decorator-based definition with automatic type inference. Developers had to manually keep argument definitions and TypeScript types in sync, leading to runtime type mismatches.

**Novel / Inventive Aspects**

- Decorator-based CLI command and option definition
- Automatic TypeScript type inference for parsed arguments — no separate type declarations needed
- Class-based command hierarchy for complex CLI applications
- Type-safe argument validation derived from TypeScript types
- Integration with TypeScript's reflection metadata for automatic help generation

**References**

- GitHub: [https://github.com/jspears/ts-arg](https://github.com/jspears/ts-arg)
- npm: `ts-arg`

### INV-024: worktree — Git Worktree ZSH Plugins

**Organization:** jspears (personal) | **Language:** Shell (ZSH) | **Status:** Documented — Open Source

**Summary**ZSH plugins for managing git worktrees with enhanced shell integration, providing shortcuts and automation for common worktree operations.

**Problem Addressed**Git worktrees are a powerful feature for working on multiple branches simultaneously, but the CLI commands are verbose and lack shell integration. Developers needed streamlined workflows for creating, switching, and managing worktrees from the command line.

**Novel / Inventive Aspects**

- ZSH shell integration for git worktree management
- Shortcut commands for common worktree operations
- Tab completion for worktree names and paths

**References**

- GitHub: [https://github.com/jspears/worktree](https://github.com/jspears/worktree)

### INV-025: scrolldata — React Virtual Table

**Organization:** jspears (personal) | **Language:** JavaScript (React) | **Status:** Documented — Open Source

**Summary**A React virtual scrolling table component for efficiently rendering large datasets. It uses virtualization to render only visible rows, enabling smooth scrolling through datasets with thousands or millions of rows without browser performance degradation.

**Problem Addressed**Rendering large data tables in React caused severe performance issues — the browser DOM cannot efficiently handle thousands of table rows. Existing virtualization libraries were often complex to integrate or didn't support full table features (sorting, column resizing, fixed headers).

**Novel / Inventive Aspects**

- Virtual scrolling for large datasets with minimal DOM node creation
- Smooth scrolling experience with dynamic row height support
- React-native table component API (not a wrapper around a non-React library)
- Support for table features (sorting, filtering, column management) with virtualization

**References**

- GitHub: [https://github.com/jspears/scrolldata](https://github.com/jspears/scrolldata)
- npm: `scrolldata`

### INV-026: Deno JWT Libraries (deno-jsonwebtoken, deno-jws, deno-jwa)

**Organization:** speajus | **Language:** TypeScript (Deno) | **Status:** Documented — Open Source

**Summary**Ports of the established Node.js JSON Web Token libraries (`jsonwebtoken`, `jws`, `jwa`) to the Deno runtime. These libraries provide JWT creation, verification, signing (JWS), and algorithm support (JWA) for Deno applications, maintaining API compatibility with the Node.js originals while using Deno-native APIs.

**Problem Addressed**The Deno runtime lacked mature JWT libraries. The widely-used Node.js `jsonwebtoken` ecosystem could not run on Deno due to Node.js-specific APIs (Buffer, crypto module). Deno developers needed Deno-native JWT libraries with the same battle-tested API surface.

**Novel / Inventive Aspects**

- Deno-native ports of the `jsonwebtoken`, `jws`, and `jwa` libraries
- API compatibility with Node.js originals for easy migration
- Uses Deno's built-in Web Crypto API instead of Node.js crypto module
- Maintains the same security guarantees as the original libraries
- Three-library stack (JWA → JWS → JWT) preserving the modular architecture

**References**

- GitHub: [https://github.com/speajus/deno-jsonwebtoken](https://github.com/speajus/deno-jsonwebtoken), [https://github.com/speajus/deno-jws](https://github.com/speajus/deno-jws), [https://github.com/speajus/deno-jwa](https://github.com/speajus/deno-jwa)

## Notes for Inventor

The following items require additional documentation or action:

1. **INV-015 (Inquorum)** — As a commercial venture, detailed technical disclosure may need legal review. Consider providing more detail on key differentiators.
2. **INV-016 (Kubitical)** — Provide additional detail on technology stack and project status.
3. **INV-017 (ts-wift)** — Provide additional detail on transpilation approach and project status.
4. **Additional projects** — Review the following repositories for potential inclusion: `prisma-generator-hasura-compat`, `css-locals-loader`, `ts-named-params`, `lerna-relinker`, `@spea/pea`, `Draft-Day-Softball`, `softball-draft-system`.
5. **Commercial ventures** — Consider legal review of INV-012 (Tenence) and INV-015 (Inquorum) disclosures to ensure appropriate level of detail for proprietary technology.

## Disclaimer

This document is provided for informational purposes only, in connection with a new employment agreement. It lists personal inventions, original works of authorship, and contributions created prior to or outside the scope of any employment relationship.

**Catch-All:** Any personal projects published under the GitHub accounts `jspears` or `speajus`, or through the organizations `bobamo`, `inquorum-app`, `kubitical`, `mr-builder`, `pbinj`, `skibididrizz`, `speajus`, `subschema`, `tenence`, or `ts-wift`, or through the npm accounts `jspears`, `speajus`, or `speajus-root`, that are not individually listed above are also considered prior inventions and original works of the author.

All projects listed were created independently and are not the property of any employer, past or present, except where noted (see INV-009). The author retains all rights to these works as permitted by applicable open-source licenses and/or as proprietary intellectual property.

*This document was prepared on February 27, 2026.*
