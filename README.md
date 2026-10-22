# Qwen3-TTS Voice Clone Studio (v4.2.0)

Clone a voice from a short recording and generate new speech, all inside one Google Colab cell.

## Quick start

1. Open the notebook in Google Colab.
2. Go to **Runtime → Change runtime type** and pick **GPU**.
3. Choose your models in the cell form, then run it:
   - `MODEL_SIZE`: `1.7B` (default, better quality) or `0.6B` (for T4 or low-memory GPUs)
   - `WHISPER_SIZE`: `tiny`, `base` (default) or `small`
4. Wait for **✅ READY**. The first run downloads the models and can take several minutes.

## How to use

1. **Upload a reference recording.** One file: WAV, MP3, M4A, FLAC, OGG, AAC, OPUS or WEBM, up to 100 MB and 10 minutes.
2. **Select the speech to use.** Drag across the waveform to create regions (up to 16). Reorder them with ↑/↓. Aim for 5–15 seconds of clean speech in total (1–20 seconds allowed). Click **Preview splice** to hear the result.
3. **Pick a clone mode.**
   - **High fidelity (ICL):** best quality. Needs an exact transcript of the selected audio. Click **Transcribe splice**, then correct any mistakes.
   - **Embedding only:** no transcript needed, but the voice match may be weaker.
4. **Write your script** (up to 8,000 characters), choose the language, and click **Generate voice**. Long scripts are split into chunks and joined automatically.
5. **Play and download.** Earlier takes are kept in **History**. Download a single WAV or all takes as a ZIP.

Note: changing your regions clears the transcript, since it must match the selected audio exactly.

## Output

Generated audio is saved as mono 16-bit WAV at the model's native sample rate, with volume normalized to -1 dBFS. You can also make a converted copy (for example 8 kHz mono) using **Optional WAV conversion**. The original file is never changed.

## Files

- Generated audio: `/content/qwen3_tts_outputs/`
- Reference working files: `/content/qwen3_tts_work/`

Download your files before the runtime ends.

## Rerunning

Rerunning with the same settings keeps your session and loaded models. Changing the model or code version restarts the studio. **Reset studio** clears your work but keeps the models loaded.

## Troubleshooting

- **GPU out of memory:** switch to `0.6B`, shorten the script or chunk size, or click **Clear GPU cache**.
- **"Restart the Colab session":** use **Runtime → Restart session**, then run the cell again.
- **Dependency install fails:** use **Runtime → Disconnect and delete runtime**, then run again.
- **Waveform editor won't load:** it needs internet access to load WaveSurfer. A basic audio player appears instead.
- **Check audio processing:** run `studio["self_check_audio"]()` in a new cell.

## Responsible use

Only clone voices and recordings you have permission to use.