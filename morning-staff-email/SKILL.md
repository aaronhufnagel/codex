---
name: morning-staff-email
description: Generate the daily morning staff email for Homecroft Elementary from the Frontline daily report. Use when Aaron asks for the morning staff email, says things like "morning email," names a weekday plus "morning email," or uses similar phrasing indicating he wants the day's staff absence email prepared. Open Frontline, pause for Aaron to log in, extract active absences and floating substitutes, ask for the daily quote, format the message, apply requested corrections, and prepare a Gmail draft when approved.
---

Generate the Homecroft morning staff email by following this workflow exactly.

Use this skill for normal school-day morning emails, Monday through Friday. It is not intended for weekend use unless Aaron explicitly asks for it.

## Build The Date

Get today's date in this format:

```bash
date +"%A, %B %-d, %Y"
```

Use that value for the subject line date.

## Open Frontline

Open a browser and go to:

```text
https://login.frontlineeducation.com/login?signin=9d6c2b5b8299f9750cedd98736c3c7cb&productId=ABSMGMT&clientId=ABSMGMT#/login
```

Ask Aaron to log in if login is required. Never enter credentials.

After Aaron logs in, select the daily report from the left menu.

When the report page is visible, wait 4 seconds, then read the page using:

- `filter: all`
- `depth: 15`
- `max_chars: 80000`

Extract these fields for each entry:

- Teacher name as shown in `Last, First` format, then keep only the last name for the email
- Absence duration: `Full Day`, `Half Day AM`, or `Half Day PM`
- Assigned substitute, if any
- Section: `Unfilled`, `Filled`, `No Sub Required`, or `Closed`

Ignore all `Closed` entries because they are not active today.

## Identify Floating Subs

Treat `Roaming Teacher ELEM` entries as floating substitute assignments, not teacher absences.

Only use `Roaming Teacher ELEM` entries from the `Filled` section.

The assigned substitute is the floating substitute. Build one line per floating substitute using the duration:

- `Full Day` -> `[Name] is floating today.`
- `Half Day AM` -> `[Name] is floating the AM only.`
- `Half Day PM` -> `[Name] is floating the PM only.`

Do not include any `Roaming Teacher ELEM` entry in the absence list.

Use `Karen` as the floating-sub contact name unless Aaron explicitly asks for a different name, such as `Joshua`.

## Build The Absence List

Format entries by section:

- `Filled`: `LastName (duration)--FirstName LastName`
- `Unfilled`: `LastName (duration)--No Sub`
- `No Sub Required`: `LastName--No Sub Required`

Format duration like this:

- `Full Day` -> `(all day)`
- `Half Day AM` -> `(1/2 day AM)`
- `Half Day PM` -> `(1/2 day PM)`

If Aaron's normal style for a full-day absence is to omit `(all day)`, it is acceptable to omit it.

Never include fill rate information or fill rate percentages anywhere in the email.

## Ask For The Quote

Ask Aaron exactly:

```text
What is the quote for today?
```

Wait for the response before writing the final email.

If Aaron gives both quote text and author, use both.

## Style References

Read these helper files before drafting the email:

- `references/email-examples.md` as the primary style authority for tone, section wording, reminder phrasing, floating-sub phrasing, and closing style
- `references/greeting-and-closing-options.md` for rotating greeting and closing choices

Treat `references/email-examples.md` as the default style guide whenever there is a wording choice. Match the examples as closely as the current day's data allows.

Use `references/email-examples.md` to decide:

- whether to use `Today's Absences:` or `Here are the people who are out:`
- how to write a brief quote connection after the greeting
- whether to include operational reminders such as testing schedule notes as their own short paragraph
- whether floating substitutes should appear as a labeled section or as compact sentences followed by `Let Karen know how they can help you.`
- whether the closing should be the standard `Have a wonderful day, everyone! 🌟`, a variant such as `Have a wonderful day!!`, or another pattern supported by the examples

Always place the quote before the greeting, even if a reference example shows the older quote-after-greeting order. After the greeting, write 1-2 thoughtful sentences connecting the quote to Homecroft Elementary, students, teaching, or education in general. Keep the connection warm, specific, and concise; avoid generic filler or a long speech.

When there is no strong reason to do otherwise, prefer the sample style that best matches the current day and the amount of content available.

Use the greeting and closing options on a rotating basis, but keep the final wording aligned with the patterns shown in `references/email-examples.md`.

Apply these rotation rules:

- Do not repeat the same greeting two days in a row
- Do not repeat the same closing two days in a row
- On Fridays, use a Friday-specific greeting if one is available
- On Fridays, rotate among the Friday-specific closings instead of using the general closing list

If prior-day history is not available, choose any option that fits the day and avoid reusing it within the same conversation.

## Write The Email

Use this structure exactly:

```text
Subject: Good Morning, Homecroft! – [Day], [Month] [Date]

*"[Quote text]"* —[Author]

Good morning, Homecroft family! [Rotating greeting]

[One or two sentences connecting the quote to Homecroft Elementary, students, teaching, or education in general.]

**Today's Absences:**

[Absence list — one entry per line]

**Floating Subs — Please contact [Karen/Joshua] if needed:**
[Name] is floating [today / the AM only / the PM only].
[Additional floating subs on separate lines if any.]

[Rotating closing]
```

Apply these rules:

- If there are no absences, replace the absence section content with `No one is out today — full staff present!`
- If there are no floating substitutes, omit the floating substitutes section entirely
- Never include fill rate information
- Put the quote first in the email body, before the greeting
- Use a short rotating greeting after `Good morning, Homecroft family!`
- After the greeting, write 1-2 thoughtful sentences connecting the quote to Homecroft Elementary, students, teaching, or education in general
- Keep the quote connection specific and concise; do not write a generic motivational paragraph or more than two sentences
- Use a rotating closing from the helper file instead of a fixed closing line

## Corrections

If Aaron requests changes after seeing the draft, apply them immediately and redisplay the full updated email.

Typical correction patterns include:

- `Add [Teacher]--[Sub]`
- `Put [Sub] in [Teacher]'s absence`
- `[Teacher]--NO SUB`
- `Change the quote`
- `Say Joshua today`

Do not require confirmation before applying a clear correction.

## Gmail Draft

When Aaron approves with language such as `looks good`, `send it`, `approved`, or `that works`, create a Gmail draft.

Use these draft settings:

- To: leave blank
- Subject: use the exact generated subject line
- Body: use the full email body as plain text

After saving the draft, reply with:

```text
Draft saved to Gmail. Ready to send whenever you are.
```
