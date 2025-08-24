# 📅 Day 2: First Promptfoo Experiment

Welcome to **Day 2** of the Promptfoo Experiments project!
Today’s focus is on setting up and running your very first prompt evaluation using [Promptfoo](https://github.com/promptfoo/promptfoo).

---

## 🎯 What Was Done

* Configured a simple translation prompt in `promptfooconfig.yaml`.
* Created 3 test cases in `tests.yaml`.
* Ran the evaluation using Promptfoo.
* Logged and reviewed the outputs.

---

## 📂 Project Structure for Day 2

```
.
├── promptfooconfig.yaml    # Main prompt configuration
├── tests.yaml             # Test cases for the prompt
└── README.md              # This file
```

---

## 🛠️ How to Reproduce

### 1. Prerequisites

* [Node.js](https://nodejs.org/) installed
* [Promptfoo](https://promptfoo.dev/docs/installation/) installed globally (`npm install -g promptfoo`)
* An API key for your LLM provider (e.g., OpenAI, Anthropic, etc.)

---

### 2. Configuration Files

#### **promptfooconfig.yaml**

```yaml
description: >
  This configuration defines a simple prompt that translates English sentences to French,
  using OpenAI's GPT-3.5-turbo model as the provider.
  It is designed for basic prompt evaluation and can be extended with additional providers or prompts.

prompts:
  - "Translate the following English sentence to French: {{input}}"
providers:
  - openai:gpt-3.5-turbo  # Replace with your preferred provider/model if needed
```

#### **tests.yaml**

```yaml
# Test cases for evaluating English-to-French translation using the prompt in promptfooconfig.yaml.
# Each test provides a unique English sentence as input.
# Test cases for evaluating English-to-French translation.
- vars:
    input: "Hello, how are you?"
- vars:
    input: "The weather is nice today."
- vars:
    input: "Can you help me with my homework?"

```

```yaml
# Test cases for evaluating English-to-French translation.
# Providing Description for each test case. (can try both ways)

- description: "Basic greeting translation"
  vars:
    input: "Hello, how are you?"

- description: "Weather statement translation"
  vars:
    input: "The weather is nice today."

- description: "Request for help with homework"
  vars:
    input: "Can you help me with my homework?"

```

---

### 3. Run the Evaluation

In your terminal, execute:

```bash
npx promptfoo eval -t tests.yaml --no-cache 
```

---

### 4. Sample Results

| Input                             | Output                                 |
| --------------------------------- | -------------------------------------- |
| Hello, how are you?               | Bonjour, comment ça va ?               |
| The weather is nice today.        | Il fait beau aujourd'hui.              |
| Can you help me with my homework? | Pouvez-vous m'aider avec mes devoirs ? |

> *Note: Your outputs may vary depending on provider/model and API version.*

---

## 📝 Reflections

* **Setup was fast and easy.**
* **YAML configuration keeps things simple and readable.**
* **Promptfoo makes it easy to run repeatable tests and see LLM outputs side by side.**

---

## 🔜 What’s Next?

* Add a second provider/model for comparison.
* Use `promptfoo view` for interactive result visualization.
* Explore output assertions for automated result checking.

---

## 📬 Contact

* [LinkedIn – Ravikiran Bhonagiri](https://www.linkedin.com/in/ravikiran-bhonagiri/)
* Email: [bhonagiri.ravikiran@gmail.com](mailto:bhonagiri.ravikiran@gmail.com)

---

**Happy experimenting!**
