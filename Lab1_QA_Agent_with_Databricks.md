# Lab 1: Building a Q&A Agent with Databricks Agent Bricks (UI-Based / No-Code)

> 🎯 **100% UI-Based Lab**: This lab uses the Databricks Agents UI exclusively. No Python coding required!

## Overview
In this lab, you will learn how to create an intelligent Question & Answer agent using **Databricks Agents UI** with **zero coding**. Using Databricks' intuitive point-and-click interface and built-in wizards, you'll build a production-ready RAG (Retrieval Augmented Generation) agent that can answer questions about your organization's documents. 

The agent will automatically process PDF documents including employee handbooks, benefits information, and role descriptions, and provide accurate, context-aware answers to user questions.

## Learning Objectives
By the end of this lab, you will be able to:
- 🖱️ Navigate the **Databricks Agents UI** to create agents visually
- 📁 Upload and manage PDF documents through **Unity Catalog Volumes UI**
- 🔍 Configure **Vector Search** automatically using the wizard
- 🤖 Build a **Q&A agent** using the **Agent Builder visual interface**
- ✅ Test and evaluate your agent in the **built-in Playground**
- 🚀 Deploy your agent to production with **one-click deployment**
- 📊 Monitor agent performance through the **Analytics Dashboard**

## Prerequisites
- Access to a Databricks workspace (AWS, Azure, or GCP)
- Databricks Runtime 14.3 LTS or higher
- PDF documents for your knowledge base (provided in this repo)
- **No coding experience required!**

## Lab Architecture
```
📄 PDF Documents 
    ↓ (Upload via UI)
📁 Unity Catalog Volume 
    ↓ (Auto-processing)
🔍 Vector Search Index 
    ↓ (Configured in Agent Builder UI)
🤖 Agent Builder UI 
    ↓ (One-click creation)
💬 Q&A Agent (Ready to deploy!)
```

## ⚙️ What Happens Behind the Scenes (All Automatic!)
When you use the Agent Builder UI, Databricks automatically:
- ✨ Extracts text from your PDFs
- ✨ Chunks documents into searchable pieces
- ✨ Generates embeddings using foundation models
- ✨ Creates and syncs a vector search index
- ✨ Configures the RAG pipeline
- ✨ Sets up the LLM and retrieval logic

**You just point, click, and configure!**

---

## Step 1: Access Databricks and Navigate to Agents (5 minutes)

> 🎯 **Goal**: Find and open the Databricks Agents UI interface

### 1.1 Log into Databricks

1. Open your web browser and navigate to your Databricks workspace URL
2. Log in with your credentials
3. You should see the Databricks workspace home page

### 1.2 Navigate to the Agents Interface

1. On the left sidebar, look for one of these options:
   - **"Generative AI"** → **"Agents"** (newer workspaces)
   - **"Machine Learning"** → **"Agents"** (some workspaces)
   - Or search for **"Agents"** in the top search bar

2. Click on **"Agents"** to open the Agents dashboard
3. You'll see the Agents dashboard with options to create new agents

> 💡 **Can't find Agents?** Make sure your workspace has Databricks Runtime 14.3+ and Generative AI features enabled. Contact your workspace admin if needed.

### 1.3 Understand the Interface

The Agents dashboard shows:
- **Your existing agents** (if any)
- **"Create Agent"** button (top right)
- **Templates** for common agent types
- **Recent agent activity**

---

## Step 2: Upload Documents Using Unity Catalog Volumes (10 minutes)

> 🎯 **Goal**: Upload your PDF documents to a Unity Catalog Volume using the UI

### 2.1 Create a Unity Catalog Volume

1. In the left sidebar, click on **"Catalog"**
2. Navigate to your catalog (e.g., `main`) or create a new one
3. Create or select a schema (e.g., `agent_lab`)
4. Click on the **"+ Create"** button and select **"Volume"**
5. Name your volume: `hr_documents_volume`
6. Select **"External"** or **"Managed"** based on your preference
7. Click **"Create"**

### 2.2 Upload PDF Files via UI

1. Click on the newly created volume `hr_documents_volume`
2. Click the **"Upload Files"** button
3. Drag and drop or browse to upload all your PDF files:
   - `employee_handbook.pdf`
   - `Benefit_Options.pdf`
   - `Northwind_Health_Plus_Benefits_Details.pdf`
   - `Northwind_Standard_Benefits_Details.pdf`
   - `PerksPlus.pdf`
   - `role_library.pdf`

4. Wait for the upload to complete (you'll see a progress indicator)
5. Verify all 6 files are uploaded successfully

**✅ Checkpoint**: You should now see all 6 PDF files listed in your volume

---

## Step 3: Use the Agent Builder Wizard (15 minutes)

> 🎯 **Goal**: Create your Q&A agent using the visual Agent Builder interface

### 3.1 Start Creating a New Agent

1. Navigate back to **Generative AI** → **Agents**
2. Click the **"Create Agent"** button (usually in the top-right corner)
3. You'll see several template options:
   - **Document Q&A Agent** ← Select this one!
   - Code Assistant Agent
   - Custom Agent (blank template)
4. Click **"Use Template"** or **"Get Started"** on the Document Q&A Agent card

> 📝 **Why this template?** The Document Q&A template is pre-configured for RAG-based question answering, which is perfect for our HR documents use case.

### 3.2 Configure Agent Basic Information

In the Agent Builder wizard, fill in:

1. **Agent Name**: `HR_QA_Agent`
2. **Description**: `Answers questions about employee benefits, policies, and company roles`
3. **Catalog**: Select `main` (or your catalog)
4. **Schema**: Select `agent_lab` (or your schema)
5. Click **"Next"**

### 3.3 Configure Document Source

1. **Data Source Type**: Select **"Unity Catalog Volume"**
2. **Volume Path**: Browse and select your volume:
   - `main.agent_lab.hr_documents_volume`
3. **File Types**: Ensure **PDF** is checked
4. **Auto-sync**: Enable this option to automatically process new files
5. Click **"Next"**

**💡 Tip**: The system will automatically:
- Extract text from PDFs
- Chunk documents intelligently
- Create embeddings
- Build a vector search index

### 3.4 Configure Vector Search (Auto-Generated)

The wizard automatically configures:

1. **Vector Search Endpoint**: Creates or uses existing endpoint
2. **Embedding Model**: `databricks-bge-large-en` (auto-selected)
3. **Chunk Settings**:
   - Chunk size: 1000 tokens
   - Chunk overlap: 200 tokens
4. **Index Name**: `hr_documents_vs_index` (auto-generated)

Simply review the settings and click **"Next"**

**⏱️ Wait Time**: The system will now process your documents (2-5 minutes). You'll see a progress bar.

---

## Step 4: Configure the Language Model (5 minutes)

> 🎯 **Goal**: Select and configure the AI model that will power your agent's responses

### 4.1 Select Foundation Model

In the Agent Configuration screen:

1. **LLM Provider**: Select **"Databricks Foundation Models"**
2. **Model**: Choose from dropdown:
   - **Recommended**: `databricks-meta-llama-3-1-70b-instruct` (best accuracy)
   - Alternative: `databricks-mixtral-8x7b-instruct` (faster)
3. **Temperature**: Set to **0.1** (for more factual, less creative responses)
4. **Max Tokens**: **500** (adjust based on desired response length)

### 4.2 Configure Retrieval Settings

1. **Number of documents to retrieve (K)**: **5**
2. **Similarity threshold**: **0.7** (only use highly relevant chunks)
3. **Reranking**: Enable **"Smart Reranking"** (optional, improves relevance)

### 4.3 Set System Prompt (Optional)

Customize the agent's behavior with a system prompt:

```
You are an HR assistant for the company. Answer questions about employee benefits, 
policies, and roles based ONLY on the provided documents. If you don't know the 
answer, say "I don't have that information in the available documents."

Be concise, professional, and helpful. Always cite the source document when possible.
```

Click **"Create Agent"** to finish!

**✅ Success**: Your agent is now created and ready to test!

---

## Step 5: Evaluate Agent Performance (15 minutes)

### 5.1 Create Evaluation Dataset

```python
# Create evaluation dataset
eval_data = [
    {
        "question": "What health insurance plans does the company offer?",
        "expected_topics": ["Health Plus", "Standard", "insurance"]
    },
    {
        "question": "How many vacation days do employees get?",
        "expected_topics": ["vacation", "PTO", "days"]
    },
    {
        "question": "What wellness benefits are included?",
        "expected_topics": ["wellness", "gym", "health"]
    },
    {
        "question": "What is the company's remote work policy?",
        "expected_topics": ["remote", "work from home", "policy"]
    }
]

eval_df = pd.DataFrame(eval_data)
print("Evaluation dataset created:")
display(eval_df)
```

### 5.2 Run Agent Evaluation

```python
from databricks import agents

# Evaluate the agent
evaluation_results = agents.evaluate(
---

## Step 5: Test Your Agent in the Playground (15 minutes)

> 🎯 **Goal**: Test your agent's responses using the built-in chat playground

### 5.1 Open the Agent Playground

After creation, you'll automatically be taken to the **Agent Playground**:

1. You'll see a chat interface on the right
2. Agent configuration details on the left
3. A test panel in the middle

### 5.2 Ask Test Questions

Try these sample questions in the chat interface:

1. **Question 1**: `What health insurance options are available?`
   - Review the response
   - Check if it mentions Health Plus and Standard plans

---

## Step 6: Evaluate and Improve (10 minutes)

> 🎯 **Goal**: Measure your agent's performance and make improvements using the UI

### 6.1 Run Automated Evaluation

1. In the Agent Playground, click **"Evaluate"** tab at the top
2. Click **"Create Evaluation Set"**
3. Add your test questions:

| Question | Expected Answer Type |
|----------|---------------------|
| What health insurance plans does the company offer? | Should mention Health Plus and Standard |
| How many vacation days do employees get? | Should specify PTO days |
| What wellness benefits are included? | Should list wellness programs |
| What is the company's remote work policy? | Should explain remote work rules |

4. Click **"Run Evaluation"**
5. Review the results:
   - **Relevance Score**: How relevant is the answer?
   - **Groundedness Score**: Is it based on the documents?
   - **Completeness Score**: Did it answer fully?

### 6.2 Analyze Performance Metrics

1. View the **Metrics Dashboard**:
   - Average response time
   - Retrieval accuracy
   - User satisfaction (from thumbs up/down)

2. Click on **"View Traces"** to see:
   - Which documents were retrieved for each question
   - The reasoning chain
   - Token usage and costs

### 6.3 Improve Agent Performance

If scores are low, try these adjustments:

1. **Adjust Retrieval Settings**:
   - Increase K (retrieve more documents)
   - Lower similarity threshold
   - Enable reranking

2. **Refine System Prompt**:
   - Add more specific instructions
   - Include examples of good responses

3. **Process More Documents**:
   - Add more PDFs to the volume
   - The agent will auto-sync

**Click "Save" after making changes**
```python
# Create a review app for stakeholder feedback
review_app = agents.create_review_app(
    agent=agent,
    app_name="HR Q&A Agent Review"
)

print(f"Review app created! Share this URL with stakeholders:")
print(review_app.url)
```

### 7.2 Collect Feedback

The review app allows users to:
- Ask questions to the agent
- Rate responses (👍 or 👎)
- Provide written feedback
- Flag incorrect or problematic responses

---

## Lab Summary

Congratulations! You have successfully:
✅ Set up a Databricks environment for Agent Bricks
✅ Processed and indexed PDF documents in a vector store
✅ Created an intelligent Q&A agent using RAG
✅ Evaluated agent performance
✅ Deployed the agent to a serving endpoint
---

## Step 7: Deploy to Production (5 minutes)

> 🎯 **Goal**: Deploy your agent to a production endpoint with one click

### 7.1 One-Click Deployment

1. In the Agent interface, click the **"Deploy"** button (top right)
2. Configure deployment settings:
   - **Endpoint Name**: `hr-qa-agent-prod`
   - **Compute Size**: Select **Small** (sufficient for testing)
   - **Scale to Zero**: Enable (saves costs when idle)
   - **Enable Authentication**: Check this for security

3. Click **"Deploy"**
4. Wait for deployment (2-3 minutes)

**✅ Status**: You'll see "Endpoint Ready" when complete

### 7.2 Get API Endpoint

---

## Step 8: Monitor and Maintain (Ongoing)

> 🎯 **Goal**: Use the Analytics UI to monitor usage and continuously improve your agent

### 8.1 View Usage Analytics

1. Navigate to your agent in the Agents dashboard
2. Click **"Analytics"** tab
3. Review metrics:
   - Total queries per day
   - Average response time
   - User satisfaction rate
   - Most common questions
   - Failed queries

### 8.2 Review User Feedback

1. Click **"Feedback"** tab
2. Filter by:
   - 👎 Negative feedback (prioritize these!)
   - Questions with low confidence scores
   - Queries that returned no results

3. Use feedback to:
   - Identify missing information in documents
   - Improve system prompts
   - Add new documents

### 8.3 Update Documents

To add new documents:
1. Navigate to your Unity Catalog volume
2. Upload new PDFs
3. The agent will **automatically re-index** (if auto-sync enabled)
4. No code or configuration changes needed!

---

## Lab Summary

🎉 Congratulations! You have successfully created a production-ready Q&A agent **without writing any code**!

### What You Accomplished:
✅ Uploaded PDF documents using Unity Catalog Volumes UI
✅ Created a Q&A agent using the visual Agent Builder
✅ Configured vector search and embeddings automatically
✅ Tested and evaluated agent responses in the Playground
✅ Deployed the agent to a production endpoint
✅ Created a review app for stakeholder feedback
✅ Set up monitoring and analytics

### Key Takeaways:
- **No coding required**: Everything done through Databricks UI
- **Automatic document processing**: PDFs are parsed and chunked automatically
- **One-click deployment**: From testing to production in minutes
- **Built-in evaluation**: Metrics and feedback collection included
- **Easy maintenance**: Add new documents without rebuilding

## Next Steps

### Immediate Actions:
1. **Share with stakeholders**: Send the review app link to HR team
2. **Collect feedback**: Monitor initial usage and ratings
3. **Add more documents**: Upload additional PDFs as needed

### Advanced Enhancements:
1. **Fine-tune responses**: Adjust system prompt based on feedback
2. **Add guardrails**: Configure content filters for sensitive topics
3. **Integrate with apps**: Use API endpoint in Slack, Teams, or web apps
4. **Create custom UI**: Build a branded interface using the API
5. **Add conversation memory**: Enable multi-turn conversations

### Optimization Tips:
- **Chunk size**: Experiment with 800-1500 tokens for different document types
- **Model selection**: Try different foundation models for speed vs. accuracy
- **Retrieval tuning**: Adjust K and similarity threshold based on use case
- **Cost optimization**: Enable scale-to-zero for development endpoints
1. Click **"Share"** button in the Agent interface
2. Enable **"Create Review App"**
3. Configure access:
   - Add email addresses of stakeholders
   - Set permissions (view/test only)
4. Click **"Generate Shareable Link"**

**Share this link** with HR team members to test the agent!

The review app provides:
- ✅ Clean chat interface (no technical details)
- ✅ Feedback collection (thumbs up/down)
- ✅ Usage analytics
- ✅ No code or configuration visiblelong
- **Solution**: Check endpoint status in the Serving UI
- **Solution**: Ensure model is properly registered

**Issue**: Out of memory errors
- **Solution**: Use a larger cluster size
- **Solution**: Process documents in smaller batches

## Resources

### Databricks Documentation
- [Agent Builder Guide](https://docs.databricks.com/en/generative-ai/agent-builder.html)
- [Unity Catalog Volumes](https://docs.databricks.com/en/volumes/index.html)
- [Vector Search Overview](https://docs.databricks.com/en/generative-ai/vector-search.html)
- [Foundation Models](https://docs.databricks.com/en/machine-learning/foundation-models/index.html)

### Video Tutorials
- [Getting Started with Agent Builder (YouTube)](https://www.youtube.com/databricks)
- [Building RAG Applications Without Code](https://www.youtube.com/databricks)

### Community
- [Databricks Community Forums](https://community.databricks.com/)
- [Databricks Academy](https://www.databricks.com/learn/training)

## Appendix: Using the API (Optional)

If you want to integrate your agent into an application, here's a simple example:

### Python Example
```python
import requests
import os

# Configuration
endpoint_url = "https://<workspace-url>/serving-endpoints/hr-qa-agent-prod/invocations"
token = os.environ.get("DATABRICKS_TOKEN")

# Ask a question
def ask_agent(question):
    headers = {
        "Authorization": f"Bearer {token}",
        "Content-Type": "application/json"
    }
    
    data = {
        "messages": [
            {"role": "user", "content": question}
        ]
    }
    
    response = requests.post(endpoint_url, headers=headers, json=data)
    return response.json()

# Example usage
answer = ask_agent("What health insurance options are available?")
print(answer)
```

### JavaScript/Node.js Example
```javascript
const axios = require('axios');

const endpointUrl = 'https://<workspace-url>/serving-endpoints/hr-qa-agent-prod/invocations';
const token = process.env.DATABRICKS_TOKEN;

async function askAgent(question) {
    const response = await axios.post(
        endpointUrl,
        {
            messages: [
                { role: 'user', content: question }
            ]
        },
        {
            headers: {
                'Authorization': `Bearer ${token}`,
                'Content-Type': 'application/json'
            }
        }
    );
    return response.data;
}

// Example usage
askAgent('What are the vacation policies?')
    .then(answer => console.log(answer));
```

---

## Questions or Feedback?

If you encounter any issues or have suggestions for improving this lab:
- 💬 Ask in the workshop chat
- 📧 Email your instructor
- 🐛 Create an issue in the GitHub repository

---

**Lab Duration**: Approximately 60-90 minutes
**Difficulty Level**: Beginner (No coding required!)
**Last Updated**: October 2025
