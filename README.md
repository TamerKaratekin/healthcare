# Healthcare Product Analytics & AI Portfolio

### 👨‍💻 Tamer Karatekin | AI Product Manager
**MIT EECS, Econ & Healthcare Alum | Ex-OCI | Healthcare IT & Strategy**  
[LinkedIn](https://linkedin.com/in/tamerkaratekin) | [Portfolio Website](https://github.com/tamerkaratekin/healtchare)

---

### 🏥 Project Portfolio Strategy
This repository demonstrates a **"Full Stack" Healthcare Product Strategy**, moving from data ingestion and standards to advanced AI implementation. Each project addresses a specific barrier to AI adoption in modern healthcare systems: **Interoperability, Privacy, Trust, Infrastructure, and Automation.**

## 📂 1. Enterprise Architecture & Interoperability
*Foundational layers required to make health data usable.*

### [01_fhir_population_health_dashboard.ipynb](./Product_Analytics_FHIR_Interoperability_%26_Population_Risk_Dashboard.ipynb)
**"The Standards Layer"**
*   **The Problem:** Health data is siloed. To build scalable products, we must leverage interoperability standards.
*   **The Solution:** A dashboard connecting to public **HL7 FHIR (R4)** servers to ingest raw patient resources, parse complex JSON, and visualize population risk scores.
*   **Tech Stack:** `Python`, `HL7 FHIR`, `REST APIs`, `Seaborn`.

### [04_intersystems_iris_hybrid_xai.ipynb](./Hybrid_AI_with_InterSystems_IRIS_&_Embedded_Python.ipynb)
**"The Infrastructure Layer"**
*   **The Problem:** Hospitals rely on legacy databases (Epic/InterSystems) that are often disconnected from modern Python AI stacks.
*   **The Solution:** A hybrid architecture using the **InterSystems Native SDK** to train models in Python and write results directly back to high-speed **NoSQL Globals** (`^PatientRisk`) for real-time EMR alerts.
*   **Tech Stack:** `InterSystems IRIS`, `Embedded Python`, `NoSQL`.

---

## 🔒 2. Trust, Safety & Regulatory Compliance
*Ensuring AI is safe, legal, and trusted by clinicians.*

### [02_nlp_phi_redaction_pipeline.ipynb](./Product_Prototype_HIPAA_Compliant_NLP_Pipeline_(Redaction_%26_Extraction).ipynb)
**"The Privacy Layer"**
*   **The Problem:** You cannot train AI on patient data without violating HIPAA/GDPR.
*   **The Solution:** A "Privacy-First" pipeline utilizing **Microsoft Presidio** to detect and redact PHI (names, dates) *before* data enters the analytics stream.
*   **Tech Stack:** `Microsoft Presidio`, `SpaCy`, `Transformers`.

### [03_explainable_ai_cds_dashboard.ipynb](./Explainable_AI_(Glass_Box)_Dashboard.ipynb)
**"The Trust Layer"**
*   **The Problem:** "Black Box" models (Deep Learning) are often rejected by the FDA and clinicians due to lack of transparency.
*   **The Solution:** A "Glass Box" Clinical Decision Support (CDS) tool using **Explainable Boosting Machines (EBM)**. It provides local feature attribution (e.g., *"Risk is high because Glucose > 180"*), mirroring the approach used in my research on Retinopathy of Prematurity.
*   **Tech Stack:** `InterpretML` (Microsoft), `Scikit-Learn`, `Matplotlib`.

---

## 🤖 3. Generative AI & Clinical Automation
*Next-generation tools to reduce provider burnout and operational waste.*

### [05_Evidence_Based_Medical_RAG_Assistant_(Toy_data_version)](./Evidence_Based_Medical_RAG_Assistant_(Toy_data_version).ipynb)
**"The Automation Layer"**
*   **The Problem:** Physicians spend hours manually reviewing unstructured text in Discharge Summaries to find specific details.
*   **The Solution:** A **Retrieval-Augmented Generation (RAG)** pipeline. It ingests messy, unstructured clinical notes, chunks them for context, and retrieves precise evidence (Meds, Procedures) to answer natural language queries.
*   **Tech Stack:** `LangChain`, `ChromaDB`, `HuggingFace Embeddings`.

### [06_Product_Prototype_Clinical_RAG_for_Automated_Chart_Review](./Product_Prototype_Clinical_RAG_for_Automated_Chart_Review.ipynb)
**"The Automation Layer"**
*   **The Problem:** Physicians spend hours manually reviewing unstructured text in Discharge Summaries to find specific details.
*   **The Solution:** A **Retrieval-Augmented Generation (RAG)** pipeline. It ingests messy, unstructured clinical notes, chunks them for context, and retrieves precise evidence (Meds, Procedures) to answer natural language queries.
*   **Tech Stack:** `LangChain`, `ChromaDB`, `HuggingFace Embeddings`.

###
