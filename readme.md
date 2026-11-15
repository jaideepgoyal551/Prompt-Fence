# PromptFence 🛡️
### Secure AI Infrastructure & Enterprise AI Security Platform

**Protect AI applications. Secure enterprise knowledge. Control AI execution.**

PromptFence is an AI security and infrastructure platform designed to help businesses build, deploy, and manage secure AI-powered applications.

It combines an intelligent AI security firewall, enterprise knowledge management, Retrieval-Augmented Generation (RAG), and a secure AI API gateway into one unified platform.

Businesses can connect their own knowledge bases, configure custom AI instructions, integrate LLM providers such as Gemini and OpenAI, and expose secure AI endpoints to their customers — while PromptFence monitors and protects AI interactions against prompt injection, sensitive data leakage, and unauthorized tool execution.

---

## 🚀 Vision

As organizations increasingly integrate AI into their products and workflows, security and data privacy have become critical challenges.

Traditional AI integrations often lack centralized security controls, enterprise-specific knowledge isolation, and reliable protection against malicious inputs.

PromptFence aims to solve these challenges by providing a security layer between users, enterprise applications, and AI models.

**Our vision is to make secure AI adoption accessible to every organization.**

---

## ✨ Core Features

### 1. AI Security Firewall

An intelligent security layer that analyzes AI interactions and helps prevent malicious instructions and unauthorized operations.

- **Prompt Injection Detection:** Identify malicious instructions in user prompts and external content.
- **Context Trust Analysis:** Distinguish trusted system instructions from untrusted documents and retrieved content.
- **Risk Scoring:** Assign risk scores to suspicious prompts and AI actions.
- **Security Decisions:** Allow, sanitize, require approval, or block suspicious requests.
- **Security Auditing:** Maintain detailed records of security events and decisions.

### 2. Enterprise Knowledge Hub

Enable organizations to create their own AI-powered knowledge assistants using internal company data.

- Upload company documents in PDF, DOCX, and TXT formats.
- Automatically extract and process document content.
- Split documents into smaller semantic chunks.
- Generate vector embeddings.
- Store embeddings in isolated company-specific vector collections.
- Retrieve relevant information using semantic similarity search.
- Generate context-aware answers using connected LLM providers.
- Configure custom instructions and company-specific AI behavior.

**Example:** An e-commerce company can upload its product catalog, warranty policies, FAQs, and documentation. Its customers can then interact with an AI assistant that answers questions using the company's knowledge base.

### 3. Secure AI API Gateway

Allow businesses to integrate their configured AI assistants into their own applications.

- Generate secure API keys for company workspaces.
- Provide company-specific AI endpoints.
- Support Gemini and OpenAI model integrations.
- Authenticate and authorize incoming API requests.
- Apply rate limiting and usage controls.
- Enforce security checks before forwarding requests to AI providers.
- Track API requests, token usage, and operational metrics.

Developers can integrate PromptFence without building their own complete AI security infrastructure.

### 4. Data Loss Prevention (DLP)

Protect sensitive information throughout AI interactions.

- Detect exposed API keys and credentials.
- Identify passwords, tokens, and sensitive information.
- Scan incoming prompts and outgoing AI responses.
- Redact sensitive information where appropriate.
- Prevent unauthorized disclosure of confidential data.

### 5. AI Tool Execution Firewall

Control the actions AI agents are allowed to perform.

- Intercept AI tool execution requests.
- Validate tool permissions before execution.
- Block unauthorized operations.
- Support approval-based execution for sensitive actions.
- Maintain an audit trail of tool calls and security decisions.

### 6. Security Monitoring & Analytics

A centralized dashboard for monitoring AI application security.

- Total requests processed.
- Threats detected and blocked.
- Prompt injection attempts.
- Sensitive data exposure incidents.
- API usage and token consumption.
- Risk distribution and security event timelines.
- Detailed incident reports and audit logs.

---

## 🏗️ System Architecture

```text
                    CLIENT APPLICATIONS
                 Web Apps | Mobile Apps | APIs
                            |
                            v
                  PROMPTFENCE API GATEWAY
                            |
              Authentication & Rate Limiting
                            |
                            v
                 AI SECURITY FIREWALL
                            |
             +--------------+--------------+
             |              |              |
             v              v              v
        Prompt          DLP Engine      Risk Engine
        Analyzer        & Redaction     & Policy Engine
             |              |              |
             +--------------+--------------+
                            |
                            v
                ENTERPRISE KNOWLEDGE HUB
                            |
                 Document Processing
                            |
                   Text Extraction
                            |
                     Chunking
                            |
                     Embeddings
                            |
                            v
                    QDRANT VECTOR DB
                            |
                  Semantic Retrieval
                            |
                            v
                  CONTEXT CONSTRUCTION
                            |
                            v
                   LLM INTEGRATION
                    /           \
                   v             v
                GEMINI         OPENAI
                   \             /
                    \           /
                     v         v
                   RESPONSE VALIDATION
                            |
                  Security Policy Checks
                            |
                            v
                    FINAL RESPONSE
                            |
                            v
                     END USER
```

*The architecture represents the proposed system design. Security validation and tool authorization are enforced independently of LLM-generated decisions.*

---

## 🔄 Enterprise RAG Workflow

PromptFence uses Retrieval-Augmented Generation (RAG) to provide company-specific AI responses.

**Document ingestion:**

1. A company uploads its internal documents.
2. The backend extracts text from uploaded files.
3. Extracted content is divided into smaller chunks.
4. An embedding model converts chunks into vector representations.
5. Vectors and associated metadata are stored in Qdrant.
6. Each company's data is isolated using workspace-level access controls.

**Query processing:**

1. A customer sends a question through the company's AI API endpoint.
2. PromptFence authenticates the API request.
3. The security firewall analyzes the incoming content.
4. The RAG engine generates an embedding for the question.
5. Qdrant retrieves relevant company-specific information.
6. Retrieved content is checked and treated as untrusted external context.
7. The system combines relevant information with authorized custom instructions.
8. The configured LLM generates a response.
9. The response passes through security and sensitive-data checks.
10. The final answer is returned to the customer.

If relevant information is unavailable, the assistant can be configured to avoid unsupported answers and indicate that the knowledge base does not contain the requested information.

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React.js, Tailwind CSS |
| Backend | Node.js, Express.js |
| Security Engine | Python, FastAPI |
| AI Integration | Gemini API, OpenAI API |
| Embeddings | Gemini / OpenAI Embedding Models |
| Vector Database | Qdrant |
| Relational Database | PostgreSQL |
| Caching & Rate Limiting | Redis |
| Document Processing | PyMuPDF |
| Authentication | JWT |
| Real-time Communication | Socket.IO |
| Containerization | Docker |

---

## 🔐 Security Architecture

Security is a fundamental part of PromptFence rather than an additional feature.

Key security considerations include:

- **Workspace Isolation:** Prevent unauthorized cross-company access to documents and vector data.
- **API Key Protection:** Store provider credentials securely using encryption and never expose secret keys to frontend clients.
- **Request Authentication:** Validate API credentials before processing requests.
- **Prompt Injection Defense:** Analyze malicious instructions in user inputs and retrieved documents.
- **Data Loss Prevention:** Inspect sensitive information in AI inputs and outputs.
- **Tool Authorization:** Enforce server-side permissions before executing AI-requested actions.
- **Audit Logging:** Maintain traceable records of security decisions and API activity.
- **Rate Limiting:** Protect endpoints against excessive requests and abuse.

---

## 📂 Proposed Project Structure

```text
PromptFence/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── dashboard/
│   │   ├── services/
│   │   └── hooks/
│   └── package.json
│
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── services/
│   │   ├── models/
│   │   ├── config/
│   │   └── utils/
│   └── package.json
│
├── security-engine/
│   ├── analyzers/
│   ├── prompt_injection/
│   ├── dlp/
│   ├── risk_engine/
│   ├── policy_engine/
│   ├── document_scanner/
│   └── main.py
│
├── docker/
│
├── docs/
│
├── tests/
│
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## 🗺️ Development Roadmap

### Phase 1 — Core Security Infrastructure
- [ ] Set up frontend and backend architecture.
- [ ] Implement authentication and workspace management.
- [ ] Develop prompt injection detection.
- [ ] Implement risk scoring and security policies.
- [ ] Build sensitive data detection.

### Phase 2 — Enterprise Knowledge Hub
- [ ] Implement document upload and processing.
- [ ] Develop text extraction and chunking pipelines.
- [ ] Integrate embedding generation.
- [ ] Configure Qdrant vector storage.
- [ ] Implement company-specific RAG.
- [ ] Add custom AI instructions.

### Phase 3 — AI API Gateway
- [ ] Integrate Gemini and OpenAI APIs.
- [ ] Implement company-specific AI endpoints.
- [ ] Generate and manage API keys.
- [ ] Implement rate limiting and usage tracking.
- [ ] Add secure request and response validation.

### Phase 4 — Advanced Security
- [ ] Implement AI tool execution firewall.
- [ ] Add approval-based tool permissions.
- [ ] Improve prompt injection detection.
- [ ] Implement security audit logs.
- [ ] Add advanced threat analytics.

### Phase 5 — Deployment & Testing
- [ ] Containerize services using Docker.
- [ ] Implement integration testing.
- [ ] Evaluate detection accuracy and false-positive rates.
- [ ] Test multi-tenant isolation.
- [ ] Deploy the application.
- [ ] Prepare security demonstrations.

---

## 🎯 Target Users

PromptFence is designed for:

- AI-powered startups.
- Enterprises adopting generative AI.
- SaaS companies building AI assistants.
- Backend developers integrating LLM APIs.
- Organizations managing sensitive internal knowledge.
- Developers building AI agents and RAG applications.

---

## 💡 What Makes PromptFence Different?

Instead of offering only an AI chatbot or an isolated prompt scanner, PromptFence combines multiple capabilities into one platform:

| Capability | Purpose |
|---|---|
| AI Security Firewall | Protect AI interactions |
| Enterprise RAG | Generate company-specific answers |
| AI API Gateway | Simplify secure AI integration |
| Data Loss Prevention | Protect sensitive information |
| Tool Execution Firewall | Control AI agent actions |
| Security Analytics | Monitor and investigate threats |

The goal is to provide businesses with a unified platform where they can build, integrate, and monitor secure AI applications without independently implementing every security component.

---

## 🚀 Getting Started

The following setup will be supported as the project is implemented.

**Prerequisites**

- Node.js
- Python 3.11+
- PostgreSQL
- Redis
- Docker
- Qdrant
- Gemini or OpenAI API credentials

**Clone the repository**

```bash
git clone https://github.com/YOUR_USERNAME/PromptFence.git

cd PromptFence
```

**Install frontend dependencies**

```bash
cd frontend
npm install
```

**Install backend dependencies**

```bash
cd ../backend
npm install
```

**Install security engine dependencies**

```bash
cd ../security-engine
pip install -r requirements.txt
```

**Configure environment variables**

Create `.env` files using the provided `.env.example` templates.

Never commit API keys, database passwords, or other secrets to GitHub.

**Run the application**

The development services will be started through their respective development commands and Docker Compose configuration.

*Note: Setup commands and deployment instructions will be finalized as implementation progresses.*

---

## 📊 Project Status

**Development Status:** Planned / In Development

PromptFence is being designed as a modular AI security and enterprise infrastructure platform. Features will be marked complete as they are implemented, integrated, and tested.

---

## 🔮 Future Scope

- Multi-LLM provider support.
- Developer SDK for Node.js and Python.
- Advanced AI agent security.
- Automated security policy recommendations.
- Enterprise role-based access control.
- Organization-level usage and billing management.
- Advanced attack simulation and security testing.
- Integration with enterprise identity providers.

---

## 👥 Team

Built by a team focused on backend engineering, artificial intelligence, and cybersecurity innovation.

---

## 📜 License

To be decided.

---

**PromptFence — Making AI Applications Secure, Reliable, and Enterprise-Ready.**
