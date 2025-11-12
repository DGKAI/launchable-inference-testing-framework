# Inferencing Test Application

This project is used to deploy a ready-to-use inferencing test application within the Nvidia AI Workbench environment, leveraging Open WebUI, n8n, and PostgreSQL as a vector database for efficient embedding storage and retrieval.

## Description

This inferencing test application is designed specifically for seamless deployment in Nvidia AI Workbench. By simply cloning the project and configuring a single environment variable (`VECTORDB_PASSWORD`), users can start the entire stack via Docker Compose. The solution integrates Open WebUI as a user-friendly interface for model inference, n8n for workflow automation, and PostgreSQL (via pgvector) as a vector database to persist and query embeddings, enabling quick testing and evaluation of AI model outputs.

## Getting Started

1. **Clone the Project**  
   In Nvidia AI Workbench, click on **Clone Project** and copy this repository's link into the text field.

2. **Set Environment Variable**  
   When prompted, set the variable `VECTORDB_PASSWORD` to secure your PostgreSQL vector database instance.

3. **Start the Application**  
   Click the **Start Compose** button in Nvidia AI Workbench to launch all services via Docker Compose. This will start PostgreSQL, Open WebUI, and n8n containers automatically.

4. **Access the Services**  
   - Open WebUI interface: [http://localhost:8080](http://localhost:8080)  
   - n8n workflow automation UI: [http://localhost:5678](http://localhost:5678)


5. **Test Inferencing**  
   Use Open WebUI to interact with your favourite Large Language Model (LLM). For detailed usage and configuration of Open WebUI, please refer to the [Official Open WebUI Documentation](https://docs.openwebui.com/getting-started/quick-start/starting-with-openai).

   > **Tip:** Open WebUI enables you to create Knowledgebases by uploading files which are then embedded and stored in the vector database. These stored embeddings can be leveraged within n8n workflows to enrich or condition downstream inference tasks.  
   >  
   > **Important:** Ensure that both Open WebUI and n8n are configured to use the same embedding model to maintain consistency and compatibility when processing vector data.

## Environment Variables

The following environment variables can be configured in Nvidia AI Workbench under **Environment → Project Container → Environment Variables** to customize behavior:

### n8n Variables
| Variable           | Description                                 | Default / Example       |
|--------------------|---------------------------------------------|------------------------|
| `GENERIC_TIMEZONE` | Timezone used by n8n                         | `Europe/Berlin`        |
| `SUBDOMAIN`        | Subdomain for the n8n instance               | `n8n`                  |
| `DOMAIN_NAME`      | Domain name used for n8n (if applicable)    | `example.com`          |
| `SSL_EMAIL`        | Email used for SSL certificate registration | `user@example.com`     |
| `N8N_SECURE_COOKIE`| Boolean flag to toggle secure cookies       | `false`                |

### Vector Database (PostgreSQL) Variables
| Variable             | Description                                         | Default / Example     |
|----------------------|-----------------------------------------------------|----------------------|
| `VECTOR_DB`          | Type of vector database used                         | `pgvector`           |
| `VECTORDB_USER`      | PostgreSQL username                                 | `test`               |
| `VECTORDB_NAME`      | Database name                                      | `testdb`             |
| `VECTORDB_PASSWORD`  | Password for PostgreSQL user (set when prompted)  | *Your chosen password*|

---

For further customization or troubleshooting, refer to the service-specific documentation or the Nvidia AI Workbench user guide.
