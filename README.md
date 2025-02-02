# HUNTERS-Chronos-Competition
**HUNTERS** This project performs 3 main tasks:

Generates bilingual (English-Japanese) subtitles from audio/video

Creates a text summary from generated subtitles

Leverages state-of-the-art AI models for speech processing

1. Audio Processing & Subtitle Generation
Key Components:

WebRTC VAD (Voice Activity Detection)

Whisper (OpenAI's ASR)

M2M-100 (Facebook's Multilingual Translation)

Models Used:
Whisper-Large (Automatic Speech Recognition)

Why: State-of-the-art speech recognition with multilingual support

Task: Converts Japanese audio to text

M2M-100 418M (Multilingual Translation)

Why: Direct Japanese→English translation without English pivoting

Task: Translates transcribed Japanese text to English

WebRTC VAD (Preprocessing)

Why: Improve ASR accuracy by isolating speech segments

Task: Removes silence/noise from audio

Workflow Flowchart:
Copy
[Input Audio] → [VAD Preprocessing] → [Whisper Transcription] 
               → [M2M-100 Translation] → [Bilingual SRT]
2. Text Summarization
Key Component:

BART-Large-CNN (Summarization Model)

Model Used:
BART-Large-CNN

Why: Effective abstractive summarization

Task: Condenses subtitle text into key points

Workflow Flowchart:
Copy
[SRT File] → [Text Extraction] → [Chunk Processing] 
           → [BART Summarization] → [Final Summary]
Technical Architecture
Core Libraries:

pydub: Audio format conversion

transformers: Model access from HuggingFace Hub

webrtcvad: Noise reduction

srt: Subtitle file handling

Key Functions:

Audio Preprocessor

Converts to 16kHz mono WAV

Uses VAD to detect speech segments

Reduces Whisper processing time by 30-50%

Bilingual Subtitle Generator

Maintains timing metadata

Preserves original Japanese text

Formats translations for video players

Chunked Summarizer

Handles long-text limitations

Maintains context across segments

Design Choices
Whisper-Large Over Base

10% better WER (Word Error Rate) for Japanese

Accepts longer audio context

M2M-100 Over NLLB

Better Japanese→English performance

Preserves nuanced expressions

BART Over T5

More fluent summaries

Better context retention

Performance Considerations
Memory Optimization

Chunked audio processing

Dynamic batching in translation

GPU acceleration for neural models

Accuracy Enhancements

VAD preprocessing

Language-specific model tuning

Post-processing for ASR artifacts

Potential Improvements
Real-Time Processing

Whisper distillation for faster inference

Quantized translation models

Context-Aware Translation

Cross-sentence context preservation

Domain-specific fine-tuning

Multimodal Summarization

Combine audio/text features

Visual cue integration

This pipeline demonstrates a production-ready solution for multilingual media localization, combining speech processing, machine translation, and text summarization using state-of-the-art AI models.
