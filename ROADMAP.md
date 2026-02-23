# Roadmap

Ideas and growth directions for frameup.

---

## Native screen recording (v2 concept)

Instead of stitching screenshots into a video, launch a headed Chromium window at a known screen position and capture the region with ffmpeg's `avfoundation` input (macOS) in real time.

**What you'd gain:**
- Genuine 60fps with real browser rendering — GPU compositing, subpixel antialiasing, the works
- CSS animations, transitions, and parallax play at full fidelity
- No screenshot latency or frame rate ceiling
- Scroll momentum feels real because it is real

**Approach:**
1. Launch Chromium headed (`headless: false`) with `--app` flag (removes address bar/tabs), positioned at a known coordinate
2. Start `ffmpeg -f avfoundation` capturing that exact screen region at 60fps
3. Trigger scroll via `page.mouse.wheel()` — browser compositor handles animation
4. Stop ffmpeg when scroll reaches bottom, crop and encode

**Hard parts:**
- macOS Screen Recording permission — one-time user setup, can't be automated
- Window positioning — OS can be unpredictable, needs a reliable offset
- OS title bar crop — `--app` removes browser chrome but not the ~28px macOS title bar
- Scroll control — handing animation to the browser means less precise speed/easing control
- Start/stop sync — ffmpeg needs to be capturing before scroll begins

**Verdict:** Local macOS tool for designers — totally viable, quality jump would be massive. Server/CI use case — falls apart without a display. Essentially what Rotato and Screen Studio do internally.
