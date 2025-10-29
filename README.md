# Hack Hour: Agent Bricks Foundry 🤖

Welcome to the **Agent Bricks Foundry** - your comprehensive guide to building AI agents in Databricks! This repository contains hands-on lab guides that will take you from zero to production-ready AI agents.

## 🎯 What You'll Learn

Build intelligent Q&A agents powered by Databricks AI that can:
- Answer questions from your document knowledge base
- Provide accurate responses with source citations
- Handle multi-turn conversations
- Deploy to production with built-in monitoring

## 📚 Available Labs

### Lab 1: Low-Code Agent Creation (No Coding Required!) ✨

**File:** [`Lab1_QA_Agent_with_Databricks.md`](./Lab1_QA_Agent_with_Databricks.md)

**Perfect for:** Business analysts, product managers, and anyone who wants to create AI agents without writing code.

**What you'll build:** An HR Q&A agent that answers employee questions about benefits, policies, and workplace information.

**Key Features:**
- ✅ 100% UI-based workflow - no Python or SQL required
- ✅ Upload PDFs through visual interface
- ✅ Automatic document processing and embedding
- ✅ Built-in testing and quality improvement tools
- ✅ One-click deployment to production
- ✅ Shareable agent interface

**Time to complete:** 45-60 minutes

**What you'll use:**
- Databricks Agent Builder (UI)
- Unity Catalog Volumes (drag-and-drop)
- Knowledge Assistant template
- Vector Search (automatic)
- Improve Quality with labeling sessions

---

### Lab 2: Pro-Code Agent Development (Coming Soon) 💻

**File:** `Lab2_Advanced_Agent_Development.md` *(Work in Progress)*

**Perfect for:** Data scientists, ML engineers, and developers who want full control and customization.

**What you'll build:** A customized agent with advanced features like custom tools, complex RAG pipelines, and API integrations.

**Key Features:**
- ✅ Python SDK for agent creation
- ✅ Custom document processing pipelines
- ✅ Advanced retrieval strategies
- ✅ Custom tool integration
- ✅ Fine-tuning and optimization
- ✅ CI/CD deployment workflows

**Time to complete:** 2-3 hours

**What you'll use:**
- Databricks Python SDK
- LangChain / LlamaIndex
- MLflow for tracking
- Custom vector search configurations
- Advanced prompt engineering

---

## 🚀 Getting Started

### Prerequisites

Before starting any lab, ensure you have:

1. **Databricks Workspace Access**
   - Azure Databricks workspace (or AWS/GCP)
   - Compute resources enabled
   - Unity Catalog enabled

2. **Permissions**
   - Create and manage schemas
   - Create and manage volumes
   - Create agents
   - Access foundation models

3. **Sample Data** (Provided)
   - HR documents in the `data/` folder
   - 6 PDF files covering employee benefits and policies

### Choose Your Path

#### 🎨 **I want to build quickly without coding**
→ Start with **Lab 1: Low-Code Agent Creation**
- Perfect for rapid prototyping
- Production-ready in under an hour
- Visual tools and templates

#### 💻 **I need advanced customization and control**
→ Start with **Lab 2: Pro-Code Agent Development** *(Coming Soon)*
- Full programmatic control
- Custom integrations
- Advanced ML workflows

#### 🔄 **I want both!**
→ Start with Lab 1 to understand the concepts, then move to Lab 2 for advanced features

---

## 📁 Repository Structure

```
hackhour-agentbricks-foundry/
│
├── README.md                              # This file
├── Lab1_QA_Agent_with_Databricks.md      # Low-code agent creation guide
├── Lab2_Advanced_Agent_Development.md    # Pro-code guide (coming soon)
│
└── data/                                  # Sample documents
    ├── employee_handbook.pdf
    ├── Benefit_Options.pdf
    ├── Northwind_Health_Plus_Benefits_Details.pdf
    ├── Northwind_Standard_Benefits_Details.pdf
    ├── PerksPlus.pdf
    └── role_library.pdf
```

---

## 🎓 Learning Objectives

By completing these labs, you will:

### Core Skills
- ✅ Understand RAG (Retrieval-Augmented Generation) architecture
- ✅ Work with Unity Catalog for data governance
- ✅ Configure vector search and embeddings
- ✅ Deploy and monitor production AI agents
- ✅ Implement quality improvement workflows

### Low-Code Path (Lab 1)
- ✅ Use Databricks Agent Builder UI
- ✅ Configure agents with visual tools
- ✅ Test and evaluate without code
- ✅ Share agents with stakeholders

### Pro-Code Path (Lab 2)
- ✅ Use Databricks Python SDK
- ✅ Customize document processing
- ✅ Implement advanced retrieval strategies
- ✅ Build custom tools and integrations
- ✅ Optimize for performance and cost

---

## 💡 Use Cases

These labs can be adapted for various domains:

**Customer Support:**
- Product documentation Q&A
- Troubleshooting guides
- FAQ automation

**Enterprise Knowledge Management:**
- Internal policy documents
- Compliance and regulatory information
- Training materials

**Healthcare:**
- Medical procedure guidelines
- Patient education materials
- Research paper summarization

**Legal:**
- Contract analysis
- Case law research
- Regulatory compliance

**Finance:**
- Investment research
- Financial policy documentation
- Regulatory filings

---

## 🛠️ Technologies Used

### Databricks Platform
- **Agent Builder** - Visual agent creation
- **Unity Catalog** - Data governance and management
- **Vector Search** - Semantic search and retrieval
- **Model Serving** - Production deployment
- **Foundation Models** - Pre-trained LLMs

### AI/ML Components
- **Embeddings** - databricks-bge-large-en
- **LLM** - Meta Llama 3.1 70B Instruct (or your choice)
- **RAG Pipeline** - Automatic chunking and retrieval
- **Evaluation** - Built-in quality metrics

### Data Management
- **Unity Catalog Volumes** - Document storage
- **Delta Lake** - Vector index storage
- **Schemas** - Logical data organization

---

## 📖 Additional Resources

### Documentation
- [Databricks Agent Builder Documentation](https://docs.databricks.com/en/generative-ai/agent-builder.html)
- [Unity Catalog Guide](https://docs.databricks.com/en/data-governance/unity-catalog/index.html)
- [Vector Search Documentation](https://docs.databricks.com/en/generative-ai/vector-search.html)
- [Model Serving Guide](https://docs.databricks.com/en/machine-learning/model-serving/index.html)

### Tutorials
- [RAG Fundamentals](https://docs.databricks.com/en/generative-ai/tutorials/ai-cookbook/rag-fundamentals.html)
- [Agent Evaluation](https://docs.databricks.com/en/generative-ai/agent-evaluation/index.html)
- [Foundation Models on Databricks](https://docs.databricks.com/en/machine-learning/foundation-models/index.html)

### Community
- [Databricks Community Forums](https://community.databricks.com/)
- [Databricks Blog](https://www.databricks.com/blog)
- [Databricks YouTube Channel](https://www.youtube.com/@Databricks)

---

## 🤝 Contributing

Have improvements or additional labs to suggest? Contributions are welcome!

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📝 License

This project is provided as-is for educational purposes.

---

## 🏆 What's Next?

After completing the labs:

1. **Build Your Own Agent**
   - Use your organization's documents
   - Customize for your specific use case
   - Deploy to your stakeholders

2. **Explore Advanced Features**
   - Multi-turn conversation memory
   - Custom tools and APIs
   - Guardrails and content filtering
   - Cost optimization strategies

3. **Scale to Production**
   - Monitor usage and performance
   - Collect user feedback
   - Iterate and improve
   - Integrate with existing workflows

---

## 💬 Feedback

Found an issue or have suggestions? Please open an issue in this repository!

---

**Happy Building! 🚀**

*Created for Databricks Hack Hour - Agent Bricks Foundry*
