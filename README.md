# 🔍 Dev‑Docs Link Classifier

A binary classifier pipeline that determines whether a given URL (along with its title and snippet) points to **developer documentation** or not. All code, dataset creation, preprocessing, model training, and inference are included.

---

## 📘 Problem Statement

**Input**: `link` (URL), `title` (page title), `snippet` (short text snippet)  
**Output**: Binary label —  
- `1`: Developer documentation (e.g., official API pages, tutorials, guides)  
- `0`: Non‑dev content (e.g., blog, marketing, forums)

This is useful for filtering and prioritizing dev docs in search tools, knowledge bases, or RAG systems.

---

## 🗃️ Dataset

Data is **collected and labeled from scratch**, with columns:
- `url`: Full URL
- `url_length`: Length of the URL in characters.
- `path_depth`: Number of segments in the URL path.
- `has_query`: `1` if the URL contains a query string (`?`), else `0`.
- `has_keyword`: `1` if the URL contains common dev-related keywords (e.g., `docs`, `api`, `reference`), else `0`.
- `has_docs_subdomain`: `1` if the subdomain includes 'docs' (e.g., `docs.python.org`), else `0`.
- `code_count`: Number of code snippets extracted from the page.
- `tech_keyword_count`: Count of tech-related terms found in the page.
- `content_length`: Length of extracted HTML/text content (in characters).
- `has_table`: `1` if a `&lt;table&gt;` tag is present in the content, else `0`.

- `is_dev_docs`: 1 for dev docs, 0 otherwise

🔗 **Kaggle dataset**: _[https://www.kaggle.com/datasets/iamfaham/developer-doc-urls-vs-non-developer-urls-dataset?select=url_dataset_enhanced.csv]_  
The dataset CSV should be named `url_dataset_enhanced.csv`.

---

## 🧠 Model Training (`binary_classification.ipynb`)

- Loads the CSV dataset
- Splits into train/test (default 80/20)
- Trains a **Logistic Regression** classifier
- Evaluates performance: accuracy, classification report, confusion matrix
- Outputs:
  - `scaler_content.pkl`  
  - `classifier_model_content.pkl`

---

## 📈 Results

Accuracy: 0.96

Use binary_classification.ipynb to compute & print these metrics.

## 📂 Project Structure
```bash
dev-docs-classification/
├── url_dataset_enhanced.csv        
├── binary_classification.ipynb                         
├── data_gathering.ipynb                       
├── scaler_content.pkl                  
├── classifier_model_content.pkl             
└── feature_engineering.ipynb
```

## 💾 Pretrained Files
You can host your pickle files on Hugging Face for shared access:

🔗 scaler_content.pkl: [add link here]
🔗 classifier_model_content.pkl: [add link here]

## 🧑‍💻 Author
Built by Faham (@iamfaham) – making dev‑docs classification smarter.
