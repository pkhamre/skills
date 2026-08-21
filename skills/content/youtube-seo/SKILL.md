---
name: youtube-seo
description: Build the complete YouTube upload package from a video or podcast transcript; three title options, a search-optimized description with chapter timestamps, comma-separated tags that stay inside YouTube's limits, a pinned comment meant to draw replies, and thumbnail suggestions, saved as a structured markdown file. Use this whenever the user shares a transcript, recording notes, or spoken-word content and wants to publish, rank, or SEO it on YouTube. Triggers on phrases like "SEO for this video", "write a YouTube description", "suggest titles and tags", "chapters for my video", "help me upload this", "make this rank", or a transcript file dropped in with publishing intent, even when the user never says "SEO". Do not use for blog posts, general copywriting, or non-YouTube content.
---

# YouTube SEO

A skill that turns a transcript into the whole upload package for a YouTube video. The user ends up with three title options, a description with chapter timestamps ready to paste, comma-separated tags within YouTube's character limits, a pinned comment built to start conversation, and thumbnail suggestions. Everything lands in one markdown file they can copy sections from while uploading.

## When this runs

The user hands over a transcript, recording notes, or spoken-word content and wants it ready to publish on YouTube. That can arrive as "write the SEO for this" or "help me upload this video" or as a bare transcript file dropped in with no instructions at all. Even the last one counts: someone who pastes a transcript is usually thinking about publishing it.

## Gather context before writing a word

### Read the transcript first

Read the whole transcript before deciding anything about titles, chapters, or keywords. A half-read transcript produces a description that names the wrong takeaways.

### Mine the repository

Users often keep their previous transcripts and ideas in the same repo. Before asking anything, look for context that already exists: sibling transcript files, past SEO documents, channel notes, an ideas folder, or a README that describes what the channel is about. Match the terminology and tone you find. If the video belongs to a recurring series, keep its naming style. Note what you found and where, so the user knows the copy was shaped by their own history.

### Ask only for what is missing

Good SEO depends on who the video is for and what phrase should rank. Fill the gaps the repo cannot: the channel's niche or topic, the target audience, and any keyword or search phrase the user wants to win. Ask at most two or three short questions, and only when the answer is not already available. If the transcript plus repo context already answer these, skip the questions and generate. If the moment for questions has passed, for instance when the transcript arrived with an expectation of output rather than dialogue, make sensible assumptions from the transcript itself and note them in the document so the user can correct course.

### Handle timestamps

Inspect the transcript for timecodes before planning chapters. Timecodes appear in forms like `00:12:34`, `[12:34]`, or `(12:34)`. When they exist, map each chapter to the nearest real timecode. When they are absent, split the transcript into chapters by topic and estimate each start time by word proportion, then mark every timestamp as an estimate and tell the user to verify before publishing. Never present estimated times as real.

## Style

Conservative and straightforward. The copy should read like a confident professional wrote it, not a hype machine. That means descriptive titles that deliver what they promise, no ALL CAPS, no exclamation points, no "you won't believe", no fake urgency, and no emoji clutter. Search engines reward the same thing viewers do: copy that clearly states what the video contains.

Load the `anti-ai-slop-writing` skill when it is available in this environment. Check the available skills list; if that skill can be loaded, load it and apply its rules to the titles, description, and pinned comment. When it is not available, apply its principles directly: vary sentence length, drop banned filler words, avoid em dashes and exclamation marks, skip the rule-of-three rhythm, and stay away from corporate cheerleading. The description and the pinned comment are where this matters most, because those are the copy a viewer actually reads.

## The output document

Generate a markdown file and save it as `<transcript-name>.seo.md` next to the transcript, or in the working directory if the transcript is pasted in chat. Report the path when done. Use this template exactly:

```markdown
# SEO Package: <working title>

## Titles
1. <title option 1> (~<n> chars)
2. <title option 2> (~<n> chars)
3. <title option 3> (~<n> chars)

## Description
<copy-paste ready description>

## Tags
<comma separated>

## Pinned Comment
<comment text>

## Thumbnail Suggestions
- <suggestion>
- <suggestion>
```

## Titles

Three options, each under 70 characters so they do not truncate in search results, each with the primary keyword as early as possible. Make them read naturally rather than stuffed. Give each a different angle: a keyword-first version, a how-to or question version, and a version built around the outcome the viewer gets. Consult `references/youtube-platform-limits.md` for the constraints that matter.

## Description

Open with two to four sentences that state what the video covers and what the viewer gets out of it, with the primary keyword in the first 150 characters because that is the part search results show. Follow with the chapter list. Then leave a short line inviting subscriptions or comments only if it fits the channel's voice. Use one to three hashtags at most, and keep the whole thing under the description limit in `references/youtube-platform-limits.md`.

Chapters follow YouTube's rules: the first timestamp is 0:00, there are at least three total, and each chapter runs at least ten seconds. Group by topic shifts, not by every sentence. A chapter title names the topic plainly, so a viewer scanning the list knows what each section covers.

## Tags

Comma-separated, total length under 500 characters. Mix one or two broad tags with several specific ones: phrases people actually search for, synonyms, and common alternate spellings of key terms. Pull tags from words and phrases that genuinely appear in the transcript, not from a generic list you could attach to any video.

## Pinned Comment

One or two sentences. Ask a question tied to the video's actual content, the kind that invites people to share their own experience or answer. Optionally add a single call to action, like pointing to the next video in the series. This is engagement bait in the good sense: it gives a viewer a reason to type something.

## Thumbnail Suggestions

Two or three ideas, each with a concrete visual: a text overlay of three to five words, the focal subject, and the background or contrast treatment. Reference the channel's existing thumbnails for consistency when repo context shows them. Keep the style clean and readable at small sizes, since that is how most viewers first see it. Note the 16:9 aspect ratio.
