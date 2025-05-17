📚 Agentic RAG AI Agent (n8n Workflow)

This AI agent is an automated Retrieval-Augmented Generation (RAG) system built with n8n and integrated with Google Drive, Pinecone, and Google Gemini. It enables real-time question answering based on documents uploaded or updated in a specific Google Drive folder.

🚀 Features

- Watches a Google Drive folder for new or updated files
- Loads and splits documents into chunks
- Embeds the chunks using Google Gemini Embedding API
- Stores the vectorized data in Pinecone Vector Database
- Uses Google Gemini Chat Model for intelligent, context-aware Q&A
- Responds to chat messages using retrieved context (RAG-style)
- Outputs answers with additional formatting or custom logic via a code node

🧩 Workflow Structure

🔁 Trigger Nodes
- File Created / Updated (Google Drive): Watches a folder and initiates vector embedding flow.
- Chat Message Received: Accepts user queries.

📄 Document Processing Flow
1. Default Data Loader: Ingests binary documents from Drive.
2. Recursive Character Text Splitter: Splits documents into smaller chunks for efficient embedding.
3. Google Gemini Embedding: Generates vector embeddings.
4. Pinecone Vector Store: Stores embedded vectors into a Pinecone index.

🧠 RAG QA Flow
1. Vector Store Retriever: Pulls relevant chunks based on query.
2. Google Gemini Chat Model: Provides natural language answers.
3. Question and Answer Chain: Formats the final response with context.
4. Code Node: Structures the output to return only the answer.

📂 Folder Structure

- Google Drive Folder: RAG Agent  
  Monitored for new/updated files to add to the knowledge base.
  Link: https://drive.google.com/drive/folders/1pnnmaviCVQbpwhmi6bycWvgb-8H4wMTc

🛠️ Credentials Required

Service        | Credential Name                  | Notes
---------------|----------------------------------|----------------------------------
Google Drive   | Google Drive account             | OAuth2 credential in n8n
Google Gemini  | Google Gemini(PaLM) Api account  | API key setup via Google Cloud
Pinecone       | PineconeApi account              | Pinecone environment and key

📌 Setup Steps

1. Create a folder in Google Drive and note the folder ID.
2. Configure credentials in n8n for Google Drive, Gemini, and Pinecone.
3. Deploy the workflow in n8n (preferably self-hosted or cloud).
4. Start uploading documents to the folder.
5. Use the webhook/chat trigger to send queries and receive answers.

🧠 System Prompt Template

You are an assistant for question-answering tasks. Use the following pieces of retrieved context to answer the question.
If you don't know the answer, just say that you don't know, don't try to make up an answer.
----------------
Context: {context}

💡 Use Cases

- Internal document search agents
- Knowledge base chatbots
- Smart support assistants
- Research tools with dynamic content ingestion

📞 Contact

Feel free to reach out if you want help extending this agent with voice input, Slack integration, or agent memory!