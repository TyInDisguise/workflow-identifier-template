# Setup Questionnaire

## Opening (agent delivers this before asking questions)

Before we get into workflows, I need about 5 minutes to understand your context. That lets me calibrate how I ask questions and how I structure what I document.

A few things that will make this easier:

**You can speak instead of type.** Most people find it faster.
- Mac: press Fn twice to open Dictation, or use Voice Control
- Windows: Win + H for voice typing
- Any device: dictate into ChatGPT, Claude, or Gemini and paste the transcript back
- Cross-platform app: Wispr Flow

**Don't worry about structure.** Just describe what you do. I'll organize it. Rough is fine.

Answer all seven questions in one message if you like — or go one at a time. Either works.

---

## Questions

1. **Your name and role.** What do you do day-to-day?

2. **Your company in one sentence.** What does it do?

3. **Approximate team size.** Ballpark is fine (e.g., "just me," "5-10," "50+").

4. **Tech comfort level.** How would you describe yourself? Examples:
   - "I use spreadsheets daily but don't code"
   - "I'm comfortable with tools like Zapier or Airtable"
   - "I'm a process analyst — I know BPMN and have documented workflows before"

5. **Preferred tone.** When I explain things or summarize, do you prefer:
   - Plain / conversational
   - Technical / precise
   - Either is fine

6. **Your relationship to the workflow.** Are you the person who actually performs the work, or are you documenting a workflow on behalf of someone else? Either is fine — just flag it so I can calibrate. The closer you are to the actual work, the more detail we can capture.

7. **Anything else I should know?** Optional. Industry, tools you're already using, specific workflows you have in mind — whatever feels relevant.

---

## After collecting answers

Populate `_config/user-profile.md` with fields 1-4 and 6-7.
Populate `_config/tone-preferences.md` with field 5.
Confirm to the user that setup is complete and they can type `start` to begin.
