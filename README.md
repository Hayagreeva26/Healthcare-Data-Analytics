
📌 Overview
A reference architecture for **healthcare data analytics**, integrating EHR/claims data, validating ICD/CPT codes, and training predictive models (e.g., appointment no-shows).

**Note:** This repo uses synthetic data — do not store PHI in public repositories.

🏗 Architecture
```
        EHR / Claims Data
                |
         +------v------+
         | Ingestion   | <- src/etl/ingest_ehr.py
         +------^------+
                |
         +------v------+
         | Validation  | <- src/etl/validation.py
         +------^------+
                |
         +------v------+
         | ML Models   | <- src/models/no_show_model.py
         +-------------+
```

🔧 Tech Stack
- **Python 3.10+**
- **AWS S3**, **PostgreSQL**
- **Pandas**, **Scikit-learn**, **Prophet**
- **pytest**, **GitHub Actions**

📂 Project Structure
```
healthcare-analytics-platform/
├── src/
│   ├── etl/
│   ├── models/
│   └── dashboard/
├── infra/terraform/
├── tests/
├── .env.example
├── requirements.txt
└── README.md
```

⚙️ Setup
```bash
git clone https://github.com/<your-username>/healthcare-analytics-platform.git
cd healthcare-analytics-platform
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

🚀 Usage
- **Validate ICD codes**:
  ```bash
  python src/etl/validation.py --file sample_claims.csv
  ```
- **Train no-show model**:
  ```python
  from src.models.no_show_model import train_no_show
  model, auc = train_no_show(df)
  print("Model AUC:", auc)
  ```

🧪 Testing
```bash
pytest -q
```

⚡ CI/CD
- GitHub Actions runs tests automatically
- Terraform folder contains placeholder infra for AWS

📈 Future Improvements
- Real-time streaming ingestion
- HIPAA-compliant access controls
- Interactive dashboards for care KPIs
