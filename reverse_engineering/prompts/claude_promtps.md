Here's a structured prompt series you can feed to Claude Code:

---
 
**STEP 0 — Project Orientation Prompt**

```
You are my expert Python tutor and software architect. I've cloned crawl4ai and want to learn it by rebuilding it from scratch.

Before we start coding, do the following:

1. Read the entire project structure (all folders, files, README, pyproject.toml/setup.py)
2. Give me a bird's-eye view: what does this project do, what are its core subsystems, and how do they connect?
3. Draw an ASCII architecture diagram showing the major components and data flow
4. List the top 10 most important files I need to understand, in order of importance
5. Identify what advanced Python patterns/features are used in this codebase (async/await, metaclasses, decorators, dataclasses, protocols, etc.) — I'll need to learn these along the way

Do NOT write any code yet. Just orient me.
```

---

**STEP 1 — Bare Minimum Skeleton Prompt**

```
Now let's build crawl4ai from scratch, starting with the absolute minimum working version.

Do the following:
1. Identify the smallest possible set of files/classes needed to fetch a URL and return raw HTML — nothing more
2. For each file, show me:
   - What the real crawl4ai file does (brief summary)
   - A bare-minimum version I should write myself (stripped of all advanced features)
   - Any Python concepts this file teaches (e.g. context managers, async, dataclasses)
3. Give me explicit instructions: "Create file X, paste this code, then run this command to test it"
4. End with a working test: a single script I can run that proves Step 1 works

Keep it to 3 files or fewer. No chunking, no markdown parsing, no plugins yet.
```

---

**STEP 2 — Content Extraction Layer Prompt**

```
Step 1 is working. Now add the content extraction layer.

1. Look at how crawl4ai handles raw HTML → cleaned content (markdown, text, etc.)
2. Show me the real files responsible for this, summarize what they do
3. Give me a Step 2 version of these files — more complete than Step 1 but still no advanced plugins
4. Explain any new Python patterns introduced here (e.g. strategy pattern, abstract base classes, dataclasses with post_init)
5. Show me how to wire this into my Step 1 code
6. End with a test: fetch a real URL and print cleaned markdown output
```

---

**STEP 3 — Async Architecture & Browser Control Prompt**

```
Step 2 is working. Now I want to understand crawl4ai's async architecture and how it controls a real browser (Playwright/Selenium).

1. Explain the async design: why is it async, how does it manage concurrent crawls?
2. Show me the browser management files — how does crawl4ai launch, reuse, and close browser instances?
3. Rebuild this layer step by step:
   - First show me the real implementation
   - Then show me a simplified version I can write
   - Highlight async patterns: asyncio, context managers, semaphores, task management
4. Add this to my growing codebase
5. Test: crawl 3 URLs concurrently and show timing vs sequential
```

---

**STEP 4 — Chunking, Strategies & Design Patterns Prompt**

```
Now let's tackle the plugin/strategy architecture in crawl4ai.

1. Find all places where crawl4ai uses the Strategy Pattern, Factory Pattern, or dependency injection
2. Show me concrete examples from the real code
3. Explain WHY these patterns are used here (what problem do they solve?)
4. Rebuild the chunking/extraction strategy system:
   - Abstract base class for strategies
   - 2-3 concrete implementations
   - A factory or registry to select them
5. Teach me the Python specifics: ABCs, Protocol classes, __init_subclass__, registry patterns
6. Wire it into my existing code and test with different extraction strategies
```

---

**STEP 5 — Advanced Features & Production Hardening Prompt**

```
Final step. Let's close the gap between my version and production crawl4ai.

1. List every significant feature in crawl4ai I haven't built yet (caching, rate limiting, config system, hooks, error handling, logging)
2. For each one:
   - Show the real implementation
   - Explain the Python technique used
   - Show me how to add it to my codebase
3. Deep dive on 2-3 of the most advanced Python techniques in the whole project — the stuff that's non-obvious even to intermediate Python devs
4. Final challenge: give me a mini-project that uses my rebuilt crawl4ai to solve a real problem (e.g. scrape and summarize 10 pages)
```

---

**Tips for using these prompts:**

Start each session by saying *"We're continuing from Step X, here's what I've built so far: [paste your files]"* so Claude Code has full context. You can also ask it to slow down on any step by saying *"Don't move on — teach me more about [concept] before we continue."*