# 🐾 PetVision-v2
An upgraded internal veterinary AI system model including **RAG-Based Clinical Reasoning** and an **Agentic Appointment Automation Assistant** for veterinary clinics.

It supports:
1. Veterinary diagnostic assistance
2. Medical knowledge retrieval from internal datasets
3. Conversational appointment management via Google Calendar + database sync

## 🧠 System Overview
### 1. 🏥 Veterinary Diagnostic Assistant (RAG-based)
An AI assistant for veterinarians that helps generate reliable diagnosis and treatment suggestions based on:
* Patient symptoms
* Historical medical records
* Internal veterinary knowledge base

📊 Example Use Case 1
```python
"QUESTION_1: Buddy was diagnosed with demodicosis, what should I do?"

"ANSWER:"
=== PATIENT RECORD: Buddy ===
=== Medical Records ===
 record_type                      title                                                                         description severity condition
   diagnosis Dermatophytosis (Ringworm) Circular alopecic lesions with scaling highly suggestive of fungal dermatophytosis.     None  ringworm
  lab_result       Fungal Skin Scraping                            Microscopic examination revealed fungal hyphae presence.     None      None
prescription Topical Antifungal Therapy                     Miconazole cream prescribed for daily application over 21 days.     None      None

Based on the medical records provided, Buddy has been diagnosed with demodicosis, specifically localized demodicosis. Treatment options include:
1. Topical Antifungal Therapy: A prescription for Miconazole cream has been issued for daily application over 21 days.
2. Anti-parasitic Drugs: The spot-on combination imidacloprid/moxidectin has been recommended for use at a two-week interval and then monthly.
3. Antibiotics: For secondary bacterial infections, amoxicillin has been prescribed twice a day for 14 days.

It is important to follow the prescribed treatment regimen closely and monitor the progress of the condition. Regular check-ups will help ensure the effectiveness of the treatment and address any potential complications promptly. 

If the condition does not improve within a reasonable timeframe, further diagnostic tests might be necessary to rule out other possible causes. Always consult with a veterinarian for personalized advice regarding your pet's health.

Please note that the above recommendations are based on the available medical records and may need adjustments depending on the specific circumstances of Buddy's case.
---
References:
[1] Efficacy of oral afoxolaner for the treatment of canine generalised demodicosis. Parasite (2016). https://pmc.ncbi.nlm.nih.gov/articles/PMC4807374/pdf/parasite-23-14.pdf
[2] Efficacy of oral fluralaner chewable tablets for the treatment of generalized demodicosis in dogs. Parasites & Vectors (2015). https://pmc.ncbi.nlm.nih.gov/articles/PMC4675583/pdf/12639_2013_Article_405.pdf
[3] Demodicosis caused by Demodex canis and Demodex cornei in dogs. Journal of Parasitic Diseases (2013). https://ijmpes.com/PDF/ijmpes-3141.pdf
```

### 2. 📅 Clinic Appointment Automation Agent
An administrative assistant chatbot for clinic staff to manage appointments through natural conversation.

Core Capabilities:
* Create / update / delete appointments via chat
* Sync with Google Calendar
* Maintain consistency with Supabase database
* Context-aware conversation handling

📊 Example Use Case 2
```python
"QUESTION_1: Thanks! Can you remind me what time the appointment is?"

"ANSWER:"
The event summary is General Checkup. It starts at 2pm on May 29th, 2026, in Kuala Lumpur time zone.

If you need any further assistance or have questions about your appointment, feel free to ask!

-------------

"FOLLOW-UP QUESTION: Actually, move it to 4pm to 5pm"

"ANSWER:"
Understood. Your updated appointment has been moved to 4pm to 5pm on May 29th, 2026.

Here’s the updated information:
- Visit ID: 0863b510-c050-484f-8d13-700537cee5e2
- Calendar Event ID: ndfiro71k8hpg1chho79lo7nxx
- HTML Link: https://www.google.com/calendar/event?eid=bmRmaXJvNzFrOGhwZzFjaGhvNzlsbzduMjQgbGVleTI3MDYwNxxx

The event summary is now General Checkup and it will start at 4pm in Kuala Lumpur time zone.

Is there anything else I can help you with today?
```

# ⚙️ Tech Stack
1. LangChain (Python)
2. Qwen2.5-1.5B Instruct https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct
3. BGE Small English v1.5 https://huggingface.co/BAAI/bge-small-en-v1.5
4. DistilBERT NER (CoNLL03 fine-tuned) https://huggingface.co/elastic/distilbert-base-uncased-finetuned-conll03-english
5. Supabase (PostgreSQL)
6. JSON Document Store (medical records)
7. In-memory Vector Store (clinical papers)
8. Google Calendar API

# 🔬 Veterinary Knowledge Base
The diagnostic module is grounded in peer-reviewed veterinary dermatology literature. These references are used to support reasoning in the RAG pipeline and ensure clinically grounded outputs.

**Demodicosis**
* https://pmc.ncbi.nlm.nih.gov/articles/PMC4675583/pdf/12639_2013_Article_405.pdf 
* https://pmc.ncbi.nlm.nih.gov/articles/PMC4807374/pdf/parasite-23-14.pdf 
* https://ijmpes.com/PDF/ijmpes-3141.pdf 

# 🚀 Future Improvements
* Expand to multi-species (cats, exotic pets)
