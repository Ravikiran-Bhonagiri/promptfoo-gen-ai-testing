# 🦾 Promptfoo Experiments: A 15-Day Prompt Engineering Journey

Welcome! This repository documents a **15-day hands-on exploration and systematic testing** of prompt engineering and LLM evaluation using [Promptfoo](https://github.com/promptfoo/promptfoo).

If you want to learn how to build, evaluate, and secure LLM prompts using open-source tools—**follow along!**

---

## 🚩 Project Goals

* **Learn** the *full workflow* of prompt engineering with Promptfoo.
* **Explore** provider/model comparisons, robust evaluation, dataset generation, and red teaming.
* **Build** reproducible configs and experiments anyone can use or adapt.
* **Share** all learnings, code, and configs day by day.

---

## 📁 Repository Structure

```
.
├── promptfooconfig.yaml      # Main promptfoo configuration file
├── tests.yaml               # Example: hand-crafted and generated test cases
├── dataset/                 # (optional) Custom or real-world datasets
├── docs/
│   └── daywise/             # Daily logs: day01.md, day02.md, ...
├── scripts/                 # (optional) Helper scripts (logging, automation)
├── PLAN.md                  # 15-day plan and outline
├── DAYLOG.md                # (or use docs/daywise/) All daily progress logs
├── README.md                # This file!
└── .github/workflows/       # (optional) CI configs for automation
```

---

## 🛠️ What is Promptfoo?

[Promptfoo](https://promptfoo.dev/) is an open-source toolkit for:

* Comparing multiple models/providers side by side
* Running robust test suites against prompts
* Adding assertions for correctness, safety, and style
* Automating regression testing for your prompts and datasets
* Red teaming and discovering vulnerabilities before they hit production

---

## 🗓️ Daywise Plan

All daily progress is tracked in [PLAN.md](./PLAN.md) and [DAYLOG.md](./DAYLOG.md) (or see `docs/daywise/` for per-day logs).

**Highlights:**

* **Day 1–3:** Setup, first prompt, multi-model comparison
* **Day 4–6:** Expanding test cases, dataset automation
* **Day 7–9:** Performance, chat evaluation, advanced assertions
* **Day 10–11:** Red teaming, output transformation
* **Day 12–13:** CI/CD, HuggingFace integration
* **Day 14:** Real-world datasets & edge cases
* **Day 15:** Docs, polish, and release

See [PLAN.md](./PLAN.md) for the full breakdown.

---

## 🚀 Quick Start

1. **Clone this repo:**

   ```bash
   git clone https://github.com/Ravikiran-Bhonagiri/promptfoo-gen-ai-testing.git
   cd promptfoo-gen-ai-testing
   ```

2. **Install Promptfoo:**

   ```bash
   npm install -g promptfoo
   ```

3. **Run your first test:**

   ```bash
   promptfoo eval
   ```

4. **Visualize results:**

   ```bash
   promptfoo view
   ```

5. **Generate datasets or red team:**

   ```bash
   promptfoo generate dataset
   promptfoo redteam init
   ```

> See the [Promptfoo documentation](https://promptfoo.dev/docs/getting-started/) and [DAYLOG.md](./DAYLOG.md) for more.

---

## 📝 Daily Log

**All additions, test outputs, learnings, and next steps are logged each day.**
See: [DAYLOG.md](./DAYLOG.md) *(or navigate to `docs/daywise/` for each day’s details).*

---

## 🧩 Example Features Explored

* Multi-provider/model comparison
* Assertion types: contains, equals, regex, classifier, semantic similarity, metrics (BLEU/ROUGE/etc.)
* Dataset generation & coverage expansion
* Caching and performance tweaks
* Multi-turn chat thread evaluation
* Prompt injection and security red teaming
* Output transformation and advanced config
* Integration with CI/CD
* HuggingFace models for classification and grading
* Real-world datasets & edge case handling

---

## 📣 Contributing / Feedback

* **Ideas? Bugs?** [Open an issue](https://github.com/Ravikiran-Bhonagiri/promptfoo-gen-ai-testing/issues).
* **Want to fork, star, or adapt?** Please do—and let me know!
* PRs for better tests, docs, or new experiments are welcome.
* See [CONTRIBUTING.md](./CONTRIBUTING.md) (if present) for guidelines.

---

## 📜 License

MIT License.
Promptfoo is [MIT-licensed](https://github.com/promptfoo/promptfoo/blob/main/LICENSE).

---

## 📬 Contact

* \[Your Twitter/LinkedIn/email/etc.]
* Or just open an issue or PR!

---

**Happy prompting!**

> *“You can’t improve what you don’t measure.” – Start evaluating your prompts today!*

---