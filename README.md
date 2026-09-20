# Ask ConveyorAI · answer latency

Static builds of two prototypes for what a person sees while ConveyorAI is answering.

- **Launchpad prototype** — https://ivanatso-conveyor.github.io/ask-conveyorai-latency/prototype/
  The ⌘K palette with a recorded run playing at real pace, the run inspector (scrub, speed, run length, how it ends), and the answer with its sources. Mock data, no API.
- **Narration studio** — https://ivanatso-conveyor.github.io/ask-conveyorai-latency/narration-studio/
  The eight narration states and the ConveyorAI wheel: edit lines, icons and timing, replay a run from a dropped-in LangSmith trace or run `.json`, export the states as a sheet and the wheel as an animated SVG. *Push to prototype* sends edits to the prototype live (both pages share this origin).

The sample traces the studio ships with internally are left out of this public copy; drop your own `.json` in.

## Rebuilding

Source lives in the `comply-ui` repo, branch `claude/ai-answer-latency-prototype-08b80b`, under `packages/app-sandbox/` and `public/narration-studio/`.

```bash
# prototype → prototype/
APP_PACKAGE=app-sandbox NODE_ENV=production ARTIFACT_OUT=/tmp/sandbox-artifact \
  node_modules/.bin/webpack --config webpack/artifact-sandbox.js
# then drop the status.conveyor.com script tag from index.html, copy labs.svg and
# conveyor-favicon.ico from public/, and copy the folder to prototype/.

# studio → narration-studio/index.html
# copy public/narration-studio/index.html, removing the "Or start from a captured run" buttons.
```
