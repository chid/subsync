# Subsync (Linux Fork)

> **Note**: This is a fork of the original [Subsync](https://github.com/sc0ty/subsync) project, which is no longer maintained. This fork is actively patched to support **Linux systems**, modern compilers (GCC 13+), and recent dependencies (FFmpeg 5+, wxPython 4).

## Overview
**Subtitle Speech Synchronizer** (Subsync) automatically synchronizes subtitles with video by aligning speech with text.

## Linux Installation & Usage

This fork simplifies the installation process on Linux by providing helper scripts and removing hardcoded Windows dependencies.

### 1. Prerequisites (Ubuntu/Debian)
Install the necessary system libraries for building the C++ extensions and running the GUI:

```bash
sudo apt install build-essential python3-dev ffmpeg libavcodec-dev libavformat-dev libavdevice-dev libavutil-dev libswscale-dev libswresample-dev libpocketsphinx-dev libsphinxbase-dev portaudio19-dev libwxgtk3.0-gtk3-dev
```

### 2. Setup (One-time)
Use the provided `linux_setup.sh` script to create a Python virtual environment and install all dependencies:

```bash
./linux_setup.sh
```

### 3. Running the Application
Launch the application using the runner script:

```bash
./run_linux.sh
```

## Development

### Ruff linting
Install the developer tooling and run Ruff against the hand-written Python
application code:

```bash
python -m pip install -r requirements-dev.txt
python -m ruff check bin run.py subsync
```

To apply safe automatic fixes such as import sorting:

```bash
python -m ruff check --fix bin run.py subsync
```

## Technical Changes in this Fork
*   **Build System**: Updated `setup.py` to use `pkg-config` for locating system libraries on Linux.
*   **FFmpeg 5.x**: Ported C++ code to use the new `AVChannelLayout` API.
*   **Compilation**: Fixed headers (`<cstdint>`) and removed Windows-specific flags for GCC compatibility.
*   **wxPython**: Fixed type errors in GUI calls for compatibility with wxPython 4.x.

## Original Credits
*   Author: Michał Szymaniak
*   Original Repo: [sc0ty/subsync](https://github.com/sc0ty/subsync)
*   License: GPLv3
