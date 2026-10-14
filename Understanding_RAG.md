# 🧠 The Knowladge Cuttoff Problem

- Ein **LLM** kennt nur Muster aus seinem **Trainingsdatensatz**.
- Ab dem **Knowledge Cutoff** ist alles Neue draußen.
- **Typisch fehlen:**
  - 🔒 **Private Daten** (interne Systeme, Wikis, Runbooks, Schemas …)
  - 📰 **Events nach dem Cutoff** (News, Incidents, neue Features …)
  - 📚 **Spezielle Domain-Dokumente**, die nie im Training waren
- Ein noch so guter **Prompt** kann fehlende Informationen nicht ersetzen – das muss über die **System-/Architektur** gelöst werden, nicht über **„Prompt-Magie“**.

# 🧠 Was ist RAG?

- **RAG (Retrieval-Augmented Generation)**: gezieltes **Retrieval** von externen, relevanten Daten + **Generierung** der Antwort mit diesen Daten im Prompt.

- 🎯 **Kernvorteil**: Antworten sind **gegroundet** in konkreten Dokus/Repos/Logs statt nur im Modellgedächtnis.

- ⚖️ **Abgrenzung**:
  - **RAG > Fine-Tuning** bei großen Dokus, privaten Daten, häufigen Änderungen.
  - **RAG > langes Kontext-Fenster / Prompt Stuffing**, weil es **selektiv** arbeitet.

# 🏗️ RAG Architecture

### 🔄 RAG-Loop

**Query** → **Embed** → **Search** → **Retrieve** → **Prompt augmentieren** → **LLM-Antwort**

### ⚙️ Rollen

- 🧠 **Embedding-Modell** (Query vorbereiten)
- 🗄️ **Vektor-Store** (relevante Dokus finden)
- 🤖 **LLM** (Antwort formulieren)

### ⚠️ Problemfall

**Schlechtes Retrieval ⇒ schlechte/irrelevante Antwort**, egal wie stark das LLM ist.
