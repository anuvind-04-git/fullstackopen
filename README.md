AI-Driven Threat Detection
This repository contains an end-to-end AI-driven Threat Detection System. It trains an Isolation Forest model on security log features to identify and flag anomalous network activity. The project includes a complete pipeline from data preprocessing to a REST API and a web-based dashboard for real-time scoring.Key Componentssrc/preprocess.py: Cleans raw log data and extracts relevant features for the model.src/train.py: Trains the unsupervised Isolation Forest model and an optional supervised Random Forest model for performance evaluation.src/api.py: A Flask-based REST API that serves the trained model for scoring new data. It also hosts the web dashboard.src/static/index.html: A clean, professional web dashboard for manually testing the model and visualizing results.src/stream_agent.py: Simulates real-time log analysis by continuously feeding new data to the API.Project Structureai-threat-detection/
├── .venv/                      # Python virtual environment
├── data/
│   ├── interim/                # Cleaned, intermediate data files
│   ├── processed/              # Final ML-ready datasets
│   └── raw/                    # Original raw data (e.g., CSV logs)
├── models/
│   ├── isoforest.joblib        # Trained Isolation Forest model
│   └── scaler_unsup.joblib     # Data scaler
├── src/
│   ├── __init__.py             # Makes 'src' a Python package
│   ├── api.py                  # REST API and dashboard server
│   ├── config.py               # Project configuration (paths, columns)
│   ├── features.py             # Feature engineering helper functions
│   ├── infer.py                # Command-line interface for inference
│   ├── preprocess.py           # Data preprocessing script
│   ├── stream_agent.py         # Real-time log streaming agent
│   └── train.py                # Model training script
├── .gitignore                  # Specifies files/folders to ignore in Git
├── README.md                   # Project overview and instructions
└── requirements.txt            # Project dependencies
InstallationClone the repositorygit clone [https://github.com/yourusername/ai-threat-detection.git](https://github.com/yourusername/ai-threat-detection.git)
cd ai-threat-detection
Set up the environmentCreate a Python virtual environment and install the required packages.python -m venv .venv
# On Windows
.venv\Scripts\activate
# On macOS/Linux
source .venv/bin/activate

pip install -r requirements.txt
Prepare the dataPlace a security log dataset (e.g., simlog.csv or a split from UNSW-NB15) into the data/raw/ folder. The preprocessing script will handle it from there.Run the pipelineExecute these commands in order to preprocess the data, train the models, and start the API.python -m src.preprocess
python -m src.train
python -m src.api
Once the API is running, open your web browser and navigate to http://127.0.0.1:8000 to see the dashboard.Project Demo & EvaluationDashboard Demo: Use the web dashboard to manually input different values and observe how the anomaly score changes. You can demonstrate a "normal" case and a highly "anomalous" case.Performance Metrics: If you use a dataset with labels, you can use the src/train.py output to discuss model performance in terms of Precision, Recall, and AUC.
