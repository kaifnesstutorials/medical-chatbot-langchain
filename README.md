 🩺 Medical RAG Chatbot (LangChain + Pinecone)

A **Medical Question-Answering Chatbot** built using **Retrieval-Augmented Generation (RAG)**.
This system reads medical PDF documents and answers user questions **strictly based on the provided content**, significantly reducing hallucinations and incorrect responses.

Instead of relying only on a language model’s internal knowledge, the chatbot first **retrieves relevant information from medical documents** and then generates accurate, context-aware answers using an LLM.

---

## 🧠 What is RAG in This Project?

The chatbot follows a **Retrieval-Augmented Generation pipeline**:

* Medical PDFs are indexed into a vector database
* User queries are converted into embeddings
* Relevant document chunks are retrieved
* The LLM generates answers grounded in retrieved context

This approach improves reliability and makes the chatbot more suitable for **medical knowledge-based applications**.

---

## 🛠️ Tech Stack

* **Python** – Core programming language
* **Flask** – Backend web framework
* **LangChain** – RAG pipeline orchestration
* **Pinecone** – Vector database for similarity search
* **HuggingFace Embeddings** – Text embedding generation
* **OpenAI** – Large Language Model for answering questions

---

## 📂 Project Structure

```
medical-rag-chatbot/
│
├── app.py                 # Flask application (chat API)
├── store_index.py         # Script to index PDFs into Pinecone
├── src/
│   ├── helper.py          # PDF loading, chunking & embeddings
│   └── prompt.py          # System prompt for the LLM
│
├── templates/
│   └── chat.html          # Web-based chat interface
│
├── Data/                  # Medical PDF documents
│   └── *.pdf
│
├── requirements.txt       # Python dependencies
├── .env                   # Environment variables (NOT pushed to GitHub)
└── README.md
```

---

## 🔄 How the System Works

1. Medical PDFs are loaded from the `Data/` directory
2. Documents are split into small, meaningful chunks
3. Each chunk is converted into vector embeddings
4. Embeddings are stored in Pinecone
5. User submits a medical question
6. Relevant content is retrieved from Pinecone
7. The LLM generates a concise and grounded answer

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/kaifnesstutorials/medical-chatbot-langchain.git
cd medical-chatbot-langchain
```

---

### 2️⃣ Create a Virtual Environment (Recommended)

**Mac / Linux**

```bash
python -m venv venv
source venv/bin/activate
```

**Windows**

```bash
python -m venv venv
venv\Scripts\activate
```

---

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🔐 Pinecone Setup

### Step 1: Create an Account

* Visit 👉 [https://www.pinecone.io](https://www.pinecone.io)
* Sign up or log in
* Open the Pinecone dashboard

### Step 2: Generate API Key

* Go to **API Keys**
* Copy your Pinecone API key

### Step 3: Configure Environment Variables

Create a `.env` file in the project root:

```env
PINECONE_API_KEY=your_pinecone_api_key_here
OPENAI_API_KEY=your_openai_api_key_here
```

> ⚠️ Never commit `.env` files to GitHub.

---

## 📌 Index Medical PDFs

Run the following command **once** to upload embeddings to Pinecone:

```bash
python store_index.py
```

This script:

* Reads medical PDFs
* Generates embeddings
* Stores vectors in Pinecone

---

## 🚀 Run the Application

```bash
python app.py
```

Open your browser and navigate to:
```
http://192.168.0.102:8080
```

Use the chat interface to ask medical questions.

🧪 Example Queries
* What is diabetes?
* What are the symptoms of heart disease?
* How is hypertension treated?

---

## ⚠️ Current Limitations

* Single-turn question support only
* No PDF upload from the UI
* Similarity-based retrieval only
* No source citation in responses

🔮 Future Enhancements

* Conversational memory
* Source citations with answers
* Metadata-based filtering
* Streaming responses
* Authentication and rate limiting

 📌 Disclaimer

This project is intended **for educational and demonstration purposes only**.
It is **not suitable for medical diagnosis or clinical use**.
Response accuracy depends entirely on the uploaded documents.

 👨‍💻 Author
Mohd Kaif Shaikh
AI and Data Science Graduate

⭐ Support
If you find this project useful, consider giving it a ⭐ on GitHub — your support is appreciated! 😊


# medical-chatbot-langchain

# Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS

# How to run?
### STEPS:

Clone the repository

```bash
git clonehttps://github.com/entbappy/Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS.git
```
### STEP 01- Create a conda environment after opening the repository

```bash
conda create -n medibot python=3.10 -y
```

```bash
conda activate medibot
```


### STEP 02- install the requirements
```bash
pip install -r requirements.txt
```


### Create a `.env` file in the root directory and add your Pinecone & openai credentials as follows:

```ini
PINECONE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
OPENAI_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```


```bash
# run the following command to store embeddings to pinecone
python store_index.py
```

```bash
# Finally run the following command
python app.py
```

Now,
```bash
open up localhost:
```


### Techstack Used:

- Python
- LangChain
- Flask
- GPT
- Pinecone



# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

	#with specific access

	1. EC2 access : It is virtual machine

	2. ECR: Elastic Container registry to save your docker image in aws


	#Description: About the deployment

	1. Build docker image of the source code

	2. Push your docker image to ECR

	3. Launch Your EC2 

	4. Pull Your image from ECR in EC2

	5. Lauch your docker image in EC2

	#Policy:

	1. AmazonEC2ContainerRegistryFullAccess

	2. AmazonEC2FullAccess

	
## 3. Create ECR repo to store/save docker image
    - Save the URI: 315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot

	
## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
# 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

   - AWS_ACCESS_KEY_ID
   - AWS_SECRET_ACCESS_KEY
   - AWS_DEFAULT_REGION
   - ECR_REPO
   - PINECONE_API_KEY
   - OPENAI_API_KEY
