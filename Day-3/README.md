# 🚀 Day 3: Adding Multiple Models/Providers — Promptfoo Experiments

Welcome to **Day 3** of my 15-day Promptfoo exploration!
Today’s focus: **Expanding prompt evaluation by adding and comparing multiple LLM providers using Promptfoo.**

---

## 🎯 Goals for Day 3

* **Add at least one new, state-of-the-art LLM provider** to the project configuration.
* **Compare outputs** from different providers on the same test suite.
* **Visualize and analyze** the strengths, weaknesses, and stylistic differences between models.
* **Log findings** with sample outputs and screenshots.

---

## 📁 Project Structure (Relevant Files)

```
.
├── promptfooconfig.yaml      # Main Promptfoo config (providers, prompts, tests)
├── tests.yaml               # (Optional) Large or generated test suite
├── README.md                # This file
└── ...                      # (other files/folders from previous days)
```

---

## 🛠️ Step-by-Step: Adding and Comparing Providers

### 1. Backup Existing Config (Recommended)

```bash
cp promptfooconfig.yaml promptfooconfig_day2_backup.yaml
```

---

### 2. Update Your `promptfooconfig.yaml` With Latest Providers

#### **Example Config:**

```yaml
providers:
  - openai:gpt-4o
  - claude-opus-4-1-20250805
```

**Note:**

* Set your API keys via environment variables or a `.env` file as required.
* See [Promptfoo Providers Documentation](https://promptfoo.dev/docs/providers/) for details on configuring providers.

---

### 3. Expand/Review Your Test Cases

Make sure you have at least 2–3 diverse test cases under `tests:`.

```yaml
tests:
  - vars: {input: "Summarize the latest global climate report."}
  - vars: {input: "Explain quantum computing to a 12-year-old."}
  - vars: {input: "Translate this to French: Hello, how are you?"}
```

---

### 4. Run Promptfoo Evaluations

```bash
npx promptfoo eval
```

*This will evaluate all test cases with all configured providers.*

---

### 5. Visualize Side-by-Side Results

```bash
npx promptfoo view
```

*This launches the Promptfoo web viewer for easy comparison.*

---

### 6. Analyze & Log Results

* **Compare outputs:** Look for differences in style, completeness, factuality, refusal to answer, etc.
* **Take notes/screenshots:** Use your browser or terminal output.
* **Record observations in your daily log** (see template below).

---

## 💡 Tips & Troubleshooting

* **Environment Variables:**
  Ensure all required API keys are exported (e.g., `OPENAI_API_KEY`, `ANTHROPIC_API_KEY`).
* **No API Keys?**
  Try open-source providers or local models (see [Promptfoo providers docs](https://promptfoo.dev/docs/providers/)).
* **Comparison:**
  Use the Promptfoo viewer for a quick, interactive inspection.
* **Never commit secrets!**
  Use `.env` and `.gitignore`.

---

## 🔗 Useful Links

* [Promptfoo Providers Documentation](https://promptfoo.dev/docs/providers/)
* [Promptfoo Getting Started Guide](https://promptfoo.dev/docs/getting-started/)
* [Promptfoo Example Configs](https://github.com/promptfoo/promptfoo/tree/main/examples)

---

## 📬 Contact

* [LinkedIn – Ravikiran Bhonagiri](https://www.linkedin.com/in/ravikiran-bhonagiri/)
* Email: [bhonagiri.ravikiran@gmail.com](mailto:bhonagiri.ravikiran@gmail.com)
* Or just open an issue or PR!

---

**Happy evaluating!**
*“You can’t improve what you don’t measure.” – Keep iterating!*

