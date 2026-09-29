---
name: bluesky-bio-generator
description: Write a Bluesky bio (profile description) of up to 256 characters, plus a display name and a pinned post idea, for the user to paste into their Bluesky profile. Use when the user asks for a Bluesky bio, a Bluesky bio generator, bio ideas, or help setting up their Bluesky profile.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# Bluesky bio generator

Write a bio that tells someone in one read who this is, what they post and why to follow. The PostOnce MCP can't edit profiles; the user pastes the result into Bluesky under **Edit profile**.

## Before writing

Get: who the account is (person, creator, project, brand), what they post about, who they want to follow them, one proof point (role, project, result), any link they want in the bio, and their current bio if any. Ask for the tone: plain, warm, dry, playful. Never invent credentials, employers, numbers or awards.

## Limits

| Field | Limit |
| --- | --- |
| Bio (description) | 256 characters |
| Display name | 64 characters |

Line breaks are allowed in the bio. Links and @mentions in the bio become clickable, so a website can go in the bio itself. Count each emoji as 2 or more characters.

## What makes a Bluesky bio work

- Say what you post about. People follow on Bluesky for topics and personality, and many find accounts through starter packs and custom feeds, so topic words help.
- One proof point or context line: "Maintainer of [project]", "[Role] at [org]", "Writing [newsletter]".
- A human line is welcome: a hobby, a place, a running joke. Keep it to one.
- Short lines separated by line breaks read better than one long sentence.
- If the account moved from X, it's fine to say "Formerly @[handle] on X", but don't make it the whole bio.
- Pronouns, location or languages if the user wants them.
- Avoid hashtag lists and "DMs open for collabs" filler.

Patterns:
- "[What I do] · [what I post about]\n[proof point]\n[link]"
- "Posting about [topic 1], [topic 2] and [topic 3]. [Role] at [org]. [One human detail]."
- "[Project] maintainer. Here for [topic] and the occasional [hobby]."

## Display name and pinned post

- Display name: the name people know, optionally with a short topic or emoji. Don't keyword-stuff.
- Pinned post: suggest one post that introduces the account (who you are, what you post, a link). If the user wants it, write it with `bluesky-post-writer` (300 characters). Pinning happens in the Bluesky app; the MCP can publish the post but can't pin it.
- A custom domain handle (`@yourname.com`) also signals who you are; see `bluesky-custom-domain-handle`.

## Output

Give 3 bio options with character counts, a display name suggestion and a pinned post draft. Remind the user to paste the bio into Bluesky themselves. Offer to publish the pinned post with the `postonce` skill (confirm the account and time before `create_post`).
