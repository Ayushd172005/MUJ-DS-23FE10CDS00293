# Batch F NLP Capstone — Training Repository

## Training Profile

- **Name:** Ayush Dudhat
- **Registration Number:** 23FE10CDS00293
- **Branch:** Computer Science & Engineering (Data Science specialization)
- **Batch:** F
- **Project Title:** Sentinel AI — Continuous Audit Intelligence
- **GitHub Username:** [Ayushd172005](https://github.com/Ayushd172005)
- **Training Program:** Batch F NLP Capstone Project Training Program, Manipal University Jaipur

## Repository Navigation

- [Assignments](assignments/)
- [Notebooks](notebooks/)
- [Code](code/)
- [Resources](resources/)
- [Presentations](presentations/)
- [Capstone](capstone/)
- [Contribution and weekly update workflow](CONTRIBUTING.md)
- [Final submission checklist](SUBMISSION_CHECKLIST.md)

> This personal repository is being organized to meet Steps 4–12 of the Batch F Capstone Project Guidelines. The existing Sentinel AI project documentation below is retained.

---

# NLP PROJECT

# 🛡️ Sentinel AI — Continuous Audit Intelligence

> **From 100% of transactions to a small, explainable, evidence-backed investigation queue.**
 
Sentinel AI is an **AI-assisted continuous-audit intelligence platform** designed to help auditors and financial-risk teams identify, prioritize, investigate, and document suspicious transaction activity.

Instead of stopping at an anomaly or fraud score, Sentinel AI connects the complete investigation workflow:


100% Transaction Population
            ↓
Risk Signals + Business Use Cases
            ↓
Prioritized Risk Queue
            ↓
Evidence + Counter-Evidence
            ↓
AI-Assisted Investigation
            ↓
Auditor Decision
            ↓
Persistent Audit Trail

Detection tells us where to look. Evidence tells us why. The auditor decides what happens next.

📌 Project Overview

Financial institutions process extremely large transaction populations. Reviewing every transaction manually is impractical, while conventional anomaly-detection systems often leave auditors with a risk score but limited investigative context.

Sentinel AI addresses this gap by combining:

Machine-learning anomaly detection
Statistical and behavioural analysis
Rule-based signals
Network intelligence
Mentor-aligned business use cases
Evidence retrieval
Supporting and counter-evidence
AI-assisted investigation
Human-in-the-loop decision making
Persistent audit trails

The objective is not to replace auditors.

The objective is to compress a large transaction population into a smaller, explainable investigation queue so auditors can spend more time making decisions and less time searching for context.

🎯 Business Problem

Traditional transaction-monitoring and audit workflows face several challenges:

1. Scale

Large transaction populations make exhaustive manual review impractical.

2. Alert overload

Simple threshold or anomaly-based systems can generate large numbers of alerts without sufficient prioritization.

3. Lack of investigative context

A high-risk score does not automatically explain:

Why the transaction is unusual
Which signals contributed to the risk
Whether similar behaviour occurred previously
What evidence supports the concern
What evidence argues against the concern
4. Investigation fragmentation

Detection, evidence collection, investigation, and final auditor decisions can exist in disconnected systems.

💡 Sentinel AI's Solution

Sentinel AI creates a continuous audit workflow that connects detection to investigation.

Step 1 — Analyze the transaction population

The system processes the available transaction population rather than relying on a manually selected sample.

Step 2 — Generate multiple risk signals

Transactions are evaluated using complementary ML, statistical, behavioural, rule-based, and network signals.

Step 3 — Prioritize

The risk engine combines the signals into a prioritized investigation queue.

Step 4 — Explain

The system provides reason codes and signal drivers explaining why a transaction was prioritized.

Step 5 — Retrieve evidence

Relevant historical and contextual evidence is retrieved while respecting transaction-time constraints.

Step 6 — Compare both sides

The investigation includes both:

Supporting Evidence

and

Counter-Evidence

This prevents the workflow from treating an anomaly as automatic proof of wrongdoing.

Step 7 — Assist the auditor

An AI-assisted investigation layer generates a structured investigation assessment.

Step 8 — Preserve accountability

The auditor makes the final decision, which is persisted in the audit trail.

🏗️ System Architecture
                         ┌──────────────────────┐
                         │ Transaction Dataset  │
                         │   100% Population     │
                         └───────────┬──────────┘
                                     │
                                     ▼
                    ┌────────────────────────────┐
                    │ Feature & Signal Layer     │
                    │                            │
                    │ ML • Rules • Benford       │
                    │ Behaviour • Temporal       │
                    │ Network • Use Cases        │
                    └──────────────┬─────────────┘
                                   │
                                   ▼
                    ┌────────────────────────────┐
                    │       Risk Engine           │
                    │                            │
                    │ Signal Fusion + Ranking    │
                    └──────────────┬─────────────┘
                                   │
                                   ▼
                    ┌────────────────────────────┐
                    │       Risk Queue            │
                    │                            │
                    │ Prioritized Cases           │
                    └──────────────┬─────────────┘
                                   │
                                   ▼
              ┌────────────────────────────────────────┐
              │          Investigation Layer           │
              │                                        │
              │ Transaction Context                    │
              │ Risk Signals                           │
              │ Historical Behaviour                   │
              │ Supporting Evidence                    │
              │ Counter-Evidence                       │
              └───────────────────┬────────────────────┘
                                  │
                                  ▼
                    ┌────────────────────────────┐
                    │      Auditor Decision       │
                    │                            │
                    │ Review / Escalate / Clear │
                    └──────────────┬─────────────┘
                                   │
                                   ▼
                    ┌────────────────────────────┐
                    │       Audit Trail           │
                    │                            │
                    │ Investigation + Decision   │
                    └────────────────────────────┘
🎯 Mentor-Aligned Business Use Cases

The final Sentinel AI prototype focuses on three highlighted business scenarios.

1. 📱 New Device + High-Value Transaction

Identifies transactions where:

the device is new for the entity
the transaction value is unusually high

The combination is more informative than either signal independently.

Business relevance

A new device can be legitimate.

A high-value transaction can also be legitimate.

However, the combination can create a higher-priority investigation scenario.

Prototype limitation

The current dataset does not contain a separate authentication/login-event stream.

Therefore, "new device" is inferred from transaction/device history rather than a literal login event.

In a production deployment, this signal could be joined with authentication, device-fingerprint, IP, session, and geolocation telemetry.

2. 🔗 Fan-In / Fan-Out Transaction Network

Identifies unusual transaction connectivity patterns.

Fan-In
Entity A ─┐
Entity B ─┤
Entity C ─┼──→ Target Entity
Entity D ─┘

Multiple entities transact toward a common entity.

Fan-Out
              ┌──→ Entity B
Entity A ─────┼──→ Entity C
              ├──→ Entity D
              └──→ Entity E

One entity distributes transactions across multiple counterparties.

Business relevance

Network-level relationships can reveal patterns that are difficult to identify by evaluating transactions independently.

3. 💰 Near-Threshold Structuring

Identifies repeated transactions occurring near an illustrative threshold within a defined time window.

The objective is to detect behavioural patterns that may be less visible when each transaction is considered independently.

Prototype limitation

Coverage varies by vertical.

The system intentionally reports this limitation rather than artificially generating detections.

🤖 AI-Assisted Investigation

Sentinel AI uses an AI-assisted, evidence-grounded investigation approach.

For a selected case, the system assembles structured context from:

Transaction information
Risk signals
Historical behaviour
Business-use-case signals
Retrieved evidence
Counter-evidence

When an LLM is configured, the assembled context is provided to the model for a structured investigation response.

The response is validated against the existing structured schema.

🔒 LLM Failure Handling

The system does not depend entirely on the availability of an LLM.

If the LLM is unavailable or the response fails validation, Sentinel AI uses a deterministic investigation fallback.

The fallback performs real evidence comparison and produces a structured investigation result.

Therefore:

LLM Available
      ↓
Structured AI Investigation
      ↓
Schema Validation
      ↓
Investigation Result


LLM Unavailable / Failure
      ↓
Deterministic Evidence-Grounded Fallback
      ↓
Investigation Result
Important disclosure

The final submission does not claim a verified live LLM execution where one was unavailable during final validation.

This is intentional.

🔎 Evidence & Counter-Evidence

One of Sentinel AI's core principles is:

An anomaly is not automatically proof of wrongdoing.

The investigation interface separates evidence into two categories.

Supporting Evidence

Information that increases concern about the transaction.

Counter-Evidence

Information that may explain the transaction or reduce the strength of the suspicion.

This provides the auditor with a more balanced investigation view.

🧠 Machine Learning & Risk Signals

Sentinel AI combines multiple analytical approaches.

Isolation Forest

Used for unsupervised anomaly detection across transaction-level features.

Autoencoder-Style Signal

Provides an additional reconstruction-based anomaly perspective.

Benford Analysis

Used where transaction characteristics make first-digit analysis meaningful.

Rule-Based Detection

Captures explicit behavioural or transactional conditions.

Behavioural Signals

Captures unusual changes or patterns in entity activity.

Temporal Signals

Captures transaction velocity and activity patterns over time.

Network Signals

Identifies unusual fan-in/fan-out relationships and transaction connectivity.

Business-Use-Case Signals

Maps transaction patterns to specific audit scenarios.

⚖️ Risk Engine

Individual signals are combined by the Sentinel risk engine into a prioritized investigation score.

The score is used to answer:

Which transactions should an auditor investigate first?

Important distinction

The Sentinel risk score is:

NOT a calibrated probability of fraud.

It is a prioritization score used to rank investigative workload.

This distinction is explicitly maintained throughout the system.

🛡️ Leakage Prevention

Sentinel AI was explicitly tested for temporal and target leakage.

Key controls include:

Chronological train/validation/holdout splitting
TRAIN-only calibration
TRAIN-period peer distributions
Temporal evidence filtering
Prevention of future information entering earlier transaction features
Regression tests for causal feature behaviour

A leakage issue identified during development was corrected and covered by regression testing.

📊 Final Technical Verification

The final submission package was independently verified from a fresh extraction of the delivered ZIP.

Verification Results
Verification	Result
Pipeline	✅ PASS
Unit Tests	✅ 41/41
Integration Tests	✅ 27/27
Total Tests	✅ 68/68
Clean Checkout Reproducibility	✅ PASS
Frontend Build	✅ PASS
Backend API	✅ PASS
Risk Queue	✅ PASS
Investigation Workflow	✅ PASS
Evidence	✅ PASS
Counter-Evidence	✅ PASS
Auditor Decision	✅ PASS
Audit Trail	✅ PASS
Mentor Use Cases	✅ PASS
Documentation Consistency	✅ PASS
Secrets Check	✅ PASS
🏆 Final Technical Score

The final independent technical assessment scored Sentinel AI:

81 / 100 — SUBMISSION READY
Category	Weight	Score
Business Problem & Value	10	8
Business Use Cases	10	8
Dataset & Data Quality	8	6
ML / Detection	12	10
Risk Engine	8	6
Explainability	8	7
Evidence / RAG	8	6
AI Investigation Agent	10	7
Full-Stack Product	8	7
Audit Trail / Governance	6	5
Testing / Engineering	6	6
Demo Readiness	6	5
TOTAL	100	81
Readiness Assessment
Area	Rating
Technical Readiness	8/10
Demo Readiness	8/10
Competitive Differentiation	8/10
Engineering Quality	9/10
AI Credibility	7/10
Final Status

🟢 GREEN — FINAL SUBMISSION READY

🖥️ Product Interface

The Sentinel AI console is organized around the auditor's workflow.

Risk Queue

The main queue provides:

Prioritized transactions
Risk scores
Risk drivers
Transaction context
Business-use-case classification
Vertical filtering
Investigation

The investigation view provides:

Transaction details
Risk signals
Relative signal strength
Business-use-case context
Supporting evidence
Counter-evidence
AI-assisted investigation
Recommended action
Auditor Decision

The auditor remains responsible for the final decision.

Possible actions can include:

Review
Escalate
Clear
Other available decision states
Audit Trail

Investigation activity and auditor decisions are persisted so that the case can be reviewed later.

This creates an auditable chain from:

Detection
   ↓
Investigation
   ↓
Evidence
   ↓
Decision
   ↓
Audit Trail
🛠️ Technology Stack
Backend
Python
FastAPI
SQLite
Pandas
NumPy
scikit-learn
Pydantic
Machine Learning & Analytics
Isolation Forest
Autoencoder-style anomaly scoring
Statistical analysis
Benford analysis
Behavioural features
Temporal features
Network analysis
Rule-based detection
Calibrated risk fusion
Evidence / Retrieval
TF-IDF retrieval
Temporal filtering
Supporting evidence
Counter-evidence

The current prototype intentionally uses TF-IDF rather than claiming a production-grade neural embedding/vector-search system.

Frontend
React
Vite
Tailwind CSS
React Router
Lucide React
📁 Repository Structure
.
├── app.py
├── agent.py
├── benford.py
├── db.py
├── evidence.py
├── model.py
├── network.py
├── prep.py
├── retrieval.py
├── risk_engine.py
├── rules.py
├── use_cases.py
├── weight_calibration.py
├── run_pipeline.py
│
├── tests/
│   ├── unit/
│   └── integration/
│
├── frontend/
│   ├── src/
│   │   ├── api/
│   │   ├── components/
│   │   ├── context/
│   │   ├── layout/
│   │   └── pages/
│   └── package.json
│
├── pro_dataset_aml.csv
├── pro_dataset_corporate.csv
├── pro_dataset_retail.csv
│
├── README.md
├── ENGINEERING_REPORT.md
├── FINAL_SUBMISSION_VERIFICATION.md
└── requirements.txt
🚀 Getting Started
1. Clone the Repository
git clone https://github.com/Ayushd172005/Delloite_Capstone.git
cd Delloite_Capstone
2. Install Python Dependencies
pip install -r requirements.txt
3. Run the Sentinel AI Pipeline
python run_pipeline.py

This prepares the analytical artifacts required by the application.

4. Start the Backend
uvicorn app:app --reload

The Sentinel API will then be available locally.

5. Start the Frontend

Open another terminal:

cd frontend
npm ci
npm run dev

The React frontend will connect to the Sentinel backend through the configured API endpoint.

🧪 Running Tests

Run the complete test suite:

pytest tests/unit tests/integration

Current verified result:

41 unit tests
27 integration tests
--------------------
68 total tests

68 passed

The integration tests are designed to work from a clean checkout without requiring a manually executed pipeline beforehand.

🔐 Security

The project is a capstone prototype and should not be connected to real customer financial systems without appropriate security and compliance controls.

The repository does not contain production credentials or hardcoded API secrets.

Use the provided example environment files for configuration.

Never commit:

.env
API keys
passwords
tokens
private credentials
⚠️ Known Limitations

Sentinel AI is a prototype and has several intentionally disclosed limitations.

Synthetic Data

The current datasets are synthetic.

They should not be interpreted as representative of production banking performance.

Single Data Generator

The three vertical datasets currently use a common synthetic generation framework.

This limits the ability to generalize performance conclusions across real-world institutions.

Retrieval

The current prototype uses TF-IDF retrieval rather than production-grade neural embeddings.

Live LLM Verification

The live LLM path was not verified against a real API key during final validation.

The deterministic evidence-grounded fallback is verified and functional.

Detection Performance

Performance varies by vertical.

AML currently demonstrates stronger detection performance than the corporate and retail datasets.

Authentication Telemetry

The current prototype does not contain a separate authentication/login-event stream.

Therefore, the new-device use case is inferred from transaction/device history.

Production Deployment

The prototype does not currently include:

Docker deployment
Cloud infrastructure
CI/CD configuration
Production authentication
Production monitoring
Enterprise identity management

These are intentionally outside the current capstone prototype scope.

👤 Human-in-the-Loop Design

Sentinel AI is designed to assist auditors rather than replace them.

The system:

Detects
   ↓
Prioritizes
   ↓
Explains
   ↓
Retrieves Evidence
   ↓
Assists Investigation

The auditor:

Reviews
   ↓
Evaluates
   ↓
Decides
   ↓
Documents

This keeps consequential audit decisions under human control.

🌟 Why Sentinel AI Is Different

A conventional anomaly-detection system may answer:

"How unusual is this transaction?"

Sentinel AI attempts to answer the broader question:

"Why should the auditor investigate this transaction, what evidence supports the concern, what evidence argues against it, what action is recommended, and what decision was ultimately made?"

The differentiation is therefore not a single ML model.

It is the combination of:

Detection
    +
Context
    +
Explainability
    +
Evidence
    +
Counter-Evidence
    +
AI-Assisted Investigation
    +
Human Decision
    +
Audit Trail
🧭 Design Philosophy

Sentinel AI follows five principles:

1. Detect broadly

Analyze the transaction population rather than relying only on manually selected samples.

2. Prioritize intelligently

Use multiple signals to focus limited auditor attention.

3. Explain the alert

Expose the signals and business context behind the prioritization.

4. Challenge the suspicion

Present counter-evidence instead of assuming every anomaly is fraudulent.

5. Preserve human accountability

The auditor remains responsible for the final decision.

📈 Future Production Direction

If developed beyond the capstone prototype, Sentinel AI could be extended with:

Real-time transaction streams
Authentication and device telemetry
Production-grade embeddings
Enterprise vector search
Real-time network analysis
Cloud deployment
Enterprise identity and access control
Model monitoring
Data drift monitoring
Human-feedback loops
Integration with existing banking/audit platforms

These are future directions rather than capabilities claimed by the current prototype.

📚 Project Documentation

Additional documentation included in the repository:

ENGINEERING_REPORT.md — engineering methodology, architecture, evaluation, and implementation details
FINAL_SUBMISSION_VERIFICATION.md — final validation and submission-readiness checks
👥 Project

Sentinel AI

Deloitte Capstone Project

Team: Stack Synapse
Institution: Manipal University Jaipur

🏁 Final Project Status
🟢 FINAL — FROZEN FOR SUBMISSION

The current prototype has:

✅ 68/68 verified tests
✅ Clean-checkout reproducibility
✅ Working backend
✅ Working React frontend
✅ Integrated Risk Queue
✅ Investigation workflow
✅ Supporting evidence
✅ Counter-evidence
✅ Three mentor-aligned business use cases
✅ Auditor decision workflow
✅ Persistent audit trail
✅ Leakage controls
✅ Evidence-grounded AI-assisted investigation
✅ Deterministic fallback
✅ No known MUST-FIX issues
Final Technical Assessment

81 / 100 — SUBMISSION READY

The prototype is now frozen for judging.

Further development should focus on:

Presentation → Demonstration → Q&A → Optional live-LLM verification

rather than adding new architecture or unnecessary features.

🏆 Core Message
Sentinel AI doesn't replace auditors.

It compresses large transaction populations into a small, explainable, evidence-backed investigation queue — so auditors spend their time deciding, not searching.
