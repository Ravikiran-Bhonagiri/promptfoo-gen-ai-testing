# 🚦 Day 5: Automated Assertions & Output Validation

Welcome to **Day 5** of the Promptfoo Experiment!
Today’s focus: making LLM evaluation reliable, automated, and scalable by integrating a full range of **assertion types**—from simple checks to deep semantic and classifier-based validations.

---

## 🎯 Goals for Day 5

* Integrate and experiment with both **basic** and **advanced** assertions.
* Validate both positive and negative cases to catch issues early.
* Document all assertion types and usage patterns for future reference.

---

## 🧩 Supported Assertion Types

### 🟢 Basic Assertions

| Assertion Type  | Description                                            |
| --------------- | ------------------------------------------------------ |
| `contains`      | Output contains a specified substring.                 |
| `icontains`     | Case-insensitive substring match.                      |
| `contains-all`  | Output contains all listed substrings.                 |
| `contains-any`  | Output contains any of the listed substrings.          |
| `regex`         | Output matches the given regular expression.           |
| `equals`        | Output exactly matches a string or JSON.               |
| `starts-with`   | Output starts with the specified string.               |
| `is-json`       | Output is valid JSON (optionally schema-checked).      |
| `contains-json` | Output contains valid JSON.                            |
| `is-html`       | Output is valid HTML.                                  |
| `contains-html` | Output contains HTML content.                          |
| `is-xml`        | Output is valid XML (can check for required elements). |
| `contains-xml`  | Output contains valid XML.                             |
| `is-sql`        | Output is valid SQL.                                   |
| `contains-sql`  | Output contains valid SQL.                             |
| `not-` prefix   | Negate any assertion (e.g., `not-contains`).           |

### 🟣 Advanced & Semantic Assertions

| Assertion Type           | Description & Typical Use                                  |
| ------------------------ | ---------------------------------------------------------- |
| `classifier`             | Uses a HuggingFace model (toxicity, bias, sentiment, etc). |
| `not-classifier`         | Inverts classifier result (e.g., passes if NOT toxic).     |
| `llm-rubric`             | Uses an LLM as a “judge” based on a rubric.                |
| `javascript`             | Custom JS function for validation.                         |
| `python`                 | Custom Python function for validation.                     |
| `similar`                | Embedding-based semantic similarity check.                 |
| `rouge-n`                | ROUGE-N recall metric, for summaries.                      |
| `bleu`                   | BLEU precision metric, for translations.                   |
| `gleu`                   | GLEU metric (sentence-level).                              |
| `meteor`                 | METEOR (semantic similarity, synonym/word order aware).    |
| `f-score`                | F1 score for classification tasks.                         |
| `latency`                | Checks LLM call response time.                             |
| `cost`                   | Checks LLM call cost.                                      |
| `webhook`                | Calls an external endpoint for validation.                 |
| `trace-span-count`       | Asserts on trace span counts (integration/observability).  |
| `trace-span-duration`    | Asserts on trace span durations.                           |
| `trace-error-spans`      | Asserts on error rates in trace spans.                     |
| `pi`                     | Uses Pi Labs’ preference scoring model.                    |
| `is-valid-function-call` | Validates function/tool call schema for OpenAI/Google.     |

---

## 📝 Extended Examples

### 🟢 Basic Assertion Examples

**Multiple Substring Check (`contains-all`):**

```yaml
- vars:
    input: "List three primary colors."
  assert:
    - type: contains-all
      value:
        - "red"
        - "blue"
        - "yellow"
```

**Case-Insensitive Match (`icontains`):**

```yaml
- vars:
    input: "Say Hello to the user."
  assert:
    - type: icontains
      value: "hello"
```

**Multiple Options (`contains-any`):**

```yaml
- vars:
    input: "The capital of Germany is Berlin."
  assert:
    - type: contains-any
      value:
        - "Berlin"
        - "berlin"
        - "BERLIN"
```

**JSON Validation (`is-json` with Schema):**

```yaml
- vars:
    input: '{"latitude": 51.5, "longitude": -0.12}'
  assert:
    - type: is-json
      value:
        required:
          - latitude
          - longitude
        type: object
        properties:
          latitude:
            type: number
            minimum: -90
            maximum: 90
          longitude:
            type: number
            minimum: -180
            maximum: 180
```

**Starts With:**

```yaml
- vars:
    input: "Once upon a time, there was a dragon."
  assert:
    - type: starts-with
      value: "Once upon a time"
```

**Exact Match for JSON (`equals`):**

```yaml
- vars:
    input: '{"success": true, "result": "done"}'
  assert:
    - type: equals
      value:
        success: true
        result: "done"
```

---

### 🟣 Advanced & Semantic Assertion Examples

**Toxicity Detection (Classifier):**

```yaml
- vars:
    input: "You are so stupid!"
  assert:
    - type: classifier
      provider: huggingface:text-classification:facebook/roberta-hate-speech-dynabench-r4-target
      value: nothate
      threshold: 0.8
```

**Semantic Similarity with Multiple References:**

```yaml
- vars:
    input: "Paris is the capital of France."
  assert:
    - type: similar
      value:
        - "France's capital is Paris."
        - "The capital of France is Paris."
        - "Paris, capital of France."
      threshold: 0.75
```

**Qualitative Rubric (LLM as Judge):**

```yaml
- vars:
    input: "Explain why the sky is blue."
  assert:
    - type: llm-rubric
      value: "Is the explanation scientifically accurate and age-appropriate for a 10-year-old?"
```

**Custom Python Function:**

```yaml
- vars:
    input: "The result is 3.14159."
  assert:
    - type: python
      value: |
        def check(output):
            return "3.14" in output and output.startswith("The result")
        check(output)
```

**Webhook to External System:**

```yaml
- vars:
    input: "Translate 'hello' to Spanish."
  assert:
    - type: webhook
      value: "https://api.mycustomvalidator.com/validate"
```

**Latency Assertion (Performance Test):**

```yaml
- vars:
    input: "What is the population of Canada?"
  assert:
    - type: latency
      threshold: 1000   # 1000 milliseconds (1 second)
```

**BLEU Score for Translation:**

```yaml
- vars:
    input: "Translate 'How are you?' to French."
  assert:
    - type: bleu
      value: "Comment ça va ?"
      threshold: 0.5
```

**ROUGE-N for Summary:**

```yaml
- vars:
    input: "Summarize the importance of clean water."
  assert:
    - type: rouge-n
      value: "Clean water is essential for health."
      threshold: 0.6
```

**Chained Assertions (Multiple in One Test):**

```yaml
- vars:
    input: "Tell me a fun fact about elephants."
  assert:
    - type: contains
      value: "elephant"
    - type: classifier
      provider: huggingface:text-classification:facebook/roberta-hate-speech-dynabench-r4-target
      value: nothate
      threshold: 0.5
    - type: llm-rubric
      value: "Is the fact about elephants true and appropriate for kids?"
    - type: latency
      threshold: 2000
```

**Trace Error Spans (Advanced Integration):**

```yaml
- vars:
    input: "Trigger an API error."
  assert:
    - type: trace-error-spans
      value:
        max_count: 0
```

---

### 🛡️ Negative Assertion Example

**Negative Assertion (Not-Contains):**

```yaml
- vars:
    input: "Who was the first US president?"
  assert:
    - type: not-contains
      value: "Abraham Lincoln"  # Should NOT mention Lincoln for this question
```

---

## 🗂️ Tips & Best Practices

* **Chain assertions** for comprehensive checks (e.g., correctness, safety, and latency).
* Use **negative assertions** (`not-`) to guard against unwanted responses.
* Prefer **semantic assertions** (`similar`, `meteor`, `bleu`, `rouge-n`) when outputs may vary in wording but not meaning.
* Leverage **classifier** and **rubric** assertions for automated red-teaming and quality review.
* Integrate **webhooks** for custom business logic or domain-specific validations.
* Monitor **latency** and **cost** to ensure your prompt setups are production-ready.

---

## 📝 Checklist for the Day

* [x] All basic and advanced assertions explored in config.
* [x] Negative and edge-case tests validated.
* [x] All assertion types and options documented for future reference.

---

## 📚 References

* [Promptfoo Assertion Docs](https://promptfoo.dev/docs/configuration/guide/)
* [HuggingFace Text Classification Models](https://huggingface.co/models?pipeline_tag=text-classification)

---

**Ready to make your prompt evaluations bulletproof?
Experiment, combine, and log your findings!**

---