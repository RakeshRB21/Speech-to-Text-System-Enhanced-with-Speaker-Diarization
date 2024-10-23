# Speech-to-Text System with Speaker Diarization

A robust speech recognition system that combines Google Speech Recognition and OpenAI Whisper for accurate transcription with speaker diarization capabilities. This system provides highly accurate transcriptions while identifying and separating different speakers in the audio.

## Features

- Dual-engine speech recognition using Google Speech API and OpenAI Whisper
- Speaker diarization for multi-speaker audio
- Support for multiple audio formats
- High accuracy transcription with timestamp mapping
- Speaker identification and labeling

## Prerequisites

- Python 3.8+
- Google Cloud account with Speech-to-Text API enabled
- OpenAI API key
- Required Python packages (see `requirements.txt`)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/speech-to-text-diarization.git
cd speech-to-text-diarization
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:
```bash
export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/credentials.json"
export OPENAI_API_KEY="your-openai-api-key"
```

## Usage

```python
from speech_diarization import SpeechDiarizationSystem

# Initialize the system
stt_system = SpeechDiarizationSystem()

# Process an audio file
result = stt_system.process_audio("path/to/audio.wav")

# Get transcription with speaker labels
transcript = result.get_transcript()
```

## Configuration

The system can be configured through a `config.yaml` file:

```yaml
speech_recognition:
  google:
    language: "en-US"
    model: "video"
  whisper:
    model: "base"
    language: "en"

diarization:
  min_speakers: 1
  max_speakers: 10
```

## Example Output

```json
{
  "transcript": [
    {
      "speaker": "Speaker 1",
      "start_time": "0:00",
      "end_time": "0:05",
      "text": "Hello, how are you today?"
    },
    {
      "speaker": "Speaker 2",
      "start_time": "0:06",
      "end_time": "0:08",
      "text": "I'm doing well, thank you."
    }
  ]
}
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Google Cloud Speech-to-Text API
- OpenAI Whisper
- Contributors and maintainers of related open-source projects

## Contact

Your Name - [@yourtwitter](https://twitter.com/yourtwitter)
Project Link: [https://github.com/yourusername/speech-to-text-diarization](https://github.com/yourusername/speech-to-text-diarization)
