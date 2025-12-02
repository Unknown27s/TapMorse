# 🎯 TapMorse — Virtual Morse Code via Webcam (v2.0)

Transform your table into an advanced Morse code input device using computer vision! Tap Morse code patterns on any surface and see them decoded into text in real-time with audio feedback and intelligent timing calibration.

## Project Name
- Code name: TapMorse

## Credits
- Built by: Unknown27s
- Assisted by: GitHub Copilot 

## License
This project is open source under the MIT License. See `LICENSE` for details.

## Community
- Please read `CONTRIBUTING.md` before opening PRs.
- Be kind and follow our `CODE_OF_CONDUCT.md`.

## ✨ Features

### Core System
- **🎥 Camera-based detection** - Uses your webcam to detect taps on any surface
- **⚡ Real-time Morse decoding** - Converts tap patterns to text instantly  
- **🎯 Auto-calibration** - Learns your tapping speed and adjusts timing automatically
- **🔊 Audio feedback** - Distinct sounds for dots, dashes, and completions
- **📊 Statistics tracking** - Monitor your progress and accuracy over time

### Enhanced Experience  
- **📋 Visual Morse guide** - On-screen reference with common patterns
- **💾 Settings persistence** - Saves your preferences automatically
- **🎮 Advanced controls** - Toggle features with keyboard shortcuts
- **🚀 Smart timing** - Intelligent word gap detection and error handling
- **📈 Progress tracking** - Full statistics with accuracy percentages

## Quick Start

### 1. Install Dependencies
Use the provided requirements file (includes OpenCV, NumPy, scikit-learn):
```powershell
python -m pip install -r requirements.txt
```

### 2. Run the System
```powershell
# Use your default Python
python table_click_detector.py

# If needed, run with an explicit interpreter path on Windows
& "C:/Program Files/Python312/python.exe" "F:/Git floder(Project)/mouse_code/table_click_detector.py"
```

### 3. Setup Process
1. **Draw ROI** – Drag the mouse to select the table area to monitor.
2. **Confirm ROI** – Press `c` to confirm the ROI.
3. **ML Training (default)** – You will be prompted to collect samples:
	- Collect `N` hovering samples (default 10). Press `SPACE` for each sample.
	- Collect `N` clicking samples (default 10). Press `SPACE` for each sample.
	- Move your hand slightly between captures for variety.
	- After training, the ML model runs in real time.
4. **Fallback (no-ML)** – If ML is disabled or fails, you’ll capture 2 references:
	- Hovering reference (hand above table), press `SPACE` to capture.
	- Clicking reference (hand down on table), press `SPACE` to capture.
5. **Start tapping!** – Begin tapping Morse code patterns.

## Morse Code Timing

- **Dot (·)**: Quick tap (< 0.3 seconds)
- **Dash (-)**: Long tap (0.5 - 1.2 seconds)  
- **Letter gap**: 0.6 second pause between letters
- **Word gap**: 1.4 second pause between words
- **Auto-decode**: 2 second timeout automatically decodes current letter

## Example Morse Patterns

| Letter | Code | Letter | Code | Number | Code |
|--------|------|--------|------|---------|------|
| A | ·- | N | -· | 1 | ·---- |
| B | -··· | O | --- | 2 | ··--- |
| C | -·-· | P | ·--· | 3 | ···-- |
| D | -·· | Q | --·- | 4 | ····- |
| E | · | R | ·-· | 5 | ····· |
| F | ··-· | S | ··· | 6 | -···· |
| G | --· | T | - | 7 | --··· |
| H | ···· | U | ··- | 8 | ---·· |
| I | ·· | V | ···- | 9 | ----· |
| J | ·--- | W | ·-- | 0 | ----- |
| K | -·- | X | -··- | | |
| L | ·-·· | Y | -·-- | | |
| M | -- | Z | --·· | | |

## Practice Examples

**"HELLO":**
- H: ···· (4 quick taps)
- E: · (1 quick tap)  
- L: ·-·· (quick-long-quick-quick)
- L: ·-·· (quick-long-quick-quick)
- O: --- (3 long taps)

**"SOS":**
- S: ··· (3 quick taps)
- O: --- (3 long taps)
- S: ··· (3 quick taps)

## Controls

- `ESC`: Quit the program
- `r`: Reset decoded text and current signal
- `s`: Print detailed statistics to the console
- `g`: Toggle on-screen Morse guide
- `a`: Toggle audio feedback (Windows only)
- `c`: Toggle auto-calibration (during detection) / Confirm ROI (during selection)
- `SPACE`: Capture samples (only during training/capture screens)

## Command Line Options

```powershell
python table_click_detector.py --help
```

- `--camera 0`: Select camera device (0 = default webcam)
- `--unit-time 0.2`: Set Morse unit time in seconds (dot duration)
- `--confidence 0.1`: Minimum confidence threshold for click detection
- `--no-audio`: Disable audio feedback
- `--no-guide`: Hide on-screen Morse guide
- `--no-auto-calibrate`: Disable automatic timing calibration
- `--no-ml`: Disable ML, use traditional two-reference method
- `--ml-samples 10`: Number of ML training samples per class
- `--reset-settings`: Reset saved settings to defaults

## Tips for Best Results

1. **Good lighting** - Ensure table area is well-lit
2. **Stable camera** - Mount webcam to avoid movement
3. **Clear surface** - Use solid colored table/desk  
4. **Consistent tapping** - Try to tap in the same spot
5. **Practice timing** - Start slow, speed up as you improve

Bonus:
- Prefer a mid-sized ROI: large enough to include hand/table contact, small enough for speed.
- Keep the camera stable and minimize background motion in the ROI.

[![Watch the video]()]([https://www.youtube.com/watch?v=_5tFXJQIzi4](https://youtu.be/XALCWf4MhFA))

## Troubleshooting

**Not detecting taps?**
- Lower `--confidence` value (try 0.05–0.1)
- Ensure good contrast between hand and table
- Recapture reference states with better positioning

**Getting wrong letters?**  
- Adjust `--unit-time` (try 0.3 for slower timing)
- Practice consistent dot/dash durations
- Use pauses between letters

**Too many false positives?**
- Increase `--confidence` value (try 0.2–0.3)  
- Minimize background movement during use
- Ensure stable lighting conditions

**Program exits immediately (exit code 1) or camera won’t open?**
- Try a different camera index: `--camera 0`, `--camera 1`, etc.
- Close other apps using the camera (Teams, Zoom, browsers).
- Run with the explicit Python path shown above.
- Verify dependencies installed: `python -m pip install -r requirements.txt`.
- Run diagnostics: `python diagnostics.py` (prints versions and camera info).

**Audio not working?**
- Audio beeps use Windows `winsound`. On non-Windows, audio is disabled.
- Toggle at runtime with `a`.

## Advanced Features

**Custom timing**: Adjust the base unit time to match your tapping speed
```powershell
python table_click_detector.py --unit-time 0.15  # Faster
python table_click_detector.py --unit-time 0.3   # Slower
```

**High sensitivity mode**: For subtle tapping
```powershell
python table_click_detector.py --confidence 0.05
```

**Disable ML and use traditional detection**
```powershell
python table_click_detector.py --no-ml
```

**Adjust ML sample count**
```powershell
python table_click_detector.py --ml-samples 15
```

**Practice tool**
```powershell
python morse_practice.py
```

**Run diagnostics**
```powershell
python diagnostics.py
```

---

Have fun learning Morse code! Start with simple letters like E (·) and T (-), then work your way up to full words and sentences. If you want, I can add model save/load for faster startup and temporal smoothing for even steadier detection.
