# PixelPress Pro — Precision Image Compressor

> A fast, privacy-first, browser-based image compression tool with zero server uploads.

![PixelPress Pro Screenshot](https://img.shields.io/badge/status-active-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue) ![HTML](https://img.shields.io/badge/built%20with-HTML%2FJS-orange)

---

## ✨ Features

- **Lossless Compression** — Re-encodes using DEFLATE+Huffman/WebP lossless. No pixel data is altered. Typical reduction: 5–60%.
- **Target Size Mode** — Binary-search compression to hit your exact desired file size (KB or MB), with a configurable quality floor.
- **Batch Processing** — Drop multiple images at once; up to 4 processed simultaneously in parallel.
- **Multiple Formats** — Supports PNG, JPG/JPEG, WebP, BMP, TIFF, GIF input. Output in Auto (Best), PNG, WebP, or JPEG.
- **ZIP Download** — Download all compressed images bundled as a `.zip` in one click.
- **100% Client-Side** — All processing happens in your browser. No files are ever uploaded to any server.
- **Responsive UI** — Works on desktop and mobile browsers.

---

## 🚀 Getting Started

### Option 1 — Open directly in browser

Just double-click `index.html` — no server, no install, no dependencies.

### Option 2 — Serve locally (recommended for development)

```bash
# Using Python
python3 -m http.server 8080

# Using Node.js (npx)
npx serve .
```

Then open [http://localhost:8080](http://localhost:8080) in your browser.

### Option 3 — Deploy to GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to `main` branch, root `/`
4. Your app will be live at `https://<your-username>.github.io/PixelPress-Pro/`

---

## 🛠 How It Works

| Mode | Algorithm | Quality Impact |
|------|-----------|----------------|
| **Lossless** | Canvas → WebP Lossless / PNG re-encode | None — pixel-perfect |
| **Target Size** | Binary search over quality `[minFloor, 0.95]` | Minimal — floor is configurable |

The compression engine uses the browser's native `Canvas.toBlob()` API with format-specific tuning. For target-size mode, it binary-searches the quality parameter until the output file fits within ±5% of the desired size.

---

## 📂 Project Structure

```
PixelPress-Pro/
├── index.html        # Full single-file app (HTML + CSS + JS)
├── README.md         # This file
├── LICENSE           # MIT License
└── .gitignore        # Standard web gitignore
```

---

## 🧰 Tech Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML5 + CSS3 (CSS Variables, Grid, Flexbox) |
| Logic | Vanilla JavaScript (ES2020+) |
| Fonts | [Syne](https://fonts.google.com/specimen/Syne) + [Space Mono](https://fonts.google.com/specimen/Space+Mono) via Google Fonts |
| ZIP | [JSZip 3.10.1](https://stuk.github.io/jszip/) via CDN |
| Compression | Browser Canvas API (`toBlob`) — no native binaries |

---

## 🌐 Browser Compatibility

| Browser | Support |
|---------|---------|
| Chrome 90+ | ✅ Full |
| Firefox 89+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Edge 90+ | ✅ Full |

> WebP output requires Chrome/Edge. On Safari, the app automatically falls back to PNG.

---

## 📋 Roadmap

- [ ] AVIF output format support
- [ ] Drag-to-reorder queue
- [ ] Side-by-side before/after preview
- [ ] Offline PWA support (Service Worker)
- [ ] Bulk rename on download

---

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [JSZip](https://stuk.github.io/jszip/) for client-side ZIP generation
- [Google Fonts](https://fonts.google.com/) for Syne & Space Mono typography
- Browser Canvas API for making client-side image processing possible
