# 💻 VibeForge

> A local, multi-agent AI coding environment — where orchestrators, code-generating agents, and human approval blend into one collaborative workflow.

---

## 🧠 What is VibeForge?

**VibeForge** is a **local agent orchestration system** for coding. It lets you:

- Run multiple local LLM agents (e.g., CodeBot, RefactorBot).
- Use a central Orchestrator AI (`huihui_ai/deepseek-r1-abliterated`) to assign tasks.
- Communicate via structured Markdown and JSON files.
- Require human approval for risky changes.
- Seamlessly integrate with your IDE.

It's your own local AGI software dev team — under your control.

---

## 🧩 Features

- ✅ Fully local: no internet or cloud required.
- 🔁 Multi-agent: run two or more cooperating LLMs.
- ⚡ Orchestrator: delegate high-level tasks to agents.
- 🧾 File-based protocol: uses `task.md` and `approvals.json`.
- ✅ Human-in-the-loop: approve changes manually.
- 📂 IDE-compatible: works with any editor (VS Code recommended).
- 📜 Audit logs: every action is logged.

---

## 📁 Project Structure
vibeforge/
├── agents/
│ ├── codebot.py
│ └── refactorbot.py
├── orchestrator/
│ └── huihui.py
├── communication/
│ ├── task.md
│ └── approvals.json
├── logs/
│ ├── codebot.log
│ └── refactorbot.log
├── utils/
│ └── approve.py
└── project/
└── <your actual codebase>

yaml
Copy
Edit

---

## ⚙️ Setup Instructions

### 1. Clone the Repo

```bash
git clone https://github.com/yourusername/vibeforge.git
cd vibeforge
2. Install Ollama and Pull Models
bash
Copy
Edit
curl -fsSL https://ollama.com/install.sh | sh
```
# Orchestrator
ollama pull huihui_ai/deepseek-r1-abliterated

# Agent models
ollama pull codellama:7b-code
ollama pull deepseek-coder:6.7b
3. Install Python Dependencies (optional)
bash
Copy
Edit
pip install llama-cpp-python watchdog
🚀 Running the System
Start the Orchestrator
bash
Copy
Edit
python orchestrator/huihui.py
Start the Agents (in separate terminals)
bash
Copy
Edit
python agents/codebot.py
python agents/refactorbot.py
Approve Agent Actions
bash
Copy
Edit
python utils/approve.py codebot
python utils/approve.py refactorbot
🧾 Example Task File: communication/task.md
markdown
Copy
Edit
# Main Task
Add unit tests and refactor auth.py

## Codebot
- Task: Generate unit tests for auth.py
- Status: waiting_approval
- Diff:
```diff
+ def test_auth_valid_user():
+     assert auth("admin", "1234") == True
Refactorbot
Task: Simplify auth logic

Status: idle

yaml
Copy
Edit

```

## ✅ Approvals

Update `communication/approvals.json` or use the CLI:

```json
{
  "codebot": { "approved": false },
  "refactorbot": { "approved": false }
}
```
🧠 Future Plans
🧪 Web dashboard for control and logs

🔄 Autogen or CrewAI agent wrappers

🔌 Socket-based communication instead of file polling

🧬 Personality and memory layers

🛡️ License
MIT — feel free to fork, modify, and contribute.

✨ Author
Built with vibes by Aldin Dugolli — 2025.
