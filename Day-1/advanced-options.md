## ▶️ Running Your First Evaluation with Advanced Options

After setting up your config and test files, you can run Promptfoo’s evaluation with additional options for even more control:

### **Basic Evaluation**

```bash
promptfoo eval
```

Runs your tests and shows a summary in the terminal.

---

### **Exporting Results as HTML**

To save a detailed results matrix as an HTML file, use the `--output` flag:

```bash
promptfoo eval --output Day1.html
```

* This will generate a file called `Day1.html` in your current directory.
* Open it in your browser to visually inspect results, compare outputs, and review assertions.

---

### **Disabling Cache for Fresh Model Calls**

By default, Promptfoo caches LLM outputs for efficiency. To **force fresh outputs** on each run (ignore cache), add `--no-cache`:

```bash
promptfoo eval --no-cache
```

* This is useful if you want to make sure you’re seeing new responses from the LLM for each test, or if you’ve just updated your prompt/tests and want to avoid reusing old outputs.

---

### **Combine Both Options**

You can use both flags together:

```bash
promptfoo eval --output Day1.html --no-cache
```

* This will generate a fresh set of results and export them as an HTML file for review.

---

**Tip:**
Use these options whenever you want to track daywise progress or need to document exactly what happened on a specific date!

---