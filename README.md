# 🧠 OpenWebUI + Ollama — Enterprise AI Assistant Deployment Agent

> **Transform any Windows PC into a secure, private ChatGPT-like AI assistant**  
> One-click PowerShell deployment agent for local AI. No API keys. No monthly fees.

---

## 🧠 AI Agent Architecture

```mermaid
graph TB
    subgraph USER["👤 User Layer"]
        U1[Employee Chat\nWeb Interface]
        U2[Docker Terminal\nAdmin Access]
        U3[Browser Access\nlocalhost:3000]
    end

    subgraph DEPLOY["🤖 Deployment Agent"]
        D1[PowerShell\nSetup Script Agent]
        D2[Docker Compose\nGenerator Agent]
        D3[Model Pull\nOrchestrator Agent]
        D4[Health Check\nVerification Agent]
    end

    subgraph INFRA["🔧 Infrastructure Agents"]
        I1[Docker Desktop\nContainer Runtime]
        I2[OpenWebUI Service\nChat Frontend Agent]
        I3[Ollama Service\nModel Host Agent]
    end

    subgraph MODELS["🧠 Model Agents"]
        M1[LLaMA 3\nGeneral Purpose]
        M2[Mistral\nEfficient Agent]
        M3[Gemma\nLightweight Agent]
        M4[Phi-3\nResearch Agent]
        M5[CodeLlama\nCoding Agent]
    end

    U1 --> U3
    U3 --> D1
    D1 --> D2
    D2 --> D3
    D3 --> D4
    D4 --> I1
    I1 --> I2
    I1 --> I3
    I3 --> M1
    I3 --> M2
    I3 --> M3
    I3 --> M4
    I3 --> M5
    M1 --> I2
    M2 --> I2
    M3 --> I2
    M4 --> I2
    M5 --> I2
    I2 --> U1

    style D1 fill:#4CAF50,stroke:#333,color:#fff
    style I2 fill:#2196F3,stroke:#333,color:#fff
    style I3 fill:#FF9800,stroke:#333,color:#fff
    style M1 fill:#9C27B0,stroke:#333,color:#fff
```

## 🤖 What Makes This an AI Agent Platform

| Agent | Function |
|-------|----------|
| **PowerShell Deployment Agent** | One-click script: creates project folder, generates docker-compose.yml, pulls LLM models |
| **Docker Compose Generator Agent** | Auto-generates the entire container stack configuration |
| **Model Orchestrator Agent** | Pulls and manages multiple LLM models — switch between them at will |
| **Health Check Agent** | Verifies OpenWebUI + Ollama are running and responsive |
| **Chat Frontend Agent** | OpenWebUI provides ChatGPT-style interface with model switching |

## 🔄 Before vs After

```mermaid
graph LR
    subgraph BEFORE["❌ Before"]
        BM[Public ChatGPT\nData sent to cloud\n$20/user/month\nNo customization]
    end

    subgraph AFTER["✅ After (AI Agent)"]
        AM[Private local AI\n100% data privacy\n$0/user/month\nAny open model\nFull control]
    end

    BM -->|Deployment Agent| AM
```

## 🛠 Tech Stack

| Component | Technology | Agent Role |
|-----------|-----------|------------|
| **Chat UI** | OpenWebUI | Front-end agent |
| **LLM Runtime** | Ollama | Model hosting agent |
| **Infrastructure** | Docker + Docker Compose | Container orchestration |
| **Deployment** | PowerShell | Setup automation agent |

## ⚡ Quick Start

```powershell
# Run the deployment agent
.\setup-openwebui-ollama.ps1

# Visit http://localhost:3000
```

## 🎯 Supported AI Models

| Model | Use Case | Size |
|-------|----------|------|
| LLaMA 3 | General purpose chat | 8B |
| Mistral | Efficient, fast responses | 7B |
| Gemma | Lightweight, Google research | 7B |
| Phi-3 | Microsoft research model | 3.8B |
| CodeLlama | Code generation & analysis | 7B |

---

Built by **[Shazaly Musa](https://github.com/SparkSpheartech)** — Founder, SparkSphear Tech  
*AI Agents for Local Enterprise AI Deployment*