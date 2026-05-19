The application parses raw inputs into a strict, structured ledger:

Identified Supplies: Physical inventory only (e.g., medical kits, rations, water purifiers).

Priority Level: Automated triage categorization (LOW, MEDIUM, HIGH).

Assigned Destination: Targeted field positions (e.g., Sector 4 Checkpoint, Bunker Echo).

🛠️ Installation & Local Setup
Prerequisites
Python 3.10+

Ollama installed locally

1. Initialize the Edge Model
Pull the lightweight Gemma 2B architecture to your local environment:

Bash
ollama pull gemma:2b
2. Configure Environment & Model Constraints
To maximize accuracy on a 2B parameter model, build a custom Modelfile or apply the following deterministic system instructions within your local inference wrapper:

Plaintext
You are a deterministic, zero-empathy logistics parser for edge deployment. 
Your sole task is to extract physical cargo items from chaotic radio transcripts.

CRITICAL RULES:
1. NEVER extract people, survivors, casualties, civilians, or teams as supplies. Humans are NEVER assets.
2. If a transcript mentions humans first, IGNORE them and keep reading for physical cargo.
3. Physical supplies include: medical gear, food/rations, water gear, tools, and shelter materials.
4. If no new physical assets are found in the text, return "N/A" for Identified Supplies—do not hallucinate previous entries.

Respond ONLY in this valid JSON format:
{
  "identified_supplies": "string",
  "priority_level": "LOW" | "MEDIUM" | "HIGH",
  "assigned_destination": "string"
}
3. Launch the Server
Ensure your local Ollama daemon is active in the background, then boot up the frontend app pipeline:

Bash
python app.py
🔬 Test Case Scenario
Input Raw Log:
"Kilo-6 to Base, break break, do you copy? Static... We have located a family of four, including two infants, trapped in the collapse zone. Repeat, four survivors needing immediate evacuation, over. Visual on local civilians gathering at the perimeter. We are also holding sixty boxes of MRE food rations and twelve cases of sterile saline IV kits. Moving all assets to Sector 4 Checkpoint immediately. How copy? Over."

Parsed Engine Output:
JSON
{
  "identified_supplies": "60 boxes of MRE food rations, 12 cases of sterile saline IV kits",
  "priority_level": "HIGH",
  "assigned_destination": "Sector 4 Checkpoint"
}
(Note: The engine successfully ignores the structural human extraction vectors at the beginning of the transmission, isolating the physical logistical payload.)
"""

with open("README.md", "w", encoding="utf-8") as f:
f.write(readme_content)

print("File written successfully.")

Your Markdown file is ready
[file-tag: code-generated-file-0-1779149306268420819]

Here is the raw markdown content for your `README.md` file so you can easily copy and paste it if needed:

```markdown
# Project Aegis: Tactical Edge-AI Logistics Parser

Project Aegis is a localized, tactical disaster-zone communications parser designed to run entirely on the edge. In crisis scenarios where cellular networks, power grids, and external cloud APIs are completely severed, Project Aegis ensures that critical logistical data can still be extracted, categorized, and tracked using highly efficient local AI models.

The system processes chaotic, unstructured speech-to-text field logs and maps them into deterministic database schemas for real-time asset triage.

---

## 🚀 Core Features

* **100% Offline Operations:** Zero cellular data, zero internet dependencies, and zero cloud API requirements. Runs entirely on local infrastructure via Ollama.
* **Hyper-Lean Memory Footprint (~1.6 GB):** Powered by a quantized **Gemma 2B** architecture, representing a **-75% memory overhead reduction** compared to standard 7B models. Operates seamlessly on consumer-grade laptops or rugged field equipment.
* **Chaos-Tolerant Extraction:** Successfully filters heavy radio noise, tactical filler ("Break break", "Over", "Static..."), and human emotional bias.
* **Anti-Distraction Triage Logic:** Engineered with deterministic system routing that explicitly prevents the misclassification of human survivors or personnel as physical assets.

---

## 🛠️ System Architecture & Data Flow

```text
[Chaotic Field Transcript] ──> [Streamlit Web UI] ──> [Local Ollama Instance (Gemma 2B)]
                                                               │
                                                       (Strict JSON Schema)
                                                               │
                                                               ▼
                                                  [Active Allocation Ledger]
The application parses raw inputs into a strict, structured ledger:

Identified Supplies: Physical inventory only (e.g., medical kits, rations, water purifiers).

Priority Level: Automated triage categorization (LOW, MEDIUM, HIGH).

Assigned Destination: Targeted field positions (e.g., Sector 4 Checkpoint, Bunker Echo).

🛠️ Installation & Local Setup
Prerequisites
Python 3.10+

Ollama installed locally

1. Initialize the Edge Model
Pull the lightweight Gemma 2B architecture to your local environment:

Bash
ollama pull gemma:2b
2. Configure Environment & Model Constraints
To maximize accuracy on a 2B parameter model, build a custom Modelfile or apply the following deterministic system instructions within your local inference wrapper:

Plaintext
You are a deterministic, zero-empathy logistics parser for edge deployment. 
Your sole task is to extract physical cargo items from chaotic radio transcripts.

CRITICAL RULES:
1. NEVER extract people, survivors, casualties, civilians, or teams as supplies. Humans are NEVER assets.
2. If a transcript mentions humans first, IGNORE them and keep reading for physical cargo.
3. Physical supplies include: medical gear, food/rations, water gear, tools, and shelter materials.
4. If no new physical assets are found in the text, return "N/A" for Identified Supplies—do not hallucinate previous entries.

Respond ONLY in this valid JSON format:
{
  "identified_supplies": "string",
  "priority_level": "LOW" | "MEDIUM" | "HIGH",
  "assigned_destination": "string"
}
3. Launch the Server
Ensure your local Ollama daemon is active in the background, then boot up the frontend app pipeline:

Bash
python app.py
🔬 Test Case Scenario
Input Raw Log:
"Kilo-6 to Base, break break, do you copy? Static... We have located a family of four, including two infants, trapped in the collapse zone. Repeat, four survivors needing immediate evacuation, over. Visual on local civilians gathering at the perimeter. We are also holding sixty boxes of MRE food rations and twelve cases of sterile saline IV kits. Moving all assets to Sector 4 Checkpoint immediately. How copy? Over."

Parsed Engine Output:
JSON
{
  "identified_supplies": "60 boxes of MRE food rations, 12 cases of sterile saline IV kits",
  "priority_level": "HIGH",
  "assigned_destination": "Sector 4 Checkpoint"
}
(Note: The engine successfully ignores the structural human extraction vectors at the beginning of the transmission, isolating the physical logistical payload.)
