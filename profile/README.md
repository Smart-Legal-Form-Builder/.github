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


---

# Project Overview

This project initially aimed to develop a service that automatically generates legal complaint documents using AI. However, it became clear that establishing a consistent template format was more efficient. As a result, the project direction shifted to a template-based complaint drafting approach. To maintain and enhance the utilization of AI within the service, RAG (Retrieval-Augmented Generation) was integrated to provide legal consultation functionalities.

---

## Key Features Overview

### Initial Goals and Implementation Flow

- **Initial Goal**: Automatic generation of legal complaints using AI  
  - Attempted to integrate GPT models for complaint drafting  
  - Quality was not up to the desired standards

- **Revised Goal**: Utilize AI to generate high-quality complaint templates and then fill in required fields  
  - Achieving a consistent template format purely through LLM models proved challenging  
  - Managing static components like templates through code was more advantageous

After these adjustments, the reliance on AI decreased. To counterbalance this, AI-driven legal consultation features were introduced.

---

### AI Utilization Plan

- **Legal Consultation with RAG Integration**  
  - Use a legal case database and RAG to provide reference information for each incident  
  - Offer estimated settlement amounts and sentencing guidelines  
  - Provide simple legal advice via AI

With this approach, the static template creation is handled through code, while functions such as legal consultation, settlement and sentencing predictions, and case recommendations leverage RAG technology and GPT API integration.

---

## Dataset Composition and Utilization

(Leave this section as is)

### Dataset Example

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
    "keywords": ["SNS", "외모 비하", "모욕"]
},
{
    "id": 1,
    "category": "중고거래 사기",
    "text": "피고인은 고급 레시피 책을(를) 거래 후기 사이트를 조작해 피해자를 유인하며 피해자로부터 389000원을 송금받고, 이후 잠적했다.",
    "settlement": 583039,
    "sentence": 8,
    "verdict_summary": "고급 레시피 책 판매 사기 혐의로 징역 8개월, 합의금 583039원 선고.",
    "keywords": ["고급 레시피 책", "중고거래", "사기"]
}
```

---

## RAG Technology Overview

RAG (Retrieval-Augmented Generation) combines large language models with external databases (e.g., case law, legal statutes) to improve response accuracy. The model first searches for relevant data (Retrieval), then uses a generative model (Generation) to produce reliable answers based on the retrieved documents.

### Implementation Details

1. **Data Retrieval**:  
   - Embed the case law dataset and store it in FAISS for vector search  
   - Quickly retrieve relevant cases based on similarity to the user query

2. **Augmented Generation**:  
   - Provide the retrieved case summaries as context to the GPT model  
   - Generate a legal complaint draft, estimate settlement amounts and sentencing, and offer simple legal advice  
   - Employ prompt engineering, designating the model as a “lawyer” for more authoritative and specialized responses

### Example Workflow

- User Query: "Please find cases applicable to a physical assault incident that took place in Seoul’s Gangnam district on December 1, 2024."
- RAG Process:
  1. Perform a vector similarity search in the case law database for “physical assault”  
  2. Provide the relevant cases to GPT as context  
  3. GPT drafts a complaint and provides legal explanations based on retrieved cases

This ensures the user obtains legally grounded documentation derived from the latest and most relevant case law.

Below is the "Failure Report" section translated into English while maintaining the original structure and format. The dataset section and the rest of the content remain unchanged.

---

## Failure Report

During the development of this project, two specific failure cases were encountered. Documenting these failures aims to help prevent similar issues in the future and to explore more effective solutions.

### Failure Case 1: Technical and Model-Related Limitations in GPT-2 Fine-Tuning

Initially, the plan was to fine-tune GPT-2 to directly produce complaint documents in the desired legal format. To achieve this, we attempted to fine-tune KoGPT-2 (a Korean-adapted GPT-2 model distributed by SKT via gluonnlp) based on the following repository: [KoGPT2-FineTuning](https://github.com/gyunggyung/KoGPT2-FineTuning). However, we encountered the following problems:

- **Technical Constraints (Problem 1)**  
  - Operating environment: GTX-3070Ti, CUDA 12.3  
  - Using PyTorch compatible with CUDA 12.3 required Python 3.8 or higher  
  - KoGPT-2 fine-tuning required MXNet (a C++ library), but the compatible NumPy version for MXNet did not align with Python 3.8  
  This led to complex attempts at resolving library version conflicts, switching GPUs or machines, and other workarounds.

- **Model Characteristics (Problem 2)**  
  - GPT-2 was originally designed as a context expansion model rather than a dialog-based model. While it can generate long text from short prompts, it is difficult to ensure it produces a strictly formatted document (e.g., a legal complaint template).  
  Even with successful fine-tuning, achieving the exact formatting requirements was challenging.

Due to these issues, we abandoned the GPT-2 approach and shifted our focus to fine-tuning GPT-3.5.

### Failure Case 2: Training Failures in the GPT-3.5 Fine-Tuning Environment

GPT-3.5 can be tuned on OpenAI’s Playground without additional code, relying solely on hyperparameters and datasets (prompts). The following steps were taken:

- **Dataset Preparation**: Created a dataset suitable for GPT-3.5 (approximately 500 examples, referenced from the AI_for_dataset repository).
- **Hyperparameter Settings**:  
  1) Learning Rate: Set to 2, aiming to minimize the loss function effectively.  
  2) Epochs: Set to 3, as repeatedly training the entire dataset too many times could lead to overfitting.  
  3) Batch Size: Set to 1 to process the data in the smallest possible increments, ensuring more granular training.

However, after completing the first epoch, OpenAI returned a training execution error. Subsequently, all models under training failed, forcing the abandonment of the project. This outcome was disappointing, and if anyone reading this has insights or suggestions, we encourage them to reach out to a team member via email.
![image](https://github.com/user-attachments/assets/4c3396f0-9f6a-4438-a4b5-40b954e23814)
![image](https://github.com/user-attachments/assets/7c88b516-57cd-4bd3-bef0-3c6139a6b47c)
![image](https://github.com/user-attachments/assets/f2133d90-36f7-448e-a70a-1703bb14bd29)

---


## 📗 Related Documents
[Smart Legal Form Builder PPT](https://github.com/Smart-Legal-Form-Builder/Document/blob/main/%EC%9D%B8%EA%B3%B5%EC%A7%80%EB%8A%A5%20%EB%B0%8F%20%EC%9D%91%EC%9A%A9%20ppt_%EC%B5%9C%EC%A2%85.pdf)  

[Smart Legal Form Builder Report](https://github.com/Smart-Legal-Form-Builder/Document/blob/main/Smart%20Legal%20Form%20Builder%20Report.pdf)
