# Qwen3-TTS OpenAI-Compatible Server

A text-to-speech server that can **clone voices** and runs on **any computer** - no fancy GPU required.

## What This Does

- **Text to Speech** - Type text, get natural-sounding audio
- **Voice Cloning** - Upload a short audio clip of someone speaking, and the AI will speak in their voice
- **Works Everywhere** - Runs on regular computers (CPU) or faster with a GPU

## Getting Started

### 1. Install Docker

If you don't have Docker installed:
- **Windows/Mac**: Download [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- **Linux**: Run `sudo apt install docker.io docker-compose` (Ubuntu/Debian)

### 2. Download and Run

Open a terminal and run:

```bash
git clone https://github.com/falense/Qwen3-TTS-Openai-Fastapi.git
cd Qwen3-TTS-Openai-Fastapi
docker-compose --profile cpu up
```

Wait for the download to complete (this may take a while the first time).

### 3. Open the Web Interface

Once you see "Application startup complete" in the terminal, open your browser and go to:

**http://localhost:8880**

You'll see a web interface where you can:
- Type text and hear it spoken
- Upload audio to clone a voice

## How to Use

### Web Interface (Easiest)

1. Go to http://localhost:8880
2. **For text-to-speech**: Type your text, pick a voice, click Generate
3. **For voice cloning**: Switch to the "Voice Clone" tab, upload a reference audio file, type what you want said, click Generate

### Voice Cloning Tips

- Use a clear audio recording (3-10 seconds works well)
- For best results, also type what the person says in the reference audio
- Supported formats: WAV, MP3, FLAC

## Running with a GPU (Faster)

If you have an NVIDIA graphics card and want faster generation:

1. Install [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)
2. Run with GPU support:

```bash
docker-compose up qwen3-tts-gpu
```

| | CPU | GPU |
|---|---|---|
| Speed | Slower (but works fine) | Fast |
| Requirements | Any computer | NVIDIA GPU + CUDA |
| Memory | ~3 GB RAM | ~4 GB VRAM |

## Available Voices

Choose from these built-in voices:
- Vivian, Serena, Luna, Aurora (female)
- Ryan, Dylan, Eric, Aiden, Jessie (male)

## Stopping the Server

Press `Ctrl+C` in the terminal where it's running, or run:

```bash
docker-compose down
```

## Troubleshooting

**"Port 8880 is already in use"**
- Another program is using that port. Either stop it, or edit `docker-compose.yml` and change `8880:8880` to something like `8881:8880`

**"Cannot connect to Docker daemon"**
- Make sure Docker Desktop is running (Windows/Mac) or the Docker service is started (Linux)

**Generation is very slow**
- This is normal on CPU. Each sentence takes a few seconds. For faster results, use a GPU.

## Credits

Based on [Qwen3-TTS](https://github.com/QwenLM/Qwen3-TTS) by Alibaba Cloud.
Original server by [groxaxo](https://github.com/groxaxo/Qwen3-TTS-Openai-Fastapi).
