# Speech-to-Text System Enhanced with Speaker Diarization

A robust speech-to-text transcription system that combines Google Speech Recognition and OpenAI Whisper for accurate transcription, enhanced with speaker diarization capabilities to identify and label different speakers in audio conversations.

## Table of Contents
- [Features](#features)
- [System Architecture](#system-architecture)
- [Prerequisites](#prerequisites)
- [Usage](#usage)
- [Model Comparison](#model-comparison)

## Features

- **Dual Engine Processing**: Leverages both Google Speech Recognition and OpenAI Whisper for enhanced accuracy
- **Speaker Diarization**: Automatically identifies and labels different speakers in conversations
- **High Accuracy**: Utilizes OpenAI Whisper's advanced models for improved transcription quality
- **Multiple Audio Formats**: Supports various input formats including WAV, MP3, and FLAC
- **Real-time Processing**: Option for real-time transcription using Google Speech API
- **Batch Processing**: Support for processing multiple audio files in batch mode

## System Architecture

The system consists of three main components:
1. Audio Preprocessing Module
2. Transcription Engines (Google Speech & Whisper)
3. Speaker Diarization Module

## Prerequisites

- Python 3.8 or higher
- FFmpeg (for audio processing)
- Internet connection for API access


## Usage

### Basic Transcription

```python
from speech_diarization import Transcriber

# Initialize the transcriber
transcriber = Transcriber(use_whisper=True, use_google=True)

# Transcribe an audio file
result = transcriber.transcribe("path/to/audio.wav")

# Print results
print(result.text)
print(result.speaker_labels)
```

### Real-time Transcription

```python
from speech_diarization import RealtimeTranscriber

# Initialize real-time transcriber
rt_transcriber = RealtimeTranscriber()

# Start real-time transcription
rt_transcriber.start_streaming()
```

### Batch Processing

```python
# Process multiple files
files = ["audio1.wav", "audio2.mp3", "audio3.flac"]
results = transcriber.batch_process(files)
```

## Model Comparison

During testing, we found the following accuracy rates:

| Model             | Accuracy | Processing Time | Best Use Case               |
|-------------------|----------|-----------------|----------------------------|
| Google Speech     | 85-90%   | Real-time      | Live transcription         |
| OpenAI Whisper    | 95-98%   | Batch          | High-accuracy requirements |

OpenAI Whisper showed superior performance in:
- Handling accents and dialects
- Background noise resistance
- Complex technical vocabulary
- Multi-speaker scenarios

## Configuration

Key configuration options in `config.yaml`:

```yaml
transcription:
  whisper_model: "large"  # Options: tiny, base, small, medium, large
  use_gpu: true
  language: "en"
  
diarization:
  min_speakers: 1
  max_speakers: 6
  speech_pad_ms: 400
```

## Directory Structure

```
speech-to-text-diarization/
├── src/
│   ├── transcriber/
│   ├── diarization/
│   └── utils/
├── tests/
├── config/
├── examples/
└── requirements.txt
```

## Error Handling

The system includes robust error handling for common issues:

```python
try:
    result = transcriber.transcribe("audio.wav")
except AudioFormatError:
    print("Unsupported audio format")
except APIError:
    print("API connection error")
```


## Acknowledgments

- OpenAI Whisper team for their excellent speech recognition model
- Google Cloud Speech-to-Text API team
- Contributors to the speaker diarization research community
