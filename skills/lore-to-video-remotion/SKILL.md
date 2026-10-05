---
name: lore-to-video-remotion
description: "Research fictional lore and create or revise map-based explainer videos using Remotion exclusively for video production. Use for lore-to-map workflows, animated event timelines, or continuation of an existing map-video project when Remotion is required. Covers source research, complete frame designs, short samples, and subsequent story intervals; a simple plot question or generic clip edit does not require this skill."
---

# Lore to video with Remotion

Turn verified story events into editable map videos. This is a standalone skill: it includes its own research, design, and production guidance and does not require the original `lore-to-video` skill.

## Required production tool

Use **Remotion for every video composition, animation, transition, audio timeline, and final MP4 export** in this workflow. This is a requirement, not a preferred default. Do not ask the user to select a renderer again.

- Keep maps, routes, portraits, emblems, labels, camera movement, and event captions as editable elements in a Remotion composition.
- Render video through the Remotion CLI or `@remotion/renderer`. Make review stills from that same composition.
- React, SVG, styling, local images, and fonts are elements of the Remotion scene. Research tools, file utilities, browsers, and media probes can support the workflow.
- Remotion's internal encoding is part of the required tool. External FFmpeg may inspect media or prepare input assets, but must not replace Remotion with a separately assembled, animated, or edited final video. Do not use Python frame generation, screen recordings, another animation engine, or an external editor as a fallback renderer.
- If Remotion cannot render, diagnose the actual failure, complete independent work, and report the blocker and remaining step. Do not silently switch tools or present an export from another renderer as completion. Only a later explicit user instruction can change this requirement.

Keep project code, dependencies, work-specific images, music, and rendered videos outside the skill package. This skill distributes instructions only.

## Resume at the requested stage

Read the project README, available research, approved visual samples, current design guidelines, and latest feedback. Continue an existing Remotion setup when suitable. If the source project uses another renderer, preserve it and adapt the requested scene into a separate Remotion project; do not overwrite the released project.

Load only the references needed for the task:

- [Research and assets](references/research.md): scope, lore, geography, events, portraits, maps, and soundtrack.
- [Design and review](references/design-review.md): moodboard, complete frame variants, sample selection, feedback, and subsequent segments.
- [Remotion production](references/remotion.md): dependencies, frame-based animation, audio, rendering, and verification. Read this before video production or changes to its implementation.

A research-only request ends with research. A request to update instructions does not authorize a new video render. Reuse approved design and story boundaries instead of restarting the whole workflow.

## Decisions with the user

Ask about unresolved story boundaries, visual direction, soundtrack changes, or the next interval through AskQuestions or the available interactive question tool. Explain the project context and the effect of each option in plain language; put the recommended option first with a short reason. Allow free-form feedback. If interactive questions are unavailable, use the same choices in a concise chat question.

Do not repeat settled decisions or ask about routine implementation details. Continue independent work while a required choice is pending; silence is not approval.

For a new full workflow:

1. Gather sources and local materials; build the moodboard.
2. Show three complete frame designs and obtain the user's choice.
3. Offer 2–3 short story intervals, then render the chosen sample with music.
4. Record feedback in the design rules before rendering a new version of that same sample.
5. After approval, propose the next unvisualized interval and proceed after selection.

Skip checkpoints that the user has already resolved. An approved first sample does not need another unchanged render.

## Story and visual rules

Use these workflow defaults unless the user gives a later project-specific instruction:

- Exclude backstory and flashbacks; allow spoilers within the selected interval. Use in-world dates.
- Separate static geography from events. Event captions describe actions and their outcomes.
- Establish participants, sides, motives, cooperation, and coercion for each event. Do not assume permanent allegiances.
- Use official images from the chosen adaptation, then its visual source material when necessary. Exclude fan art; identify any unofficial map as a reconstruction.
- Match portraits to the character's period, clothing, and form. Keep transformations as separate assets linked to the same identity.
- Start at 1920 × 1080, 16:9, with Cyrillic-capable fonts. Keep the entire test sample, including its opening and ending, within 30 seconds. Full segments follow their agreed scope.
- Keep geographic names beside places, character names beside portraits, and unit names beside emblems. Give the year, event title, and explanation their own readable screen-space elements.
- Keep soundtrack titles, chapter numbers/ranges, and production labels such as “test,” “overview,” and test duration outside the video, in its documentation or viewing page.
- Explain sourced attack types, techniques, and effects when relevant to the action; do not invent canonical names.
- Use the approved local soundtrack. A streaming page is not an audio file. Ask before substituting music or delivering a silent sample.

Do not turn one franchise's palette, map, logo, music, or layout into a universal template. Preserve uncertainty about dates, routes, and distances.

## Deliver and revise

Before delivery, inspect representative frames and the complete exported MP4: actual dimensions, duration, frame rate, decoding, playback, text readability, movement, chronology, and sound. Metadata alone does not prove audible music. Report the checks actually performed and any unavailable checks.

Record the composition ID, exact dependency versions, render command/options, source/settings snapshot, and design-rule version with each MP4. Preserve previous source versions and videos.

Put user feedback in `design/feedback.md` and apply it to `design/design-guidelines.md` before a revision. Distinguish a general design rule from a scene-specific correction. If the user says not to rerender, save the requested notes or source changes, preserve the released source snapshot, and state that the MP4 is unchanged.

Show the playable MP4 and link the usable files. Keep the project README current with decisions, unresolved gaps, completed intervals, and the latest approved version. Project feedback changes the installed skill only when the user explicitly requests that update.
