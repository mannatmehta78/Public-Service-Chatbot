Multilingual Government Chatbot — Hybrid NLP Modeling under Noisy Conditions

A benchmarking-driven study and implementation of robust intent classification models for multilingual, noisy user queries in Indian public service chatbots.

📌 Project Summary

India’s digital public service ecosystem serves hundreds of millions of users, many of whom interact using Hinglish (code-mixed Hindi + English) and informal, error-prone text.

Most NLP systems are trained on clean, monolingual English, creating a critical gap between real-world input and system capability.

This project addresses that gap by:

Benchmarking classical, deep learning, and transformer models
Evaluating performance under synthetic real-world noise
Proposing a confidence-weighted hybrid ensemble for robust intent classification
🎯 Key Contributions
📊 First systematic comparison of SVM, BiLSTM, and BERT under noisy multilingual conditions
🌐 Custom trilingual dataset (English + Hindi-Latin + Hinglish)
⚙️ Noise Injection Framework simulating real mobile typing behavior
📉 Introduction of ΔAcc (Delta Accuracy) — a metric for noise robustness
🤖 Hybrid Ensemble Model outperforming all individual models
🏗️ System Architecture
User Query
   ↓
Preprocessing
   ↓
 ┌───────────────┬───────────────┬───────────────┐
 │     SVM       │    BiLSTM     │     BERT      │
 │  (TF-IDF)     │ (Sequential)  │ (Transformer) │
 └───────────────┴───────────────┴───────────────┘
              ↓
   Confidence-Weighted Ensemble
              ↓
     Final Intent Prediction
📊 Datasets
🔹 Domain-Specific Dataset
~5,000 queries
15 intent classes
Language distribution:
40% English
30% Hindi (Latin script)
30% Hinglish
🔹 CLINC150 Benchmark
22,500 training samples
150 intent classes
Clean English dataset
🔍 Noise Modeling

To simulate real-world user behavior, noise was injected into 30% of test data:

Noise Type	Description	Example
Orthographic	Typing errors	passort
Phonetic	Romanized variations	zaroorat / jarurat
Informal Syntax	Fragmented queries	pan card apply
Lexical Shift	Abbreviations	govt, docs
🤖 Models Implemented
🔹 Support Vector Machine (SVM)
TF-IDF (unigrams + bigrams)
Strong performance in low-data, noisy settings
CPU-efficient
🔹 BiLSTM
Sequential deep learning model
High sensitivity to noise
Weak generalization
🔹 BERT (bert-base-uncased)
Transformer-based contextual model
Excellent performance on large, clean datasets
Requires more data and compute
🔹 Hybrid Ensemble (Proposed)
Confidence-weighted aggregation
Weights:
BERT → 0.5
BiLSTM → 0.3
SVM → 0.2
Combines strengths of all models
📈 Results
🔸 Domain Dataset (Noisy Conditions)
Model	Accuracy	ΔAcc ↓
SVM	0.43	0.55
BERT	0.37	0.63
BiLSTM	0.14	0.84
Hybrid	0.45	0.54
🔸 CLINC150 Benchmark
Model	F1 Score
SVM	0.80
BERT	0.87
BiLSTM	0.69
Hybrid	0.88
🔥 Key Insights
⚡ Crossover Effect:
SVM > BERT in noisy, low-resource settings
BERT > SVM in large, clean datasets
❌ BiLSTM is consistently the weakest performer
✅ Hybrid model is the most reliable across all conditions
📏 Evaluation Metrics
Accuracy
Precision / Recall
F1 Score
ΔAcc (Delta Accuracy) → measures performance drop under noise
⚙️ Installation
python -m venv chatbot_env
chatbot_env\Scripts\activate

pip install scikit-learn tensorflow transformers nltk pandas numpy
▶️ Usage
1. Preprocessing
python preprocess.py
2. Train Models
python train_svm.py
python train_bilstm.py
python train_bert.py
3. Run Hybrid Inference
python hybrid_inference.py --query "mera aadhaar update kaise kru"
💡 Deployment Recommendations
Use Case	Recommended Model
Low data + noisy input	SVM
Large-scale platforms	BERT
High-stakes services	Hybrid + human fallback
Edge devices	SVM / distilled model
⚠️ Limitations
No Devanagari script support
Synthetic noise (not real production logs)
Single-turn intent classification only
🚀 Future Work
Integrate MuRIL / IndicBERT
Adaptive ensemble weighting
Real-world query log evaluation
Model compression for edge deployment
Multi-turn conversational modeling
👩‍💻 Authors
Mannat Mehta
Yugam Rana
Prabjot Singh Bali
📜 License

Academic project submitted to Chandigarh University.
For educational and research purposes only.

🙏 Acknowledgment

We sincerely thank our supervisor and Chandigarh University for their guidance and support throughout this project.
