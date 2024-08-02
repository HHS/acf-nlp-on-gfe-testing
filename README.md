## NLP on GFE testing
### **AI contracts**

This repository contains the Jupyter Notebooks for the ACF Data Surge Team’s project, titled `NLP on GFE Testing`. 

#### **Project Overview**
This project comprises a series of Jupyter notebooks dedicated to various machine learning and NLP tasks on contract datasets. The notebooks serve different purposes, including filtering the dataset for the last five years to identify AI-related keywords and visualizing word frequency through word clouds. Text pre-processing and summarization are conducted using the BART model, while topic modeling is achieved with NLTK and Gensim, followed by the LDA model to display and assign dominant topics. Frequently used AI techniques are extracted, contracts are clustered, and summarized using LLMs like BART, phi3, and llama3. URLs related to attachments are extracted using the Selenium library, and the attachments are handled and downloaded using a headless Firefox WebDriver. Additionally, text extraction from PDFs and Word files is performed for keyword identification and summarization. The project also includes a notebook that applies machine learning models to a COVID dataset and NLP on the attachments of contracts dataset, simulating various scenarios, noting computational loads on GFE.

Below are the links to the notebooks used in this project:
- [Identify AI related contracts `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/Get_AI_contracts_s1.ipynb)
- [Summarize Contracts `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/AI_contracts_summarization_s1.ipynb)
- [Identify topics `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/AI_contracts_topics_s1.ipynb)
- [Dwonload attachments `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/Get_attachments_s2.ipynb)
- [AI techniques and usecases `sam.gov attachments`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/use_cases_topics_sam_attachments_s3.ipynb)
- [AI topics `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/use_cases_topics_sam_csv_s3.ipynb)
- [AI techniques and topics `ai.gov, hhs.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/use_cases_topics_s3.ipynb)
- [Explore the limits of GFE - `COVID dataset`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/NLP_GFElimits_Covid_s1.ipynb)
- [Explore the limits of GFE - `NLP on attachments sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/NLP_GFElimits_AIcontracts_s2.ipynb)

### Setting up a local Chatbot using `anything-llm`:

The "anything-llm" repository on GitHub is an all-in-one AI application that offers full AI Chatbot capabilities. This application can be run locally or hosted remotely and provides a customizable chat UI, developer API, and integration with popular vector databases. 

Inorder to setup the local chatbot using this repository, firstly the repo needs to be cloned to the GFE using the link below:

    https://github.com/ypadilla-arch/anything-llm.git

It also requires github, docker desktop applications to be installed on the GFE.

#### To use this docker file: [docker-compose.yml](https://github.com/ypadilla-arch/anything-llm/blob/master/docker/docker-compose.yml)

Create an `.env` file in docker folder  with the following content

```.env
SERVER_PORT=3001
STORAGE_DIR="/app/server/storage"
UID='1000'
GID='1000'
LLM_PROVIDER='generic-openai'
GENERIC_OPEN_AI_BASE_PATH='http://host.docker.internal:8086/v1'
GENERIC_OPEN_AI_MODEL_PREF='Rocket'
GENERIC_OPEN_AI_MODEL_TOKEN_LIMIT='4096'
GENERIC_OPEN_AI_MAX_TOKENS='512'
EMBEDDING_ENGINE='native'
VECTOR_DB='lancedb'
DISABLE_TELEMETRY='true'

```

Create a .models in "docker" folder here

Download the model from Hugging Face: [Rocket model](https://huggingface.co/TheBloke/rocket-3B-GGUF/resolve/main/rocket-3b.Q4_K_M.gguf?download=true)

Move the model file to the .models folder

#### To run this docker:

Make sure you have disconnected from any VPN to avoid connection issues for the next step

In a command prompt navigate to docker folder

Once here, execute the following command:

```shell
docker compose -f "docker-compose.yml" up -d --build
```

It will take a couple of minutes to build the containers for the application and running the model.

Once everything is loaded you can navigate on your browser to: [http://localhost:3001](http://localhost:3001)

The Anything-LLM application is already pre-configured in this repo for ease of use. The next steps are to create a workspace, upload some **short documents** there, then add them to the workspace. You can follow additional guidance through the [main page](https://github.com/ypadilla-arch/anything-llm). After this step you can chat with your documents in the chat interface.

execute the following command to stop/remove the docker containers:

```shell
docker compose down
```

### Setting up OLLAMA API on GFE
To integrate LLMs with Python on a GFE (OS: Windows), it needs to set up the Ollama API and install the Phi3 and Llama3 models. Follow these steps:

**Download and Install Ollama API**:
   - Visit [Ollama's website](https://www.ollama.com/).
   - Click on the "Download" button to get the Windows installer.
   - Run the installer and follow the on-screen instructions to complete the installation.

**Install Models**:
   - Open a command prompt or PowerShell.
   - Use the following commands to install the models:
     ```
     ollama install phi3
     ollama install llama3
     ```

These steps will set up the Ollama API and the models on the GFE.