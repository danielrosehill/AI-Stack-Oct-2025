# My AI Stack - October 2025 Iteration

![alt text](graphics/banner.png)

[![Date](https://img.shields.io/badge/Date-2025--10--27-blue.svg)](https://github.com/AI-Stack-Oct-2025)

A point-in-time overview of my AI infrastructure, tools, and services for development, deployment, and production workflows.

> **Note**: This is not prescriptive. It's a snapshot of what I, as one person, see value in and my thoughts. Everybody is different. I update this roughly once a year, though the pace of evolution in this space is rapid enough that monthly updates would make sense.

## Core Stack Components

| Component | Primary Choice | Good Recs | Favorite Feature |
|---|---|---|---|
| **API Gateway** | [OpenRouter](https://openrouter.ai) | | Unified API access |
| **Cloud** | [GCP](https://cloud.google.com) | | Primary provider |
| **Generative AI** | [Replicate](https://replicate.com) | [Fal](https://fal.ai) | Model exploration |
| **LLM Interface** | [Claude Code](https://docs.claude.com/claude-code) | | CLI-based development |
| **Local AI** | [Ollama](https://ollama.com) | | Batch processing |
| **Prototyping** | [AI Studio](https://aistudio.google.com) | | Development environment |
| **RAG** | [Supermemory](https://supermemory.ai) | [Ragie](https://www.ragie.ai) | No DIY complexity |
| **Research** | [NotebookLM](https://notebooklm.google.com) | | Knowledge synthesis |
| **STT** | [AssemblyAI](https://www.assemblyai.com) | [Whisper](https://openai.com/research/whisper) | Speaker diarization |
| **TTS** | [OpenAI](https://openai.com) | [ElevenLabs](https://elevenlabs.io) | Cost-effective |
| **UI** | [ChatGPT](https://chat.openai.com) | | Day-to-day interface |

## Table of Contents

*   [Core Infrastructure](#core-infrastructure)
*   [Voice Applications](#voice-applications)
*   [Generative AI](#generative-ai)
*   [Data & Retrieval](#data--retrieval--processing)
*   [Development](#development-tools)
*   [Cloud & Deployment](#cloud--deployment)
*   [API Services](#api-services)
*   [Local AI](#local-ai-infrastructure)
*   [Automation](#automation--workflows)
*   [Google Ecosystem](#google-ecosystem)
*   [Honorable Mentions](#honorable-mentions)
*   [Cost Breakdown](#cost-breakdown)
*   [Philosophy](#key-insights--philosophy)
*   [Links & Resources](#links--resources)

---

## Why This Exists

Once or twice a year, usually around winter, I organize all my GitHub repositories - consolidating, deleting old ones, creating new ones. Part of this process is documenting my AI stack.

Friends and clients sometimes ask: "With so much on the market, what are you using?" This document captures:

1.  What I'm currently using for different tasks
2.  Why I've picked up or dropped certain tools
3.  What these things actually cost

The AI space moves quickly enough that these notes could be out of date in months, but I find it useful to document where things stand.

## Core Infrastructure

### Large Language Models

The backbone of the entire AI stack, powering nearly every component and workflow.

**Primary Interfaces:**

*   **CLI**: [Claude Code](https://docs.claude.com/claude-code) (Pro: $17/month | Max: $100/month)
*   **GUI**: [Claude](https://claude.ai) interface (included with Claude Code subscription)
*   [ChatGPT](https://chat.openai.com): Day-to-day interface for general tasks
*   [OpenAI](https://openai.com): API access and integrations

**Why I Use Claude Code**:

After 20 years of using Linux, CLIs are familiar, but I've generally preferred GUIs when they're available. Claude Code has changed how I approach system management.

When I started using it (along with [Gemini](https://gemini.google.com) CLI and [CodeX](https://github.com/features/copilot)), I wondered why there wasn't more focus on using these tools for local computer management. There was a project called [Open Interpreter](https://github.com/KillianLucas/open-interpreter) that had potential, but Claude Code covers more ground.

**What It Helps With**:

Linux has gotten easier over time, but there's always been a list of things that don't quite work - bugs, things I wish I could do. That list is now much shorter. When I run into issues, I can just say "Hey Claude, any chance you can figure out why..." or "create a shortcut for turning the screens on and off" - and it handles most of these.

**Use Cases**:

*   Local system administration
*   Home lab management (didn't intend to get into home labbing, but here we are)
*   Remote server fixes
*   Solving Linux issues that used to linger

**Note on Self-Hosted Interfaces**: Previously used [Open WebUI](https://github.com/open-webui/open-webui) (self-hosted chat interface). Before becoming a father and getting busy, I reached the conclusion that there wasn't a compelling reason to deal with the hassle of things breaking and needing fixes. Simplicity and reliability won out over self-hosting.

**API Access:**

*   [OpenRouter](https://openrouter.ai): Unified API gateway for multiple LLM providers
    *   Direct vendor APIs also available from all major providers
    *   Can be used with CLI tools, web apps, desktop apps, custom integrations

**Why I Use OpenRouter**:

I'm not always sure whether you get the same quality of inference as when using the vendor directly. For Claude specifically, it seems like better performance comes from Anthropic rather than routing through OpenRouter. So there's still a case for first-party access.

That said, for someone looking to go beyond ChatGPT, OpenRouter is worth considering early.

**Two Main Reasons**:

1.  **Expense Consolidation**:
    *   When you run a business and need to provide expenses to your accountant, one API bill is easier than fragmented charges
    *   It's easy to lose track when spending $20 here and there on different APIs
    *   With OpenRouter, you set spend limits in one place

2.  **Model Exploration**:
    *   Try different models without separate accounts
    *   Example: I ran an evaluation called "AI Brevity" (looking at which models actually follow conciseness instructions)
    *   Ran the same prompt through 10 models using OpenRouter and a script
    *   Convenient because you just change the model parameter

**What's Beyond the Big Names**:

There's more than OpenAI, Anthropic, Gemini worth looking at:

*   What's coming out of China
*   What's emerging at the frontier of fine-tunable models
*   Models that don't make headlines: IBM Granite, Amazon's models, Microsoft Phi
*   Some of these are good at instruction following

**Where This Matters**:

I find that many practical uses for LLMs are simple text transformations. For those, you don't need a high-reasoning model. You want something good at: "Here's the system prompt, here's your task, go from A to B."

Having a mix of open-source and commercial models through one API is convenient for this kind of work.

> **Getting Started**: Set up an account on OpenRouter. They offer some free inference to try it out. If you're self-hosting a chat interface like Open WebUI or looking for programmatic integration, this is where you can see that instructional AI and programmatic AI can be useful beyond chatbots.

> **Performance Note**: First-party vendor access (e.g., Anthropic for Claude) may provide better inference quality than routing through aggregators. For production workloads with specific models, consider direct vendor access.

**Model Context Protocol (MCP):**

*   [Smithery](https://smithery.ai)
*   [Github](https://github.com/modelcontextprotocol/servers)
*   [Firecrawl](#data--retrieval--processing) (covered in Data Retrieval section)

**Useful MCPs:**

*   [Cloudflare MCP](https://github.com/cloudflare/mcp-server-cloudflare): Manage Cloudflare resources and configurations
*   [Vercel MCP](https://github.com/vercel/mcp-server-vercel): Deploy and manage Vercel projects
*   [Context7](https://context7.com): Particularly useful MCP for enhanced context management
*   [GitHub MCP](https://github.com/github/mcp-server-github): Enhanced GitHub integration and repository management
*   [Goose](https://github.com/block/goose): Valuable MCP tool for development workflows

---

## Voice Applications

### Speech-to-Text (STT)

**Primary Services:**

*   [Whisper](https://openai.com/research/whisper) (via OpenAI API): Solid baseline, good value
    *   Note: OpenAI's newer model hasn't shown significant improvement in my workloads
*   Browser-based tools (e.g., [Blabby](https://blabby.co)): Convenient for quick tasks
*   OS-level integration tools: For continuous dictation

**Mobile/Android:**

*   [Futo Keyboard](https://keyboard.futo.org): Voice typing and ASR on Android
    *   Privacy-focused keyboard with local speech recognition
    *   No cloud processing for voice input
    *   Good accuracy for on-device processing

**Specialized Services:**

*   [AssemblyAI](https://www.assemblyai.com): Long-form transcription with speaker diarization (used frequently)
    *   Essential for meeting transcripts and AI minute extraction
    *   Diarization is a foundational element for quality downstream processing
*   [Deepgram](https://deepgram.com): Task-dependent usage
*   [Gladia](https://www.gladia.io): Very solid performance
*   [Lemonfox](https://lemonfox.ai): Budget-friendly option for cost-sensitive jobs
*   [Speechmatics](https://www.speechmatics.com): Advanced voice technology platform

**API Aggregators:**

*   [Eden AI](https://www.edenai.co): Multi-provider API batching and management

> **Critical Learning**: Don't expect the STT tool you use for live transcription to work well for asynchronous jobs like meeting transcripts. There are significant performance differences within STT tools across synchronous vs. asynchronous workloads. Match the tool to the specific task requirements.

**Use Case Recommendations:**

*   **Live/Real-time**: Whisper, browser tools, OS integration
*   **Async/Long-form with speakers**: AssemblyAI, Speechmatics
*   **Budget-conscious batch jobs**: Lemonfox
*   **General reliability**: Gladia

### Text-to-Speech (TTS)

**Premium Option:**

*   [ElevenLabs](https://elevenlabs.io): Best-in-class quality with excellent expressiveness
    *   Drawback: Very expensive
    *   Recommendation: Use when audio quality is critical

**Budget-Friendly Options:**

*   [OpenAI TTS](https://openai.com): Good enough for majority of use cases
    *   Lacks the expressiveness of ElevenLabs but significantly cheaper
    *   Recommended for most projects unless premium audio is essential
*   Various alternative providers: Available based on specific needs

**Budget Decision Framework:**

*   **Quality-first budget**: ElevenLabs
*   **Cost-conscious budget**: OpenAI TTS or OpenAI Mini

### Real-Time / Live Audio

Requires separate API subscriptions. Generally expensive but essential for live interaction use cases.

---

## Generative AI

### Multi-Modal Generation Platforms

**Primary Platforms:**

*   [Fal](https://fal.ai): Similar offering, seems to have more Chinese models
*   [Replicate](https://replicate.com): Good for model exploration and API-based workflows
    *   [Collections](https://replicate.com/collections): Organized model categories
    *   [Text-to-Image](https://replicate.com/collections/text-to-image): Image generation models
    *   [Image Editing](https://replicate.com/collections/image-editing): Image inpainting and manipulation
    *   [Text-to-Video](https://replicate.com/collections/text-to-video): Video generation models

**Why These Are Useful**:

Both platforms offer the same value as OpenRouter but for generative AI.

**Discovery Beyond Convenience**:

Yes, it's convenient to run generative AI tasks like text-to-video through one API account. But the discovery aspect is equally valuable:

*   You can explore available models in one place
*   Find capabilities you didn't know existed (audio inpainting, for example)
*   Try out models before committing budget to a specific workload
*   Find companies and models you haven't heard of

New generative AI models and modalities appear on these platforms regularly.

**Fal vs Replicate**:

I don't have strong opinions about which is better. Fal seems to have more Chinese models. Both work well.

> **Note**: Similar to OpenRouter for LLMs, these platforms provide consolidated access to generative capabilities through a single API. The discovery aspect is as useful as the consolidation.

### Image Generation & Manipulation

**Capabilities:**

*   Text-to-image generation
*   Image-to-image transformation
*   Image inpainting and editing
*   Available through Replicate, Fal, and direct model APIs

**Noteworthy Models:**

*   [Nano Banana](https://replicate.com/google/nano-banana): Google's image-to-image model
    *   Fast, efficient transformations
    *   Good for style transfer and variations

### Video Generation

**Capabilities:**

*   Image-to-video conversion
*   Text-to-video creation
*   Accessible via Replicate and Fal platforms

**Noteworthy Models:**

*   [Wan Video 2.5 I2V Fast](https://replicate.com/wan-video/wan-2.5-i2v-fast): Budget-friendly image-to-video
    *   Cost-effective for experimental video generation
    *   Good balance of speed and quality

### Multimodal Inference

**Image-Based:**

*   Vision LLMs (available across most modern LLMs)

**Video-Based:**

*   Gemini (primary choice for video understanding)

**Audio-Based:**

*   Gemini 2.5 (primary choice)
*   Enormous transformative potential beyond simple STT

> **Note**: Audio-based inference represents a significant opportunity for innovation beyond traditional speech-to-text approaches.

---

## Data & Retrieval / Processing

### Internal Data (RAG)

Retrieval-Augmented Generation for working with proprietary datasets and knowledge bases.

**RAG-as-a-Service:**

*   [Ragie](https://www.ragie.ai): RAG as a service via API
*   [Supermemory](https://supermemory.ai): Philosophy of "don't build your own RAG pipeline"

**Why Not DIY RAG**:

Unless you have enterprise-level document stores, building RAG from scratch ([Pinecone](https://www.pinecone.io), [Qdrant](https://qdrant.tech), custom embeddings, chunking strategies, vector sizes) is often time-consuming. Services like Supermemory and memory layer tools handle this complexity, letting you focus on grounding AI in documents rather than becoming a retrieval engineer.

> **Note**: For most use cases not at massive scale, managed RAG services save setup time for relatively simple document retrieval tasks.

### External Data

**[Firecrawl](https://www.firecrawl.dev)**: Web scraping and data extraction

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

*   Pulling your own historical content
*   API documentation lookup via MCP
*   Converting web content to AI-friendly formats
*   Retrieving notes from various platforms

> **Note on Scraping**: Web scraping tools are useful for retrieving your own content, documentation, and notes from various platforms for AI processing.

### Document Processing & OCR

*   [Mistral](https://mistral.ai): Document understanding
*   [LlamaIndex](https://www.llamaindex.ai): Document processing and indexing

---

## Development Tools

### Code Generation & Editing

**Primary Tools:**

*   [Aider](https://aider.chat) (AI pair programming)
*   [Claude Code](https://docs.claude.com/claude-code) (CLI-based development)
*   [Codex](https://github.com/features/copilot) (GitHub Copilot integration)

**Vendor CLIs:**

The various vendor CLIs (Gemini CLI, Claude CLI, OpenAI CLI, Qwen CLI) provide valuable direct command-line access to their respective models. These are particularly useful for:

*   Quick API testing and experimentation
*   Scripting and automation workflows
*   CI/CD pipeline integration
*   Direct model access without abstraction layers

### IDEs & Editors

*   [VS Code](https://code.visualstudio.com): Primary IDE for development work
    *   Extensive extension ecosystem
    *   Excellent AI integration support
    *   Strong debugging and Git integration

### Note-Taking & Knowledge Management

*   [Obsidian](https://obsidian.md): Primary tool for note capture and knowledge management
    *   Local-first, markdown-based note-taking
    *   Excellent for organizing AI outputs and research
    *   Graph view for connecting ideas
    *   Extensible with plugins

> **Note on Output Management**: Output management and storage remains an oddly underaddressed part of the AI universe. Most tools focus on generation, but systematic capture, organization, and retrieval of AI outputs is still largely an afterthought. Having a solid knowledge management system like Obsidian helps bridge this gap.

### Python Environment Management

*   [Conda](https://docs.conda.io): Managing complex Python environments with system dependencies
    *   Excellent for ML/AI projects with specific library requirements
    *   Handles non-Python dependencies well
*   [UV](https://github.com/astral-sh/uv): Modern, fast Python package installer and resolver
    *   Extremely fast for creating lightweight virtual environments
    *   Great for quick projects and scripts
    *   Rust-based performance benefits

### General Tooling

**Containerization & Development:**

*   [Docker](https://www.docker.com): Essential for containerized development, especially for local workloads
    *   Useful for isolating dependencies
    *   Creating reproducible development environments
    *   Testing deployment configurations locally
    *   Running services and databases for development

### Code Hosting

*   [GitHub](https://github.com) (primary repository hosting)

---

## Cloud & Deployment

### Cloud Infrastructure

*   [Google Cloud Platform (GCP)](https://cloud.google.com): Primary cloud provider

### Deployment Platforms

*   On-server: Self-hosted deployments
*   [Vercel](https://vercel.com): Serverless frontend deployments
    *   Recently migrated from [Netlify](https://www.netlify.com)
    *   More AI-forward feature set
    *   Environment variable sharing across projects is excellent

### Hardware On-Demand / Serverless

*   [Modal](https://modal.com): Serverless compute platform
*   [RunPod](https://www.runpod.io): GPU compute on demand

### Prototyping & Lightweight Execution

*   [Hugging Face Spaces](https://huggingface.co/spaces): Rapid prototyping and lightweight app hosting
    *   Supports private deployments
    *   Excellent for quick experiments

### Media Storage & Management

*   [Cloudinary](https://cloudinary.com): AI-friendly media storage and transformation
    *   Optimized for AI-generated images and media assets
    *   Automatic optimization and transformation APIs
    *   CDN delivery for fast access
    *   Good integration with generative AI workflows

---

## API Services

### Versatile AI APIs

**Multi-Model Platforms:**

*   [Fal](https://fal.ai) (fast inference)
*   [Fireworks](https://fireworks.ai) (fast inference)
*   Individual vendor APIs
*   [OpenRouter](https://openrouter.ai) (unified API access)
*   [Replicate](https://replicate.com) (model marketplace)

---

## Local AI Infrastructure

### Software Stack

*   [LM Studio](https://lmstudio.ai): GUI interface for local models
    *   User-friendly interface for model management
    *   Good for experimenting with different models
    *   Supports multiple model formats
*   [Ollama](https://ollama.com): CLI-based local inference
    *   Preferred for batch processing and automation
    *   Efficient model management
    *   Easy integration with scripts and workflows
*   [ComfyUI](https://github.com/comfyanonymous/ComfyUI): Node-based interface for Stable Diffusion
    *   Workflow-driven image generation
    *   Powerful for complex generation pipelines
    *   Good for iterative experimentation
*   [rmbg](https://github.com/zhbhun/rmbg): Background removal tool
    *   Local background removal
    *   Fast and efficient processing

### Hardware

*   High-performance GPU for local model inference
    *   Current: [AMD Radeon](https://www.amd.com/en/graphics/radeon-rx-graphics) ([ROCm](https://www.amd.com/en/products/software/rocm.html)-compatible)
    *   **Recommendation**: Go with [NVIDIA GPU](https://www.nvidia.com) for fewer compatibility issues
        *   AMD works but adds complexity
        *   NVIDIA has broader model support and easier setup

### Current Status & Use Cases

**Why I Use Local AI** (and why it's limited):

*   **Not for privacy**: Not a driving factor for my use
*   **Not for cost savings**: Cloud inference (Whisper STT, cheap models) offers excellent value
*   **Primary reason**: Speed for specific workloads

**Where Local AI Works Well**:

*   **Large batch jobs**: Processing thousands of files (e.g., voice note classification)
    *   No rate limiting concerns
    *   Can run overnight
    *   Models like [Meta Llama 3.1](https://ai.meta.com/llama/) for text transformation tasks

**Where Local AI Falls Short** (for me):

*   **Agentic workflows**: Local agents (Qwen models, GLM 4.6) haven't matched cloud quality
*   **Code generation**: Local models not yet competitive with cloud options
*   **Image generation**: Cloud services remain more practical

> **Honest Assessment**: I keep exploring local AI and am eager for it to improve, but currently find myself defaulting to cloud services for most tasks. The quality gap hasn't closed enough to justify the added complexity, except for specific batch processing scenarios.

### Security & Sensitive Data

**Offline AI:**

*   Local models and interfaces for sensitive workloads
*   No external API calls

**Air-Gapped Environments:**

*   Adapted local AI stack for completely isolated systems
*   Separate infrastructure domain

---

## Automation & Workflows

### Automation Pipelines

*   [N8N](https://n8n.io): Visual workflow automation

### Voice-First Workflows

**Why Voice Workflows Matter**:

A significant pattern in my stack is voice-based context generation and documentation:

1.  **Efficiency**: 30-minute voice recording captures more information than hours of typing
2.  **Natural expression**: Speaking allows more natural, comprehensive context sharing
3.  **Transformation pipeline**: Voice -> STT -> Context extraction -> AI workspace

**Current Project - Voice Note Classification**:

Working on automated classification system for voice notes using batch processing with local models.

**The Meta-Workflow**:

This document itself was created using this pattern:

1.  Claude Code generated interview questions
2.  Recorded 30-minute voice response
3.  Transcribed and integrated into documentation

> **Advantage**: Voice workflows excel at generating rich, personalized context that makes AI significantly more useful for ongoing tasks.

---

## Google Ecosystem

**Integrated Services:**

*   [AI Studio](https://aistudio.google.com): Development environment
*   [AI Studio](https://aistudio.google.com) + [Cloud Run](https://cloud.google.com/run): Production deployments (API costs apply)
*   [Gemini](https://gemini.google.com): Free with Google Workspace
*   [NotebookLM](https://notebooklm.google.com): Free with Google Workspace - **Favorite tool** for research and knowledge synthesis

### NotebookLM

**Why I Use It:**

*   Originally limited to 10 sources; now more capable
*   Good at assembling building blocks: retrieval -> questions -> generation based on retrieval
*   Alternative to [LlamaIndex](https://www.llamaindex.ai) for many use cases, but simpler

**Use Case - Deliberate Context Generation:**

I've been working on a pattern for a while around building context once rather than repeatedly.

**The Pattern**:

When you have an ongoing situation that's personal and complex - not just asking for a pasta recipe.

**Real Example - Home Lab Infrastructure**:

When managing a home lab with multiple servers, network configurations, hardware specs, and custom setups, it's tedious to re-explain the entire infrastructure every time you need help troubleshooting or planning an upgrade.

**The Approach**:

1.  Record the context once (30-minute voice note covering network topology, hardware specs, software stack, configuration decisions)
2.  Transform to text
3.  Use as workspace foundation in NotebookLM
4.  Get troubleshooting help, upgrade recommendations, configuration suggestions - without re-explaining your entire setup

**Why This Helps**:

When you're working on a few of these ongoing situations (home lab infrastructure, project architecture, complex workflows), you see the advantage of this approach over repeatedly defining context.

**Two Approaches to Context:**

1.  **OpenAI's approach**: Chat first, AI extracts memories over time
2.  **This approach**: Generate deliberate context upfront through structured recording

Both are trying to solve the same question: How can AI be more useful when personalized to your life circumstances?

**Why Voice Workflows**:

I can record a voice note and in 30 minutes gather a lot of information. Transform that (extracting the context data), and that's the starting context.

**Working in Reverse**:

This is working backwards from the OpenAI approach. They have you chat with ChatGPT, and it learns about you over time. This generates context upfront.

**Variations**:

*   **Basic**: Speak for 30 minutes into a microphone
*   **Structured**: A bot asks questions like an interview
*   This stack documentation used the second approach: the bot came up with questions, I spoke for 30 minutes

> **Note**: This pattern creates comprehensive context in a single focused session rather than hoping it emerges from conversation.

---

## Honorable Mentions

### Privacy-First AI

*   [Lumo](https://proton.me/ai) (by Proton): Privacy-focused AI assistant
    *   Built by Proton with strong privacy guarantees
    *   Good option for users already in the Proton ecosystem
    *   Emphasis on data protection and user privacy
*   [Venice.ai](https://venice.ai): Privacy-first AI platform
    *   No data collection or tracking
    *   Uncensored model access
    *   Anonymous usage supported

### Community & News

*   [Reddit](https://www.reddit.com): Essential for AI news and discussions
    *   Subreddits like r/LocalLLaMA, r/StableDiffusion, r/MachineLearning
    *   Real-time updates on model releases and techniques
    *   Community troubleshooting and experience sharing
*   [Discord](https://discord.com): Primary platform for AI community conversations
    *   Most AI projects maintain active Discord servers
    *   Direct access to developers and community experts
    *   Real-time support and collaboration
    *   Examples: Ollama, Stable Diffusion, various model communities

---

## Cost Breakdown

### Monthly Subscriptions

| Service | Tier | Cost |
|---------|------|------|
| Claude Code | Pro (Basic) | $17/month |
| Claude Code | Max | $100/month |

### Usage-Based Services

*   **STT**: OpenAI Whisper API (per-usage)
*   **TTS**: 11 Labs (premium) or OpenAI (budget)
*   **Real-Time APIs**: Various providers (generally expensive)
*   **Cloud Infrastructure**: GCP (variable based on usage)
*   **Serverless Compute**: RunPod, Modal (pay-per-use)
*   **AI Studio + Cloud Run**: API costs (variable)

---

## Key Insights & Philosophy

### What I Find Most Useful

**Simple Text Transformations**:

Many practical uses for LLMs are simple text transformations. For these:

*   You don't need high-reasoning models
*   You want good instruction-following
*   Models like IBM Granite, Microsoft Phi work well
*   Cost-effective and reliable

> **Example**: Running evaluations across 10+ models to find which handles "AI Brevity" best (avoiding verbose outputs that resist system prompting)

**Programmatic AI**:

I find programmatic integration and instructional AI more useful than chatbots. This provides value through automation, batch processing, and system integration.

### How I Think About This Stack

This AI stack reflects a few principles:

1.  **Flexibility**: Multiple options for each capability (premium vs. budget, cloud vs. local)
2.  **Task-Appropriate Tooling**: Different tools for different workload types (sync vs. async, batch vs. real-time)
3.  **Security Tiers**: Options from cloud APIs to air-gapped local inference
4.  **Cost Balance**: Premium services for some things, cost-effective alternatives for others
5.  **CLI Tools**: Preference for CLI tools and automation pipelines
6.  **Stack Consolidation**: Minimize API fragmentation through unified platforms (OpenRouter, Replicate, Fal)
7.  **Expense Management**: Practical accounting and budgeting (matters for business use)

---

## Links & Resources

### Core AI Platforms

*   [ChatGPT](https://chat.openai.com) - Day-to-day LLM interface
*   [Claude](https://claude.ai) - Primary LLM interface
*   [Claude Code](https://docs.claude.com/claude-code) - CLI development tool
*   [Gemini](https://gemini.google.com) - Google's LLM platform
*   [OpenAI](https://openai.com) - LLM API access
*   [OpenRouter](https://openrouter.ai) - Unified multi-model API

### Development Tools

*   [Aider](https://aider.chat) - AI pair programming
*   [Conda](https://docs.conda.io) - Python environment management
*   [Docker](https://www.docker.com) - Containerization platform
*   [GitHub](https://github.com) - Code hosting
*   [GitHub Copilot](https://github.com/features/copilot) - Code completion
*   [Obsidian](https://obsidian.md) - Note-taking and knowledge management
*   [Open Interpreter](https://github.com/KillianLucas/open-interpreter) - Natural language interface
*   [UV](https://github.com/astral-sh/uv) - Fast Python package installer
*   [VS Code](https://code.visualstudio.com) - Primary IDE

### Model Context Protocol (MCP)

*   [MCP Servers](https://github.com/modelcontextprotocol/servers) - Official MCP servers
*   [Smithery](https://smithery.ai) - MCP marketplace
*   [Context7](https://context7.com) - Enhanced context management
*   [Cloudflare MCP](https://github.com/cloudflare/mcp-server-cloudflare) - Cloudflare resource management
*   [Vercel MCP](https://github.com/vercel/mcp-server-vercel) - Vercel project management
*   [GitHub MCP](https://github.com/github/mcp-server-github) - Enhanced GitHub integration
*   [Goose](https://github.com/block/goose) - Development workflow MCP

### Speech & Voice

*   [AssemblyAI](https://www.assemblyai.com) - Long-form with diarization
*   [Blabby](https://blabby.co) - Browser-based
*   [Deepgram](https://deepgram.com) - Task-dependent
*   [Eden AI](https://www.edenai.co) - Multi-provider batching
*   [ElevenLabs](https://elevenlabs.io) - Premium quality TTS
*   [Futo Keyboard](https://keyboard.futo.org) - Android voice typing/ASR
*   [Gladia](https://www.gladia.io) - Solid performance
*   [Lemonfox](https://lemonfox.ai) - Budget-friendly
*   [Speechmatics](https://www.speechmatics.com) - Advanced voice platform
*   [Whisper](https://openai.com/research/whisper) - Baseline transcription

### Generative AI Platforms

*   [Fal](https://fal.ai) - Fast inference platform
*   [Fireworks](https://fireworks.ai) - Fast inference API
*   [Replicate](https://replicate.com) - Multi-modal generation
    *   [Collections](https://replicate.com/collections) - Organized model categories
    *   [Nano Banana](https://replicate.com/google/nano-banana) - Image-to-image model
    *   [Wan Video 2.5 I2V Fast](https://replicate.com/wan-video/wan-2.5-i2v-fast) - Budget video generation

### Data & Retrieval

*   [Firecrawl](https://www.firecrawl.dev) - Web to markdown
*   [LlamaIndex](https://www.llamaindex.ai) - Document processing
*   [Mistral](https://mistral.ai) - Document understanding
*   [Pinecone](https://www.pinecone.io) - Vector database
*   [Qdrant](https://qdrant.tech) - Vector search
*   [Ragie](https://www.ragie.ai) - RAG as a service
*   [Supermemory](https://supermemory.ai) - Managed RAG

### Cloud & Deployment

*   [Cloudinary](https://cloudinary.com) - AI-friendly media storage
*   [Google Cloud Platform](https://cloud.google.com) - Primary cloud
*   [Hugging Face Spaces](https://huggingface.co/spaces) - Rapid prototyping
*   [Modal](https://modal.com) - Serverless compute
*   [Netlify](https://www.netlify.com) - (Previously used)
*   [RunPod](https://www.runpod.io) - GPU on demand
*   [Vercel](https://vercel.com) - Serverless frontend

### Local AI

*   [AMD Radeon](https://www.amd.com/en/graphics/radeon-rx-graphics) - GPU hardware
*   [ComfyUI](https://github.com/comfyanonymous/ComfyUI) - Node-based Stable Diffusion interface
*   [LM Studio](https://lmstudio.ai) - Local model interface
*   [Meta Llama](https://ai.meta.com/llama/) - Open model family
*   [NVIDIA](https://www.nvidia.com) - Recommended GPU
*   [Ollama](https://ollama.com) - Local inference CLI
*   [rmbg](https://github.com/zhbhun/rmbg) - Background removal tool
*   [ROCm](https://www.amd.com/en/products/software/rocm.html) - AMD compute

### Automation

*   [n8n](https://n8n.io) - Visual automation

### Google Ecosystem

*   [AI Studio](https://aistudio.google.com) - Development environment
*   [Cloud Run](https://cloud.google.com/run) - Serverless containers
*   [NotebookLM](https://notebooklm.google.com) - Knowledge synthesis

### Self-Hosted & Open Source

*   [Open WebUI](https://github.com/open-webui/open-webui) - Self-hosted interface

### Honorable Mentions

*   [Discord](https://discord.com) - AI community platform
*   [Lumo](https://proton.me/ai) - Privacy-focused AI by Proton
*   [Reddit](https://www.reddit.com) - AI news and discussions
*   [Venice.ai](https://venice.ai) - Privacy-first AI platform