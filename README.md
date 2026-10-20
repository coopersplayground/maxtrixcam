# Matrix Cam

Watch your security cameras in Matrix-style ASCII art. Falling katakana rain over a live camera feed, rendered in your terminal.

![demo](demo.gif)

## Features

- Live camera feeds rendered as ASCII art with Matrix digital rain overlay
- Rain animates at 10fps independently of camera refresh
- Supports RTSP network cameras and USB webcams (v4l2)
- Configurable: feed frame rate, rain density, trail length, mirror image, camera display names
- Auto-detects Frigate NVR cameras, or define sources manually

## Requirements

- Python 3.8+
- `ffmpeg` in PATH
- `pillow` (`pip install pillow`)

## Install

```bash
sudo cp matrix-cam /usr/local/bin/matrix-cam
sudo chmod +x /usr/local/bin/matrix-cam
```

## Usage

```bash
sudo matrix-cam
```

Pick a camera from the menu. Press Ctrl+C to stop.

### Options menu

- **Feed frame rate** — camera refresh rate, 1-30 fps (default 5)
- **Rain density** — % of columns with active rain (default 70%)
- **Trail length** — characters in each rain trail (default 5)
- **Mirror image** — flip the feed horizontally (default **On**)
- **Rename cameras** — display names, app-only

Settings save to `~/.matrix-cam.json`.

## Camera sources

By default, cameras are auto-detected from your Frigate config (`config.yml` path configurable). You can also define sources manually in `~/.matrix-cam.json`:

```json
{
  "sources": {
    "front_door": {"kind": "rtsp", "url": "rtsp://user:pass@192.168.1.10:554/stream"},
    "webcam": {"kind": "v4l2", "device": "/dev/video0"}
  }
}
```

## License

MIT
