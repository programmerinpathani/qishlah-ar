# Deploying the RIB Heritage AR Experience

This folder is a ready-to-publish AR web page. Once your final video is in `assets/experience.mp4`, follow these steps to get a live HTTPS URL and a QR code.

> **Why HTTPS matters:** Browser camera access (required for AR) only works over HTTPS. GitHub Pages gives you free HTTPS automatically — that's why we use it.

---

## Step 1 — Add your video

1. Export your final cut from DaVinci Resolve (see settings in `assets/README.txt`).
2. Save it as `assets/experience.mp4` inside this folder, replacing nothing else.

---

## Step 2 — Create the GitHub repository

1. Sign in at [github.com](https://github.com).
2. Click **New repository** (the green button or the `+` top-right).
3. Name it e.g. `rib-ar-experience`, set it to **Public**, and create it.

---

## Step 3 — Push these files

**Option A — Web upload (no command line):**
1. On the new repo page, click **uploading an existing file**.
2. Drag in `index.html`, the `assets/` folder (with your `experience.mp4`), `DEPLOY.md`, and `FFMPEG_REFERENCE.md`.
3. Click **Commit changes**.

**Option B — Command line:**
```bash
cd rib-ar-experience
git init
git add .
git commit -m "RIB Heritage AR experience"
git branch -M main
git remote add origin https://github.com/<YOUR_USERNAME>/rib-ar-experience.git
git push -u origin main
```

---

## Step 4 — Enable GitHub Pages

1. In the repo, go to **Settings → Pages**.
2. Under **Source**, choose **Deploy from a branch**.
3. Select branch **main** and folder **/ (root)**, then **Save**.
4. Wait ~1 minute. Your live URL appears at the top:
   ```
   https://<YOUR_USERNAME>.github.io/rib-ar-experience/
   ```

---

## Step 5 — Test on a phone

1. Open the live URL on your phone (Chrome on Android / Safari on iOS).
2. Tap **Start Experience** and allow camera access.
3. Point the camera at your printed **Hiro marker** — the video should appear on top of it.

---

## Step 6 — Print the marker

- The page uses the standard AR.js **Hiro** marker.
- Search "AR.js Hiro marker PDF" and print it on **matte** paper (avoid glossy — glare breaks tracking).
- Print it reasonably large (at least ~8 cm / 3 inches square) with strong black/white contrast.

---

## Step 7 — Generate the QR code

1. Go to any free QR generator, e.g. [qr-code-generator.com](https://www.qr-code-generator.com).
2. Paste your live GitHub Pages URL.
3. Download the QR as PNG/SVG and place it next to the printed marker (e.g. on a wall plaque or flyer).

When someone scans the QR, their phone opens the AR page; pointing at the marker launches the heritage video.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Camera doesn't open | Make sure you're on the **https://** URL, not a local file. Allow camera permission. |
| Video appears but no sound | iOS blocks autoplay audio — the **Start Experience** tap unlocks it. Make sure you tapped it. |
| Marker not detected | Better lighting, hold phone steadier, print marker larger / higher contrast on matte paper. |
| Video loads slowly | Re-export smaller (720p, lower bitrate) so the file is under ~25–30 MB. |
| Black/blank video | Confirm the file is really at `assets/experience.mp4` and committed to the repo. |
