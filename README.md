# Captcha Solver (Browser-based)

MIT-licensed, single-page web app that accepts an image URL via the `?url=` query parameter, displays the captcha image, and attempts to solve it using on-device OCR (Tesseract.js). If no URL is provided, it defaults to a built-in sample captcha.

## Overview

- Input: `?url=https://.../image.png` (any direct image URL)
- Processing: Optional preprocessing (grayscale + Otsu binarization) then OCR via Tesseract.js (runs entirely in the browser).
- Output: Displays the image, preprocessed preview, progress logs, and the solved text (usually within ~15 seconds, depending on network/CPU).
- CORS-friendly: Uses an image proxy (images.weserv.nl) by default to improve compatibility with cross-origin images.
- No server required: Pure static HTML/JS.

## Setup

1. Download the repository files:
   - index.html
   - README.md

2. Host the files using any static HTTP server or open `index.html` directly in a modern browser. A local HTTP server is recommended so that the OCR worker and language files load correctly from the CDN.

   Examples:
   - Python 3: `python -m http.server 8080`
   - Node (http-server): `npx http-server -p 8080`

3. Open the app in your browser:
   - http://localhost:8080/index.html

## Usage

- Pass an image URL in the query string:
  - http://localhost:8080/index.html?url=https://example.com/captcha.png
- Or paste a URL into the input field and click “Solve.”
- If you don’t have a captcha handy, click “Use sample” to load the built-in example.
- Keep “Use CORS image proxy” checked for best compatibility. You can uncheck it if the target server already sends permissive CORS headers.

Notes:
- The app shows the exact URL used to display the captcha.
- The OCR result is cleaned to uppercase alphanumerics (A–Z, 0–9).
- Some heavily distorted/obfuscated captchas may not be solvable with generic OCR. You can try toggling the proxy or using the original vs preprocessed image paths (the app falls back automatically if needed).

## License

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.