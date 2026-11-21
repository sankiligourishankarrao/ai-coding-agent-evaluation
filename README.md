# AI Coding Agent Evaluation

I build and harden evaluation tasks for frontier AI coding agents. This repository summarizes that work: the kinds of tasks I build, how each one is checked, and the tools I use.

All of this was paid client work under confidentiality rules, so no task files, prompts, datasets or client details are published here. The descriptions below are in my own words.

**Sankili Gourishankar Rao** · B.Tech, Electronics and Communication Engineering (JNTU Vizianagaram, 2024) · Gurugram, India

---

## 1. Terminal-Bench 2 tasks for coding agents

*Handshake AI Fellowship · AI Trainer, Software Engineering · Jun 2026 to present*

I build terminal tasks end to end in the open [Terminal-Bench](https://www.tbench.ai/) format. An AI coding agent works inside a Docker container, and a verifier scores its output automatically.

Tasks I have built (described by type only; the tasks themselves are unreleased):

| Category | What the agent must do | Agent's output | Expert time |
|---|---|---|---|
| Debugging and repair: pipeline and orchestration | Diagnose a failed recovery of an event-driven job system and rebuild its correct state from logs, data and a written specification | Repaired SQLite database + JSON reconciliation report | ~10 hours |
| File and media operations: video processing | Repair a broken video-recovery tool so it rebuilds the correct timeline from many partial, overlapping clips | Fixed program, rebuilt MP4 video + JSON manifest | ~14 hours |

What I build for each task:

- **Instruction:** the problem, absolute file paths, and every output the agent must produce, without giving away the method.
- **Environment:** a Dockerfile with pinned dependencies and the input data the agent needs, never the solution or the tests.
- **Reference solution:** a script that actually computes the answer, proving the task can be solved.
- **Verifier:** pytest tests, one per requirement, that check the files the agent produces, not its source code.

How I check a task before submitting it:

- Run it in the [Harbor](https://github.com/laude-institute/harbor) harness: the reference solution must score 1.0 and an agent that does nothing must score 0.0.
- Trace every test back to a requirement stated in the instruction, so no hidden rule decides pass or fail.
- Look for answer leaks, shortcuts and reward hacking an agent could use.
- Read agent run logs from repeated trials and raise difficulty until a frontier agent fails on genuine wrong answers, not timeouts or unclear wording.
- Submit through GitHub pull requests and fix whatever the automated checks flag.

## 2. Multi-hop web-research questions

*Handshake AI Fellowship*

- Wrote questions with one short, verifiable answer that frontier browsing models answered wrongly.
- Each answer needs 3 or more independent public sources, chained so no single page gives it away.
- Wrote a step-by-step research trail for every question so a reviewer could check each fact at its exact place on the page.

## 3. Coding tasks with Fail-to-Pass tests

*Outlier AI · Prompt Engineering Contributor · Jan 2025 to present*

- Write coding task prompts with fully specified interfaces and only one correct reading.
- Build unit test suites that fail on the starting code and pass on the reference solution, confirmed in Docker.
- Deliver the full package: prompt, reference solution, tests, rubric and Docker validation scripts.
- Example: a Rust concurrency task, a bounded lock-free multi-producer multi-consumer channel with blocking and async APIs. It is graded by 50 Fail-to-Pass tests (all 50 fail on the empty starting code and all 50 pass on the reference solution), with loom model-checking tests for thread interleavings and throughput benchmarks.

## 4. Hardening multimodal coding tasks

*Outlier AI*

Tasks built from real GitHub pull requests that fix a visual bug, where the screenshot is the main evidence. Example: a cross-file visual bug fix in a large open-source TypeScript data-visualization web app with deck.gl map charts, where the task can only be solved by reading the screenshot.

- Check the screenshot evidence against the original issue and replace it if it is cropped, wrong or missing.
- Remove solution hints from the instruction so the agent has to work from the symptom and the screenshot.
- Rewrite tests so any correct fix passes, not only the original one.
- Rerun the reference, no-op and agent trials after every change until a frontier agent fails the task.

## 5. Agent evaluation tasks

*Outlier AI*

- Design multi-step agent tasks (gather data, reason, produce an output) and run them live on two models. Example: an agent that searches live rental listings, compares them with a lease renewal using fixed price thresholds, and saves a short report.
- Write weighted pass/fail rubrics, pytest verifiers that check the final system state, and safety-failure annotations.
- Write tool-calling prompts that need 4 or more chained tool calls across tools such as an issue tracker, email and accounting records, with 10+ distractor tools, one verifiable answer and step-level rubrics.

## 6. Reviewing other contributors' work

*Outlier AI*

- Review prompts, tests and rubrics for ambiguity, contradictions, impossible asks and over-specific tests.

---

## Tools and skills

Python (Pandas, NumPy) · pytest · Rust test tooling (cargo test, loom) · Bash · SQL · Docker · Harbor · Terminal-Bench · Git · GitHub · Linux command line · Cursor

**Evaluation skills:** LLM evaluation, rubric writing, Fail-to-Pass test design, adversarial prompt design, red-teaming, agentic and tool-use task design, model failure analysis, fact-checking against primary sources

**Languages:** English, Hindi, Telugu

## Contact

[LinkedIn](https://www.linkedin.com/in/sankili-gourishankar-rao-060b49267/) · [HackerRank](https://www.hackerrank.com/profile/sankiligourisha1)
