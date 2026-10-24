# CloudCheck ☁️

> **Unofficial study tool.** Not affiliated with, endorsed by, or sponsored by any cloud vendor. All practice questions are original and written for this project. No vendor logos are used.

**Hackathon problem statement:** 📝 Practice & Assessment: Smart Quiz Builder (with a 📊 Readiness Tracker)

**Live demo:** https://chala-prog.github.io/cloudcheck-unofficial-quiz/
*(also available as a Claude artifact: https://claude.ai/artifact/A6kj6P485n2o9cugnkDTnk)*

## The problem
Many practice quizzes only mark an answer right or wrong. Learners can't tell *why* they missed something, or whether they are actually ready for their exam.

## The solution
CloudCheck is a small web app for cloud fundamentals practice:

- **Quiz builder:** choose topics (Cloud concepts, Architecture & services, Security & identity, Cost & governance) and a quiz length of 4, 8 or 12 questions. Questions and answer order are shuffled every time.
- **Instant explanations:** after each answer you see the correct option and a short explanation of why it works and why the tempting alternatives don't.
- **Readiness tracker:** accuracy per topic (last 15 answers each), an overall readiness status, recent quiz scores, and a "next step" tip that points to your weakest or untouched topic.
- **Private by design:** progress is saved only in your browser (`localStorage`). No account, no server, and a one-click reset.

## Learning design
- Questions are scenario-based, not memorization of definitions.
- Explanations teach the concept, not just the answer.
- Readiness only reads "Looks ready" when **all four topics** are covered and the average is 80% or higher, so one strong topic can't hide a weak one.

## Prompt engineering
The question bank and explanations were drafted with Claude using prompts that asked for: one scenario per question, one clearly correct option, plausible distractors, and an explanation that also addresses the distractors. All questions were then reviewed and edited by hand.

## Tech
Single-file HTML, CSS and vanilla JavaScript. No build step, no dependencies. Works on mobile, supports light and dark mode, keyboard accessible.

## Run locally
1. Download or clone this repo.
2. Open `index.html` in any browser.

## Add your own questions
Open `index.html` and find the `Q` array. Add an object in this format. The **first** option must be the correct one (options are shuffled when the quiz runs):

```js
{d:"sc", q:"Your question?", o:["Correct answer","Wrong 1","Wrong 2","Wrong 3"], e:"Why the correct answer is right."}
```

Topic keys: `cc` (Cloud concepts), `ar` (Architecture & services), `sc` (Security & identity), `cg` (Cost & governance).

## Roadmap
- Move the question bank to Supabase and let learners submit their own questions
- Generate fresh questions and "explain it simply" follow-ups with the Claude API
- Study planner that turns weak topics into a dated revision schedule

## Disclaimer
This project is for learning purposes only. It does not contain real exam questions, and passing it does not guarantee any exam result.

## License
MIT
