# Healthcare Product Management & AI Portfolio

### 👨‍💻 Tamer Karatekin | AI Product Manager
**MIT EECS, Econ & Healthcare Alum | Ex-OCI PM | Healthcare IT & Strategy**  
[LinkedIn](https://linkedin.com/in/tamerkaratekin) | [Portfolio Website](https://github.com/tamerkaratekin/healthcare)

---

### 🏥 Project Portfolio Strategy
This repository demonstrates a **"Full Stack" Healthcare Product Strategy**, moving from data ingestion and standards to advanced AI implementation. Each project addresses a specific barrier to AI adoption in modern healthcare systems: **Interoperability, Privacy, Trust, Infrastructure, and Automation.**

**New portfolio addition:** the **InterSystems IRIS FHIR Care Gap & Readmission Risk Engine** notebook (Colab-ready) now lives in Section 1 alongside the existing interoperability projects below.

## 📂 1. Enterprise Architecture & Interoperability
*Foundational layers required to make health data usable.*

### [Product_Analytics_FHIR_Interoperability_&_Population_Risk_Dashboard.ipynb](./Product_Analytics_FHIR_Interoperability_%26_Population_Risk_Dashboard.ipynb)
**"The Standards Layer"**
*   **The Problem:** Health data is siloed. To build scalable products, we must leverage interoperability standards.
*   **The Solution:** A dashboard connecting to public **HL7 FHIR (R4)** servers to ingest raw patient resources, parse complex JSON, and visualize population risk scores.
*   **Tech Stack:** `Python`, `HL7 FHIR`, `REST APIs`, `Seaborn`.

### [Hybrid_AI_with_InterSystems_IRIS_&_Embedded_Python.ipynb](./Hybrid_AI_with_InterSystems_IRIS_&_Embedded_Python.ipynb)
**"The Infrastructure Layer"**
*   **The Problem:** Hospitals rely on legacy databases (Epic/InterSystems) that are often disconnected from modern Python AI stacks.
*   **The Solution:** A hybrid architecture using the **InterSystems Native SDK** to train models in Python and write results directly back to high-speed **NoSQL Globals** (`^PatientRisk`) for real-time EMR alerts.
*   **Tech Stack:** `InterSystems IRIS`, `Embedded Python`, `NoSQL`.

### [InterSystems_IRIS_FHIR_Care_Gap_and_Readmission_Risk_Engine.ipynb](./InterSystems_IRIS_FHIR_Care_Gap_and_Readmission_Risk_Engine.ipynb)
**"The Care Gap + Risk Engine"**
*   **The Problem:** Care teams lack unified visibility into readmission risk and missing guideline-based interventions when data is scattered across FHIR resources.
*   **The Solution:** An end-to-end notebook that connects to the **IRIS for Health FHIR Server**, computes **LACE-style readmission risk** and diabetes/hypertension care gaps, then writes results back as FHIR Observations or IRIS Globals—plus an optional ingest of a real de-identified UCI hospital dataset to enrich the repository.
*   **Tech Stack:** `InterSystems IRIS for Health`, `FHIR R4`, `Python`, `Requests`, `Seaborn`, `IRIS Native SDK`.

#### How to run this notebook in Google Colab
1. Open directly in Colab: [colab.research.google.com/github/tamerkaratekin/healthcare/blob/main/InterSystems_IRIS_FHIR_Care_Gap_and_Readmission_Risk_Engine.ipynb](https://colab.research.google.com/github/tamerkaratekin/healthcare/blob/main/InterSystems_IRIS_FHIR_Care_Gap_and_Readmission_Risk_Engine.ipynb) (or `File → Open Notebook → GitHub` and paste this repository URL).
2. Run the setup cell to install dependencies (GPU not required). If you need the IRIS Native SDK, add `intersystems-irisnative` to the list:
   ```python
   !pip install -q pandas numpy seaborn matplotlib requests fhir.resources
   ```
3. In the configuration cell, point `FHIR_BASE_URL` to your IRIS FHIR endpoint. The notebook defaults to a public HAPI test server for read-only exploration if you skip IRIS.
4. To use your local IRIS docker instance from Colab, start the [IRIS FHIR template](https://github.com/intersystems-community/iris-fhir-template), load Synthea patients, and tunnel port **32783** to Colab (e.g., `ssh -L 32783:localhost:32783 ...` or `cloudflared tunnel --url http://localhost:32783`). Paste the tunneled URL into `FHIR_BASE_URL` and rerun the FHIR fetch cells.
5. If you do not have IRIS reachable, you can still execute the notebook’s UCI dataset section to test the care-gap and scoring logic entirely offline.

---

## 🔒 2. Trust, Safety & Regulatory Compliance
*Ensuring AI is safe, legal, and trusted by clinicians.*

### [Product_Prototype_HIPAA_Compliant_NLP_Pipeline_(Redaction_&_Extraction).ipynb](./Product_Prototype_HIPAA_Compliant_NLP_Pipeline_(Redaction_%26_Extraction).ipynb)
**"The Privacy Layer"**
*   **The Problem:** You cannot train AI on patient data without violating HIPAA/GDPR.
*   **The Solution:** A "Privacy-First" pipeline utilizing **Microsoft Presidio** to detect and redact PHI (names, dates) *before* data enters the analytics stream.
*   **Tech Stack:** `Microsoft Presidio`, `SpaCy`, `Transformers`.

### [Explainable_AI_(Glass_Box)_Dashboard.ipynb](./Explainable_AI_(Glass_Box)_Dashboard.ipynb)
**"The Trust Layer"**
*   **The Problem:** "Black Box" models (Deep Learning) are often rejected by the FDA and clinicians due to lack of transparency.
*   **The Solution:** A "Glass Box" Clinical Decision Support (CDS) tool using **Explainable Boosting Machines (EBM)**. It provides local feature attribution (e.g., *"Risk is high because Glucose > 180"*), mirroring the approach used in my research on Retinopathy of Prematurity.
*   **Tech Stack:** `InterpretML` (Microsoft), `Scikit-Learn`, `Matplotlib`.

---

## 🤖 3. Generative AI & Clinical Automation
*Next-generation tools to reduce provider burnout and operational waste.*

### [Evidence_Based_Medical_RAG_Assistant_(Guideline_Prototype).ipynb](./Evidence_Based_Medical_RAG_Assistant_(Guideline_Prototype).ipynb)
**"The Knowledge Layer: Protocol Compliance"**
*   **The Problem**: Clinical protocols (e.g., Sepsis Guidelines) change frequently. Clinicians cannot memorize every update, and generic LLMs (ChatGPT) often hallucinate medical advice.
*   **The Solution**: A **Retrieval-Augmented Generation (RAG)** prototype that ingests specific medical guidelines (Source of Truth). It forces the AI to "look up" the approved protocol before answering questions about dosage or resuscitation steps, ensuring Safe GenAI practices.
*   **Tech Stack**: `LangChain`, `RecursiveCharacterTextSplitter`, `ChromaDB`.

### [Product_Prototype_Clinical_RAG_for_Automated_Chart_Review.ipynb](./Product_Prototype_Clinical_RAG_for_Automated_Chart_Review.ipynb)
**"The Automation Layer"**
*   **The Problem:** Physicians spend hours manually reviewing unstructured text in Discharge Summaries to find specific details.
*   **The Solution:** A **Retrieval-Augmented Generation (RAG)** pipeline. It ingests messy, unstructured clinical notes, chunks them for context, and retrieves precise evidence (Meds, Procedures) to answer natural language queries.
*   **Tech Stack:** `LangChain`, `ChromaDB`, `HuggingFace Embeddings`.

### [Hospital_Readmission_Risk_&_Cost_Optimizer.ipynb](./Hospital_Readmission_Risk_&_Cost_Optimizer.ipynb)
**"The Business Layer: ROI & Value-Based Care"**
*   **The Problem:** Under Value-Based Care models, hospitals lose millions in CMS penalties when patients are readmitted within 30 days. Operational inefficiencies are often invisible without data.
*   **The Solution:** An operational analytics model that generates patient risk profiles using the LACE Index, identifies high-risk cohorts lacking follow-up appointments, and models the Financial ROI of deploying a digital intervention tool.
*   **Tech Stack:** Pandas, Financial Modeling, Risk Stratification.

## 📱 4. Product Prototyping (UX & Simulation)
*Interactive tools for stakeholder alignment and "What-If" analysis.*

### [Interactive_roi_app.ipynb](./Interactive_roi_app.ipynb)
**"The Interactive Layer"**
*   **The Problem:** Stakeholders (CFOs, Medical Directors) often struggle to understand the financial value of complex clinical interventions using static spreadsheets.
*   **The Solution:** An interactive **Streamlit Web App** prototype. It allows executives to adjust key operational variables (e.g., Annual Patient Volume, CMS Penalty Risk) and instantly visualize the **Net ROI** of purchasing digital health software.
*   **Tech Stack:** `Streamlit`, `Python`, `Interactive Visualization`.
###
