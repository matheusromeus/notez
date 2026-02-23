
**never let Claude write code until you’ve reviewed and approved a written plan**.



### Step 1: Define Your Schemas
### Step 2: Use Schemas for Validation
### Step 3: Use RPC for Service-to-Service Communication
### Step 4: Generate SDKs and Docs
### Step 5: CI Enforces the Contract

The principle is language agnostic. Protocol Buffers generate types for Go, Java, Python, C++. [Smithy](https://smithy.io/) generates for everything. JSON Schema can generate validators for any language. The insight is schema-first, not TypeScript-first.

phase 1 research
*prompt examples*
> read this folder in depth, understand how it works deeply, what it does and all its specificities. when that’s done, write a detailed report of your learnings and findings in research.md

> study the notification system in great details, understand the intricacies of it and write a detailed research.md document with everything there is to know about how notifications work

> go through the task scheduling flow, understand it deeply and look for potential bugs. there definitely are bugs in the system as it sometimes runs tasks that should have been cancelled. keep researching the flow until you find all the bugs, don’t stop until all the bugs are found. when you’re done, write a detailed report of your findings in research.md

This is the most expensive failure mode with AI-assisted coding, and it’s not wrong syntax or bad logic. It’s implementations that work in isolation but break the surrounding system. A function that ignores an existing caching layer. A migration that doesn’t account for the ORM’s conventions. An API endpoint that duplicates logic that already exists elsewhere. The research phase prevents all of this.

phase 2: planning

Once I’ve reviewed the research, I ask for a detailed implementation plan in a separate markdown file.

> I want to build a new feature "name and description" that extends the system to perform "business outcome". write a detailed plan.md document outlining how to implement this. include code snippets

> the list endpoint should support cursor-based pagination instead of offset. write a detailed plan.md for how to achieve this. read source files before suggesting changes, base the plan on the actual codebase

I use my own `.md` plan files rather than Claude Code’s built-in plan mode. The built-in plan mode sucks. My markdown file gives me full control. I can edit it in my editor, add inline notes, and it persists as a real artifact in the project.

**One trick I use constantly:** for well-contained features where I’ve seen a good implementation in an open source repo, I’ll share that code as a reference alongside the plan request. If I want to add sortable IDs, I paste the ID generation code from a project that does it well and say “this is how they do sortable IDs, write a plan.md explaining how we can adopt a similar approach.” Claude works dramatically better when it has a concrete reference implementation to work from rather than designing from scratch.

After Claude writes the plan, I open it in my editor and **add inline notes directly into the document**. These notes correct assumptions, reject approaches, add constraints, or provide domain knowledge that Claude doesn’t have.

> I added a few notes to the document, address all the notes and update the document accordingly. don’t implement yet

Claude is excellent at understanding code, proposing solutions, and writing implementations. But it doesn’t know my product priorities, my users’ pain points, or the engineering trade-offs I’m willing to make. The annotation cycle is how I inject that judgement.

Before implementation starts, I always request a granular task breakdown:
> add a detailed todo list to the plan, with all the phases and individual tasks necessary to complete the plan - don’t implement yet

phase 3: implementation

standard prompt.
> implement it all. when you’re done with a task or phase, mark it as completed in the plan document. do not stop until all tasks and phases are completed. do not add unnecessary comments or jsdocs, do not use any or unknown types. continuously run typecheck to make sure you’re not introducing new issues.


If reverted
- _“I reverted everything. Now all I want is to make the list view more minimal — nothing else.”_

Claude will sometimes propose solutions that are technically correct but wrong for the project. Maybe the approach is over-engineered, or it changes a public API signature that other parts of the system depend on, or it picks a more complex option when a simpler one would do. I have context about the broader system, the product direction, and the engineering culture that Claude doesn’t.


**Cherry-picking from proposals:** When Claude identifies multiple issues, I go through them one by one: _“for the first one, just use Promise.all, don’t make it overly complicated; for the third one, extract it into a separate function for readability; ignore the fourth and fifth ones, they’re not worth the complexity.”_ I’m making item-level decisions based on my knowledge of what matters right now.

**Trimming scope:** When the plan includes nice-to-haves, I actively cut them. _“remove the download feature from the plan, I don’t want to implement this now.”_ This prevents scope creep.

**Protecting existing interfaces:** I set hard constraints when I know something shouldn’t change: _“the signatures of these three functions should not change, the caller should adapt, not the library.”_

**Overriding technical choices:** Sometimes I have a specific preference Claude wouldn’t know about: _“use this model instead of that one”_ or _“use this library’s built-in method instead of writing a custom one.”_ Fast, direct overrides.

