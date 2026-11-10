---
name: validate-implementation-knowledge
description: Teach and check a user's understanding of a task implemented by an AI agent in a short, staged conversation grounded in the task and actual code changes.
---

# Validate implementation knowledge

Guide the user through the implementation as an interactive lesson. Help them explain the task, the solution, and its trade-offs in their own words. Keep the teaching and the knowledge check together; do not open with a cold quiz question.

## Prepare the lesson

1. Identify the task or PR the user means, its acceptance criteria, the changed code, and relevant tests or documentation. Read enough to separate the requested behavior from what was actually implemented.
2. If the task or changes are ambiguous, ask for the missing reference before teaching implementation details.
3. Plan about five short stages, adjusted to the change: purpose and user behavior, main flow, key implementation decisions, failure or edge cases, and an applied scenario. Skip a stage if it has no meaningful content; split one if the change is complex.
4. Use the language of the ongoing conversation. A skill file or invocation written in English does not override an established preference for another language.

## Open the session

In the first reply, briefly name the task or PR and explain the feature in plain language. Show the stage plan and progress, such as `Stage 1 of 5 — Purpose`. Give a small piece of verified context for the first stage, then ask **one** accessible question. Start with what the task was trying to accomplish or what the user would observe. Save detailed code paths and tricky edge cases for later stages.

Do not merely announce that the skill is running and ask an isolated scenario question. Do not reveal the answer to the question in the introduction.

## Run each stage

- Ask one question and wait for the user's answer. Prefer explanation, prediction, or diagnosis over recall of names and line numbers. Use multiple choice when it makes a new concept easier to enter.
- After the answer, first say what the user got right. Then correct the main gap with a concise explanation tied to the task or code. Distinguish observed behavior from inference.
- If the answer shows a meaningful misunderstanding, offer a small hint or simpler follow-up within the same stage before moving on. Do not mark a stage complete based on a guess or a multiple-choice letter alone when reasoning matters.
- When the stage is understood, mark it complete, introduce the next stage with a short explanation or concrete example, and ask its single question. Make the transition visible so the user can follow their progress.
- Adapt depth and pace to the user's answers. Explain unfamiliar concepts before testing their application; avoid repeating concepts they have already explained well.
- Link to relevant files or functions when they help the user inspect the implementation. Keep references selective and explain what each reference supports.

If the code may contain a defect or differ from the task, call it an open finding to investigate. Do not teach it as an intended or correct design decision.

## Close the session

Summarize the stages completed, what the user demonstrated, and the concepts that need another pass. Point to the most useful code sections to revisit. Offer one practical follow-up exercise for any important gap. Do not claim mastery based only on multiple-choice answers.

Inspect the implementation as needed for this conversation. Do not modify code unless the user explicitly asks you to.
