# HUNTERS-Chronos-Competition
**HUNTERS**# Audio Transcription and Summarization Tool

This tool provides a comprehensive solution for converting audio files to text transcripts with timestamps and generating summaries. It utilizes advanced audio processing techniques, the Whisper ASR model, and BART summarization to deliver accurate results.

## Features

### Audio Conversion
- Converts audio files (MP3/MP4) to WAV format using the pydub library.
- Handles potential errors during conversion.

### Audio Preprocessing
- Resamples audio to 16kHz for optimal performance.
- Applies noise reduction using spectral gating.
- Normalizes audio to -3dB peak.
- Trims leading and trailing silence.

### Transcription
- Uses the whisper_timestamped library for accurate transcription.
- Supports GPU acceleration if available.
- Provides word-level timestamps for precise alignment.
- Configurable transcription parameters including language, beam size, and temperature.
- Implements voice activity detection (VAD) for improved accuracy.

### Output Formats
- Generates transcripts in SRT format with timestamps.
- Produces plain text transcripts without timestamps.
- Saves transcription parameters for reproducibility.

### Summarization
- Utilizes the BART-large-CNN model for text summarization.
- Handles long transcripts by splitting into manageable chunks.
- Combines chunk summaries for a comprehensive overview.

## Usage

1. Set the input audio file path.
2. Run the script to perform the following steps:
   - Convert audio to WAV format (if necessary).
   - Preprocess and transcribe the audio.
   - Save transcriptions in SRT and plain text formats.
   - Generate a summary of the transcript.

## Dependencies

- pydub
- whisper_timestamped
- librosa
- numpy
- torch
- transformers

## Note

Ensure all file paths are correctly set and the necessary libraries are installed before running the script.
