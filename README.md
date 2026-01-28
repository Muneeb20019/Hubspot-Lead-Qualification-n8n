# 📈 HubSpot AI Lead Engine: Autonomous Qualification & CRM Orchestration 🚀

![n8n](https://img.shields.io/badge/Workflow-n8n-EF5B25?style=for-the-badge&logo=n8n) ![AI](https://img.shields.io/badge/AI-GPT--4o-412991?style=for-the-badge&logo=openai) ![CRM](https://img.shields.io/badge/CRM-HubSpot-FF7A59?style=for-the-badge&logo=hubspot) ![Trigger](https://img.shields.io/badge/Trigger-Gmail-EA4335?style=for-the-badge&logo=gmail)

An intelligent, enterprise-grade B2B sales pipeline that transforms unstructured inbound emails into qualified, scored, and enriched HubSpot deals. This system eliminates manual data entry and uses dual-stage AI analysis to ensure sales teams focus only on high-value opportunities.

---

## 📸 Workflow Architecture
![Hubspot Workflow](Hubspot.png) 
*End-to-end orchestration from Gmail ingestion to HubSpot Deal creation.*

---

## 🎯 The Problem & The Solution

### **The Problem 😫**
Sales teams often suffer from **"Lead Fatigue."** Inbound emails are frequently unstructured, missing key company data, and mixed with low-quality inquiries. Manually entering this data into a CRM and researching companies takes hours, leading to slow response times (**Lead Decay**).

### **The Solution ⚡**
This autonomous engine provides a **zero-touch pipeline** that:
1.  **Extracts Data:** Instantly identifies company names and contact info from raw text.
2.  **Enriches Intel:** Uses HubSpot’s native insights to fetch deep company data.
3.  **Scores Automatically:** Employs AI to judge if a lead is "Hot" or "Cold" based on a specific business rubric.
4.  **Routes Logic:** Automatically moves hot leads to "Appointment Scheduled" and cold leads to "Nurture" stages.

---

## ✨ Key Features

*   **📧 Intelligent Ingestion:** Monitors Gmail in real-time for specific labels or keywords.
*   **🤖 Dual-Stage AI Analysis:** 
    *   *Stage 1:* Data Extraction (Structuring the unstructured).
    *   *Stage 2:* Qualitative Scoring (Analyzing company fit and intent).
*   **💎 Automated Enrichment:** Automatically populates HubSpot Company records to trigger background data fetching.
*   **🔥 Smart Routing:** Uses a dynamic `Switch` node to treat leads differently based on their AI-generated "Temperature."
*   **📊 Clean CRM Sync:** Ensures all Deals are correctly associated with the proper Contact and Company IDs.

---

## 🛠️ Technical Stack

| Layer | Technology | Role |
| :--- | :--- | :--- |
| **Automation Hub** | **n8n** 🔗 | Central Orchestrator |
| **Intelligence** | **OpenAI GPT-4o** 🧠 | Data Structuring & Qualitative Scoring |
| **CRM / DB** | **HubSpot** 📊 | Lead Management & Data Enrichment |
| **Interface** | **Gmail API** ✉️ | Trigger Source for Inbound Leads |

---

## ⚙️ Detailed Logic Flow

### **1. Capture & Structure 📥**
The **Gmail Trigger** node picks up the email body. **OpenAI (GPT-4o)** acts as a "Data Secretary," converting messy email text into a clean JSON object containing the `Company Name`, `Contact Email`, and `Inquiry Topic`.

### **2. Validation & Filter 🛑**
An **If Node** acts as a gatekeeper. If the AI cannot find a valid Company Name (e.g., a personal message or spam), the workflow terminates, keeping the CRM clean of "junk" data.

### **3. Enrichment Loop 🔄**
The workflow creates a **HubSpot Company** record. Once created, it fetches the profile back after a momentary delay, allowing HubSpot's internal engine to enrich the record with industry, revenue, and location data.

### **4. AI Qualification Scoring ⚖️**
A second AI node receives the **full enriched profile**. It compares the data against a predefined rubric (e.g., "Is the company in the Tech sector? Is their revenue >$1M?"). It returns a status: **HOT** or **COLD**.

### **5. Dynamic CRM Routing 🛣️**
The **Switch Node** reads the AI score:
- **IF HOT:** Creates a Deal in the **"Appointment Scheduled"** stage for immediate sales follow-up.
- **IF COLD:** Creates a Deal in the **"Qualified to Buy"** (Nurture) stage for long-term marketing.

---

## ✍️ Author

**Muneeb Ali Khan**
- **GitHub:** [@Muneeb20019](https://github.com/Muneeb20019)
- **LinkedIn:** [Muneeb Ali Khan](https://www.linkedin.com/in/muneeb-ali-khan-2a1675365)
