# MLOPS Project: Fake News Detection using SVM | Docker + AWS Lambda + FastAPI

![Python](https://img.shields.io/badge/Python-3.9-blue)  
![Docker](https://img.shields.io/badge/Docker-ready-blue)  
![AWS Lambda](https://img.shields.io/badge/AWS-Lambda-orange)  
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

This project is an end-to-end machine learning deployment pipeline that detects fake news using a Support Vector Machine (SVM) model and serves predictions via a serverless API using AWS Lambda and FastAPI.

---

## 📌 Project Overview

- Trained a machine learning model to classify news articles as real or fake  
- Applied TF-IDF vectorization for text preprocessing  
- Containerized the app using Docker  
- Deployed the container on AWS Lambda using Amazon ECR  
- Exposed a REST API using FastAPI, integrated with Lambda using Mangum

---

## 📁 Folder Structure

```
deploy-ml-model-aws-lambda-docker-main/
├── deploy/
│   ├── app.py                 # FastAPI app for inference
│   ├── Dockerfile             # Container setup
│   ├── news_model.pkl         # Trained SVM model
│   ├── tfidf_vectorizer.pkl   # Pre-fitted vectorizer
│   └── requirements.txt       # Python dependencies
├── train.py                   # Model training script
├── invoke_api.py              # Script to invoke Lambda endpoint
├── sample.json                # Sample input for testing
├── True.csv / Fake.csv        # Datasets
```

---

## 🧰 Tech Stack

- **Machine Learning**: Python, scikit-learn, SVM, TF-IDF  
- **API Framework**: FastAPI, Pydantic  
- **Deployment**: Docker, AWS Lambda, Amazon ECR  
- **Integration**: Mangum (FastAPI + Lambda), Uvicorn

---

## ⚙️ Setup & Usage

### 1. Train the Model

```bash
python train.py
```

Generates:
- `news_model.pkl`  
- `tfidf_vectorizer.pkl`

### 2. Build Docker Image

```bash
docker build -t fake-news-detector .
```

### 3. Push to Amazon ECR

Tag and push your image using AWS CLI as per [AWS documentation](https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-push-ecr-image.html).

### 4. Deploy to AWS Lambda

- Create a Lambda function from the ECR image  
- Set the handler to: `app.handler`

### 5. Test the Endpoint

```bash
python invoke_api.py
```

Or use Postman with the following input:

---

## 🧪 Sample Input (`sample.json`)

```json
{
  "title": "Breaking News: Major Event Unfolds",
  "text": "Details are emerging about a significant event that is currently developing."
}
```

### ✅ Expected Output

```json
{
  "prediction": "FAKE"
}
```

---

## 🚀 Live Demo

You can **view the demo API's interactive Swagger documentation** at:  
[https://alaqswk3bilncbhkj63mtowwei0bovnm.lambda-url.ap-south-1.on.aws/docs](https://alaqswk3bilncbhkj63mtowwei0bovnm.lambda-url.ap-south-1.on.aws/docs)

> ⚠️ *Note: This is a demo URL and is currently non-functional, as the associated AWS Lambda resources have been terminated.*

---

## 📊 Dataset

Used dataset: [Fake News Detection Dataset by emineyetm](https://www.kaggle.com/datasets/emineyetm/fake-news-detection-datasets)  
Contains labeled news articles categorized as 'FAKE' and 'REAL', suitable for binary classification.

---

## 🤝 Contributing

Feel free to fork the repository, open issues, or suggest improvements. I’m open to feedback and collaboration.

---

## 📬 Contact

For questions or collaborations, feel free to reach out via [LinkedIn](https://www.linkedin.com/in/humaila-muhammad-farooq).

---

## 🙏 Acknowledgements

- FastAPI  
- Docker  
- AWS Lambda  
- scikit-learn  

---

## 📄 License

This project is licensed under the **MIT License**.  
You are free to use, modify, and distribute this code with proper attribution.

See the [LICENSE](./LICENSE) file for full details.


Let me know if you'd like to add GitHub Actions badges, coverage reports, or contributor guidelines next. I can help you make this repo sparkle for recruiters and collaborators alike.
