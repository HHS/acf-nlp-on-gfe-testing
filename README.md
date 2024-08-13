## NLP on GFE testing

### **AI contracts**

This repository contains the Jupyter Notebooks for the ACF Data Surge Team’s project, titled `NLP on GFE Testing`.

#### **Project Objectives**

This project aims to identify AI use cases across federal agencies, particularly those providing public benefits (e.g., HHS, USDA, DOE, HUD, SSA, SBA, VA), and assess their applicability to the Administration for Children and Families (ACF). The project will explore the use of natural language processing (NLP) to analyze federal contract datasets, identifying AI-related procurements and summarizing key findings to enhance decision-making. Additionally, it will investigate the limitations of Government Furnished Equipment (GFE) laptops for NLP tasks, including the identification of suitable local LLM chatbot options that can be easily installed and operated within HHS-approved software constraints.

#### **Project Overview**

This project comprises a series of Jupyter notebooks dedicated to various machine learning and NLP tasks on contract datasets. The notebooks serve different purposes, including filtering the dataset for the last five years to identify AI-related keywords and visualizing word frequency through word clouds. Text pre-processing and summarization are conducted using the BART model, while topic modeling is achieved with NLTK and Gensim, followed by the LDA model to display and assign dominant topics. Frequently used AI techniques are extracted, contracts are clustered, and summarized using LLMs like BART, phi3, and llama3. URLs related to attachments are extracted using the Selenium library, and the attachments are handled and downloaded using a headless Firefox WebDriver. Additionally, text extraction from PDFs and Word files is performed for keyword identification and summarization. The project also includes a notebook that applies machine learning models to a COVID dataset and NLP on the attachments of contracts dataset, simulating various scenarios, noting computational loads on GFE.

Below are the links to the notebooks used in this project:

#### **Data Pre-processing**
- [Identify AI related contracts `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/Get_AI_contracts_s1.ipynb)
**Key Takeaway:** 156 contracts are related to AI. 
- [Summarize Contracts `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/AI_contracts_summarization_s1.ipynb)**Key Takeaway:** Summarizes `Description` column of each contract using BART model, Summarization can be improved using LLMs.
- [Dwonload attachments `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/Get_attachments_s2.ipynb)**Key Takeaway:** Selenium python library and FireFox webdriver were used to download attachements of AI contracts. 

#### **AI usecases and Topic Tagging**
- [Identify topics `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/AI_contracts_topics_s1.ipynb)**Key Takeaway:** Topic identification using unsupervised machine learning (Latent Dirichlet Allocation) technique, it is a preliminary exploration and the following noted uses LLM (llama3) to identify the topics.
- [AI topics `sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/use_cases_topics_sam_csv_s3.ipynb)**Key Takeaway:** f
- [AI techniques and usecases `sam.gov attachments`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/use_cases_topics_sam_attachments_s3.ipynb)**Key Takeaway:** f
- [AI techniques and topics `ai.gov, hhs.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/use_cases_topics_s3.ipynb)**Key Takeaway:** f

#### **GFE limits**
- [Explore the limits of GFE - `COVID dataset`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/NLP_GFElimits_Covid_s1.ipynb)**Key Takeaway:**  30 million records of structured data (3.9 GiB) is essentially the limit of the GFE.
- [Explore the limits of GFE - `NLP on attachments sam.gov`](https://github.com/HHS/acf-nlp-on-gfe-testing/blob/main/code/NLP_GFElimits_AIcontracts_s2.ipynb)**Key Takeaway:** 1655 pdf pages of unstructured data is essentially the limit of the GFE.

### Setting up a local chatbot using `ollama` and `anything-llm`:

To ensure you don't encounter network issues, ensure that VPN is disconnected prior to following the steps below. It also recommended that GitHub Desktop, and docker desktop applications to be installed on the GFE.

#### Setting up OLLAMA API on GFE

To integrate LLMs with Python on a GFE (OS: Windows), it needs to set up the Ollama API and install the Phi3 and Llama3 models. Follow these steps:

**Download and Install Ollama API**:

- Visit [Ollama&#39;s website](https://www.ollama.com/).
- Click on the "Download" button to get the Windows installer.
- Run the installer and follow the on-screen instructions to complete the installation.

**Install Models**:

- Open a command prompt or PowerShell.
- Use the following commands to install the models:
  ```
  ollama pull phi3
  ollama pull llama3.1
  ```

It can take several minutes to download these models.

These steps will set up the Ollama API and the models on the GFE.

#### Setting up Anything-LLM on GFE

The "anything-llm" repository on GitHub is an all-in-one AI application that offers full AI Chatbot capabilities and allows for interacting with documents. This application can be run locally or hosted remotely and provides a customizable chat UI, developer API, and integration with popular vector databases.

In order to setup the local chatbot using this repository, firstly the GitHub repository needs to be cloned to the GFE using the link below:

    https://github.com/ypadilla-arch/anything-llm.git

#### To run this docker:

Make sure you have disconnected from any VPN to avoid connection issues for the next step.

In a command prompt navigate to docker folder in the cloned reporitory.

Once here, execute the following command:

```shell
docker compose -f "docker-compose.yml" up -d
```

It will take a several minutes to download, build and execute the container for the application.

Once everything is loaded you can navigate on your browser to: [http://localhost:3001](http://localhost:3001)

The Anything-LLM application is already pre-configured in this repo for ease of use. The next steps are to:

* Create a workspace
* Upload some documents there (short documents have worked better in our testing)
* Add the documents to the workspace

After this step you can chat with your documents as context in the chat interface. Depending on how much it is provided to the model, it can take several minutes for the model to provide a response. You can follow additional guidance through the [main page](https://github.com/ypadilla-arch/anything-llm).

Execute the following command to stop/remove the docker containers:

```shell
docker compose down
```
