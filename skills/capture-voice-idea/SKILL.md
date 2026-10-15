---
name: capture-voice-idea
description: Capture a business idea from a voice memo / audio file. Transcribes the recording, preserves the raw transcript, then hands off to capture-idea so the user can optionally generate executive summary, elevator pitch, technical deep-dive, and timeline variants. Use when the user has an audio file or recording of an idea pitch.
---

# Capture Idea (voice)

Pipeline: audio → transcript → structured idea workspace.

## Steps

1. Resolve config (workspace path, user context).
2. Take the audio file path from the user. Verify it exists and looks like an audio file.
3. Transcribe. Prefer the `transcription-pipeline` plugin's skills if installed:
   - `transcription-pipeline:transcribe-gemini-cleaned` — fastest path, removes filler words
   - `transcription-pipeline:transcribe-gemini-raw` — verbatim if the user wants every word preserved
   - Fallback: prompt the user to install `transcription-pipeline` or supply an existing transcript.
4. Save the raw transcript to a temp path. Show the user a short preview (first ~200 words) before proceeding.
5. Hand the transcript to `capture-idea`:
   - Pass the transcript text as the raw input
   - Tag the resulting `idea.md` frontmatter with `source: voice` and `audio_file: <original-path>`
   - Copy the audio file (or symlink) into `<workspace_path>/ideas/<idea-slug>/source-audio.<ext>` so the recording stays with the workspace
6. Continue through `capture-idea`'s formatted-variant menu so the user can pick which derived versions to generate.

## Notes

- Voice captures often contain digressions and false starts. Prefer the cleaned transcription unless the user explicitly wants raw.
- For long recordings (>30 min), suggest `transcription-pipeline:truncate-silence` first.
- Always preserve the original audio file in the workspace — it's the ultimate source.
