# Remotion workflow

Use this guide when producing or revising a map-based video. Remotion is the required production tool for this skill, including the video composition, animation, audio timing, and final export. Follow the project's approved research, design, story interval, and feedback. A request to test rendering does not approve a new visual direction or new story facts.

This skill ships instructions only. Keep the Remotion project, franchise assets, music, and rendered videos in the work's project folder, outside the skill repository.

## Prepare the project

1. Inspect existing Remotion source files, package versions, render scripts, and assets. Continue the existing setup when it fits the requested test; preserve the released source and MP4.
2. For a new setup, create a separate project with `package.json`, a package-manager lockfile, a registered composition, local media in `public/`, and documented preview and render commands. Use the package manager already chosen for that project.
3. Pin all `remotion` and `@remotion/*` packages used by the project to the same tested version. Include every package imported directly by a render script as a direct dependency. Do not assume another local project's `node_modules` or an absolute machine-specific path will exist for the next user.
4. Use the agreed frame size. The workflow default is 1920×1080; 30 fps is a useful starting point unless the project specifies another rate. Calculate duration from frames and fps, and keep the complete sample within 30 seconds.
5. Select the composition explicitly when rendering. Record its ID, fps, dimensions, duration, and package versions with each output.

Suggested project layout:

```text
project/
  README.md
  package.json
  <package-manager lockfile>
  src/
    index.tsx
    Root.tsx
    MapVideo.tsx
    timeline.ts
  public/
    maps/
    portraits/
    emblems/
    fonts/
    audio/
  scripts/
    render.mjs
  sources.md
  design/
    design-guidelines.md
    feedback.md
  samples/
    sample-v01.mp4
    sample-v01.md
```

Adapt this structure to an existing project instead of reorganizing working code for its own sake.

## Connect story data to the frame

Keep event data separate from rendering: event ID, start and end frames, in-world year, title, explanation, participants, locations, actions, and source references. Geography is background information, not an event in the timeline.

Use distinct layers for the map, movement paths, participant markers, geographic labels, and the year/event caption. Keep camera transforms separate from screen-space text so zooming does not make labels unreadable. Portraits and emblems must retain their identity and scale as the map moves.

Use local images through `staticFile()` and Remotion's `Img`. Load local fonts before capturing frames; where loading is asynchronous, release the render delay on success and fail explicitly on error. Confirm Cyrillic glyph coverage when using Russian labels.

Build animation from `useCurrentFrame()` and the composition fps, using `interpolate()`, `spring()`, or deterministic functions of the frame. Avoid wall-clock timers, unseeded randomness, and CSS animations whose state depends on playback history. Scrubbing to a frame and rendering that frame should produce the same visual state.

Map routes and movement are explanatory schematics unless sources establish precise positions. Carry that distinction into the project documentation. Do not invent attacks or event details to make an animation more dramatic.

## Add the approved audio

Use the selected local recording and document its source, credits, offset, volume, and fades. Put the audio inside the Remotion composition so preview and export share its timing. Set the selected offset, volume, and fades there; do not assemble the final soundtrack in a separate postproduction pipeline. A soundtrack carried over from a previous approved version may be reused for a new test within the authorized scope.

If the selected file is missing, report the gap and ask for a file or another recording. A silent sample needs the user's agreement. Do not substitute a track without approval.

## Preview and render

Remotion Studio is useful for playback and frame-by-frame inspection. The CLI can render a named composition from an entry point:

```bash
npx remotion studio src/index.tsx
npx remotion still src/index.tsx MapVideo samples/frame-v01.png --frame=300
npx remotion render src/index.tsx MapVideo samples/sample-v01.mp4 --codec=h264 --pixel-format=yuv420p --overwrite=false
```

These are command patterns: use the actual entry point, composition ID, frame number, and versioned output path from the project. Run them only after installing the pinned dependencies. Use the project's package-manager equivalent where appropriate. A Node renderer using `bundle()`, `selectComposition()`, `renderStill()`, and `renderMedia()` is also suitable.

Let Remotion manage its browser by default. If the environment requires a specific installed browser, pass it as a documented local option or environment variable; do not hardcode a personal machine path in reusable source.

## Verify the actual result

Before presenting the sample:

- Render representative stills from the same composition, including the densest frame, event boundaries, and intermediate positions during motion. Inspect text clipping, label collisions, missing images, fonts, map positions, and camera framing.
- Render the complete MP4. Check codec, pixel format, dimensions, frame rate, duration, and audio stream with a media probe.
- Decode the complete file to catch corrupt frames; a full frame count with decoding or a supported decoder can establish this. Do not assume every bundled media utility supports every output format. Play it back to evaluate pacing, movement, transitions, and audible music. Stream metadata alone does not establish that the sound is audible.
- Check that the sequence matches the approved interval and that the final event has enough time to read. Keep production notes and source credits in the accompanying documentation when the approved design does not place them in the video.
- Record what actually passed. Distinguish source validation, a successful render, media checks, and observed playback. If playback or audio review is unavailable, state that limit rather than claiming it passed.

For revisions, update the project's design guidelines and feedback first, then save a new MP4 and the source/settings used for that version. Never overwrite an approved render as a side effect of a test.

## Troubleshooting

Keep Remotion as the renderer throughout troubleshooting. Start with the failing command and its diagnostic output. Check package version alignment, local asset paths, font-loading errors, the browser executable, and writable temporary/output folders. If rendering exhausts resources, lower concurrency before changing visual quality.

In restricted or non-interactive environments, use an available Node runtime and the package manager's supported non-interactive mode. Keep local environment workarounds in the project notes; verify them in the current environment before treating them as a general requirement.

If a supported environment fix is unavailable, stop the render step and report the concrete missing dependency, permission, or runtime capability. Preserve the prepared project and continue independent tasks. Do not route the final export through another renderer or ask the user to choose a renderer already settled by this skill.

## Official references

- [Compositions](https://www.remotion.dev/docs/composition)
- [Animating properties](https://www.remotion.dev/docs/animating-properties)
- [CLI rendering](https://www.remotion.dev/docs/cli/render)
- [Rendering with the Node API](https://www.remotion.dev/docs/renderer/render-media)

Consult documentation for the installed version when an API has changed.
