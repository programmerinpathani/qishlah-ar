# ffmpeg Command Reference — Stitching & Prep (Workshop 05)

Copy-paste commands to join your Veo 3 clips, attach audio, and prep the final `experience.mp4`. Run these in the folder containing your clips. Verify ffmpeg is installed first: `ffmpeg -version`.

---

## 1. Stitch clips together (same resolution/codec)

Create a text file `list.txt` listing your clips in order:
```
file 'scene1_gate.mp4'
file 'scene2_courtyard.mp4'
file 'scene3_souq.mp4'
file 'scene4_governance.mp4'
file 'scene5_dissolve.mp4'
```
Then concatenate without re-encoding (fast, lossless):
```bash
ffmpeg -f concat -safe 0 -i list.txt -c copy stitched.mp4
```

> Use this when all clips share the same resolution, frame rate, and codec (Veo 3 exports usually do).

---

## 2. Stitch when clips differ (re-encode to match)

If concat fails or clips have mismatched specs, normalize them first:
```bash
ffmpeg -i scene1_gate.mp4 -vf "scale=1280:720,fps=30" -c:v libx264 -crf 20 -c:a aac s1.mp4
```
Repeat for each clip (s1.mp4, s2.mp4...), then concat the normalized versions with the method in section 1.

---

## 3. Add a crossfade / dissolve between two clips (present ↔ past)

For the signature present→past dissolve (Scene 5), an 1.5-second crossfade:
```bash
ffmpeg -i present.mp4 -i past.mp4 -filter_complex \
"[0:v][1:v]xfade=transition=dissolve:duration=1.5:offset=4[v]" \
-map "[v]" dissolve.mp4
```
> `offset` = the time (seconds) into the first clip where the dissolve starts. Set it to (clip1 length − 1.5).

---

## 4. Add the voiceover + music track

Combine your final video with a mixed audio file:
```bash
ffmpeg -i stitched.mp4 -i mixed_audio.mp3 -c:v copy -map 0:v:0 -map 1:a:0 -shortest with_audio.mp4
```

To mix voiceover (ElevenLabs) and music (Suno) into one track, lowering music under the voice:
```bash
ffmpeg -i voiceover.mp3 -i music.mp3 -filter_complex \
"[1:a]volume=0.25[m];[0:a][m]amix=inputs=2:duration=longest[a]" \
-map "[a]" mixed_audio.mp3
```
> Tip: For finer control over levels and ducking, do the mix in **DaVinci Resolve** instead — these commands are the quick CLI fallback.

---

## 5. Final export for the AR page

Make the web-ready file the AR page expects (`assets/experience.mp4`):
```bash
ffmpeg -i with_audio.mp4 -vf "scale=1280:720" -c:v libx264 -profile:v baseline \
-pix_fmt yuv420p -movflags +faststart -crf 23 -c:a aac -b:a 128k experience.mp4
```
Why these flags:
- `baseline` profile + `yuv420p` → maximum mobile browser compatibility (iOS Safari is picky)
- `+faststart` → video starts playing before fully downloaded
- `crf 23` → good quality, small file (raise to 26–28 for smaller files on mobile data)

---

## 6. Handy utilities

Trim a clip (from 2s, for 6s):
```bash
ffmpeg -ss 2 -i input.mp4 -t 6 -c copy trimmed.mp4
```
Check file info (duration, resolution, codecs):
```bash
ffmpeg -i experience.mp4
```
Make a poster image from frame at 3s:
```bash
ffmpeg -ss 3 -i experience.mp4 -frames:v 1 poster.jpg
```
Mute a clip:
```bash
ffmpeg -i input.mp4 -an -c:v copy muted.mp4
```
