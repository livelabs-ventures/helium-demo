# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a 4-grid HLS video player application that displays a single video stream split into four quadrants. The application uses HLS.js for streaming video playback and Canvas API for rendering the quadrants.

## Architecture

### Core Components

- **HLS Video Streaming**: Uses HLS.js library to load and play HLS video streams
- **Canvas Rendering**: Four canvas elements render different quadrants of the video
- **Grid/Expanded View**: Click any quadrant to expand it with thumbnails of other quadrants

### Key Implementation Details

- Video source is rendered to hidden `<video>` element
- Canvas contexts draw specific regions of the video frame (top-left, top-right, bottom-left, bottom-right)
- Animation frame loop continuously updates canvases during playback
- Responsive grid layout with hover effects and smooth transitions

## Development Commands

Since this is a static HTML application with no build process:

- **Run locally**: Open `index.html` directly in a browser or use a local server:
  ```bash
  python3 -m http.server 8000
  # or
  npx serve .
  ```

- **Test HLS playback**: Ensure the HLS stream URL in line 223 is accessible and CORS-enabled

## Working with the Code

- The entire application is contained in a single `index.html` file
- Styles are embedded in `<style>` tag (lines 8-157)
- JavaScript logic is in `<script>` tag (lines 196-499)
- HLS.js is loaded from CDN (line 7)

## Important Considerations

- HLS stream URL is hardcoded at line 223 - update this for different video sources
- Canvas dimensions are set based on video metadata once loaded
- Error handling for HLS loading is implemented with recovery mechanisms
- Safari uses native HLS support instead of HLS.js