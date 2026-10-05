# lore-to-video

### Fictional worlds → timelines → map-based videos

Two standalone Codex skills for researching fictional worlds and turning their events into map-based videos. Both support films, TV series, anime, manga, books, and games, from verified sources to approved samples and subsequent story intervals.

## Choose a skill

| Skill | Use it for | Video production |
|---|---|---|
| **[lore-to-video-remotion](skills/lore-to-video-remotion/SKILL.md)** — recommended | The complete lore-to-map workflow with mandatory Remotion | Remotion for composition, animation, audio timing, review stills, and final MP4 export; no fallback renderer |
| [lore-to-video](SKILL.md) | The original workflow and existing installations | Remotion by default, with the original project's renderer-transition rules |

The new skill is independent and written in English. The original skill remains at the repository root for compatibility; its instructions are in Russian. Their documentation is shipped without franchise media, test projects, or rendered videos.

[Install the Remotion skill](#install-lore-to-video-remotion) · [Install the original skill](#installation) · [Example prompts](#example-prompts) · [Project outputs](#project-outputs)

## Install lore-to-video-remotion

Download this private repository using **Code → Download ZIP**, or clone it with a GitHub account that has access. Copy only the `skills/lore-to-video-remotion` folder into your local skills directory, such as `~/.agents/skills/`. The resulting entrypoint must be `~/.agents/skills/lore-to-video-remotion/SKILL.md`. Keep its `agents/` and `references/` folders alongside it.

Preserve any existing local changes before replacing an installed copy. To update, download or pull the latest repository and copy the complete skill folder again. This copied installation does not update itself when the repository checkout changes.

Invoke the new skill explicitly to select the required Remotion workflow:

```text
Use $lore-to-video-remotion for [title and adaptation].
Read the materials in [project folder] and use the approved design.
Create a sample of up to 30 seconds for [opening event] through
[closing event]. Use Remotion for animation, audio, and MP4 export.
```

The skill may also be selected automatically when a matching task requires Remotion. If Remotion is unavailable, it diagnoses the rendering problem and reports the blocker instead of changing production tools. Research, asset preparation, and media inspection remain available as supporting work.

The new package contains its own [research guide](skills/lore-to-video-remotion/references/research.md), [design and review guide](skills/lore-to-video-remotion/references/design-review.md), and [Remotion production guide](skills/lore-to-video-remotion/references/remotion.md). It does not depend on the original skill being installed.

## Workflow

| Stage | What Codex does | What the user decides |
|---|---|---|
| Research | Verifies lore and collects maps, characters, a timeline, and music | The work, adaptation, and story boundaries |
| Moodboard and design | Gathers visual references and creates three complete frame designs | The layout of the map, labels, and participants |
| Video sample | Produces a sample of up to 30 seconds with the selected music | Which story interval to use for evaluating the design |
| Revisions | Records feedback in the design guidelines and creates a new version of the same sample | Requested changes and approval |
| Next segment | Suggests story intervals that have not yet been visualized | Which part of the story to cover next |

Use the entire workflow or request a single stage. When continuing a project, Codex reads the existing materials, approved decisions, and latest feedback.

## Project outputs

Working materials are saved in a dedicated project folder alongside their sources and previous versions.

| Material | Files and folders |
|---|---|
| Scope, decisions, and current stage | `README.md` |
| Lore, geography, and events | `lore.md`, `geography.md`, `chronology.md` |
| Sources and image inventory | `sources.md`, `assets.csv` |
| Maps, portraits, and emblems | `maps/`, `characters/`, `factions/` |
| Soundtrack and recording details | `soundtrack.md`, `music/` |
| Moodboard and frame designs | `moodboard/`, `design/variants.html` |
| Design guidelines and feedback | `design/design-guidelines.md`, `design/feedback.md` |
| Video sample versions and subsequent segments | `samples/`, `videos/` |

Moodboards and frame designs are available for review, and videos are saved as MP4 files. The deliverables depend on the requested stage and available sources.

## Installation

The steps in this section install the original `lore-to-video` skill. For the required Remotion workflow, use the separate package described above.

Requires Codex with local skill support. Cloning this private repository also requires Git and GitHub authentication with access to `Lennydeer/lore-to-video`.

### Using Git

For a new installation on macOS or Linux:

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Lennydeer/lore-to-video.git "$HOME/.agents/skills/lore-to-video"
```

If a `lore-to-video` folder already exists, check the installed version and preserve any local changes before proceeding.

### Using a ZIP download

On GitHub, select **Code → Download ZIP**. Extract the archive, rename the folder to `lore-to-video`, and place it under `~/.agents/skills/`. The `SKILL.md` file must sit directly inside `lore-to-video`, with no extra folder level.

Codex discovers local skills automatically. If the skill does not appear, restart the application. See the [OpenAI documentation](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills) for skill locations and discovery behavior.

### Updating

For a copy installed using Git:

```bash
git -C "$HOME/.agents/skills/lore-to-video" pull --ff-only
```

For a ZIP installation, replace the entire skill folder with the new version. Save any local changes separately before replacing files.

## Example prompts

These examples use the original skill name. Use `$lore-to-video-remotion` instead to require Remotion throughout video production.

Replace the bracketed placeholders with the work, events, or project folder you want to use.

### Full workflow

```text
Use $lore-to-video for [title and adaptation].
Cover the period from [opening event] to [closing event].
Gather sources, maps, characters, and a timeline. Then prepare
a moodboard and three complete frame designs. After I choose
a design, suggest a story interval and create a video sample
of up to 30 seconds.
```

### Research only

```text
Use $lore-to-video to research [title and adaptation]
from [opening event] to [closing event].
I need lore, geography, participants, a timeline, and sources.
Stop after completing the research at this stage.
```

### Design from existing materials

```text
Use $lore-to-video. The materials are in [project folder].
Read them, prepare a moodboard, and create three complete
frame designs showing the map, year, event, participants,
and explanatory text. Present the designs for selection.
```

### Continue and revise

```text
Use $lore-to-video. The project is in [project folder].
Read the README, design guidelines, and latest feedback.
Apply the agreed changes to the guidelines and produce
a new version of the same video sample. Keep the previous
version for comparison.
```

## Working principles

- Keep geographic descriptions separate from events. Use dates from the fictional world's timeline.
- Verify substantial claims against sources. Mark unknown dates, distances, and routes as unknown.
- Save maps and images with their source information. Character portraits must match the story period and character form.
- Agree on the design by comparing three complete frames. Record feedback in the project guidelines before rendering revisions.
- Preserve previous video versions and track completed story intervals in the project README.

Defaults: **1920×1080, 16:9, fonts with Cyrillic support, and video samples of up to 30 seconds**. Backstory and flashbacks are excluded; spoilers within the selected interval are allowed. These settings can be adjusted for a specific project.

## Video production with Remotion

The skill uses Remotion for new map-based videos. Maps, participant markers, labels, camera movement, and event captions remain editable components. Animation follows the frame timeline, and the approved local soundtrack is included in the composition where practical.

The [Remotion workflow](references/remotion.md) covers project setup, local assets, animation, preview, MP4 rendering, and output verification. Existing Remotion projects can be continued; switching an existing project from another renderer requires agreement.

This repository contains the instructions. Remotion test projects, work-specific assets, and rendered videos are kept separately in the relevant project folder.

## Requirements for running the workflow

Each skill package contains Codex instructions and three reference guides. Research requires access to sources and local files. Video production requires a Node.js environment, compatible React and Remotion packages, a rendering browser, and tools for inspecting the resulting media. Package versions and commands are recorded in the separate video project.

Maps, portraits, video, and music are collected separately for the selected work. The skill calls for checking file availability and sources; a soundtrack streaming link does not itself provide an audio file or permission to use it.

## Skill files

The table describes the original root package. The separate Remotion-only package is in [`skills/lore-to-video-remotion/`](skills/lore-to-video-remotion/SKILL.md).

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | Main instructions, stages, approvals, and verification rules |
| [agents/openai.yaml](agents/openai.yaml) | Display name, short description, and example invocation for the Codex interface |
| [references/research.md](references/research.md) | Step-by-step guide to lore research and material collection |
| [references/design-video.md](references/design-video.md) | Moodboards, frame designs, video samples, and revision cycles |
| [references/remotion.md](references/remotion.md) | Remotion setup, frame-based animation, audio, rendering, and verification |
