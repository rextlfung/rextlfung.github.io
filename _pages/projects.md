---
layout: archive
title: "Personal Projects"
permalink: /projects/
author_profile: true
---

<b>Volleybot</b>
======
[github.com/rextlfung/volleybot](https://github.com/rextlfung/volleybot)

Automatic volleyball video editing toolkit. Detects rallies in fixed-angle amateur footage and cuts out the dead time between points, turning a full game recording into a highlight reel of serves, rallies, and kills.

- Detects the volleyball in each frame using a YOLOv8 model fine-tuned on ~500 labeled frames from 3 different gyms, beating a pretrained YOLOv8x baseline by +17pp detection rate while running 6x faster
- Segments the video into rally windows with a detection state machine, refined by a frame-level live/dead classifier for precise rally boundaries
- Cuts and concatenates each rally into a single highlight reel using ffmpeg

**Ball tracking**

The fine-tuned YOLOv8 detector locating the volleyball frame-by-frame in fixed-angle gym footage.

<video controls muted playsinline loop style="max-width: 100%; height: auto;">
  <source src="/videos/volleybot_ball_tracking.mp4" type="video/mp4">
</video>

**Live vs. dead play discrimination**

The frame-level classifier telling live rally play (green) apart from dead time (red) — this signal drives which parts of the game footage get kept in the highlight reel.

<video controls muted playsinline loop style="max-width: 100%; height: auto;">
  <source src="/videos/volleybot_live_dead.mp4" type="video/mp4">
</video>
