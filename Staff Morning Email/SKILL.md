---
name: staff-morning-email
description: Generate the daily morning staff email for Homecroft Elementary from the Frontline daily report. Use when Aaron asks for the morning staff email, says things like "morning email," names a weekday plus "morning email," or uses similar phrasing indicating he wants the day's staff absence email prepared. Open Frontline, pause for Aaron to log in, extract active absences and floating substitutes, ask for the daily quote, format the message, apply requested corrections, and prepare a Gmail draft only after explicit approval.
---

Generate the Homecroft morning staff email by following this workflow exactly.

Use this skill for normal school-day morning emails, Monday through Friday. It is not intended for weekend use unless Aaron explicitly asks for it.

## Open Frontline

Open the Browser skill and go to:

```text
https://absenceadminweb.frontlineeducation.com/access
```

Ask Aaron to log in if login is required. Never enter credentials.

After Aaron logs in, navigate to the Daily Report. If the dashboard exposes a dated `DAILY REPORT` link, use that visible link instead of guessing a URL.

Read the Daily Report date from the report page. Use that report date, not the computer's current date, for all email date decisions and for the Gmail draft subject.

Extract these fields for each entry:

- Teacher name as shown in `Last, First` format, then keep only the last name for the email
- Absence duration: `Full Day`, `Half Day AM`, or `Half Day PM`
- Assigned substitute, if any
- Section: `Unfilled`, `Filled`, `No Sub Required`, or `Closed`

Ignore all `Closed` entries because they are not active today.

## Identify Floating Subs

Treat `Roaming Teacher ELEM` vacancy entries as floating substitute assignments, not teacher absences.

Only use `Roaming Teacher ELEM` entries from the `Filled` section.

The assigned substitute is the floating substitute. Build one line per floating substitute using the duration:

- `Full Day` -> `[Name] is floating all day.`
- `Half Day AM` -> `[Name] is floating the AM only.`
- `Half Day PM` -> `[Name] is floating the PM only.`

Do not include any `Roaming Teacher ELEM` entry in the absence list.

Use `Karen` as the floating-sub contact name unless Aaron explicitly asks for a different name, such as `Joshua`.

## Build The Absence List

Format entries by section:

- `Filled`: `LastName (duration) - FirstName LastName`
- `Unfilled`: `LastName (duration) - No Sub`
- `No Sub Required`: `LastName - No Sub Required`

Use dashes between the teacher entry and the substitute or status.

Format duration like this:

- `Full Day` -> `(all day)`
- `Half Day AM` -> `(1/2 day AM)`
- `Half Day PM` -> `(1/2 day PM)`

Never include fill rate information or fill rate percentages anywhere in the email.

## Ask For The Quote

Ask Aaron exactly:

```text
What is the quote for today?
```

Wait for the response before writing the final email.

If Aaron gives both quote text and author, use both.

Check the quote text for likely typos, misspellings, or obvious wording errors. Point them out briefly before or during the review prompt. Do not silently correct the quote unless Aaron asks you to.

## Style References

Read these helper files before drafting the email when they are available:

- `references/email-examples.md` as the primary style authority for tone, reminder phrasing, and quote-connection style
- `references/greeting-and-closing-options.md` for rotating greeting and closing choices

The rules in this `SKILL.md` override the helper files when they conflict.

Always place the quote before the greeting, even if a reference example shows the older quote-after-greeting order. After the greeting, write 1-2 thoughtful sentences connecting the quote to Homecroft Elementary, students, teaching, or education in general. Keep the connection warm, specific, and concise; avoid generic filler or a long speech.

Use greeting and closing options on a rotating basis.

Apply these rotation rules:

- Use a different greeting for 10 runs before repeating.
- Use a different closing for 8 runs before repeating.
- If prior-day history is not available, choose options that fit the day and avoid reusing them within the same conversation.

## Write The Email

Use this structure exactly:

```text
Subject: Subs MM-DD

"[Quote text]" —[Author]

[Rotating greeting]

[One or two sentences connecting the quote to Homecroft Elementary, students, teaching, or education in general.]

**Today’s Absences:**

[Absence list - one entry per line]

**Floating Subs - Please contact [Karen/Joshua] if needed:**

[Name] is floating [all day / the AM only / the PM only].
[Additional floating subs on separate lines if any.]

[Rotating closing]
```

Apply these rules:

- Use subject `Subs MM-DD`, where `MM-DD` comes from the Daily Report date.
- Always bold `Today’s Absences:` exactly as `**Today’s Absences:**`.
- Always bold `Floating Subs - Please contact [Karen/Joshua] if needed:` exactly as `**Floating Subs - Please contact [Karen/Joshua] if needed:**`.
- If there are no absences, replace the absence section content with `No one is out today - full staff present!`.
- If there are no floating substitutes, omit the floating substitutes section entirely.
- Never include fill rate information.
- Put the quote first in the email body, before the greeting.
- After the greeting, write 1-2 thoughtful sentences connecting the quote to Homecroft Elementary, students, teaching, or education in general.
- Keep the quote connection specific and concise; do not write a generic motivational paragraph or more than two sentences.
- Use a rotating greeting and closing.

## Corrections

If Aaron requests changes after seeing the draft, apply them immediately and redisplay the full updated email.

Typical correction patterns include:

- `Add [Teacher] - [Sub]`
- `Put [Sub] in [Teacher]'s absence`
- `[Teacher] - NO SUB`
- `Change the quote`
- `Say Joshua today`

Do not require confirmation before applying a clear correction.

After every correction, ask whether the updated information is correct before creating a Gmail draft.

## Gmail Draft

Create a Gmail draft only after Aaron explicitly asks you to make or create the draft, such as `make it a draft`, `make it a Gmail draft`, or `create the draft`.

Do not create a Gmail draft from general approval language alone, such as `looks good`, `approved`, or `that works`. Treat that language as approval of the content, then wait for Aaron to ask for the draft.

Use these draft settings:

- To: leave blank
- Subject: `Subs MM-DD`, using the Daily Report date
- Body: use the full confirmed email body as plain text

Do not send the draft.

After saving the draft, reply with:

```text
Draft saved to Gmail. Ready to send whenever you are.
```
