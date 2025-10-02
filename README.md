<div align="center">
  <img src="logo.svg" alt="GenZPlayer Logo" width="100" height="auto">
  
  # GenZPlayer
  
  **🚀 The Ultimate Video Player for Web** - Just drop any video and it plays! Works with **ALL formats** automatically.
  
  [![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/GulshiDevs/genzplayer)
  [![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
  [![Bundle Size](https://img.shields.io/badge/bundle-625KB-orange.svg)](genzplayer.js)
  [![Support](https://img.shields.io/badge/support-Buy%20Me%20Coffee-yellow.svg)](https://buymeacoffee.com/GenZplayer)
  
</div>

---

## ✨ Key Features

- 🎯 **Universal Format Support** - Plays all video formats automatically
- 📦 **Industry Standard** - Uses HLS.js v1.5.13 and dash.js v5.0.3
- 🚀 **Production Ready** - Battle-tested libraries with robust error handling
- ⚡ **Optimized** - Main bundle 625KB, DASH lazy-loaded (921KB chunk)
- 🎨 **Modern UI** - Clean, responsive design with custom controls
- ⌨️ **Keyboard Shortcuts** - Full keyboard control
- 📱 **Mobile Optimized** - Touch-friendly controls
- 🎚️ **Quality Selector** - Manual & Auto quality switching (ABR)
- 🔊 **Volume Boost** - Up to 400% using Web Audio API
- 📊 **Buffer Visualization** - Real-time buffer display
- 🎬 **Context Menu** - Right-click menu with version & developer info

---

## 🎥 Supported Formats

### ✅ Fully Supported (HTML5 Native)
These formats work **out of the box** in modern browsers:
- **MP4** (.mp4, .m4v) - H.264/H.265 + AAC - **Best for web**
- **WebM** (.webm) - VP8/VP9/AV1 + Opus - **Modern & efficient**
- **OGG** (.ogg, .ogv) - Theora + Vorbis - **Open format**

### 🌐 Streaming Protocols (Industry Standard)
- **HLS** (.m3u8) - HTTP Live Streaming via **hls.js v1.5.13**
- **DASH** (.mpd) - MPEG-DASH via **dash.js v5.0.3**
- Smooth Streaming (.ism) - Microsoft (fallback to DASH)

### ⚠️ Limited Support
Browser support varies - may work in some browsers:
- **MOV** (.mov) - QuickTime (Safari ✅, Chrome partial)
- **3GP** (.3gp, .3g2) - Mobile formats (Android browsers)

### ❌ Not Supported by Browsers
These formats **require conversion** to MP4/WebM for web playback:
- **AVI** (.avi) - Legacy format, no browser support
- **MKV** (.mkv) - Not a web standard
- **WMV** (.wmv) - Microsoft proprietary
- **FLV** (.flv, .f4v) - Flash is deprecated
- **VOB** (.vob) - DVD format
- **TS/MTS** (.ts, .mts, .m2ts) - Limited browser support
- Others: MXF, WTV, RealMedia, SWF, etc.

💡 **See [FORMATS.md](FORMATS.md) for detailed browser compatibility**

### 🎬 Recommended Formats for Web
1. **MP4 (H.264 + AAC)** - Maximum compatibility
2. **WebM (VP9 + Opus)** - Modern, efficient, open
3. **HLS (.m3u8)** - Adaptive streaming
4. **DASH (.mpd)** - Adaptive streaming

---

## 🚀 Quick Start

### Method 1: CDN (Fastest)
```html
<!DOCTYPE html>
<html>
<body>
  <div id="player"></div>
  
  <!-- Include from CDN -->
  <script src="https://cdn.jsdelivr.net/gh/GulshiDevs/genzplayer@1.0.0/genzplayer.js"></script>
  
  <script>
    // Auto-detects format from URL!
    const player = new GenzPlayer('player', {
      src: 'your-video.mp4',  // or .m3u8, .mpd, .webm
      controls: true,
      autoplay: false
    });
  </script>
</body>
</html>
```

### Method 2: Download Files
1. Download: `genzplayer.js` (625 KB) + `798.genzplayer.js` (921 KB)
2. Include: `<script src="genzplayer.js"></script>`
3. Use: Same code as CDN method above

### ✨ That's it!
Player automatically detects if it's MP4, HLS, or DASH and plays it!

---

## 📖 Examples

### MP4 Video
```javascript
const player = new GenzPlayer('player', {
    src: 'video.mp4'
});
```

### MKV / AVI / MOV / Any Format
```javascript
const player = new GenzPlayer('player', {
    src: 'video.mkv'  // or .avi, .mov, .wmv, .flv, .webm, .3gp, etc.
});
```

### HLS Stream (.m3u8)
```javascript
const player = new GenzPlayer('player', {
    src: 'https://example.com/playlist.m3u8'
});
```

### DASH Stream (.mpd)
```javascript
const player = new GenzPlayer('player', {
    src: 'https://example.com/manifest.mpd'
});
```

### Smooth Streaming (.ism)
```javascript
const player = new GenzPlayer('player', {
    src: 'https://example.com/video.ism/Manifest'
});
```

**No need to specify `type`** - it's auto-detected from URL!

---

## ⚙️ Configuration

```javascript
const player = new GenzPlayer('player', {
    src: 'video.mp4',           // Video URL (auto-detected)
    poster: 'poster.jpg',       // Poster image
    autoplay: false,            // Auto-start
    controls: true,             // Show controls
    fluid: true,                // Responsive
    aspectRatio: '16:9',        // Aspect ratio
    volume: 1.0,                // Initial volume (0-1)
    playbackRate: 1.0,          // Playback speed
    quality: 'auto',            // Quality (auto/index)
    keyboard: true,             // Keyboard shortcuts
    tooltips: true,             // Show tooltips
    onReady: function() {},     // Ready callback
    onPlay: function() {},      // Play callback
    onPause: function() {},     // Pause callback
    onEnded: function() {},     // End callback
    onError: function(err) {}   // Error callback
});
```

---

## 🎮 API Methods

### Playback Control
```javascript
player.play()                   // Play video
player.pause()                  // Pause video
player.togglePlay()             // Toggle play/pause
player.stop()                   // Stop and reset
player.seek(seconds)            // Seek to time
player.forward(seconds)         // Skip forward
player.backward(seconds)        // Skip backward
```

### Volume Control
```javascript
player.setVolume(0.5)          // Set volume (0-1)
player.getVolume()             // Get current volume
player.mute()                  // Mute audio
player.unmute()                // Unmute audio
player.toggleMute()            // Toggle mute
```

### Playback Speed
```javascript
player.setPlaybackRate(1.5)    // Set speed (0.25-2.0)
player.getPlaybackRate()       // Get current speed
```

### Quality Control
```javascript
player.setQuality(index)       // Set quality level
player.setQuality('auto')      // Enable auto quality (ABR)
player.getQualities()          // Get available qualities
player.getCurrentQuality()     // Get current quality
```

### Display Modes
```javascript
player.toggleFullscreen()      // Toggle fullscreen
player.enterFullscreen()       // Enter fullscreen
player.exitFullscreen()        // Exit fullscreen
player.togglePIP()             // Toggle Picture-in-Picture
```

### Player State
```javascript
player.isPlaying()             // Check if playing
player.isPaused()              // Check if paused
player.getDuration()           // Get video duration
player.getCurrentTime()        // Get current time
player.getBufferInfo()         // Get buffer statistics
```

### Cleanup
```javascript
player.destroy()               // Destroy player and cleanup
```

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Play/Pause |
| `K` | Play/Pause |
| `M` | Mute/Unmute |
| `F` | Fullscreen |
| `P` | Picture-in-Picture |
| `←` | Backward 10s |
| `→` | Forward 10s |
| `↑` | Volume Up |
| `↓` | Volume Down |
| `0-9` | Seek to 0%-90% |
| `<` | Decrease Speed |
| `>` | Increase Speed |

---

## 🎨 Context Menu

Right-click on video player to access:
- Player version info
- Developer credit (GulshiDevs)
- Support link (Buy Me a Coffee)
- Auto-hides after 2 seconds

---

## 📦 Installation

### 🚀 CDN (Recommended)
**jsDelivr CDN:**
```html
<script src="https://cdn.jsdelivr.net/gh/GulshiDevs/genzplayer@1.0.0/genzplayer.js"></script>
```

**Unpkg CDN:**
```html
<script src="https://unpkg.com/genzplayer@1.0.0/genzplayer.js"></script>
```

**GitHub CDN (Raw):**
```html
<script src="https://raw.githubusercontent.com/GulshiDevs/genzplayer/v1.0.0/genzplayer.js"></script>
```

### 📥 Download
1. Go to [Releases](https://github.com/GulshiDevs/genzplayer/releases)
2. Download `genzplayer.js` and `798.genzplayer.js`
3. Include in your project

### 🔗 Direct Links
Right-click and save:
- [genzplayer.js](genzplayer.js) - Main player (625 KB)
- [798.genzplayer.js](798.genzplayer.js) - DASH chunk (921 KB)

### 📋 HTML Template
```html
<!DOCTYPE html>
<html>
<head>
  <title>GenZPlayer Demo</title>
</head>
<body>
  <!-- Player Container -->
  <div id="player" style="width:100%; max-width:800px;"></div>
  
  <!-- Include GenZPlayer -->
  <script src="https://cdn.jsdelivr.net/gh/GulshiDevs/genzplayer@1.0.0/genzplayer.js"></script>
  
  <!-- Initialize Player -->
  <script>
    const player = new GenzPlayer('player', {
      src: 'https://example.com/video.mp4',
      controls: true,
      fluid: true
    });
  </script>
</body>
</html>
```

---

## 🌐 Browser Support

| Browser | Version | Support |
|---------|---------|---------|
| Chrome | 70+ | ✅ Full |
| Firefox | 65+ | ✅ Full |
| Safari | 12+ | ✅ Full |
| Edge | 79+ | ✅ Full |
| Opera | 57+ | ✅ Full |
| iOS Safari | 12+ | ✅ Full |
| Chrome Android | Latest | ✅ Full |

---

## 📚 Documentation

- Complete API documentation included in README
- All examples provided above
- Browser compatibility guide included

---

## 🤝 Support

- ⭐ **Star this repo** if you find it useful!
- 🐛 **Report issues** in the Issues tab
- ☕ **Buy me a coffee** to support development: [buymeacoffee.com/GenZplayer](https://buymeacoffee.com/GenZplayer)

---

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details

---

## 👨‍💻 Developer

**GulshiDevs** - Full Stack Developer

- 💻 **GitHub:** [@GulshiDevs](https://github.com/GulshiDevs)
- ☕ **Support:** [Buy Me a Coffee](https://buymeacoffee.com/GenZplayer)
- 🐦 **Contact:** Available via GitHub Issues

---

## 🙏 Acknowledgments

Built with industry-standard libraries:
- [hls.js](https://github.com/video-dev/hls.js) - HLS streaming support
- [dash.js](https://github.com/Dash-Industry-Forum/dash.js) - DASH streaming support

---

<div align="center">
  
  **🎬 GenZPlayer v1.0.0 - Production Ready!**
  
  **Made with ❤️ by GulshiDevs**
  
  ⭐ **Star this repo if you find it useful!** ⭐
  
  [Download Now](https://github.com/GulshiDevs/genzplayer/releases) • [Report Bug](https://github.com/GulshiDevs/genzplayer/issues) • [Buy Coffee ☕](https://buymeacoffee.com/GenZplayer)
  
</div>
