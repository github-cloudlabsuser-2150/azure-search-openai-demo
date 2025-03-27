<!--
---
name: RAG chat app with your data (Python)
description: Chat with your domain data using Azure OpenAI and Azure AI Search.
languages:
- python
- typescript
- bicep
- azdeveloper
products:
- azure-openai
- azure-cognitive-search
- azure-app-service
- azure
page_type: sample
urlFragment: azure-search-openai-demo
---
-->

# RAG Chat App with Azure OpenAI and Azure AI Search (Python)

This project demonstrates a Retrieval Augmented Generation (RAG) approach to build a ChatGPT-like application using Azure OpenAI and Azure AI Search. The backend is implemented in Python, leveraging various libraries and frameworks for efficient data processing and interaction.

## Key Features

- **Retrieval Augmented Generation (RAG)**: Combines GPT models with Azure AI Search for enhanced data retrieval and response generation.
- **Multi-turn Chat**: Supports conversational interactions with context awareness.
- **Customizable Approaches**: Includes modular implementations for different retrieval and generation strategies.
- **Extensibility**: Designed to integrate additional data sources and processing pipelines.

## Prerequisites

Ensure the following tools and dependencies are installed:

- Python 3.9, 3.10, or 3.11
- Azure CLI
- Required Python libraries (see [Installation](#installation))

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/azure-samples/azure-search-openai-demo.git
    cd azure-search-openai-demo
    ```

2. Install the required Python dependencies:

    ```bash
    pip install -r requirements.txt
    ```

    Key dependencies include:
    - `azure-search-documents`: For interacting with Azure Cognitive Search.
    - `openai`: For accessing Azure OpenAI GPT models.
    - `fastapi`: For building the backend API.
    - `pydantic`: For data validation and settings management.

3. Configure environment variables for Azure services (e.g., Azure OpenAI and Azure AI Search keys).

## Backend Overview

The backend logic is implemented in `app/backend/approaches/approach.py`. It defines modular approaches for handling retrieval and generation tasks. Key components include:

- **Retrieval**: Queries Azure AI Search to fetch relevant documents based on user input.
- **Generation**: Uses Azure OpenAI GPT models to generate responses based on retrieved documents.
- **Hybrid Approach**: Combines retrieval and generation for contextually rich responses.

### Example Code Snippet

```python
# filepath: c:\Users\azureuser\Documents\dev-env\azure-search-openai-demo\app\backend\approaches\approach.py
# ...existing code...
class HybridApproach:
    def retrieve_and_generate(self, query: str) -> str:
        # Retrieve relevant documents
        documents = self.search_client.search(query)
        # Generate response using GPT model
        response = self.openai_client.generate_response(documents)
        return response
# ...existing code...
```

## Running the Application

1. Start the backend server:

    ```bash
    uvicorn app.main:app --reload
    ```

2. Access the application at `http://127.0.0.1:8000`.

## Usage

- Send a query to the `/chat` endpoint to interact with the RAG-based chatbot.
- Explore different retrieval and generation strategies by modifying `approach.py`.

## Clean Up

To remove all resources created during deployment, delete the Azure resource group or run:

```bash
az group delete --name <resource-group-name>
```

## Contributing

Contributions are welcome! Please submit issues or pull requests to improve the project.

## License

This project is licensed under the [MIT License](LICENSE).
