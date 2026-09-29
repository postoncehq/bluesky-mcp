---
name: bluesky-post-writer
description: Write Bluesky posts within 300 characters, with links, #hashtags and @mentions that become clickable, and up to 4 images or 1 video, ready to publish with the PostOnce Bluesky MCP. Use when the user asks to write a Bluesky post, a skeet, or to turn an update, article, video or tweet into a Bluesky post.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# Bluesky post writer

Write one Bluesky post that fits in 300 characters and reads like a person wrote it, then hand it to the `postonce` skill if the user wants it published or scheduled.

## Before writing

Get or infer: the account and its voice, who they want to reach, the one idea, and any fact, link or example that proves it. From a long source, pick one idea. Never invent numbers, results, customers or quotes. If the user hands you a tweet, rewrite it for Bluesky rather than pasting it.

## The limit

300 characters. Text over it is cut off at publish, not rejected, so the ending disappears. Count links at full length and count each emoji as 2 or more (some emoji are several characters). Aim for 150–280 so there's room.

## What works on Bluesky

- Conversational and direct. Bluesky readers respond to people talking, not brand announcements.
- Line 1 says the point. No slow wind-up.
- Specifics: a number, a screenshot, a real example, a named thing.
- One idea per post. If it needs more, write standalone posts (see below).
- Community-minded tone: credit people with @mentions when you're building on their work.
- Custom feeds pick up posts by keyword and hashtag, so use the words the audience actually searches for.

## Rich text

Links, #hashtags and @mentions are turned into clickable rich text when the post publishes.

- @mentions need the full handle (`@name.bsky.social` or a custom domain handle like `@name.com`).
- Hashtags: 0–2, specific ones people follow (`#buildinpublic`, `#rstats`), at the end or inline.
- Links are clickable but no link preview card is attached. If the link needs a visual, add an image.

## Media

Up to 4 images (JPEG, PNG, WEBP or GIF; large images are resized to fit Bluesky's 2 MB limit), or 1 video (up to 3 minutes and 100 MB). Don't mix images and video. Alt text isn't sent through this server, so put anything essential about the image in the post text, or post from the Bluesky app if alt text matters for that post.

## What this server can't do

No threads or replies, no quote posts, no link cards, no editing after it's published. For a longer idea, offer either standalone posts that each make sense alone (schedule them apart), or publishing the first post and giving the user the rest to add as replies in the Bluesky app.

## Anti-patterns

- Cross-posted tweets with X-only references ("RT", "quote tweet", `@handles` that don't exist on Bluesky).
- Hashtag walls, engagement bait, "🧵" on a single post.
- "Game-changer", "unlock", "let's dive in".

## Output

Give 2 versions, each with its character count, and mark the one you'd post. Note any image to attach. Offer to publish or schedule it with the `postonce` skill; confirm the Bluesky account and the time (with timezone) before calling `create_post`.
