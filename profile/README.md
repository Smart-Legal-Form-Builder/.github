# Smart Legal Form Builder: AI-Enhanced Document Creation
> LawReady is smart legal form builder for everyone. 
Create legal documents and get personalized legal advice effortlessly with LawReady!


![lawready-001 (1)](https://github.com/user-attachments/assets/a76d3d53-092e-4db0-9685-36526923e3ac)



## 🎬 Demo video! (click below)
🔗 https://www.youtube.com/watch?v=zhuRicXTcVs




## 📢 Group Members

| Name         | Organization                                              | Email                        | Role             |
|--------------|-----------------------------------------------------------|------------------------------|------------------|
| Seoyeon Kim  | Department of Tourism (관광학부), Hanyang University      | soen0814@hanyang.ac.kr       | AI / AI backend               |
| Jiwon Han    | Department of Business Administration (경영학부), Hanyang University | jiwon8623@hanyang.ac.kr      | Document         |
| Taeyeon Kim  | Department of Information System (정보시스템학과), Hanyang University | tangboll5075@gmail.com       | Frontend         |
| Suhyeon Yu   | Department of Information System (정보시스템학과), Hanyang University | sh265826@naver.com           | Frontend/Backend |
| Soohan Jeong | Department of Information System (정보시스템학과), Hanyang University | soohan9909@gmail.com         | UI Design        |




## 📖 Topic - Smart Legal Form Builder: AI-Enhanced Document Creation

### I. Introduction
The Smart Legal Form Builder is designed for individuals who struggle with legal document preparation due to a lack of legal expertise or access to affordable professional assistance. Many people face challenges in understanding and drafting legal documents because they lack formal legal education or experience, leaving them unsure about the structure, required elements, and proper legal terminology. This often leads to errors or delays in processing important legal documents.

According to the 2019 국민법의식통계 (Korean Legal Awareness Statistics), approximately 76.3% of respondents found legal terminology difficult to understand, and 78.4% struggled with comprehending legal sentences. In the same study, 61.6% of respondents evaluated that legal services in society are quantitatively insufficient. Additionally, hiring a lawyer or legal professional can be expensive and time-consuming. Simple document preparation often involves significant financial investment, and individuals with limited budgets may feel discouraged from pursuing legal remedies or formal agreements. A 2020 report from the Judicial Policy Research Institute highlights that legal service costs pose a major burden to the public, prompting discussions on introducing legal service insurance systems.

The AI-powered legal form builder addresses these issues by offering a user-friendly interface that guides individuals through the process of creating formal documents, such as complaints. The tool is specifically tailored to assist in the preparation of legal documents for cases involving fraud in secondhand transaction fraud, online abuse, sexual harassment, assault and injury. It simplifies the creation of high-quality legal documents for non-experts by providing step-by-step guidance via a chatbot interface that gathers the necessary information.

This solution not only enables users to create legal documents without professional assistance but also improves accessibility to legal solutions by offering a cost-effective alternative to traditional legal services. By making legal support more accessible, the tool helps underrepresented communities and small businesses navigate legal challenges efficiently and affordably.


---


### II. Datasets
This repository contains the dataset used for training the Retrieval-Augmented Generation (RAG) system, which focuses on legal case analysis. The dataset is structured in JSON format and includes annotated legal case data for categories like Sexual Harassment, Online Defamation, Fraud in Online Transactions, and Sexual Assault.


```json
{
        "id": 1,
        "category": "성추행",
        "text": "피고인은 지하철 내에서 피해자의 신체를 고의로 접촉하여 추행하였다.",
        "settlement": 3000000,
        "sentence": 8,
        "verdict_summary": "강제추행죄로 징역 8개월, 합의금 300만원 선고.",
        "keywords": ["대중교통", "강제추행", "성범죄"]
},
{
        "id": 1,
        "category": "성희롱",
        "text": "피고인은 회사 회식 자리에서 여직원들에게 '술은 오빠랑 마셔야 제맛이지'라는 등의 성적 발언을 수차례 하였다.",
        "settlement": 3000000,
        "sentence": 0,
        "verdict_summary": "성희롱 혐의로 벌금 300만원 선고. 회사 징계위원회에서 정직 3개월 처분.",
        "keywords": ["회식", "언어적성희롱", "직장내성희롱"]
},
{
      "id": 1,
      "category": "온라인 욕설",
      "text": "피고인은 SNS에서 피해자의 외모를 조롱하며 인신공격성 댓글을 지속적으로 게시했다.",
      "settlement": 150000,
      "sentence": 3,
      "verdict_summary": "SNS에서 피해자의 외모를 조롱하며 명예훼손 및 모욕 혐의로 징역 3개월, 합의금 150000원 선고.",
      "keywords": [
        "SNS",
        "외모 비하",
        "모욕"
      ]
},
{
    "id": 1,
    "category": "중고거래 사기",
    "text": "피고인은 고급 레시피 책을(를) 거래 후기 사이트를 조작해 피해자를 유인하며 피해자로부터 389000원을 송금받고, 이후 잠적했다.",
    "settlement": 583039,
    "sentence": 8,
    "verdict_summary": "고급 레시피 책 판매 사기 혐의로 징역 8개월, 합의금 583039원 선고.",
    "keywords": [
      "고급 레시피 책",
      "중고거래",
      "사기"
    ]
}
```

#### Dataset Structure:

The dataset consists of legal case records with the following fields:

- id: Unique identifier for each case
- category: Legal category (e.g., "Sexual Harassment")
- text: A brief summary of the legal incident
- settlement: Financial settlement awarded (if any)
- sentence: Sentence imposed by the court (in months)
- verdict_summary: Summary of the verdict
- keywords: Relevant keywords describing the case (e.g., type of crime, location)


#### Dataset Generation Method

The dataset is generated through the following steps:

1. Data Collection: Legal cases are collected from public legal sources (court records, news articles) and categorized into four main types.
2. Preprocessing: Raw data is cleaned, formatted, tokenized, and indexed for easy retrieval by the RAG system.
3. Annotation: Each case is annotated with relevant information (category, settlement, sentence, verdict summary, keywords).
4. Categorization: The dataset is divided into categories to allow efficient case querying.
5. Data Storage and Indexing: The dataset is stored in JSON format and indexed using FAISS for fast retrieval.

#### Dataset Overview

##### Legal/Regulatory Text Analysis Data
- Source: AI Hub Dataset 71723
- Description: Includes over 60,000 annotated legal case data with labels for case summaries, Q&A sets, and keywords.
- Purpose: Supports AI research in legal natural language processing, improving legal case summarization, prediction, and understanding tasks.

##### Legal/Regulatory Judgment and Contract Analysis Data
- Source: AI Hub Dataset 580
- Description: Contains data from over 10,000 legal judgments and contract analyses, with tagging for advantageous/disadvantageous clauses.
- Purpose: Enhances AI performance in understanding legal text structures and identifying critical elements.

#### Download the Dataset

[Download Dataset- 민사](https://github.com/Smart-Legal-Form-Builder/.github/blob/main/01.%EB%AF%BC%EC%82%AC.zip)

[Download Dataset- 형사](https://github.com/Smart-Legal-Form-Builder/.github/blob/main/02.%ED%98%95%EC%82%AC.zip)


#### Optimization

The initial dataset included a broad range of civil and criminal law data, but lacked relevant examples for specific categories like fraud and online defamation. To optimize the RAG system's performance, 1,000 tailored legal cases were generated by filtering and customizing the dataset to improve relevance for categories like online abuse and fraud.

#### Real (Manipulation) Dataset Used in App
[RAG_dataset](https://github.com/Smart-Legal-Form-Builder/.github/blob/main/RAG_dataset.zip)

---


### III. Methodology

#### 1. Model and Environment Setup

The system is built with the following key technologies:

- Flask: A lightweight Python web framework for handling HTTP requests and serving the API.
- OpenAI GPT-4: A large language model for generating human-like responses to legal queries.
- LangChain: A framework for integrating LLMs with external data sources, used for constructing the RAG pipeline.
- FAISS: A library for fast similarity search, used to store and search document embeddings.
- OpenAIEmbeddings: Converts legal documents into vector representations for similarity search.

##### Frontend and Backend Integration:
- Frontend (Flutter): Provides a responsive UI for Android/iOS, handling user input and generating PDF previews.
- Backend (AWS EC2 & Flask): Handles user requests, processes data, and generates legal documents via the Flask API.

##### Environment Setup:
- Python 3.8+ required
- LangChain & FAISS for document retrieval and embedding.
- .env file for securely storing API keys.

#### 2. Dataset Preparation
The RAG system requires a dataset of legal documents in JSON format, each containing:
- Text: Case descriptions
- Metadata: Case category, settlement amount, and sentence length

#### 3. Data Preprocessing and Tokenization
- Text Preprocessing: Clean and structure legal texts for seamless processing.
- Tokenization and Embedding: Legal documents are tokenized and embedded using LangChain and FAISS for efficient retrieval.

#### 4. Legal Document Generation Workflow
A hybrid approach is used to ensure legal document generation:
- Dynamic Templates: Pre-designed templates for legal categories (e.g., fraud, harassment).
- Data Insertion: User-provided data is inserted into the templates.
- Static Sections: Predefined sections for consistency.

#### 5. RAG System Implementation
RAG combines document retrieval and generative AI:
- Retrieval: Relevant legal documents are retrieved from a prebuilt vector store using FAISS.
- Augmentation: Retrieved data is provided as context to GPT-4 for generating responses.

##### Implementation Workflow:
1. User inputs are processed through the frontend and sent to the backend.
2. FAISS searches for relevant documents.
3. Retrieved documents are passed to GPT-4.
4. GPT-4 generates detailed legal advice or draft documents.

##### System Outputs:
- Predicted Settlement Amounts: Based on similar cases.
- Estimated Sentences: Using retrieved data.
- Legal Insights: Tailored advice from the AI legal advisor.
- Source References: Documents used for the response.

#### 6. Dataset Preparation and Customization
Two main datasets were used for training:
- AI Hub Dataset 71723: Over 60,000 annotated legal cases, ensuring balanced representation across legal categories.
- AI Hub Dataset 580: 10,000+ legal judgments and contract documents, with labeled clauses for consumer impact.

##### Customization for Target Categories:
- Datasets were filtered to focus on relevant categories: Fraud in Online Transactions, Sexual Harassment, Online Defamation, and Sexual Assault.
- A customized dataset of 1,000 cases was created to improve accuracy and resolve data imbalance.

##### Data Filtering and Storage:
- Filtering: Relevant cases were selected based on project objectives.
- Storage: Processed data stored in JSON format and indexed using FAISS for fast retrieval.


---

### IV. Evaluation & Analysis

The Smart Legal Form Builder is currently under training, and performance evaluation will take place once the model is fully trained and validated. However, based on current progress, the following evaluation and analysis directions have been established.

#### 1. Evaluation Metrics
Key metrics for evaluating the model’s performance include:
- Accuracy: Measures how closely the generated complaints match predefined templates and meet legal requirements.
- Precision: Evaluates how accurately the model generates legally relevant information in the complaint text.
- Recall: Ensures that all necessary elements, such as complainant details and incident descriptions, are included in the generated complaint text.
- F1-score: Balances precision and recall, providing an overall performance metric.

These metrics will guide the assessment of how effectively the model generates legally compliant and relevant complaints.

#### 2. Initial Results and Analysis
- Initial results show that basic details like complainant and defendant information are being generated accurately.
- However, more complex sections like incident descriptions and legal outcomes require further refinement.
- Data imbalance, particularly in categories such as sexual harassment and assault, is observed, which could affect model accuracy for these cases.

#### 3. Improvement Strategy
To improve the model’s performance, the following strategies will be implemented:
- Data Augmentation: Increase training data for underrepresented categories to improve generalization.
- Hyperparameter Tuning: Optimize hyperparameters like learning rate, batch size, and training epochs.
- Fine-tuning: Specialize the model for different incident types to ensure compliance with legal requirements.

These strategies are expected to enhance model accuracy and legal compliance over time.

#### 4. Initial Challenges
Initial implementation faced challenges due to imbalanced datasets, particularly for case categories like online defamation and harassment, affecting retrieval and generation accuracy.

#### 5. Dataset Optimization
- Customized datasets were created to address data imbalances, with 1,000 tailored legal cases for targeted categories.
- Improved dataset relevance significantly enhanced RAG system performance, especially for categories like fraud and harassment.

#### 6. RAG System Advantages
- Reliability: Pre-retrieved legal data ensures factual and trustworthy outputs.
- Efficiency: Speeds up document drafting, enabling legal complaints to be generated quickly.
- Scalability: RAG's architecture allows easy expansion into additional case types with minimal overhead.


---

### V. Related Work

There have been various studies and projects that have explored AI-based legal document generation and natural language processing (NLP) techniques in the legal domain.

#### 1. Legal Text Generation Using NLP

In recent years, many studies have focused on natural language processing (NLP) for legal text generation, particularly using models like BERT, GPT-2, and T5. These models are used to automatically generate legal documents, such as contracts or complaints, with a focus on generating legally accurate and contextually correct texts. For example, Sutskever et al. (2014) developed Sequence-to-Sequence models for text generation, which have been applied to legal documents in recent years to improve text consistency and legal accuracy.

#### 2. Complaint Generation Using GPT Models

While there has been less research specifically on complaint generation, the GPT model has been applied to legal document generation. Studies using GPT-3 for text generation have shown promising results in generating complaints, contracts, and judgments. However, these models still face challenges in maintaining legal accuracy and ensuring that the generated text fully meets legal standards, which often requires expert legal review.

#### 3. Challenges in Legal Document Automation

A significant challenge in automating legal documents is ensuring legal accuracy and compliance with legal standards. Several projects, such as Deep Legal and LexPredict, have attempted to address these challenges by using machine learning and NLP technologies to improve the generation of legal documents, particularly by ensuring legal terms and document structure are properly understood and followed.

#### 4. Legal Document Automation Platforms

Several popular legal document automation platforms offer tools for creating, managing, and storing legal documents. These platforms use pre-built templates and guided questionnaires to help users create customized legal documents, similar to the AI-driven approach used in this project. Some notable platforms include:

- Rocket Lawyer: A versatile platform that provides users with tools to create, manage, and store legal documents. It offers a variety of pre-built templates for common legal needs, including contracts, leases, and wills. The platform streamlines document creation with guided questionnaires, allowing users to customize templates with case-specific details. Rocket Lawyer also connects users with licensed attorneys to provide on-demand legal advice and document reviews, offering a balance of automation and human assistance.
  
- LegalZoom: One of the most well-known platforms for creating personalized legal documents online. It offers an extensive library of templates and provides users with a guided process to input relevant details and create custom documents for personal and business use. LegalZoom’s services extend beyond document creation, including trademark registration, business formation assistance, and access to expert legal advice. While not specialized in complaints handling, LegalZoom is a great solution for individuals and businesses looking for efficient and accessible legal tools.
  
- LawDepot: A platform that enables users to create legal documents quickly and efficiently. It offers a wide range of customizable templates, including contracts, agreements, and estate planning documents. By answering a series of guided questions, users can create documents tailored to their specific situation. LawDepot is especially useful for individuals seeking a cost-effective solution for everyday legal matters without the need for professional assistance.

These platforms, like the Smart Legal Form Builder, aim to simplify the legal document creation process, making legal services more accessible and affordable. However, while these platforms focus on user-driven document creation, the Smart Legal Form Builder aims to automatically generate legal complaints, offering a more hands-off solution that can enhance efficiency and accuracy for users with less legal expertise.

---

### VI. Conclusion: Discussion

In this research, the Smart Legal Form Builder was developed using the GPT-2 model to automate the generation of legal complaints. The model focuses on filling in the required information such as complainant details, defendant information, incident description, and complaint intent, based on structured templates.

#### Key Findings:
- The model has generated complaints with basic information (e.g., complainant details, defendant details) with high accuracy.
- However, the incident description and legal outcomes sections still need improvement in terms of accuracy and legal compliance.

#### Future Directions:
To improve the model's performance, we plan to augment the dataset to address data imbalance, especially for categories like sexual harassment and assault. Additionally, fine-tuning the model for different legal cases and optimizing hyperparameters will help improve its overall performance. Legal accuracy will be a key focus of further improvements, with an emphasis on incorporating expert legal reviews.

The Smart Legal Form Builder presents a significant step toward automating legal document generation. By improving its accuracy and generalization, this model has the potential to make legal services more accessible and efficient for individuals, especially in cost-sensitive legal contexts.


## 📗 Related Documents
[Smart Legal Form Builder PPT](https://github.com/Smart-Legal-Form-Builder/Document/blob/main/%EC%9D%B8%EA%B3%B5%EC%A7%80%EB%8A%A5%20%EB%B0%8F%20%EC%9D%91%EC%9A%A9%20ppt_%EC%B5%9C%EC%A2%85.pdf)  

[Smart Legal Form Builder Report](추후 추가 예정)
