# 🤖 AI Agent with Hugging Face Chat Models

This project demonstrates how to build a simple **ReAct-style AI agent** using any chat-compatible language model from Hugging Face. The agent reasons through user prompts using a structured loop of `Thought → Action → PAUSE → Observation → Answer`, with tool-use capabilities like arithmetic and querying dog breed weights.

---

## 🧠 What is This?

Inspired by OpenAI's function-calling and ReAct pattern, this agent:
- Maintains a conversation history.
- Performs reasoning steps (`Thought`, `Action`, `Observation`, `Answer`).
- Executes custom tools/actions.
- Uses **Hugging Face `transformers`** for inference, so no OpenAI keys or APIs are required.

---

## 📦 Dependencies

Install the required libraries:

```bash
pip install transformers torch accelerate
```

You may also need `sentencepiece` or `bitsandbytes` depending on the model.

---

## 🛠 How it Works

- **Agent class** simulates a conversation with a system prompt and dynamically appends user/assistant messages.
- Hugging Face `pipeline` is used for generating responses.
- Pattern-matching (`Action: tool: input`) is used to detect when the agent wants to use a tool.
- Tools like `calculate` and `average_dog_weight` are defined and executed in Python.

---

## 🚀 Running the Agent

### 1. Clone the Repo (or copy the script)

```bash
git clone https://github.com/your-username/hf-ai-agent
cd hf-ai-agent
```

### 2. Modify `model_id` if Needed

Change this line to the model of your choice (see below for suggestions):

```python
model_id = "HuggingFaceH4/zephyr-7b-alpha"
```

Make sure your machine supports the model size (e.g., 7B models need a GPU or quantization).

---

### 3. Run the Agent

```bash
python main.py
```

Example prompt:

```python
query("I have 2 dogs, a border collie and a scottish terrier. What is their combined weight?")
```

Agent will reason through the question, call actions like `average_dog_weight`, and finally produce an answer.

---

## 🧰 Tools Available

| Action               | Example                            | Description                              |
|----------------------|------------------------------------|------------------------------------------|
| `calculate`          | `calculate: 4 * 7 / 3`              | Executes basic Python arithmetic         |
| `average_dog_weight` | `average_dog_weight: Border Collie` | Returns average weight for dog breeds    |

---

## 🧪 Suggested Chat Models

Here are some chat-compatible Hugging Face models you can use:

| Model Name | Hugging Face ID | Notes |
|------------|------------------|-------|
| Zephyr 7B | `HuggingFaceH4/zephyr-7b-alpha` | Small, tuned for chat |
| Mistral 7B | `mistralai/Mistral-7B-Instruct-v0.1` | Fast, strong performer |
| LLaMA 2 Chat | `meta-llama/Llama-2-7b-chat-hf` | Requires Meta access |
| OpenHermes | `NousResearch/Nous-Hermes-2-Mistral-7B-DPO` | Instruction-tuned |
| TinyLLaMA | `TinyLlama/TinyLlama-1.1B-Chat-v1.0` | Lightweight alternative |

---

## 📌 Notes

- If you're running on CPU, switch to smaller models or quantized GGUF versions.
- You can extend the agent by adding more actions or integrating external tools (e.g., web search, code execution).
- Use `auto-gptq`, `llama.cpp`, or `transformers` with quantization for better inference performance.

---

## 📜 License
