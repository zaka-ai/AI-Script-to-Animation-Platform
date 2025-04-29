# 🎬 AniMind AI Story Video Generator

AniMind is an advanced AI-powered application that transforms text prompts into complete stories with matching video animations and narration. It combines multiple AI models to create a seamless storytelling experience.

## 🌟 Features

- Generate complete stories from single-sentence prompts or a large article
- Create AI-generated video animations for each story segment
- Add sentiment-aware voice narration
- Automatic video-audio synchronization
- Interactive web interface
- API access available

## Step-By-Step Usage Guide

1. Go to this link: https://colab.research.google.com/drive/16WmebY0aIJqI2H2MFLFAUxx8pPXedUBZ?usp=sharing
2. Navigate to **Runtime -> Change runtime type** in the menu
3. Select **T4 GPU** then click **Save**
5. Run the cell and wait until the gradio interface appears
6. Enter any **long story** or **short promt** and the code will do the rest
7. Once complete a video file called **"final_video_with_audio.mp4"** will be generated
8. Download it
9. Enjoy ;)

## 🔧 Technical Architecture

### AI Models & Components

1. **Text Generation**:
   - Model: `Qwen/Qwen2.5-1.5B-Instruct`
   - Purpose: Story generation and summarization
   - Features:
     - 15-20 sentence story generation
     - Token-length management
     - Narrative flow optimization

2. **Video Generation**:
   - Base Model: `emilianJR/epiCRealism`
   - Motion Adapter: `ByteDance/AnimateDiff-Lightning`
   - Features:
     - Frame generation: 256x256 resolution
     - Crossfade transitions
     - 8 FPS output
     - CUDA acceleration support

3. **Audio Generation**:
   - Text-to-Speech: `edge_tts`
   - Sentiment Analysis: HuggingFace pipeline
   - Features:
     - Dynamic voice selection based on sentiment
     - Adjustable speech rate and pitch
     - MP3 output format

### Processing Pipeline

1. **Story Generation**:
   ```python
   def generate_story(prompt):
       # Generates 15-20 sentence story
       # Enforces token limits per sentence
       # Returns formatted story text
   ```

2. **Video Creation**:
   ```python
   def generate_video(summary):
       # Splits story into scenes
       # Generates frames for each scene
       # Applies transitions
       # Returns video path
   ```

3. **Audio Generation**:
   ```python
   async def generate_audio_with_sentiment(text):
       # Analyzes sentiment
       # Selects appropriate voice
       # Generates audio narration
       # Returns audio path
   ```

## 🚀 API Usage

### Endpoint

### API Response Format
```json
{
    "story": "Generated story text",
    "video_path": "Path to generated video",
    "audio_summary": "Narration text",
    "download_link": "HTML download link",
    "file_path": "Direct file path"
}
```

### Example API Call
```python
import requests

api_url = "https://a03fe99a8a99d63578.gradio.live/api/generate"
response = requests.post(api_url, json={
    "prompt": "A detective discovers a hidden room in an abandoned mansion"
})
```

## 💻 Technical Requirements

- Python 3.8+
- CUDA-capable GPU
- Required packages:
  - `torch`
  - `gradio`
  - `edge_tts`
  - `diffusers`
  - `transformers`
  - `moviepy`
  - `imageio`
  - `opencv-python`

## 🛠️ Environment Setup

```bash
pip install gradio edge_tts torch diffusers transformers moviepy imageio opencv-python
```

## 🏃‍♂️ Running Locally

1. Clone the repository
2. Install dependencies
3. Run the Jupyter notebook
4. Access the interface at `http://localhost:7860`

## ⚙️ Configuration Options

- Video Resolution: 256x256 (configurable)
- Frame Rate: 8 FPS
- Story Length: 15-20 sentences
- Token Limit: 77 tokens per sentence
- Audio: Adaptive voice selection based on sentiment

## 🔄 Processing Flow

1. **Input Validation**: Checks prompt length and content
2. **Story Generation**: Creates structured narrative
3. **Video Generation**: Processes each sentence into visual scenes
4. **Audio Creation**: Generates narration with sentiment analysis
5. **Final Compilation**: Combines video and audio

## 🚫 Limitations

- Processing time varies with story length
- GPU memory requirements for video generation
- API availability may be subject to rate limiting
- Video resolution fixed at 256x256

## 📝 License

This project is licensed under MIT License.


## 👥 Contributors

This project was developed by:
- Ali Kanbar
- Karim Ramadan
- Jameel Zbib

Under the supervision of:
- Eng. Jean-Pierre Fakhry

---
