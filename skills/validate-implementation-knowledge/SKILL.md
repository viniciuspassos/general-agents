---
name: validate-implementation-knowledge
description: Assess a user's understanding of a task implemented by an AI agent through a guided conversation grounded in the task and the actual code changes.
---

# Validate implementation knowledge

Help the user understand what an AI agent implemented, why the solution works, and how it behaves in relevant scenarios. Assess the user's reasoning through a conversation, one question at a time. This is a knowledge check, not a code review or a certification.

## Prepare

1. Identify the task, its acceptance criteria, and the corresponding implementation. Use the available task description, diff, changed files, tests, and documentation.
2. Read enough of the implementation to distinguish observed behavior from intended behavior. Do not assume the agent's implementation is correct because the task was marked complete.
3. If the task or the relevant changes cannot be identified reliably, ask for the missing link, diff, or path before asking implementation-specific questions.
4. Choose a short sequence of questions covering the task's purpose, the main flow, key design decisions, and the most important failure or edge cases. Adjust the depth to the change and the user's answers.

## Guide the conversation

- Briefly identify the implementation being discussed, then ask the first question. If the target is ambiguous, clarify it before starting.
- Ask one question at a time and wait for the user's answer.
- Begin with the goal and observable behavior. Move toward code flow, design decisions, and edge cases as the user demonstrates understanding.
- Prefer questions that ask the user to explain, predict behavior, or diagnose a scenario. Use multiple choice only when it helps introduce a concept.
- Do not reveal an answer before the user's attempt. If the user is stuck, give a small hint and another opportunity.
- Ground questions in concrete parts of the implementation. Refer to files or functions when that helps the user navigate.
- Adapt each next question to the answer: explore uncertainty and avoid repeating concepts the user has already explained well.

## Give feedback

After each answer:

1. State what is correct, partly correct, or incorrect, with a concrete reason.
2. Explain the main gap using the task and implementation as evidence. Separate observed facts from inference.
3. When useful, offer a short scenario that tests the same concept from another angle.
4. Continue with the next question only after giving feedback.

If you find a possible defect or a mismatch with the task, describe it as something to investigate. Do not teach it as an intended or correct design decision.

## Finish

Summarize what the user demonstrated, what still needs review, and the most useful files or code sections to revisit. If a significant gap remains, offer one practical follow-up question or exercise. Base the assessment on the user's explanations and reasoning; multiple-choice answers alone do not establish mastery.

Inspect the task, code, and tests as needed for this conversation. Do not change the implementation unless the user explicitly asks you to.
