RAG Chatbot using n8n, Pinecone & Google Gemini
📌 Project Overview

This project is a Retrieval-Augmented Generation (RAG) Chatbot developed using n8n, Google Gemini, Pinecone Vector Database, and OpenAI Embeddings. The chatbot answers restaurant-related queries by retrieving relevant information from a vector database instead of relying only on the language model's knowledge.

The chatbot is designed for Oak & Barrel Restaurant and can answer questions about:

Menu items
Food prices
Reservation policies
Restaurant timings
Restaurant information
General FAQs
🛠️ Technologies & Tools Used
Tool	Purpose
n8n	Workflow automation platform
Google Gemini Chat Model	Large Language Model (LLM) for generating responses
Pinecone Vector Database	Stores document embeddings for semantic search
OpenAI Embeddings	Converts restaurant documents into vector embeddings
Simple Memory (n8n)	Maintains conversation history
Answer Questions with a Vector Store Node	Retrieves relevant documents from Pinecone
Chat Trigger Node	Receives user messages
PDF/Restaurant Documents	Knowledge source for the chatbot
📂 Project Workflow
User
   │
   ▼
When Chat Message Received
   │
   ▼
AI Agent
   ├── Google Gemini Chat Model
   ├── Simple Memory
   └── Answer Questions with a Vector Store
            │
            ▼
     Pinecone Vector Store
            │
            ▼
     OpenAI Embeddings
            │
            ▼
Relevant Documents Retrieved
            │
            ▼
Google Gemini Generates Final Answer
            │
            ▼
User Receives Response
🚀 Step-by-Step Implementation
Step 1: Create an n8n Workflow
Open n8n.
Create a new workflow.
Name the workflow Oak & Barrel Assistant.
Step 2: Add the Chat Trigger
Add the When Chat Message Received node.
This node accepts questions from users.

Example:

What is the price of Paneer Butter Masala?
Step 3: Add the AI Agent
Drag and drop the AI Agent node.
Connect it to the Chat Trigger.
Configure the AI Agent to use the connected chat trigger as the prompt source.
Step 4: Configure the Chat Model
Add the Google Gemini Chat Model.
Connect it to the Chat Model input of the AI Agent.
Select an appropriate Gemini model (e.g., gemini-2.5-flash).

Purpose:

Generates natural language responses.
Step 5: Configure Memory
Add the Simple Memory node.
Connect it to the Memory input of the AI Agent.
Configure the session ID from the connected chat trigger.
Set the context window length (e.g., 5).

Purpose:

Maintains conversation context during a chat session.
Step 6: Add the Vector Store Tool
Add the Answer Questions with a Vector Store node.
Connect it to the Tool input of the AI Agent.

Purpose:

Enables retrieval of relevant information from the vector database.
Step 7: Configure Pinecone Vector Store
Add the Pinecone Vector Store node.
Connect it to the Vector Store input of the Answer Questions node.

Configuration:

Credentials
Pinecone Index
Operation Mode: Retrieve Documents (As Tool for AI Agent)

Purpose:

Retrieves the most relevant restaurant documents.
Step 8: Configure OpenAI Embeddings
Add the OpenAI Embeddings node.
Connect it to the Pinecone Vector Store.

Purpose:

Converts documents into embeddings for semantic search.
Step 9: Connect a Chat Model to the Retrieval Tool
Add another Google Gemini Chat Model (or OpenAI Chat Model).
Connect it to the Model input of the Answer Questions with a Vector Store node.

Purpose:

Generates answers using the retrieved documents.
Step 10: Prepare the Knowledge Base

Create restaurant documents containing:

Menu
Food prices
FAQs
Reservation policy
Restaurant timings
Address
Contact details

Convert these documents into embeddings and upload them to the Pinecone index.

Step 11: Test the Chatbot

Run the workflow and ask questions such as:

What is the price of Paneer Butter Masala?
Do you serve vegan food?
What are your opening hours?
How can I reserve a table?
Where is Oak & Barrel located?
Do you accept online payments?
What desserts do you serve?
What beverages are available?
Is parking available?
Can I book a table for six people?
📊 Workflow Summary
Chat Trigger
      │
      ▼
AI Agent
      ├─────────────► Google Gemini Chat Model
      │
      ├─────────────► Simple Memory
      │
      └─────────────► Answer Questions with a Vector Store
                              │
                              ▼
                    Pinecone Vector Store
                              │
                              ▼
                     OpenAI Embeddings
                              │
                              ▼
                   Restaurant Knowledge Base
🎯 Features
Retrieval-Augmented Generation (RAG)
Semantic search using vector embeddings
Restaurant menu lookup
Reservation assistance
FAQ support
Conversational memory
Fast and accurate document retrieval
Natural language responses using Google Gemini
📚 Skills Demonstrated
AI Workflow Automation
Retrieval-Augmented Generation (RAG)
Vector Databases
Prompt Engineering
Embeddings
Large Language Models (LLMs)
Pinecone Integration
Google Gemini Integration
n8n Automation
AI Agent Development
Conversational AI
Semantic Search
✅ Outcome

Successfully developed a Restaurant RAG Chatbot that retrieves relevant information from a Pinecone Vector Database using OpenAI Embeddings and generates context-aware responses with Google Gemini. The chatbot provides accurate answers about restaurant menus, pricing, reservations, operating hours, and FAQs while maintaining conversational context through memory, making it an efficient AI-powered customer support assistant.
