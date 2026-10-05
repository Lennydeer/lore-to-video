# Design and review

## Use the work's visual language

Gather official maps, title sequences, typography, palettes, symbols, and relevant user references into `moodboard/`. Save viewable files and explain which design choice each informs. Separate published design rules from your own interpretation. If a design is already approved, resume it instead of demanding a new moodboard.

Define layout, safe areas, map scale, typography, faction colors, labels, portraits, emblems, transitions, camera motion, information density, and audio treatment in `design/design-guidelines.md`. Check actual Cyrillic glyphs and the densest frame.

## Compare complete frames

For a new design, show three substantially different whole-frame variants using the same geography, event, and participants. Each includes the map, year, event caption, names, portraits/emblems, and explanation. Include a wide map view and an event close-up when they expose different readability risks.

Build the variants as Remotion compositions or props and render their stills with Remotion. A viewing page may arrange the resulting stills for comparison; it must not implement a competing animation pipeline.

Present the variants through an interactive choice with the recommendation and consequences. Allow a combination of specific elements or written feedback. Save the chosen stills in `design/approved/` and mark the selected rules as approved.

## Produce the selected sample

Offer 2–3 short intervals with precise event boundaries, in-world dates, material readiness, and the visual behavior each tests. If the user already chose an interval, proceed with it.

Plan the sample's timing, then implement it using [Remotion production](remotion.md). The total opening, action, transitions, and ending must fit within 30 seconds. Reduce the number of events if text becomes unreadable. Use the approved soundtrack inside the composition.

Inspect intermediate frames as well as holds: moving rocks, routes, portraits, or emblems can cross a name even when the start and end frames are clear. Check after camera zooms and at event boundaries. Allow enough time to read the final result.

Save a versioned MP4, the source/settings used to produce it, a short timeline, and a verification record. Show the playable result and ask for feedback on clarity, pace, design, and music without treating a successful export as design approval.

## Revise the same interval

Record each comment in `design/feedback.md`:

| Version / time | User feedback | Planned change | Scene or general rule | Status |
|---|---|---|---|---|

Update `design/design-guidelines.md` before rendering a revision. Preserve the approved/released source and previous MP4. Save the revised sample under a new version, with a snapshot of its rules. Respect requests to update instructions or source without rerendering.

Repeat only for actual changes. Once approved, record approval and offer the next 2–3 unvisualized story intervals, or the one remaining interval. State event boundaries, dates, likely duration, participants, assets still missing, and any chronology gaps. Start the next segment after the user's choice. The 30-second limit applies to samples, not automatically to every later segment.
