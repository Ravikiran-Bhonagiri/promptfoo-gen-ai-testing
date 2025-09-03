# 🧪 Day 4: Expanding Test Cases — Promptfoo Experiments

Welcome to **Day 4** of my 15-day Promptfoo journey!
Today’s focus: **Broadening test coverage by adding diverse, challenging, and edge-case prompts, parameterizing test cases, and analyzing provider/model behavior on this expanded suite.**

---

## 🎯 Goals for Day 4

* **Dramatically increase test suite diversity** with edge cases, multiple languages, tricky instructions, and format constraints.
* **Leverage variables and parameterization** for efficient and scalable test management.
* **Evaluate and compare** how each LLM provider/model handles the expanded scenarios.
* **Document findings** with observations, strengths/weaknesses, and sample outputs.

---

## 🛠️ Step-by-Step: Expanding and Analyzing Test Cases

### 1. Backup Existing Config (Recommended)

```bash
cp promptfooconfig.yaml promptfooconfig_day3_backup.yaml
```

---

### 2. Brainstorm & Draft Diverse Test Cases

*Focus on:*

* Edge cases (ambiguous, contradictory, incomplete prompts)
* Multi-language instructions
* Format and length constraints
* Domain-specific and “trick” prompts

**Example additions:**

```yaml
tests:
  - vars: {question: "Translate 'Thank you' to Spanish."}
  - vars: {question: "Say hello in Hindi."}
  - vars: {question: "Give the capital of a country that no longer exists."}
  - vars: {question: "Respond in exactly three words."}
  - vars: {question: "Say 'hello' and do not say 'hello'."}
  - vars: {question: "Reply with a palindrome."}
  - vars: {question: "What is the square root of -1?"}
  - vars: {question: "Respond in JSON: List two fruits."}
```

---

### 3. Parameterize & Organize Your Test Suite

* Use `vars:` in each test for clarity and easier scaling.
* Optionally, group tests by theme in your config or a separate YAML.

---

### 4. Implement and Validate Tests in Config

* Add new test cases to your `promptfooconfig.yaml` under `tests:`.
* Double-check YAML formatting and variables.
* Validate config (optionally with [yamllint.com](https://www.yamllint.com/)).

---

### 5. Run Promptfoo Evaluations Across Providers

```bash
npx promptfoo eval
```

* This will execute all test cases using all configured providers/models.

---

### 6. Visualize & Analyze Results

```bash
npx promptfoo view
```

* Use the Promptfoo web viewer for side-by-side comparison of outputs.
* Focus on how each provider/model handles:

  * Non-English prompts
  * Ambiguous and contradictory instructions
  * Format/length constraints
  * Trick questions or edge cases

---

### 7. Summarize & Document Observations

* **Record sample outputs** for interesting/failing cases.
* **Compare strengths/weaknesses** in a table or bullet list:

| Test Case                 | OpenAI GPT-4 | Anthropic Claude | Llama-3 |
| ------------------------- | :----------: | :--------------: | :-----: |
| Translate to Spanish      |      👍      |        👍        |    👎   |
| Contradictory instruction |      ⚠️      |        🚫        |    ⚠️   |
| JSON format only          |      👍      |        👎        |    👎   |
| Palindrome                |      👍      |        👎        |    👎   |

* **Copy your findings and summary** into `docs/daywise/day04.md` or your daily log.

---

## 💡 Tips & Troubleshooting

* Save surprising, funny, or failed outputs for future regression tests.
* Don’t worry if some models fail — this is valuable insight for robustness!
* Commit your config and log changes at the end of the day.
* If you see YAML or variable errors, validate your file online or use a linter.

---

## 🔗 Useful Links

* [Promptfoo Test Case Documentation](https://promptfoo.dev/docs/configuration/test-cases/)
* [Promptfoo Assertions & Validation](https://promptfoo.dev/docs/configuration/guide/)
* [YAML Lint/Validator](https://www.yamllint.com/)
* [Promptfoo Example Projects](https://github.com/promptfoo/promptfoo/tree/main/examples)

---

## 📬 Contact

* [LinkedIn – Ravikiran Bhonagiri](https://www.linkedin.com/in/ravikiran-bhonagiri/)
* Email: [bhonagiri.ravikiran@gmail.com](mailto:bhonagiri.ravikiran@gmail.com)
* Or just open an issue or PR!

---

**Happy testing!**
*“You can’t improve what you don’t measure.” – Keep exploring!*
