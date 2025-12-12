# Hand Gesture Display

Webcam hand-gesture recognizer using MediaPipe Hands. Learns gestures directly from reference images in `gestures/` and matches “close enough” live poses to those references. Shows the webcam feed with the detected label and the matched reference image.

## Install
```bash
pip install opencv-python mediapipe numpy
```

## Files
- `hand_gesture_display.py` – main script.
- `gestures/` – put your reference images here. Filenames (without extension) become gesture labels.

## Prepare reference gestures
1. Create/collect one clear image per gesture (hand visible).
2. Place them in `gestures/` (e.g., `thumbs_up.jpg`, `peace.png`, `fist.jpg`).
3. The script will extract landmarks from each image at startup; any image without a detectable hand is skipped.

## Run
```bash
python hand_gesture_display.py
```
Press `q` to quit.

## How matching works
- Landmarks from your reference images are normalized (position/scale).
- Live hand landmarks are normalized the same way.
- The script finds the reference with the smallest distance; if under a threshold, it counts as a match and shows that reference image.

## Tune matching
- Adjust the `threshold` argument in `match_gesture` (default `0.25`); increase to be more lenient, decrease to be stricter.
- Ensure reference images are clear and centered for best results.

