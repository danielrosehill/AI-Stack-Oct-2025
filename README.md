# AI Stack Documentation
### October 27, 2025

Point in time overview of my AI infrastructure, tools, and services for development, deployment, and production workflows.
 

## Core Infrastructure

### Large Language Models
The backbone of the entire AI stack, powering nearly every component and workflow.

**Primary Interfaces:**
- **CLI**: Claude Code (Pro: $17/month | Max: $100/month)
- **GUI**: Claude interface (included with Claude Code subscription)
- **ChatGPT**: Day-to-day interface for general tasks
- **OpenAI**: API access and integrations

**API Access:**
- **OpenRouter**: Unified API gateway for multiple LLM providers
- Direct vendor APIs available from all major providers
- Frontend choice is virtually limitless - CLI, web apps, desktop apps, custom integrations

**Model Context Protocol (MCP):**
- Smithery
- Github

---

## Voice Applications

### Speech-to-Text (STT)

**Primary Services:**
- Whisper (billed via OpenAI API)
- Browser-based tools (e.g., Blabby)
- OS-level integration tools

**Specialized Services:**
- **AssemblyAI**: Long-form transcription with speaker diarization (used frequently)
- **Deepgram**: Task-dependent usage
- **Speechmatics**: Advanced voice technology platform
- **Lemonfox**: Budget-friendly option for cost-sensitive jobs

**API Aggregators:**
- **Eden AI**: Multi-provider API batching and management

> **Learning**: Synchronous and asynchronous workloads perform differently across models and services. Match the tool to the specific task requirements.

### Text-to-Speech (TTS)

**Premium Option:**
- 11 Labs (best-in-class quality)

**Budget-Friendly Options:**
- OpenAI TTS
- Various alternative providers

### Real-Time / Live Audio

Requires separate API subscriptions. Generally expensive but essential for live interaction use cases.

---

## Generative AI

### Image Generation & Manipulation

**Capabilities:**
- Text-to-image generation
- Image-to-image transformation

### Video Generation

**Capabilities:**
- Image-to-video conversion
- Text-to-video creation

### Multimodal Inference

**Image-Based:**
- Vision LLMs (available across most modern LLMs)

**Video-Based:**
- Gemini (primary choice for video understanding)

**Audio-Based:**
- Gemini 2.5 (primary choice)
- Enormous transformative potential beyond simple STT

> **Note**: Audio-based inference represents a significant opportunity for innovation beyond traditional speech-to-text approaches.

---

## Data Retrieval & Processing

### Internal Data (RAG)
Retrieval-Augmented Generation for working with proprietary datasets and knowledge bases.

- **Ragie**: RAG as a service via API

### External Data
- **Firecrawl**: Web scraping and data extraction

### Document Processing & OCR
- Mistral
- LlamaIndex

---

## Development Tools

### Code Generation & Editing

**Primary Tools:**
- **Claude Code** (CLI-based development)
- **Codex** (GitHub Copilot integration)
- **Aider** (AI pair programming)

### Code Hosting
- **GitHub** (primary repository hosting)

---

## Cloud & Deployment

### Cloud Infrastructure
- **Google Cloud Platform (GCP)** (primary cloud provider)

### Deployment Platforms
- **On-server** (self-hosted deployments)
- **Vercel** (serverless frontend deployments)

### Hardware On-Demand / Serverless
- **RunPod** (GPU compute on demand)
- **Modal** (serverless compute platform)

### Prototyping & Lightweight Execution
- **Hugging Face Spaces** (rapid prototyping and lightweight app hosting)

---

## API Services

### Versatile AI APIs

**Multi-Model Platforms:**
- **OpenRouter** (unified API access)
- **Fal** (fast inference)
- **Replicate** (model marketplace)
- **Fireworks** (fast inference)
- Individual vendor APIs

---

## Local AI Infrastructure

### Software Stack
- **LM Studio** (GUI interface for local models)
- **Ollama** (CLI-based local inference)

### Hardware
- High-performance GPU for local model inference

### Security & Sensitive Data

**Offline AI:**
- Local models and interfaces for sensitive workloads
- No external API calls

**Air-Gapped Environments:**
- Adapted local AI stack for completely isolated systems
- Separate infrastructure domain

---

## Automation & Workflows

### Automation Pipelines
- **N8N** (visual workflow automation)

---

## Google Ecosystem

**Integrated Services:**
- **NotebookLM** (free with Google Workspace)
- **Gemini** (free with Google Workspace)
- **AI Studio** (development environment)
- **AI Studio + Cloud Run** (production deployments, API costs apply)

> **Favorite Tool**: NotebookLM for research and knowledge synthesis

---

## Cost Breakdown

### Monthly Subscriptions

| Service | Tier | Cost |
|---------|------|------|
| Claude Code | Pro (Basic) | $17/month |
| Claude Code | Max | $100/month |

### Usage-Based Services

- **STT**: OpenAI Whisper API (per-usage)
- **TTS**: 11 Labs (premium) or OpenAI (budget)
- **Real-Time APIs**: Various providers (generally expensive)
- **Cloud Infrastructure**: GCP (variable based on usage)
- **Serverless Compute**: RunPod, Modal (pay-per-use)
- **AI Studio + Cloud Run**: API costs (variable)

---

## Architecture Philosophy

This AI stack is designed around several core principles:

1. **Flexibility**: Multiple options for each capability (premium vs. budget, cloud vs. local)
2. **Task-Appropriate Tooling**: Different tools for different workload types (sync vs. async, batch vs. real-time)
3. **Security Tiers**: Options ranging from cloud APIs to fully air-gapped local inference
4. **Cost Optimization**: Balance between premium services and cost-effective alternatives
5. **Developer Experience**: Strong emphasis on CLI tools and automation pipelines

---

**Last Updated**: October 27, 2025