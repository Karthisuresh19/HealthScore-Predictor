# HealthScore-Predictor

A predictive data-driven framework designed to forecast restaurant health inspection scores and identify establishments at higher risk of violations using modern machine learning models.

---

## Overview

Health inspections are typically reactive—conducted periodically or only in response to complaints. **HealthScore-Predictor** explores whether machine learning models can proactively identify restaurants likely to fail inspections by analyzing:
- Historical violation patterns.
- Restaurant characteristics.
- Public perception metrics (e.g., Google Reviews).

By integrating official **San Francisco Health Inspection Scores** (2024-current) with public **Google restaurant data**, this system provides early warnings and actionable insights into restaurant health compliance.

---

## Key Features

### Data Integration
- **Multi-source Data Fusion:** Seamlessly links official San Francisco health inspection records with Google Places data.
- **Advanced Matching Algorithm:** Employs fuzzy string matching (RapidFuzz), geographic proximity (Haversine distance via Geopy), and address canonicalization to bridge disparate datasets.

### Machine Learning Pipeline
- **Multiple Model Architectures:** Implements Random Forest, XGBoost, and Gradient Boosting algorithms to predict inspection outcomes.
- **Robust Evaluation:** Extensively evaluated using stratified cross-validation, ROC-AUC, precision, recall, and F1-score.
- **Class Imbalance Handling:** Uses resampling techniques (imbalanced-learn) and class weighting to address real-world dataset skewness.

### Temporal Analysis
- **Strict Time-based Validation:** Prevents data leakage by ensuring models strictly use information available at prediction time.
- **Trend Detection:** Evaluates violation trajectory and seasonal variations in inspection capabilities.

---

## Technical Stack

### **Data Science & ML Core**
- **Python 3.x:** Core programming language
- **Pandas & NumPy:** Data manipulation
- **Scikit-learn & XGBoost:** Machine learning algorithms
- **Imbalanced-learn:** Resampling tools
- **Matplotlib & Seaborn:** Data visualization
- **RapidFuzz & Geopy:** Entity matching & geospatial analysis

### **Frontend Dashboard**
- **React (v19):** Modern component-based web interface
- **Recharts:** Interactive data visualization components
- **React-Leaflet:** Web mapping for restaurant locations

---

## Project Structure

```text
HealthScore-Predictor/
├── data/                  # Raw and processed datasets
├── notebooks/             # Jupyter notebooks for experimentation and analysis
├── backend/               # Python API for model inference and serving
├── dashboardv1/           # React-based interactive web dashboard
├── main.ipynb             # Core analysis & model training notebook
├── requirement.txt        # Machine learning dependencies
└── README.md              # Project documentation
```

---

## Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/LkNeha/HealthScore-Predictor.git
cd HealthScore-Predictor
```

### 2. Backend & Data Pipeline Setup
Ensure you have Python 3.x installed, then set up your environment:

```bash
# It is recommended to use a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows use: .venv\Scripts\activate

# Install the necessary ML & backend packages
pip install -r requirement.txt
```

### 3. Frontend Dashboard Setup
To run the React dashboard locally:

```bash
cd dashboardv1

# Install dependencies
npm install

# Start the development server
npm start
```
The application will be accessible at `http://localhost:3000`.

---

## Methodology

1. **Data Collection & Integration:** Gathered SF Health Data and Google Places info. Unified matching across disparate restaurant identifiers.
2. **Feature Engineering:** Extracted temporal trends, historical violation behaviors, categorical cuisine types, and contextual risk indicators.
3. **Addressing Challenges:** Mitigated temporal leakage via strict index splitting and countered class imbalance using class weights and over/under-sampling techniques.
4. **Model Development:** Progressed from statistical baselines to parameter-tuned ensemble classifiers (RF, XGBoost).
5. **Evaluation:** Extracted critical feature importance (e.g., proving previous critical violations and rating aggregates accurately forecast future failures).

---

## Future Enhancements

- [ ] Incorporate additional data dimensions (local weather, foot traffic, neighborhood events).
- [ ] Implement full deep-learning sequence models for better time-series pattern recognition.
- [ ] Add explainability features like SHAP or LIME for stakeholder trust.
- [ ] Deploy the complete API + Dashboard via Docker/Cloud platform for public access.


- **Contributors** - See [contributors](https://github.com/LkNeha/HealthScore-Predictor/graphs/contributors) list


## License & Acknowledgments

- **Data Sources:** We thank the San Francisco Department of Public Health and Google for the public data enabling this research.
- **License:** Distributed for educational/research purposes. Check with the repository owners for specific licensing info.

> **Note:** Developed explicitly to demonstrate applied machine learning within public health and safety domains.
