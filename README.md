## NLP on GFE testing
### AI contracts

This repository contains the Jupyter Notebooks for the ACF Data Surge Team’s project, titled `NLP on GFE Testing`. 

#### Project Overview
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

### Setting up a local Chatbot using LLMs





### Setting up OLLAMA API on GFE
