---
name: bluesky-content-calendar
description: Plan 1–4 weeks of Bluesky posts from the user's goals and content pillars, or by repurposing a blog URL, video or transcript, draft every 300-character post, and schedule them with the PostOnce Bluesky MCP. Use when the user asks for a Bluesky content calendar, a Bluesky posting schedule, post ideas for Bluesky, or to turn one piece of content into weeks of Bluesky posts.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# Bluesky content calendar

Plan a run of Bluesky posts, write every one, and schedule them once the user approves.

## Inputs to get first

- The Bluesky account and its voice (a few past posts help).
- The goal: followers in a community, traffic to a blog or product, a launch, a newsletter.
- 2–4 content pillars (topics the account owns), or a source to repurpose: a blog URL, video, transcript, newsletter or notes.
- How many weeks (1–4), posts per week, the timezone and preferred times.
- The communities or custom feeds they want to show up in, and the words and hashtags those use.

## Build the plan

- Pick a cadence the user can keep; 3–7 posts a week is realistic for most accounts.
- Rotate formats so the feed doesn't repeat itself:

| Format | What it is |
| --- | --- |
| Insight | One opinion or lesson in plain words |
| Show your work | A screenshot, photo or short video of something real |
| Question | A specific question the community can answer from experience |
| Resource | A link to the user's own post, video or project, with why it's worth a click |
| Credit | Pointing to someone else's good work with an @mention |
| Behind the scenes | What's being built, learned or fixed this week |

- Repurposing: pull 5–10 distinct ideas from the source, one per post. Each post must stand alone within 300 characters.
- Keep links to about one post in four. Links become clickable, but there's no preview card, so pair important links with an image.
- Use 0–2 specific hashtags per post, matched to the feeds the user wants to reach.

## Write every slot

Draft each post with the `bluesky-post-writer` rules: the point in line 1, one idea, under 300 characters (count each emoji as 2 or more). Text over the limit is cut off at publish. Note media for each slot: up to 4 images or 1 video up to 3 minutes. Alt text isn't sent through this server, so keep essential information in the text.

This server can't publish threads, replies or quote posts, so don't schedule them. A longer idea becomes standalone posts on different days, or one post plus a note for the user to add replies in the Bluesky app.

## Output

Return a table: date, time (with timezone), format, the full post, character count, media needed. Ask for approval. On approval, for each slot call `create_post` with the Bluesky account and `publish_at`, or `create_draft` if the user wants to review in PostOnce first. Upload media with `create_upload_url` before scheduling slots that need it. Report each post's ID and time, and follow the `postonce` skill for confirming account and times before any call.
