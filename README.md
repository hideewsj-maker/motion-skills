# Motion Skills: make videos with Claude Code, Codex or Cursor

**A free Claude Code skill for making short animated films.** You give your coding agent your own material (a site, a repo, a changelog, a spreadsheet, notes) and it directs a short animated film with music, then renders it as an MP4 on your computer.

- **No Remotion setup.** The agent writes the film as one HTML page (HTML, CSS and GSAP), and the engine renders it in the Chrome you already have.
- **Any Claude plan.** It works on Pro and Max and in other agents; you don't need Claude Motion, which is in beta on Team and Enterprise.
- **No video model, no credits, no upload.** Everything runs and renders locally.
- **Checked before you see it.** Before rendering, the engine looks for cut-off, covered and low-contrast text, blank stretches and single-frame pops.

<p align="center">
  <img src="assets/motion-director-tally.gif" width="640" alt="A 20-second launch teaser for a sample app, Tally 2.0, made by Motion Director from its CHANGELOG.md: the name, the new payment link shown in use, and the average time to get paid falling from 18 to 9 days, with its source on screen.">
  <br><sub>Made by Motion Director from the sample <code>examples/CHANGELOG.md</code> (a made-up app). The real film has its own score.</sub>
</p>

## Quick start

**1. Check your machine.** You need Node.js 22+, FFmpeg and Chrome:

```sh
npx motion-skills doctor
```

**2. Install the skill.** Copy `skills/motion-director` into your agent's skills folder:

| Agent | Folder |
|---|---|
| Claude Code | `~/.claude/skills/motion-director/` (or `.claude/skills/` inside a project) |
| Codex | `~/.agents/skills/motion-director/` |
| Cursor | `.cursor/skills/motion-director/` inside the project |
| Gemini CLI | `~/.gemini/skills/motion-director/` |

```sh
git clone https://github.com/hideewsj-maker/motion-skills.git
mkdir -p ~/.claude/skills && cp -R motion-skills/skills/motion-director ~/.claude/skills/
```

Or ask your agent to do it: *"Install the motion-director skill from https://github.com/hideewsj-maker/motion-skills into your skills folder."*

**3. Ask for a film:**

> Use the motion-director skill: a 15-second launch teaser for our 2.0 release, 16:9, from the notes in CHANGELOG.md.

The agent proposes **three directions**, each a one-line pitch with one still. You pick one, and it builds the film, writes its music, checks every frame and renders `out/film.mp4`. To change it, say so in plain words: *"make the second scene shorter"*, *"use our brand colours"*. You can also open `npx motion-skills studio`, click a spot in the frame and type the change there.

## What Motion Director makes

One 10–20 second film of whatever you bring:

| You bring | You get |
|---|---|
| A product, a site, a release | A teaser: the name, the one thing it does, shown in use, and the line |
| A number or a dataset | One data point that lands, drawn to scale, with its source |
| An idea, notes, an article | One idea explained, with the thing itself moving |
| A script or a hook | A vertical 9:16 hook for TikTok, Reels or Shorts |

## Full films

Motion Director is deliberately short. Each kind of film has its own full-film skill. It picks up the same project and makes the whole film (30–90 s), with that type's structure and styles built in. These skills are paid: **$4.90 each, once**, or all of them for $9.90 a month. Browse them at **[claude-motion.com/skills](https://claude-motion.com/skills)**.

| Scene | Full-film skills |
|---|---|
| Launch | [Launch Video](https://claude-motion.com/directors/launch-director) · [Walkthrough](https://claude-motion.com/directors/walkthrough-director) · [Comparison](https://claude-motion.com/directors/comparison-director) · [Brand Intro](https://claude-motion.com/directors/brand-director) · [Event Promo](https://claude-motion.com/directors/event-director) · [App Store Preview](https://claude-motion.com/directors/app-preview-director) |
| Social | [Vertical Short](https://claude-motion.com/directors/shorts-director) · [Talking-head Video](https://claude-motion.com/directors/talking-head-director) · [Titles & Transitions](https://claude-motion.com/directors/titles-director) · [Social Card](https://claude-motion.com/directors/card-director) |
| Reports | [Data Video](https://claude-motion.com/directors/data-director) · [Team Update](https://claude-motion.com/directors/update-director) · [Narrated Deck](https://claude-motion.com/directors/deck-director) · [Investor Update](https://claude-motion.com/directors/investor-director) · [Session Replay](https://claude-motion.com/directors/replay-director) |
| Teach | [Explainer](https://claude-motion.com/directors/explainer-director) · [Lesson](https://claude-motion.com/directors/lesson-director) · [Research Paper](https://claude-motion.com/directors/paper-director) · [Timeline](https://claude-motion.com/directors/timeline-director) · [Math Explainer](https://claude-motion.com/directors/math-director) |
| Personal | [Year in Review](https://claude-motion.com/directors/year-director) · [Travel Map](https://claude-motion.com/directors/trip-director) · [Video Invitation](https://claude-motion.com/directors/invitation-director) |
| Commerce | [Product Video](https://claude-motion.com/directors/product-director) · [Drop & Sale Promo](https://claude-motion.com/directors/drop-director) |
| Evidence | [News Short](https://claude-motion.com/directors/news-director) · [Investigation Film](https://claude-motion.com/directors/investigation-director) |

## How it compares

| | Claude Motion | Remotion + Claude Code | Motion Skills |
|---|---|---|---|
| Where it runs | Inside a Claude chat | Your coding agent, in a React project you set up | Your coding agent, any plan |
| Who can use it | Team and Enterprise (beta) | Anyone; companies of more than three people need a Remotion license | Anyone; this skill is free, full-film skills are paid |
| What you start from | A prompt | A Remotion project | A skill that directs one kind of film |
| Output | MP4 | MP4 and more | MP4, MOV with alpha, WebM, GIF, CapCut / 剪映 draft |

## The engine

The skill builds with the [`motion-skills`](https://www.npmjs.com/package/motion-skills) engine on npm. It provides `mo new`, `mo studio`, `mo check`, `mo sound`, `mo render` and the rest. You don't install it yourself: the skill runs it through `npx motion-skills`.

## More

- **[HTML to video](https://claude-motion.com/html-to-video):** already have an HTML animation, for example one from a Claude or ChatGPT artifact? Record it as an MP4 in your browser. Free, no upload.
- **[Claude Motion prompts](https://claude-motion.com/claude-motion-prompts):** ready-to-paste motion prompts, with previews.
- **Telemetry:** when a render finishes, the engine tells claude-motion.com which skill rendered and whether it worked. Nothing about your film is sent. Set `MOTION_SKILLS_TELEMETRY=0` to turn it off.

## License

- The Motion Director skill (`skills/motion-director/`) is free to use and modify, and everything you render with it is yours, including for commercial and client work. See [its license](skills/motion-director/LICENSE.md).

Motion Skills is an independent project and is not affiliated with Anthropic. Claude is a trademark of Anthropic, PBC.
