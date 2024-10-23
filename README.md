# InsightFinder-Smart-Query-Response-from-Research-Papers

# Gemma QA model

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Setup](#setup)
6. [Functionality](#functionality)
   - [Document Embedding](#document-embedding)
   - [Querying the Model](#querying-the-model)
   - [Viewing Context](#viewing-context)
7. [Code Explanation](#code-explanation)
   - [Library Imports](#library-imports)
   - [Session State Management](#session-state-management)
   - [Prompt Template](#prompt-template)
   - [Main Components](#main-components)
8. [Future Enhancements](#future-enhancements)
9. [Contributing](#contributing)

## Introduction

The **Gemma Q&A Model** serves as an advanced interactive question-and-answer system specifically designed to extract insights from research papers. Using state-of-the-art natural language processing technologies like LangChain and Groq, the application employs a document retrieval mechanism that allows users to query and obtain accurate answers sourced directly from a curated collection of documents.

In an age where information overload is a common challenge, this tool provides a streamlined method for researchers, students, and professionals to access critical information quickly and effectively. 

## Features

- **Document Upload**: Load an entire directory of PDF documents for analysis and answering queries.
- **Vector Embeddings**: Create efficient vector representations of textual content for optimized retrieval.
- **Contextual Q&A**: Users can input questions and receive contextually accurate responses.
- **Document Similarity Search**: Explore chunks of loaded documents that are most relevant to the user’s query.
- **Streamlit Integration**: A user-friendly web interface that simplifies interactions with the model.

## Requirements

Before running the application, ensure you have the following software and libraries installed:

### Python Version

This application requires Python 3.8 or higher.

### Required Libraries

The following Python packages are necessary to execute the application:

- `langchain`: For constructing language model chains.
- `langchain_groq`: For integrating with Groq.
- `langchain_google_genai`: For Google Generative AI embeddings.
- `streamlit`: For creating the interactive web application.
- `python-dotenv`: For managing environment variables.
- `langchain_community.vectorstores`: For utilizing the FAISS vector store.
- `langchain_community.document_loaders`: For loading documents from different formats.
- `faiss-cpu` (or `faiss-gpu`): For efficient similarity searches.

You can install these requirements using pip:

```bash
pip install langchain langchain_groq langchain_google_genai streamlit python-dotenv langchain_community faiss-cpu
```
## Installation 

git clone https://github.com/yourusername/gemma-qa-model.git
cd gemma-qa-model

python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

## Setup
##Environment Variables
GROQ_API_KEY=your_groq_api_key
GOOGLE_API_KEY=your_google_api_key

#Directory Structure

gemma-qa-model/
│
├── .env
├── Research papers/
│   ├── paper1.pdf
│   ├── paper2.pdf
│   └── paper3.pdf
└── app.py
## Functionality

## Document Embedding
Once you start the application, you will see an input field for questions and a button labeled "Documents Embedding." Clicking this button will begin the process of loading the PDF documents from the Research papers directory. The application will read each document, split the text into manageable chunks, and convert these chunks into vector embeddings using Google Generative AI.

This step enables the application to build a vector store that efficiently organizes and retrieves relevant document content based on user queries.

## Querying the Model
After the documents have been embedded successfully, you can interact with the Q&A feature. Type your question related to the content of the loaded documents in the provided text input field. Once you’ve entered your question, press the "Submit" button (or the equivalent action in the app) to send your query.

The underlying model will process your question, searching the vector store for the most pertinent information. You can expect an immediate response with an answer crafted from the context of the available documents.

## Viewing Context
To enhance understanding, the application includes a section labeled "Document Similarity Search". This feature allows users to retrieve and view relevant chunks of text from the documents that contributed to the answer returned.

You can explore this content in a collapsible section beneath the main response, providing a direct relationship between your query and the source material in the documents.

## Code Explanation
## Library Imports
At the beginning of your script, various libraries are imported to handle different functionalities:

Streamlit: To manage the interactive web interface.
LangChain Components: For loading documents, creating text chunks, and employing language models.
FAISS: For vector store creation and similarity search.
Python Dotenv: For environment variable management.
## Session State Management
Streamlit provides a session state feature that maintains the state of variables throughout user interactions. In this application, session state is utilized to store embeddings, loaded documents, and user input to ensure a seamless experience during the question-answering process.

## Prompt Template
The prompt template is constructed to provide clear instructions to the language model. It includes:

Instructions to answer questions based only on the provided context.
The structure through which the input and context will be passed to the model.
This ensures that responses remain relevant to the specific documents and do not include any extraneous information.

## Main Components
The core functionalities are encapsulated within several functions:

vector_embeddings(): This function is responsible for loading PDF documents, splitting their contents, and generating vector embeddings, setting the stage for efficient document retrieval.

create_stuff_documents_chain: This creates a processing chain that combines the language model and document retrieval, governing how the query is handled.

create_retrieval_chain: This pairs the retriever component with the document chain, so that the response can leverage the most relevant context available in the vector store.
## Future Enhancements
The Gemma Q&A Model is designed with extensibility in mind. Here are some potential future enhancements:

Support for More Document Formats: Currently, only PDF files are supported. Expanding this to include formats like Word documents and plain text files could broaden usability.
Advanced Search Features: Implement advanced filtering options to allow users to search documents by date, author, keywords, or types of studies.
User Authentication: For personalized user experiences, the integration of a user login system could allow for saved queries and history.
Multi-language Support: Extending the model to handle queries in various languages could open up the application to a wider audience.
Mobile Compatibility: Building a mobile-friendly interface would make the application accessible on a broader range of devices.

## Contributing
We welcome contributions to the Gemma Q&A Model! To contribute:

Fork the repository.
Create a new branch for your feature or bug fix.
Make your changes and write clear, descriptive commit messages.
Submit a pull request detailing the changes and why they are necessary.
Issues and feature requests can also be submitted to the repository to suggest enhancements.
