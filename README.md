# AI Stack Documentation

![Last Updated](https://img.shields.io/badge/Last_Updated-October_2025-blue?style=for-the-badge)
![Stack Type](https://img.shields.io/badge/Stack-Production_Ready-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-Personal_Use-orange?style=for-the-badge)

A point-in-time overview of my AI infrastructure, tools, and services for development, deployment, and production workflows.

> **Note**: This is not prescriptive. It's a snapshot of what I, as one person, see value in and my thoughts. Everybody is different. I update this roughly once a year, though the pace of evolution in this space is rapid enough that monthly updates would make sense.

## 🎯 Stack At a Glance

| Component | Primary Choice | Favorite Feature |
|-----------|----------------|------------------|
| **LLM Interface** | ![Claude Code](https://img.shields.io/badge/Claude_Code-CLI-191919?style=flat) | CLI-based development |
| **API Gateway** | ![OpenRouter](https://img.shields.io/badge/OpenRouter-Multi_Model-9333EA?style=flat) | Unified API access |
| **STT** | ![AssemblyAI](https://img.shields.io/badge/AssemblyAI-Diarization-00C58E?style=flat) | Speaker diarization |
| **TTS** | ![OpenAI](https://img.shields.io/badge/OpenAI-Budget-412991?style=flat) | Cost-effective |
| **Generative AI** | ![Replicate](https://img.shields.io/badge/Replicate-Marketplace-000000?style=flat) | Model exploration |
| **RAG** | ![Supermemory](https://img.shields.io/badge/Supermemory-Managed-9333EA?style=flat) | No DIY complexity |
| **Research** | ![NotebookLM](https://img.shields.io/badge/NotebookLM-Favorite-4285F4?style=flat) | Knowledge synthesis |
| **Cloud** | ![GCP](https://img.shields.io/badge/Google_Cloud-Platform-4285F4?style=flat) | Primary provider |
| **Local AI** | ![Ollama](https://img.shields.io/badge/Ollama-CLI-000000?style=flat) | Batch processing |

## 📑 Quick Navigation

| Category | What's Inside |
|----------|---------------|
| [🧠 Core Infrastructure](#-core-infrastructure) | LLMs, API gateways, MCP |
| [🎙️ Voice Applications](#️-voice-applications) | STT, TTS, live audio |
| [🎨 Generative AI](#-generative-ai) | Image, video, multi-modal |
| [📊 Data & Retrieval](#-data-retrieval--processing) | RAG, web scraping, OCR |
| [💻 Development](#-development-tools) | Code generation, hosting |
| [☁️ Cloud & Deployment](#️-cloud--deployment) | Infrastructure, serverless |
| [🔌 API Services](#-api-services) | Multi-model platforms |
| [🖥️ Local AI](#️-local-ai-infrastructure) | Self-hosted solutions |
| [⚙️ Automation](#️-automation--workflows) | Workflows, voice pipelines |
| [🔵 Google Ecosystem](#-google-ecosystem) | NotebookLM, AI Studio |
| [💰 Cost Breakdown](#-cost-breakdown) | Budget transparency |
| [💡 Philosophy](#-key-insights--philosophy) | Lessons and insights |

---

## Why This Exists

Once or twice a year, usually around winter, I organize all my GitHub repositories - consolidating, deleting old ones, creating new ones. Part of this process is documenting my AI stack.

Friends and clients sometimes ask: "With so much on the market, what are you using?" This document captures:

1. What I'm currently using for different tasks
2. Why I've picked up or dropped certain tools
3. What these things actually cost

The AI space moves quickly enough that these notes could be out of date in months, but I find it useful to document where things stand.
 

## 🧠 Core Infrastructure

### Large Language Models
![Category](https://img.shields.io/badge/Category-LLMs-9333EA?style=flat-square)
![Priority](https://img.shields.io/badge/Priority-Critical-red?style=flat-square)

The backbone of the entire AI stack, powering nearly every component and workflow.

**Primary Interfaces:**
- **CLI**: [Claude Code][claude-code] (Pro: $17/month | Max: $100/month) - *The greatest thing I've found since ChatGPT*
- **GUI**: [Claude][claude] interface (included with Claude Code subscription)
- **[ChatGPT][chatgpt]**: Day-to-day interface for general tasks
- **[OpenAI][openai]**: API access and integrations

**Why I Use Claude Code**:

After 20 years of using Linux, CLIs are familiar, but I've generally preferred GUIs when they're available. Claude Code has changed how I approach system management.

When I started using it (along with [Gemini][gemini] CLI and [CodeX][codex]), I wondered why there wasn't more focus on using these tools for local computer management. There was a project called [Open Interpreter][open-interpreter] that had potential, but Claude Code covers more ground.

**What It Helps With**:
Linux has gotten easier over time, but there's always been a list of things that don't quite work - bugs, things I wish I could do. That list is now much shorter. When I run into issues, I can just say "Hey Claude, any chance you can figure out why..." or "create a shortcut for turning the screens on and off" - and it handles most of these.

**Use Cases**:
- Local system administration
- Home lab management (didn't intend to get into home labbing, but here we are)
- Remote server fixes
- Solving Linux issues that used to linger

**Note on Self-Hosted Interfaces**: Previously used [Open WebUI][open-webui] (self-hosted chat interface). Before becoming a father and getting busy, I reached the conclusion that there wasn't a compelling reason to deal with the hassle of things breaking and needing fixes. Simplicity and reliability won out over self-hosting.

**API Access:**
- **[OpenRouter][openrouter]**: Unified API gateway for multiple LLM providers
  - Direct vendor APIs also available from all major providers
  - Can be used with CLI tools, web apps, desktop apps, custom integrations

**Why I Use OpenRouter**:

I'm not always sure whether you get the same quality of inference as when using the vendor directly. For Claude specifically, it seems like better performance comes from Anthropic rather than routing through OpenRouter. So there's still a case for first-party access.

That said, for someone looking to go beyond ChatGPT, OpenRouter is worth considering early.

**Two Main Reasons**:

1. **Expense Consolidation**:
   - When you run a business and need to provide expenses to your accountant, one API bill is easier than fragmented charges
   - It's easy to lose track when spending $20 here and there on different APIs
   - With OpenRouter, you set spend limits in one place

2. **Model Exploration**:
   - Try different models without separate accounts
   - Example: I ran an evaluation called "AI Brevity" (looking at which models actually follow conciseness instructions)
   - Ran the same prompt through 10 models using OpenRouter and a script
   - Convenient because you just change the model parameter

**What's Beyond the Big Names**:
There's more than OpenAI, Anthropic, Gemini worth looking at:
- What's coming out of China
- What's emerging at the frontier of fine-tunable models
- Models that don't make headlines: IBM Granite, Amazon's models, Microsoft Phi
- Some of these are good at instruction following

**Where This Matters**:
I find that many practical uses for LLMs are simple text transformations. For those, you don't need a high-reasoning model. You want something good at: "Here's the system prompt, here's your task, go from A to B."

Having a mix of open-source and commercial models through one API is convenient for this kind of work.

> **Getting Started**: Set up an account on OpenRouter. They offer some free inference to try it out. If you're self-hosting a chat interface like Open WebUI or looking for programmatic integration, this is where you can see that instructional AI and programmatic AI can be useful beyond chatbots.

> **Performance Note**: First-party vendor access (e.g., Anthropic for Claude) may provide better inference quality than routing through aggregators. For production workloads with specific models, consider direct vendor access.

**Model Context Protocol (MCP):**
- [Smithery][smithery]
- [Github][github]
- [Context][context-mcp] (for API documentation lookup)
- [Firecrawl][firecrawl] (covered in Data Retrieval section)

---

## 🎙️ Voice Applications

### Speech-to-Text (STT)
![Category](https://img.shields.io/badge/Category-Voice-00C58E?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Transcription-blue?style=flat-square)

**Primary Services:**
- **[Whisper][whisper]** (via OpenAI API): Solid baseline, good value
  - Note: OpenAI's newer model hasn't shown significant improvement in my workloads
- **Browser-based tools** (e.g., [Blabby][blabby]): Convenient for quick tasks
- **OS-level integration tools**: For continuous dictation

**Specialized Services:**
- **[AssemblyAI][assemblyai]**: Long-form transcription with speaker diarization (used frequently)
  - Essential for meeting transcripts and AI minute extraction
  - Diarization is a foundational element for quality downstream processing
- **[Deepgram][deepgram]**: Task-dependent usage
- **[Speechmatics][speechmatics]**: Advanced voice technology platform
- **[Gladio][gladio]**: Very solid performance
- **[Lemonfox][lemonfox]**: Budget-friendly option for cost-sensitive jobs

**API Aggregators:**
- **[Eden AI][edenai]**: Multi-provider API batching and management

> **Critical Learning**: Don't expect the STT tool you use for live transcription to work well for asynchronous jobs like meeting transcripts. There are significant performance differences within STT tools across synchronous vs. asynchronous workloads. Match the tool to the specific task requirements.

**Use Case Recommendations:**
- **Live/Real-time**: Whisper, browser tools, OS integration
- **Async/Long-form with speakers**: AssemblyAI, Speechmatics
- **Budget-conscious batch jobs**: Lemonfox
- **General reliability**: Gladio

### Text-to-Speech (TTS)
![Category](https://img.shields.io/badge/Category-Voice-000000?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Audio_Generation-blue?style=flat-square)

**Premium Option:**
- **[ElevenLabs][elevenlabs]**: Best-in-class quality with excellent expressiveness
  - Drawback: Very expensive
  - Recommendation: Use when audio quality is critical

**Budget-Friendly Options:**
- **[OpenAI TTS][openai]**: Good enough for majority of use cases
  - Lacks the expressiveness of ElevenLabs but significantly cheaper
  - Recommended for most projects unless premium audio is essential
- **Various alternative providers**: Available based on specific needs

**Budget Decision Framework:**
- **Quality-first budget**: ElevenLabs
- **Cost-conscious budget**: OpenAI TTS or OpenAI Mini

### Real-Time / Live Audio

Requires separate API subscriptions. Generally expensive but essential for live interaction use cases.

---

## 🎨 Generative AI

### Multi-Modal Generation Platforms
![Category](https://img.shields.io/badge/Category-Generative_AI-FF4785?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Multi_Modal-purple?style=flat-square)

**Primary Platforms:**
- **[Replicate][replicate]**: Good for model exploration and API-based workflows
- **[Fal][fal]**: Similar offering, seems to have more Chinese models

**Why These Are Useful**:

Both platforms offer the same value as OpenRouter but for generative AI.

**Discovery Beyond Convenience**:
Yes, it's convenient to run generative AI tasks like text-to-video through one API account. But the discovery aspect is equally valuable:

- You can explore available models in one place
- Find capabilities you didn't know existed (audio inpainting, for example)
- Try out models before committing budget to a specific workload
- Find companies and models you haven't heard of

New generative AI models and modalities appear on these platforms regularly.

**Fal vs Replicate**:
I don't have strong opinions about which is better. Fal seems to have more Chinese models. Both work well.

> **Note**: Similar to OpenRouter for LLMs, these platforms provide consolidated access to generative capabilities through a single API. The discovery aspect is as useful as the consolidation.

### Image Generation & Manipulation

**Capabilities:**
- Text-to-image generation
- Image-to-image transformation
- Available through Replicate, Fal, and direct model APIs

### Video Generation

**Capabilities:**
- Image-to-video conversion
- Text-to-video creation
- Accessible via Replicate and Fal platforms

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

## 📊 Data Retrieval & Processing

### Internal Data (RAG)
![Category](https://img.shields.io/badge/Category-RAG-6366F1?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Knowledge_Base-blue?style=flat-square)
Retrieval-Augmented Generation for working with proprietary datasets and knowledge bases.

**RAG-as-a-Service:**
- **[Ragie][ragie]**: RAG as a service via API
- **[Supermemory][supermemory]**: Philosophy of "don't build your own RAG pipeline"

**Why Not DIY RAG**:
Unless you have enterprise-level document stores, building RAG from scratch ([Pinecone][pinecone], [Qdrant][qdrant], custom embeddings, chunking strategies, vector sizes) is often time-consuming. Services like Supermemory and memory layer tools handle this complexity, letting you focus on grounding AI in documents rather than becoming a retrieval engineer.

> **Note**: For most use cases not at massive scale, managed RAG services save setup time for relatively simple document retrieval tasks.

### External Data
![Category](https://img.shields.io/badge/Category-Web_Scraping-FF4500?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Data_Collection-blue?style=flat-square)

**[Firecrawl][firecrawl]**: Web scraping and data extraction

There's a whole world of MCP tools, and Firecrawl is one I use regularly.

**Why Markdown Matters**:
Markdown is a useful format for AI workloads. Being able to quickly say, "Okay, these are the API docs for something you're struggling with" helps.

There's Context, which is a good MCP for this. But sometimes I know exactly what Claude needs in Markdown format. Having a reliable tool for this is useful.

**Model Definitions**:
Being able to define models for scraping makes the extraction more targeted.

**Scraping Your Own Content**:

People assume scraping is spammy or questionable, but I've often used these tools to scrape my own content.

**Real Use Case**:
If I wrote notes a few years ago, I can use Firecrawl to pull them in. It's quicker than digging through old Google Drive folders and formatting to Markdown.

**Use Cases**:
- Pulling your own historical content
- API documentation lookup via MCP
- Converting web content to AI-friendly formats
- Retrieving notes from various platforms

> **Note on Scraping**: Web scraping tools are useful for retrieving your own content, documentation, and notes from various platforms for AI processing.

### Document Processing & OCR
- **[Mistral][mistral]**: Document understanding
- **[LlamaIndex][llamaindex]**: Document processing and indexing

---

## 💻 Development Tools

### Code Generation & Editing
![Category](https://img.shields.io/badge/Category-Development-181717?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Coding-blue?style=flat-square)

**Primary Tools:**
- **[Claude Code][claude-code]** (CLI-based development)
- **[Codex][codex]** (GitHub Copilot integration)
- **[Aider][aider]** (AI pair programming)

### Code Hosting
- **[GitHub][github]** (primary repository hosting)

---

## ☁️ Cloud & Deployment

### Cloud Infrastructure
![Category](https://img.shields.io/badge/Category-Cloud-4285F4?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Infrastructure-blue?style=flat-square)
- **[Google Cloud Platform (GCP)][gcp]**: Primary cloud provider

### Deployment Platforms
- **On-server**: Self-hosted deployments
- **[Vercel][vercel]**: Serverless frontend deployments
  - Recently migrated from [Netlify][netlify]
  - More AI-forward feature set
  - Environment variable sharing across projects is excellent

### Hardware On-Demand / Serverless
- **[RunPod][runpod]**: GPU compute on demand
- **[Modal][modal]**: Serverless compute platform

### Prototyping & Lightweight Execution
- **[Hugging Face Spaces][hf-spaces]**: Rapid prototyping and lightweight app hosting
  - Supports private deployments
  - Excellent for quick experiments

---

## 🔌 API Services

### Versatile AI APIs
![Category](https://img.shields.io/badge/Category-APIs-9333EA?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Integration-blue?style=flat-square)

**Multi-Model Platforms:**
- **[OpenRouter][openrouter]** (unified API access)
- **[Fal][fal]** (fast inference)
- **[Replicate][replicate]** (model marketplace)
- **[Fireworks][fireworks]** (fast inference)
- Individual vendor APIs

---

## 🖥️ Local AI Infrastructure

### Software Stack
![Category](https://img.shields.io/badge/Category-Local_AI-000000?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Self_Hosted-blue?style=flat-square)
- **[LM Studio][lmstudio]**: GUI interface for local models
- **[Ollama][ollama]**: CLI-based local inference

### Hardware
- **High-performance GPU** for local model inference
  - Current: [AMD Radeon][amd-radeon] ([ROCm][rocm]-compatible)
  - **Recommendation**: Go with [NVIDIA GPU][nvidia] for fewer compatibility issues
    - AMD works but adds complexity
    - NVIDIA has broader model support and easier setup

### Current Status & Use Cases

**Why I Use Local AI** (and why it's limited):
- **Not for privacy**: Not a driving factor for my use
- **Not for cost savings**: Cloud inference (Whisper STT, cheap models) offers excellent value
- **Primary reason**: Speed for specific workloads

**Where Local AI Works Well**:
- **Large batch jobs**: Processing thousands of files (e.g., voice note classification)
  - No rate limiting concerns
  - Can run overnight
  - Models like [Meta Llama 3.1][llama] for text transformation tasks

**Where Local AI Falls Short** (for me):
- **Agentic workflows**: Local agents (Qwen models, GLM 4.6) haven't matched cloud quality
- **Code generation**: Local models not yet competitive with cloud options
- **Image generation**: Cloud services remain more practical

> **Honest Assessment**: I keep exploring local AI and am eager for it to improve, but currently find myself defaulting to cloud services for most tasks. The quality gap hasn't closed enough to justify the added complexity, except for specific batch processing scenarios.

### Security & Sensitive Data

**Offline AI:**
- Local models and interfaces for sensitive workloads
- No external API calls

**Air-Gapped Environments:**
- Adapted local AI stack for completely isolated systems
- Separate infrastructure domain

---

## ⚙️ Automation & Workflows

### Automation Pipelines
![Category](https://img.shields.io/badge/Category-Automation-EA4B71?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Workflows-blue?style=flat-square)
- **[N8N][n8n]**: Visual workflow automation

### Voice-First Workflows

**Why Voice Workflows Matter**:
A significant pattern in my stack is voice-based context generation and documentation:

1. **Efficiency**: 30-minute voice recording captures more information than hours of typing
2. **Natural expression**: Speaking allows more natural, comprehensive context sharing
3. **Transformation pipeline**: Voice → STT → Context extraction → AI workspace

**Current Project - Voice Note Classification**:
Working on automated classification system for voice notes using batch processing with local models.

**The Meta-Workflow**:
This document itself was created using this pattern:
1. Claude Code generated interview questions
2. Recorded 30-minute voice response
3. Transcribed and integrated into documentation

> **Advantage**: Voice workflows excel at generating rich, personalized context that makes AI significantly more useful for ongoing tasks.

---

## 🔵 Google Ecosystem

![Category](https://img.shields.io/badge/Category-Google-4285F4?style=flat-square)
![Use Case](https://img.shields.io/badge/Use_Case-Research_&_Dev-blue?style=flat-square)

**Integrated Services:**
- **[NotebookLM][notebooklm]**: Free with Google Workspace - **Favorite tool** for research and knowledge synthesis
- **[Gemini][gemini]**: Free with Google Workspace
- **[AI Studio][ai-studio]**: Development environment
- **[AI Studio][ai-studio] + [Cloud Run][cloud-run]**: Production deployments (API costs apply)

### NotebookLM

**Why I Use It:**
- Originally limited to 10 sources; now more capable
- Good at assembling building blocks: retrieval → questions → generation based on retrieval
- Alternative to [LlamaIndex][llamaindex] for many use cases, but simpler

**Use Case - Deliberate Context Generation:**

I've been working on a pattern for a while around building context once rather than repeatedly.

**The Pattern**:

When you have an ongoing situation that's personal and complex - not just asking for a pasta recipe.

**Real Example - Health Context**:
I had gallbladder surgery years ago. Since then, I've had digestive issues - bloating, nausea, various problems. I don't enjoy narrating the whole story every time I need help with meal planning or dietary advice.

**The Approach**:
1. Record the context once (30-minute voice note covering everything)
2. Transform to text
3. Use as workspace foundation in NotebookLM
4. Get shopping lists, recipes tailored to my needs - without re-explaining context

**Why This Helps**:
When you're working on a few of these ongoing situations (health, project planning, personal circumstances), you see the advantage of this approach over repeatedly defining context.

**Two Approaches to Context:**
1. **OpenAI's approach**: Chat first, AI extracts memories over time
2. **This approach**: Generate deliberate context upfront through structured recording

Both are trying to solve the same question: How can AI be more useful when personalized to your life circumstances?

**Why Voice Workflows**:
I can record a voice note and in 30 minutes gather a lot of information. Transform that (extracting the context data), and that's the starting context.

**Working in Reverse**:
This is working backwards from the OpenAI approach. They have you chat with ChatGPT, and it learns about you over time. This generates context upfront.

**Variations**:
- **Basic**: Speak for 30 minutes into a microphone
- **Structured**: A bot asks questions like an interview
- This stack documentation used the second approach: the bot came up with questions, I spoke for 30 minutes

> **Note**: This pattern creates comprehensive context in a single focused session rather than hoping it emerges from conversation.

---

## 💰 Cost Breakdown

![Category](https://img.shields.io/badge/Category-Budget-green?style=flat-square)
![Transparency](https://img.shields.io/badge/Transparency-Open-blue?style=flat-square)

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

## 💡 Key Insights & Philosophy

![Category](https://img.shields.io/badge/Category-Philosophy-orange?style=flat-square)
![Experience](https://img.shields.io/badge/Experience-Production-green?style=flat-square)

### What I Find Most Useful

**Simple Text Transformations**:
Many practical uses for LLMs are simple text transformations. For these:
- You don't need high-reasoning models
- You want good instruction-following
- Models like IBM Granite, Microsoft Phi work well
- Cost-effective and reliable

> **Example**: Running evaluations across 10+ models to find which handles "AI Brevity" best (avoiding verbose outputs that resist system prompting)

**Programmatic AI**:
I find programmatic integration and instructional AI more useful than chatbots. This provides value through automation, batch processing, and system integration.

### How I Think About This Stack

This AI stack reflects a few principles:

1. **Flexibility**: Multiple options for each capability (premium vs. budget, cloud vs. local)
2. **Task-Appropriate Tooling**: Different tools for different workload types (sync vs. async, batch vs. real-time)
3. **Security Tiers**: Options from cloud APIs to air-gapped local inference
4. **Cost Balance**: Premium services for some things, cost-effective alternatives for others
5. **CLI Tools**: Preference for CLI tools and automation pipelines
6. **Stack Consolidation**: Minimize API fragmentation through unified platforms (OpenRouter, Replicate, Fal)
7. **Expense Management**: Practical accounting and budgeting (matters for business use)

---

## Links & Resources

### Core AI Platforms

| Service | Description | Link |
|---------|-------------|------|
| Claude | Primary LLM interface | [![Visit Website](https://img.shields.io/badge/Visit-Website-191919?style=flat)](https://claude.ai) |
| Claude Code | CLI development tool | [![Visit Website](https://img.shields.io/badge/Visit-Website-191919?style=flat)](https://docs.claude.com/claude-code) |
| ChatGPT | Day-to-day LLM interface | [![Visit Website](https://img.shields.io/badge/Visit-Website-412991?style=flat)](https://chat.openai.com) |
| OpenAI | LLM API access | [![Visit Website](https://img.shields.io/badge/Visit-Website-412991?style=flat)](https://openai.com) |
| Gemini | Google's LLM platform | [![Visit Website](https://img.shields.io/badge/Visit-Website-4285F4?style=flat)](https://gemini.google.com) |
| OpenRouter | Unified multi-model API | [![Visit Website](https://img.shields.io/badge/Visit-Website-9333EA?style=flat)](https://openrouter.ai) |

### Development Tools

| Tool | Description | Link |
|------|-------------|------|
| GitHub Copilot | Code completion | [![Visit Website](https://img.shields.io/badge/Visit-Website-181717?style=flat)](https://github.com/features/copilot) |
| Aider | AI pair programming | [![Visit Website](https://img.shields.io/badge/Visit-Website-00ADD8?style=flat)](https://aider.chat) |
| GitHub | Code hosting | [![Visit Website](https://img.shields.io/badge/Visit-Website-181717?style=flat)](https://github.com) |
| Open Interpreter | Natural language interface | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://github.com/KillianLucas/open-interpreter) |

### Model Context Protocol (MCP)

| Service | Description | Link |
|---------|-------------|------|
| Smithery | MCP marketplace | [![Visit Website](https://img.shields.io/badge/Visit-Website-FF6B6B?style=flat)](https://smithery.ai) |
| MCP Servers | Official MCP servers | [![Visit Website](https://img.shields.io/badge/Visit-Website-181717?style=flat)](https://github.com/modelcontextprotocol/servers) |

### Speech & Voice

| Service | Type | Description | Link |
|---------|------|-------------|------|
| Whisper | STT | Baseline transcription | [![Visit Website](https://img.shields.io/badge/Visit-Website-412991?style=flat)](https://openai.com/research/whisper) |
| AssemblyAI | STT | Long-form with diarization | [![Visit Website](https://img.shields.io/badge/Visit-Website-00C58E?style=flat)](https://www.assemblyai.com) |
| Deepgram | STT | Task-dependent | [![Visit Website](https://img.shields.io/badge/Visit-Website-13EF93?style=flat)](https://deepgram.com) |
| Speechmatics | STT | Advanced voice platform | [![Visit Website](https://img.shields.io/badge/Visit-Website-00C4CC?style=flat)](https://www.speechmatics.com) |
| Gladia | STT | Solid performance | [![Visit Website](https://img.shields.io/badge/Visit-Website-6366F1?style=flat)](https://www.gladia.io) |
| Lemonfox | STT | Budget-friendly | [![Visit Website](https://img.shields.io/badge/Visit-Website-FCD34D?style=flat)](https://lemonfox.ai) |
| Blabby | STT | Browser-based | [![Visit Website](https://img.shields.io/badge/Visit-Website-FF6B6B?style=flat)](https://blabby.co) |
| ElevenLabs | TTS | Premium quality | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://elevenlabs.io) |
| Eden AI | Aggregator | Multi-provider batching | [![Visit Website](https://img.shields.io/badge/Visit-Website-00D9FF?style=flat)](https://www.edenai.co) |

### Generative AI Platforms

| Platform | Description | Link |
|----------|-------------|------|
| Replicate | Multi-modal generation | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://replicate.com) |
| Fal | Fast inference platform | [![Visit Website](https://img.shields.io/badge/Visit-Website-FF4785?style=flat)](https://fal.ai) |
| Fireworks | Fast inference API | [![Visit Website](https://img.shields.io/badge/Visit-Website-FF5A1F?style=flat)](https://fireworks.ai) |

### Data & Retrieval

| Service | Type | Description | Link |
|---------|------|-------------|------|
| Firecrawl | Scraping | Web to markdown | [![Visit Website](https://img.shields.io/badge/Visit-Website-FF4500?style=flat)](https://www.firecrawl.dev) |
| Ragie | RAG | RAG as a service | [![Visit Website](https://img.shields.io/badge/Visit-Website-6366F1?style=flat)](https://www.ragie.ai) |
| Supermemory | RAG | Managed RAG | [![Visit Website](https://img.shields.io/badge/Visit-Website-9333EA?style=flat)](https://supermemory.ai) |
| Pinecone | Vector DB | Vector database | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://www.pinecone.io) |
| Qdrant | Vector DB | Vector search | [![Visit Website](https://img.shields.io/badge/Visit-Website-DC244C?style=flat)](https://qdrant.tech) |
| Mistral | OCR | Document understanding | [![Visit Website](https://img.shields.io/badge/Visit-Website-FF6B6B?style=flat)](https://mistral.ai) |
| LlamaIndex | Framework | Document processing | [![Visit Website](https://img.shields.io/badge/Visit-Website-9333EA?style=flat)](https://www.llamaindex.ai) |

### Cloud & Deployment

| Platform | Description | Link |
|----------|-------------|------|
| Google Cloud Platform | Primary cloud | [![Visit Website](https://img.shields.io/badge/Visit-Website-4285F4?style=flat)](https://cloud.google.com) |
| Vercel | Serverless frontend | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://vercel.com) |
| Netlify | (Previously used) | [![Visit Website](https://img.shields.io/badge/Visit-Website-00C7B7?style=flat)](https://www.netlify.com) |
| RunPod | GPU on demand | [![Visit Website](https://img.shields.io/badge/Visit-Website-6366F1?style=flat)](https://www.runpod.io) |
| Modal | Serverless compute | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://modal.com) |
| Hugging Face Spaces | Rapid prototyping | [![Visit Website](https://img.shields.io/badge/Visit-Website-FFD21E?style=flat)](https://huggingface.co/spaces) |

### Local AI

| Tool | Description | Link |
|------|-------------|------|
| LM Studio | Local model interface | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://lmstudio.ai) |
| Ollama | Local inference CLI | [![Visit Website](https://img.shields.io/badge/Visit-Website-000000?style=flat)](https://ollama.com) |
| AMD Radeon | GPU hardware | [![Visit Website](https://img.shields.io/badge/Visit-Website-ED1C24?style=flat)](https://www.amd.com/en/graphics/radeon-rx-graphics) |
| ROCm | AMD compute | [![Visit Website](https://img.shields.io/badge/Visit-Website-ED1C24?style=flat)](https://www.amd.com/en/products/software/rocm.html) |
| NVIDIA | Recommended GPU | [![Visit Website](https://img.shields.io/badge/Visit-Website-76B900?style=flat)](https://www.nvidia.com) |
| Meta Llama | Open model family | [![Visit Website](https://img.shields.io/badge/Visit-Website-0668E1?style=flat)](https://ai.meta.com/llama/) |

### Automation

| Tool | Description | Link |
|------|-------------|------|
| n8n | Visual automation | [![Visit Website](https://img.shields.io/badge/Visit-Website-EA4B71?style=flat)](https://n8n.io) |

### Google Ecosystem

| Service | Description | Link |
|---------|-------------|------|
| NotebookLM | Knowledge synthesis | [![Visit Website](https://img.shields.io/badge/Visit-Website-4285F4?style=flat)](https://notebooklm.google.com) |
| AI Studio | Development environment | [![Visit Website](https://img.shields.io/badge/Visit-Website-4285F4?style=flat)](https://aistudio.google.com) |
| Cloud Run | Serverless containers | [![Visit Website](https://img.shields.io/badge/Visit-Website-4285F4?style=flat)](https://cloud.google.com/run) |

### Self-Hosted & Open Source

| Tool | Description | Link |
|------|-------------|------|
| Open WebUI | Self-hosted interface | [![Visit Website](https://img.shields.io/badge/Visit-Website-181717?style=flat)](https://github.com/open-webui/open-webui) |

---

**Last Updated**: October 27, 2025