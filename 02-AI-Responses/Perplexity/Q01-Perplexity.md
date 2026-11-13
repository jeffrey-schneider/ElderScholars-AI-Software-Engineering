The interesting part is what happens after someone says, “It works.” Companies then have to answer a much harder question: “Can we depend on it?”

What you’re calling “after the vibe” is the transition from a generated solution to an owned, secure, maintainable business system. AI can accelerate the first working version; it doesn’t automatically supply the testing, operational controls, or accountability needed to run it. IBM explicitly distinguishes code generation from the broader engineering work required for production.[[ibm](https://www.ibm.com/think/topics/vibe-coding)]

My framing: **vibe coding** makes software easier to create. The next challenge is deciding which of that software deserves to become infrastructure—and who takes responsibility when it does.

## What happens after the prototype?

A useful way to organize the work is into three paths—not a universal industry standard, but a practical synthesis of the approaches described by IBM and enterprise practitioners.[[ibm](https://www.ibm.com/think/topics/vibe-coding)][[onext](https://www.onext.es/en/insights/vibe-coding-business-apps-without-engineering/)]

|Path|What happens next|Where it fits|
|---|---|---|
|Keep it small|Leave it as a limited-use tool, with an owner and controls appropriate to its data and permissions.|Personal productivity tools and low-risk internal workflows.|
|Harden it|Keep the useful code, but add reviews, tests, security checks, deployment discipline, and monitoring.|Applications that other people will depend on.|
|Treat it as a specification|Use the prototype to establish what users actually want, then have engineering refactor or rebuild the important parts.|Experiments whose behavior is valuable but whose implementation isn’t ready for production.|

The distinction matters: a prototype can successfully demonstrate the right solution without being the right implementation. Enterprise practitioners describe using these applications both as experimental prototypes that engineering later refactors and as tools supported by shared engineering controls.[[onext](https://www.onext.es/en/insights/vibe-coding-business-apps-without-engineering/)]

## The work moves from “building” to proving, operating, and owning

### 1. Proving that it works beyond the demo

The first task is reviewing the generated code and testing the application—not merely confirming that the happy-path demonstration succeeds. That includes dependencies, security vulnerabilities, compliance requirements, and whether the architecture will remain understandable as the application changes. These are among the production requirements IBM identifies as separate from generating the code itself.[[ibm](https://www.ibm.com/think/topics/vibe-coding)]

For a hypothetical invoice app, the shift is from “Can it process this invoice?” to “What happens if the invoice is duplicated, the accounting API times out, or the wrong employee tries to approve it?”

### 2. Giving it a production environment

Some companies are trying to make deployment as easy as generation:

- Google describes “vibe deploying”: moving a generated app to a managed environment such as Cloud Run through a prompt or a click.[[cloud.google](https://cloud.google.com/discover/what-is-vibe-coding)]
- Heroku’s chief architect describes supplying the underlying application infrastructure, including managed Postgres, while emphasizing configuration management, version control, security, and scaling.[[stackoverflow](https://stackoverflow.blog/2025/06/25/you-ve-vibe-coded-an-app-now-what/)]

These are examples of what vendors are offering, not evidence that every customer has solved the operational problem. The important distinction is that making an app accessible is only part of making it dependable. The Heroku discussion specifically highlights maintenance, team collaboration, code review, and vulnerability management after generation.[[stackoverflow](https://stackoverflow.blog/2025/06/25/you-ve-vibe-coded-an-app-now-what/)]

### 3. Connecting production feedback back to the AI

There is also an emerging loop beyond “prompt → code”:

**Generate → deploy → observe → diagnose → revise.**

In the Heroku discussion, the next capability is giving an agent access to the deployed application’s logs and metrics so it can help investigate failures that don’t occur locally. That extends AI assistance into operations rather than stopping at code creation. It does not eliminate the need for engineering judgment or controls.[[stackoverflow](https://stackoverflow.blog/2025/06/25/you-ve-vibe-coded-an-app-now-what/)]

### 4. Assigning ownership and governing the growing inventory

At the organizational level, the problem becomes: Which apps exist? What information can they access? Who maintains them? What happens when their creator leaves?

One enterprise practitioner’s proposed approach includes an application inventory, reviews based on the sensitivity of the data involved, automatic checks for secrets and dependencies, and an explicit plan for orphaned applications. The review follows the application’s risk—not whether its author happens to be a professional developer.[[onext](https://www.onext.es/en/insights/vibe-coding-business-apps-without-engineering/)]

## Where the business opportunity sits

My interpretation is that “after the vibe” creates demand in three connected areas:

- Production-readiness services: assess a prototype, repair or replace weak components, and establish testing and deployment controls.
- Managed operations: host it, monitor it, patch it, and support it.
- Enterprise governance: discover employee-built applications, constrain their permissions, and establish ownership.

Those are opportunity categories, not a measured market-size claim. They follow directly from the gap between generating an application and maintaining secure, reliable production software described by IBM, Heroku, and enterprise practitioners.[[ibm](https://www.ibm.com/think/topics/vibe-coding)][[onext](https://www.onext.es/en/insights/vibe-coding-business-apps-without-engineering/)][[stackoverflow](https://stackoverflow.blog/2025/06/25/you-ve-vibe-coded-an-app-now-what/)]

The central change is not that engineering disappears. It’s that the starting point shifts: instead of receiving a requirements document, engineering may receive a working application—and must determine what is safe to keep, what needs rebuilding, and what the business is now willing to depend on.[[ibm](https://www.ibm.com/think/topics/vibe-coding)][[onext](https://www.onext.es/en/insights/vibe-coding-business-apps-without-engineering/)]