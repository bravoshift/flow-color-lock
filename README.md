# Flow Color Lock

Browser app that locks a video's color to its first frame, undoing gradual brightening/drift from chained last-frame generations (e.g. Google Flow).

Design:
- Analysis pass: sample LAB stats (mean/sd of L, a, b) across the timeline.
- Reference: first ~0.5s of video (or a supplied reference image).
- Smooth stats over a time window, build per-time affine LAB correction toward reference.
- Render pass: WebGL shader applies correction per frame; MediaRecorder exports.
- Seed Frame tool: correct a last-frame image before feeding it back to Flow.
