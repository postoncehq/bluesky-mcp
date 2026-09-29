---
name: bluesky-custom-domain-handle
description: Walk the user through setting a custom domain as their Bluesky handle (for example @yourname.com), using a DNS TXT record on _atproto or a /.well-known/atproto-did file, then verifying it in Bluesky settings. Use when the user asks how to get a Bluesky custom domain handle, use their website as their Bluesky username, verify a domain on Bluesky, or change their Bluesky handle.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# Bluesky custom domain handle

This is an advisory walkthrough. The user makes every change in their DNS provider or web host and in the Bluesky app; the PostOnce MCP doesn't change handles or DNS. Never ask for DNS, registrar or Bluesky passwords.

## Before starting

Get: the domain or subdomain they want (`name.com`, or `name.company.com` for a team member), where its DNS is managed (Cloudflare, Namecheap, Squarespace, GoDaddy, Route 53 and so on), and whether they can edit DNS or only upload files to the site. A subdomain works well for staff handles on a company domain.

## Step 1: get the DID from Bluesky

In the Bluesky app: **Settings → Account → Handle → I have my own domain**. Enter the domain. Bluesky shows the exact record to add, containing the account's DID (it looks like `did:plc:` followed by letters and numbers). Always copy the value Bluesky shows; don't type it from memory.

## Step 2, option A: DNS TXT record (recommended)

Add a TXT record in the DNS provider:

| Field | Value |
| --- | --- |
| Type | TXT |
| Host / Name | `_atproto` (for a subdomain handle: `_atproto.name`) |
| Value | `did=did:plc:...` exactly as Bluesky shows it |
| TTL | Default |

Notes:
- Some providers add the domain automatically; if the host field shows `_atproto.name.com.name.com` after saving, enter only `_atproto`.
- Remove any older `_atproto` TXT record for the same name; there must be only one.
- DNS changes can take minutes to hours. `dig TXT _atproto.name.com` (or an online DNS lookup) shows when it's live.

## Step 2, option B: file on the website

If they can't edit DNS but control the site, serve a plain text file at `https://name.com/.well-known/atproto-did` whose entire content is the DID (`did:plc:...`), with no extra spaces or HTML. It must load over HTTPS without redirects. In Bluesky, pick the "No DNS panel" or file option.

## Step 3: verify

Back in Bluesky, tap **Verify DNS record** (or **Verify text file**), then **Update to name.com**. If it fails: check the host name, check the value has `did=` for DNS but not for the file, wait for DNS to propagate, and try again.

## After the change

- Followers, posts and the account itself stay the same; the identity is the DID, not the handle.
- The old `name.bsky.social` handle is released, so links to the old handle may stop resolving.
- Keep the domain renewed and the record in place, or the handle stops verifying.
- If PostOnce later reports the Bluesky account as disconnected, reconnect it in PostOnce with the new handle and an app password.

## Output

Give the user a short numbered checklist for their provider with the exact host and value fields filled in (using the DID they paste from Bluesky), plus how to check it's live. Offer to write an announcement post about the new handle with `bluesky-post-writer`.
