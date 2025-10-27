# AI Stack Documentation
### October 27, 2025

A point-in-time overview of my AI infrastructure, tools, and services for development, deployment, and production workflows.

> **Note**: This is not prescriptive. It's a snapshot of what I, as one person, see value in and my thoughts. Everybody is different. I update this roughly once a year, though the pace of evolution in this space is rapid enough that monthly updates would make sense.

## Why This Exists

Once or twice a year, usually around winter, I organize all my GitHub repositories - consolidating, deleting old ones, creating new ones. Part of this process is documenting my AI stack.

Friends and clients frequently ask: "With so much on the market, what do you think is good?" This document serves multiple purposes:

1. **Recommendations**: A reference for people looking to build their own AI stack
2. **Evolution tracking**: The AI space moves so rapidly you could version control your stack monthly. I note what I'm adding, dropping, and why I find something valuable
3. **Budget planning**: Transparency about what AI tooling actually costs at different levels

This is a fluid, evolving entity. The pace of evolution in AI is so rapid that this is truly a point-in-time snapshot.
 

## Core Infrastructure

### Large Language Models
The backbone of the entire AI stack, powering nearly every component and workflow.

**Primary Interfaces:**
- **CLI**: Claude Code (Pro: $17/month | Max: $100/month) - *The greatest thing I've found since ChatGPT*
- **GUI**: Claude interface (included with Claude Code subscription)
- **ChatGPT**: Day-to-day interface for general tasks
- **OpenAI**: API access and integrations

**Why Claude Code Has Been Transformative**:

After 20 years of using Linux, CLIs are second nature, but I've always preferred GUIs when available. Claude Code changed that completely.

When I started using Claude Code (along with Gemini CLI and CodeX), I immediately thought: "Why isn't there a bigger movement to use these things for local computer management?" There was a project called Open Interpreter that showed promise, but Claude Code goes beyond.

**What It Solves**:
Linux has gotten easier over time, but there's always been a list of things that don't quite work - bugs, things I wish I could do. For the first time ever, that list is nearly empty. Every time I have a problem now, I just say "Hey Claude, any chance you can figure out why..." or "create a shortcut for turning the screens on and off" - and it just works through all of those issues.

**Use Cases**:
- Local system administration
- Home lab management (I hate to call it a home lab because I never intended to get into home labbing, but here we are)
- Remote server fixes in record time
- Solving persistent Linux issues

I saw someone on Hugging Face say Claude Code has been the greatest thing they've found since ChatGPT. I felt validated because I've felt exactly the same way.

**Note on Self-Hosted Interfaces**: Previously used Open WebUI (self-hosted chat interface). Before becoming a father and getting busy, I reached the conclusion that there wasn't a compelling reason to deal with the hassle of things breaking and needing fixes. Simplicity and reliability won out over self-hosting.

**API Access:**
- **OpenRouter** (Primary recommendation): Unified API gateway for multiple LLM providers
  - *First thing I'd recommend beyond ChatGPT*
  - Direct vendor APIs available from all major providers
  - Frontend choice is virtually limitless - CLI, web apps, desktop apps, custom integrations

**Why OpenRouter Is Essential**:

I'm not always sure whether you get the same quality of inference as when using the vendor directly. For Claude specifically, it seems like best performance comes from Anthropic rather than using it through Winserf or OpenRouter. I assume there's a reason for that and it's not just my imagination. So there's always a case for first-party access.

But for someone looking to go beyond ChatGPT (which is actually why I jotted down these stack notes), OpenRouter would be one of the first things I'd recommend.

**Two Major Reasons**:

1. **Expense Consolidation** (often under-articulated):
   - When you have your own business and need to provide expenses to your accountant, one API bill is vastly easier than fragmented charges
   - Budgeting: Very easy to lose track when spending $20 here and there on different APIs
   - With OpenRouter: "This is my OpenRouter account. I set my spend limits here." Clear budget control.

2. **Model Exploration**:
   - Try out many different models without separate accounts
   - Example: I ran an evaluation today called "AI Brevity" (I'm frustrated by AI verbosity, and system prompts like "be super concise" don't help)
   - Ran the same prompt through 10 models using OpenRouter and a script
   - OpenRouter is the logical entry point because you've got all the models available and just change the model parameter

**What's Beyond the Big Names**:
There's a lot more than OpenAI, Anthropic, Gemini. It's interesting to keep an eye on:
- What's coming out of China
- What's emerging at the frontier of fine-tunable models
- Models that never make the news: IBM Granite, Amazon's models, Microsoft Phi
- Some of these are particularly good at instruction following

**Where This Really Matters**:
I find the most transformative and robust uses for LLMs right now are frequently just simple text transformations. For that, you don't need or want a very high-reasoning model. You want something that's just good at: "Okay, this is the system prompt, this is your task, go from A to B."

Accessing those models through serverless inference on demand is useful, but stack consolidation is always the order of the day. Having a mix of open-source and commercial models all through the same API is a big advantage.

> **Getting Started**: Set up an account on OpenRouter. Drop in $50 if you can afford it to have balance on hand and room to play around (they also offer some free inference). Whether you're self-hosting a chat interface like Open WebUI or looking for programmatic integration, this is where AI becomes exciting and cool - when you see that instructional AI and programmatic AI is very mature and brings independent value over chatbots.

> **Performance Note**: First-party vendor access (e.g., Anthropic for Claude) may provide better inference quality than routing through aggregators. For production workloads with specific models, consider direct vendor access.

**Model Context Protocol (MCP):**
- Smithery
- Github
- Context (for API documentation lookup)
- Firecrawl (covered in Data Retrieval section)

---

## Voice Applications

### Speech-to-Text (STT)

**Primary Services:**
- **Whisper** (via OpenAI API): Solid baseline, good value
  - Note: OpenAI's newer model hasn't shown significant improvement in my workloads
- **Browser-based tools** (e.g., Blabby): Convenient for quick tasks
- **OS-level integration tools**: For continuous dictation

**Specialized Services:**
- **AssemblyAI**: Long-form transcription with speaker diarization (used frequently)
  - Essential for meeting transcripts and AI minute extraction
  - Diarization is a foundational element for quality downstream processing
- **Deepgram**: Task-dependent usage
- **Speechmatics**: Advanced voice technology platform
- **Gladio**: Very solid performance
- **Lemonfox**: Budget-friendly option for cost-sensitive jobs

**API Aggregators:**
- **Eden AI**: Multi-provider API batching and management

> **Critical Learning**: Don't expect the STT tool you use for live transcription to work well for asynchronous jobs like meeting transcripts. There are significant performance differences within STT tools across synchronous vs. asynchronous workloads. Match the tool to the specific task requirements.

**Use Case Recommendations:**
- **Live/Real-time**: Whisper, browser tools, OS integration
- **Async/Long-form with speakers**: AssemblyAI, Speechmatics
- **Budget-conscious batch jobs**: Lemonfox
- **General reliability**: Gladio

### Text-to-Speech (TTS)

**Premium Option:**
- **ElevenLabs**: Best-in-class quality with excellent expressiveness
  - Drawback: Very expensive
  - Recommendation: Use when audio quality is critical

**Budget-Friendly Options:**
- **OpenAI TTS**: Good enough for majority of use cases
  - Lacks the expressiveness of ElevenLabs but significantly cheaper
  - Recommended for most projects unless premium audio is essential
- **Various alternative providers**: Available based on specific needs

**Budget Decision Framework:**
- **Quality-first budget**: ElevenLabs
- **Cost-conscious budget**: OpenAI TTS or OpenAI Mini

### Real-Time / Live Audio

Requires separate API subscriptions. Generally expensive but essential for live interaction use cases.

---

## Generative AI

### Multi-Modal Generation Platforms

**Primary Platforms:**
- **Replicate**: Absolutely brilliant for model exploration and API-based workflows
- **Fal**: Massively impressive, slightly more exposure to Chinese models from what I can see

**Why I'm Massively Impressed**:

Both platforms are absolutely brilliant. The value proposition is the same as OpenRouter but for generative AI.

**It's Not Just Convenience**:
Yes, it's convenient to run generative AI tasks like text-to-video using an API where you can just top up one account. But the real value is discovery and exploration:

- You can explore all the models they have available
- Discover capabilities you didn't even know existed: "Oh my gosh, I never knew there was even such a thing as audio inpainting. Wait, that exists?"
- Find companies and models you've never heard of
- Test them all out with one task before deciding which is best and committing hundreds of dollars to that workload

**The Staggering Pace of Innovation**:
I'm amazed by the pace at which new generative AI modalities and models are coming to market on these platforms. It's staggering. New capabilities appear constantly that I didn't even know were possible.

**Fal vs Replicate**:
I don't have majorly strong opinions about which is better. Fal has slightly more exposure to Chinese models. Both are excellent.

> **Philosophy**: Similar to OpenRouter for LLMs, these platforms provide consolidated access to rapidly evolving generative capabilities through a single API. The discovery aspect is just as valuable as the consolidation.

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

## Data Retrieval & Processing

### Internal Data (RAG)
Retrieval-Augmented Generation for working with proprietary datasets and knowledge bases.

**RAG-as-a-Service:**
- **Ragie**: RAG as a service via API
- **Supermemory**: Philosophy of "don't build your own RAG pipeline"

**Why Not DIY RAG**:
Unless you have enterprise-level document stores, building RAG from scratch (Pinecone, Qdrant, custom embeddings, chunking strategies, vector sizes) is often not a good use of time. Services like Supermemory and memory layer tools handle this complexity, allowing developers to focus on "grounding AI in a few documents" rather than becoming retrieval engineers.

> **Philosophy**: For most developers not working at massive scale, managed RAG services prevent hours of setup and configuration for relatively simple document retrieval tasks.

### External Data

**Firecrawl**: Web scraping and data extraction

There's a whole world of MCP tools that are really useful, and Firecrawl is one I have to note here.

**Why Markdown Matters**:
Markdown is just such a useful format for AI workloads. The ability to quickly say, "Okay, these are the API docs for something that you can clearly see you're struggling with" is powerful.

There's Context, which is a great MCP for this. But sometimes I can see exactly what Claude needs: "Oh wait, I need this in Markdown." Having one tool that you know can do this over and over reliably is extremely useful.

**The Power of Model Definitions**:
Being able to define the models for scraping is a great feature. It makes the extraction much more targeted and useful.

**Why "Scraping" Shouldn't Be a Dirty Word**:

I think scraping is almost a bad word and a dirty word because people immediately assume it's spammy and illegal or whatever. But I've often used these tools to scrape my own stuff.

**Real Use Case**:
If I have notes - "Oh, I wrote these notes a few years ago" - I can just use Firecrawl to pull this in. It's actually quicker to do that than to go back through my Google Drive from four years ago and then format that in Markdown.

**Versatility**:
So it's useful across multiple domains:
- Pulling your own historical content
- Quick API documentation lookup via MCP
- Converting web content to AI-friendly formats
- Retrieving notes from various platforms

> **Philosophy on Scraping**: Despite negative connotations, web scraping tools are incredibly useful for retrieving your own content, documentation, and notes from various platforms for AI processing. It's a legitimate productivity tool, not just for questionable use cases.

### Document Processing & OCR
- **Mistral**: Document understanding
- **LlamaIndex**: Document processing and indexing

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
- **Google Cloud Platform (GCP)**: Primary cloud provider

### Deployment Platforms
- **On-server**: Self-hosted deployments
- **Vercel**: Serverless frontend deployments
  - Recently migrated from Netlify
  - More AI-forward feature set
  - Environment variable sharing across projects is excellent

### Hardware On-Demand / Serverless
- **RunPod**: GPU compute on demand
- **Modal**: Serverless compute platform

### Prototyping & Lightweight Execution
- **Hugging Face Spaces**: Rapid prototyping and lightweight app hosting
  - Supports private deployments
  - Excellent for quick experiments

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
- **LM Studio**: GUI interface for local models
- **Ollama**: CLI-based local inference

### Hardware
- **High-performance GPU** for local model inference
  - Current: AMD Radeon (ROCm-compatible)
  - **Recommendation**: Go with NVIDIA GPU for fewer compatibility issues
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
  - Models like Meta Llama 3.1 for text transformation tasks

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

## Automation & Workflows

### Automation Pipelines
- **N8N**: Visual workflow automation

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

## Google Ecosystem

**Integrated Services:**
- **NotebookLM**: Free with Google Workspace - **Favorite tool** for research and knowledge synthesis
- **Gemini**: Free with Google Workspace
- **AI Studio**: Development environment
- **AI Studio + Cloud Run**: Production deployments (API costs apply)

### NotebookLM: The Standout Tool

**Why It's Reached Maturity:**
- Originally limited to 10 sources; now much more capable
- Excellent at assembling building blocks: retrieval → questions → generation based on retrieval
- Alternative to LlamaIndex for many use cases, but much simpler

**Perfect Use Case - Deliberate Context Generation:**

I realized NotebookLM is actually perfect for a pattern I've been working on for a while. I was going to call it "AI, I have a problem" - which I realized is probably not the best marketing name I've ever come up with.

**The Pattern & Real Example**:

The pattern addresses this: when you have a problem to solve that's not just asking for a pasta recipe, but something personal and ongoing.

**Real Example - Health Context**:
I had gallbladder surgery a number of years ago. Since then, I've had really bad issues with all manner of digestion - bloating, nausea, you name it. I don't really enjoy narrating the whole story every time I need help with meal planning or dietary advice.

**The Solution**:
1. Record the context once (30-minute voice note covering everything comprehensively)
2. Transform to text
3. Use as workspace foundation in NotebookLM
4. Now I can get shopping lists that are better for me, recipes tailored to my needs - all without repetitively defining context

**Why This Is Powerful**:
When you're working on a few of these "problems" (health, project planning, personal circumstances), you really see the advantage of this approach over time, as opposed to repetitively defining context every single time.

**Two Approaches to Context:**
1. **OpenAI's approach**: Chat first, AI extracts memories to memory layer over time
2. **My approach**: Generate deliberate context upfront through structured recording

I'm not saying OpenAI's approach is wrong or mine is better - I'm just saying it's a different method for tackling the same question: How can we make AI much more useful when it's personalized to you and your particular life circumstances? How can we engineer that?

**Significant Advantage Over Repetitive Context**:
There's another significant advantage to this approach beyond just not repeating yourself. I've done some modeling in interview-first context generation, or what I've called "deliberate context generation."

**Why I'm a Big Fan of Voice Workflows**:
I can record a voice note like this and in 30 minutes gather a huge amount of information. Put that into a little transformation (extracting the context data from that), and then that's the starting context.

**Working in Reverse**:
It's really working in reverse to the way OpenAI is doing it. They have you chat with ChatGPT, and then over time it learns things about you and extracts that to a memory layer. This is working backwards.

**Experimental Variations**:
- **Basic one**: Just speak for 30 minutes into a microphone
- **Slightly jazzier one**: A bot asks me questions like a model interview
- That workflow has actually worked very well - what I'm doing here with this stack documentation is exactly that: the bot came up with questions, and I can speak for 30 minutes. That's my context data.

> **Why This Works**: AI is significantly more useful when personalized to your life circumstances. This pattern engineers that personalization deliberately rather than hoping it emerges from conversation. You're creating rich, comprehensive context in a single focused session.

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

## Key Insights & Philosophy

### The Most Transformative Use Cases

**Simple Text Transformations Are Underrated**:
The most transformative and robust uses for LLMs are frequently simple text transformations. For these tasks:
- You don't need high-reasoning models
- You want excellent instruction-following capability
- Models like IBM Granite, Microsoft Phi excel here
- Cost-effective, reliable, practical

> **Example**: Running evaluations across 10+ models to find which handles "AI Brevity" best (avoiding verbose outputs that resist system prompting)

**Programmatic AI > Chatbots**:
Where AI becomes truly exciting is in programmatic integration and instructional AI, not just chatbots. This brings independent value through automation, batch processing, and system integration.

### Architecture Philosophy

This AI stack is designed around several core principles:

1. **Flexibility**: Multiple options for each capability (premium vs. budget, cloud vs. local)
2. **Task-Appropriate Tooling**: Different tools for different workload types (sync vs. async, batch vs. real-time)
3. **Security Tiers**: Options ranging from cloud APIs to fully air-gapped local inference
4. **Cost Optimization**: Balance between premium services and cost-effective alternatives
5. **Developer Experience**: Strong emphasis on CLI tools and automation pipelines
6. **Stack Consolidation**: Minimize API fragmentation through unified platforms (OpenRouter, Replicate, Fal)
7. **Expense Management**: Practical consideration for accounting and budgeting (important for business use)

---

**Last Updated**: October 27, 2025