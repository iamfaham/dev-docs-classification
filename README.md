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

## ⚙️ Processing & Features

Code in `utils.py` handles:
- Merging `link`, `title`, `snippet`
- Lowercasing, removing HTML tags, punctuations, and stopwords
- TF-IDF vectorization using `TfidfVectorizer`

---

## 🧠 Model Training (`binary_classification.ipynb`)

- Loads the CSV dataset
- Splits into train/test (default 80/20)
- Trains a **Logistic Regression** classifier (`sklearn.linear_model`)
- Evaluates performance: accuracy, classification report, confusion matrix
- Outputs:
  - `scaler_content.pkl`  
  - `classifier_model_content.pkl`

---

## 📈 Results
You can report results in the README. Include final train/test accuracy and AUC if available:

Accuracy: 0.95
ROC-AUC: 0.98
Use binary_classification.ipynb to compute & print these metrics.

## 📂 Project Structure
```bash
dev-docs-classification/
├── data/
│   └── dev_links_dataset.csv        # Labeled dataset (Kaggle)
├── utils.py                         # Preprocessing tools
├── train.py                         # Training & evaluation pipeline
├── predict.py                       # Inference (single/batch)
├── vectorizer.pkl                  # Saved TF-IDF vectorizer
├── logistic_model.pkl              # Saved trained model
└── requirements.txt
```

## 💾 Pretrained Files
You can host your pickle files on Hugging Face for shared access:

🔗 vectorizer.pkl: [add link here]
🔗 logistic_model.pkl: [add link here]

##🔧 Future Enhancements
Replace TF-IDF + Logistic Regression with transformers (e.g. DistilBERT) for better context understanding

Extend to multiclass (e.g. categorize dev doc types: AWS, Python, React)

Add a FastAPI or Gradio frontend for interactive classification

## 🧑‍💻 Author
Built by Faham (@iamfaham) – making dev‑docs classification smarter.

---

### ✅ Next Steps:
- Upload `dev_links_dataset.csv` to **Kaggle** and paste the link in the dataset section.
- Upload `vectorizer.pkl` & `logistic_model.pkl` to **Hugging Face** and insert the URLs.
- Run `train.py` to generate final evaluation metrics and add them to **📈 Results**.

Once you've done that, I can update the links and badges for you! Let me know if you want help creating the badges or instructions.
::contentReference[oaicite:0]{index=0}
