````markdown
# 📅 Day 1: Setting Up Promptfoo and Exploring Project Scaffold

Welcome to Day 1 of the Promptfoo Experiments project!  
Today’s goal: **Install Promptfoo, create a new project scaffold, and understand the structure and purpose of each generated file.**

---

## 🚀 1. Installing Promptfoo

Begin by installing Promptfoo globally via npm:

```bash
npm install -g promptfoo
````

This makes the `promptfoo` command available everywhere on your system.

---

## 🏗️ 2. Creating a New Project Scaffold

Initialize a new Promptfoo project in your desired directory:

```bash
npx promptfoo init
```

* You’ll be prompted for a project name.
* This generates the starter files and folders necessary for prompt engineering with Promptfoo.

---


## 🗂️ 3. Generated Files and Their Importance

After running the initialization with `npx promptfoo init`, several essential files are created. Understanding the role of each will help you structure, scale, and maintain your prompt engineering experiments effectively.

---

### `promptfooconfig.yaml`

#### **Purpose**

* This is the **central configuration file** for Promptfoo.
* It serves as the “control panel” for your prompt engineering workflow.

#### **What It Contains**

* **Prompts:**
  Define the text prompts to be sent to your chosen LLMs.
  Prompts can include template variables (e.g., `{{input}}`) so you can reuse a single prompt format with different data.
* **Providers:**
  Specify which language model providers to use (e.g., OpenAI GPT-4, Anthropic Claude, local models).
  Includes API keys and model-specific settings if needed.
* **Tests:**
  Outline your test cases, including variable values, input data, or example user queries.
  Each test can define which variables to use and what the expected output looks like.
* **Assertions:**
  Specify rules to **automatically evaluate outputs** (e.g., should contain a keyword, match a pattern, not exceed a length, etc.).
  Supports types like `contains`, `equals`, `regex`, LLM-based rubric checks, and custom logic (JavaScript/Python).
* **Other Options:**
  Advanced settings like caching, concurrency, timeouts, red teaming configuration, and evaluation strategies.

#### **Why It’s Important**

* **Blueprint for Experiments:**
  Every aspect of your prompt testing—what you’re testing, how, and against which models—is defined here. It keeps your workflow organized and reproducible.

* **Central Control:**
  Easily tweak providers, prompts, or test cases in one place and re-run evaluations for rapid iteration and regression testing.

* **Collaboration:**
  Others can review or contribute to your work just by reading and editing this file—no code needed.

* **Best Practices Enablement:**
  Encourages the use of templating, parameterization, and automated assertions—all modern LLM best practices.

* **Examples of Key Sections:**

  ```yaml
  prompts:
    - "Translate this sentence into French: {{input}}"
  providers:
    - openai:gpt-3.5-turbo
    - anthropic:claude-instant
  tests:
    - vars:
        input: "Hello, how are you?"
      assert:
        - type: contains
          value: "Bonjour"
  ```

* **Scalability:**
  As your project grows, this file scales with you—simply add new prompts, providers, or tests as needed.

---

### `tests.yaml` (or `tests.json`)

#### **Purpose**

* Stores **test case data** separately from the main config.
* Each entry provides specific input variables and, optionally, expected outputs.

#### **Importance**

* Enables clear separation of configuration (the “how”) and test data (the “what”).
* Makes your test suite extensible: Add more cases by editing this file without cluttering your main config.
* Useful for both manual and auto-generated datasets.

---

### `.gitignore`

* **Purpose:** Tells Git to ignore files and folders that should not be tracked (e.g., caches, sensitive data, dependencies).
* **Importance:**

  * Keeps your repo clean and secure.
  * Prevents accidental commits of large files or secrets.

---

### `README.md` (auto-generated or create your own)

* **Purpose:** Explains your project, setup steps, and usage.
* **Importance:**

  * Provides essential documentation for you and others.
  * Describes what the project does and how to run it.

---

### (Other files/folders)

* **`cache/` or similar:** May be created for storing output cache (often gitignored).
* **Example scripts:** May be included for automation or integration examples.

---

## 📝 4. Today's Log and Reflections

**Summary of Activities:**

* Installed Promptfoo CLI globally.
* Initialized a new project with the built-in scaffold.
* Reviewed and documented the purpose of each generated file.

**Key Insights:**

* The `promptfooconfig.yaml` file is the heart of any Promptfoo project.
* Separating test data (`tests.yaml`) from config improves scalability and readability.
* Proper use of `.gitignore` keeps the project safe and manageable.

**Initial Project Questions & Goals:**

* What do I want to learn with Promptfoo?

  * Prompt comparison across LLM providers.
  * Automated, repeatable prompt testing.
  * Red teaming and security evaluation.
* What will success look like?

  * Clean, organized daily logs.
  * Reproducible experiments.
  * Clear documentation of workflow and learnings.

---

## 📌 Next Steps

* Write and add a custom prompt and basic test case to `promptfooconfig.yaml`.
* Run the first prompt evaluation and log the results.
* Begin exploring prompt variations and assertion options.

---

*End of Day 1*