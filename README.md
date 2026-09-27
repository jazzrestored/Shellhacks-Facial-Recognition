# Motion Bridge Lab

Small browser prototype for a motion-to-simulation pipeline:

`camera / keyboard → pose landmarks → normalized action event → simulation state`

## Run

Open `index.html` in a modern browser. Camera access normally requires `localhost` or HTTPS. If you have Python installed, run `python -m http.server 8000` from this folder and visit `http://localhost:8000`.

The prototype uses MediaPipe Pose from a CDN. It does not require an NVIDIA GPU. An RTX/Omniverse implementation would replace the canvas simulation with an application adapter, while keeping the normalized event contract:

```json
{
  "type": "ACTION",
  "action": "MOVE",
  "axes": {"moveX": 0.42, "moveY": -0.15},
  "confidence": 0.91,
  "timestamp": 1760000000000
}
```

## Next integration point

Send those events over WebSocket or localhost UDP to a Python/C++ simulation, game engine, or NVIDIA Omniverse/Isaac adapter. Keep perception and simulation decoupled so the simulation can run deterministically from recorded events.
