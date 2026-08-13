# Vision Ring / Freeze Logging

Run the diagnostic copy on Nano without replacing the known-good detector:

```bash
cd /home/nano/yolov5
python3 detect_ultra2_diag.py 0
```

Controls:

- `F`: freeze the in-memory ring and write CSV + JSON.
- `E`: export a snapshot without freezing recording.
- `R`: clear the ring and resume a new run.
- `Q`: freeze, export, and exit.

Automatic freeze triggers:

- camera open failure;
- frame capture failure;
- unhandled inference or post-processing exception.

Output defaults to `vision_logs/`. Override the directory and ring capacity with:

```bash
VISION_LOG_DIR=/tmp/vision_logs VISION_LOG_CAPACITY=1800 \
  python3 detect_ultra2_diag.py 0
```

Benchmark a fixed number of frames without rendering:

```bash
VISION_HEADLESS=1 VISION_MAX_FRAMES=300 VISION_PROGRESS_EVERY=30 \
  VISION_ENGINE=best_fp16_nano.engine VISION_INPUT_SIZE=256 \
  python3 detect_ultra2_diag.py 0
```

Use `VISION_POSTPROCESS=fixed` for correct XYWH, class-aware OpenCV NMS.
The default remains `baseline` so the known-good behavior can be compared.

Current Nano desktop live command (`DISPLAY=:1`):

```bash
cd /home/nano/yolov5
DISPLAY=:1 XAUTHORITY=/run/user/1000/gdm/Xauthority \
VISION_ENGINE=best_320_fp16_nano.engine VISION_INPUT_SIZE=320 \
VISION_POSTPROCESS=fixed VISION_LOG_DIR=vision_logs/live_320_fp16 \
VISION_PROGRESS_EVERY=30 python3.6 detect_ultra2_diag.py 0
```

The ring stores metadata only, not raw frames. Important fields include capture,
preprocess, GPU, postprocess, render and total time; instantaneous/rolling FPS;
candidate/final detection counts; per-class counts; maximum confidence; engine,
input size and thresholds. Disk writes occur only on freeze/export.
