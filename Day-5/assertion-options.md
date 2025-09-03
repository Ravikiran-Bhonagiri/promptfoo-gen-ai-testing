# Supported Assertion Types in Promptfoo
---

## 📚 Promptfoo Assertion Examples

---

### `contains`

```yaml
assert:
  - type: contains
    value: "Python"
```

*Passes if output contains "Python".*

---

### `icontains`

```yaml
assert:
  - type: icontains
    value: "python"
```

*Case-insensitive match for "python".*

---

### `contains-all`

```yaml
assert:
  - type: contains-all
    value:
      - "red"
      - "blue"
      - "yellow"
```

*All listed substrings must appear in output.*

---

### `contains-any`

```yaml
assert:
  - type: contains-any
    value:
      - "Berlin"
      - "Munich"
      - "Hamburg"
```

*At least one substring must appear in output.*

---

### `icontains-all`

```yaml
assert:
  - type: icontains-all
    value:
      - "python"
      - "guido"
```

*All substrings must appear, case-insensitive.*

---

### `icontains-any`

```yaml
assert:
  - type: icontains-any
    value:
      - "python"
      - "monty"
```

*Any substring, case-insensitive.*

---

### `regex`

```yaml
assert:
  - type: regex
    value: "\\b[A-Z][a-z]+\\b"
```

*Checks if output matches a capitalized word.*

---

### `equals`

```yaml
assert:
  - type: equals
    value: "42"
```

*Output must match exactly "42".*

---

### `is-json`

```yaml
assert:
  - type: is-json
    value:
      required:
        - "answer"
      type: object
```

*Output must be valid JSON with "answer" property.*

---

### `contains-json`

```yaml
assert:
  - type: contains-json
```

*Output must contain a valid JSON structure.*

---

### `is-html`

```yaml
assert:
  - type: is-html
```

*Output must be complete valid HTML (e.g., `<html>...</html>`).*

---

### `contains-html`

```yaml
assert:
  - type: contains-html
```

*Output must include any HTML markup.*

---

### `is-sql`

```yaml
assert:
  - type: is-sql
    value:
      databaseType: "MySQL"
```

*Output must be valid MySQL SQL.*

---

### `contains-sql`

```yaml
assert:
  - type: contains-sql
```

*Output must contain valid SQL, even as a fragment.*

---

### `is-xml`

```yaml
assert:
  - type: is-xml
```

*Output must be valid XML.*

---

### `contains-xml`

```yaml
assert:
  - type: contains-xml
```

*Output must contain valid XML content.*

---

### `classifier`

```yaml
assert:
  - type: classifier
    provider: huggingface:text-classification:facebook/roberta-hate-speech-dynabench-r4-target
    value: nothate
    threshold: 0.7
```

*Passes if output is NOT hate speech (per classifier).*

---

### `not-classifier`

```yaml
assert:
  - type: not-classifier
    provider: huggingface:text-classification:facebook/roberta-hate-speech-dynabench-r4-target
    value: hate
    threshold: 0.7
```

*Passes if classifier does NOT label as "hate".*

---

### `llm-rubric`

```yaml
assert:
  - type: llm-rubric
    value: "Is this response helpful and factual?"
```

*LLM-as-judge for helpfulness/factuality.*

---

### `javascript`

```yaml
assert:
  - type: javascript
    value: "output.length < 100"
```

*Passes if output is fewer than 100 characters.*

---

### `python`

```yaml
assert:
  - type: python
    value: |
      def check(output):
          return output.startswith("Answer:")
      check(output)
```

*Passes if output starts with "Answer:".*

---

### `levenshtein`

```yaml
assert:
  - type: levenshtein
    value: "cat"
    threshold: 2
```

*Edit distance to "cat" must be 2 or less.*

---

### `similar`

```yaml
assert:
  - type: similar
    value: "Paris is the capital of France."
    threshold: 0.8
```

*Output must be semantically similar.*

---

### `rouge-n`

```yaml
assert:
  - type: rouge-n
    value: "Clean water is essential for life."
    threshold: 0.6
```

*Recall overlap with reference phrase.*

---

### `bleu`

```yaml
assert:
  - type: bleu
    value: "Comment ça va ?"
    threshold: 0.5
```

*Translation accuracy (BLEU score).*

---

### `gleu`

```yaml
assert:
  - type: gleu
    value: "Hello world"
    threshold: 0.6
```

*Sentence-level precision/recall.*

---

### `meteor`

```yaml
assert:
  - type: meteor
    value: "A quick brown fox jumps over the lazy dog."
    threshold: 0.7
```

*Semantic similarity and word order.*

---

### `f-score`

```yaml
assert:
  - type: f-score
    value: 0.7
```

*F1 classification metric.*

---

### `latency`

```yaml
assert:
  - type: latency
    threshold: 1000
```

*Output must be generated in under 1 second.*

---

### `cost`

```yaml
assert:
  - type: cost
    threshold: 0.002
```

*LLM call must cost less than \$0.002.*

---

### `finish-reason`

```yaml
assert:
  - type: finish-reason
    value: stop
```

*Checks model stopped for expected reason.*

---

### `trace-span-count`

```yaml
assert:
  - type: trace-span-count
    value:
      pattern: "*llm*"
      min: 1
      max: 3
```

*Checks number of spans matching pattern.*

---

### `trace-span-duration`

```yaml
assert:
  - type: trace-span-duration
    value:
      pattern: "*llm*"
      max: 1500
```

*Spans must complete within 1.5 seconds.*

---

### `trace-error-spans`

```yaml
assert:
  - type: trace-error-spans
    value:
      max_count: 0
```

*No error spans should occur.*

---

### `webhook`

```yaml
assert:
  - type: webhook
    value: "https://example.com/validate"
```

*Custom external validation.*

---

### `is-valid-function-call`

```yaml
assert:
  - type: is-valid-function-call
```

*Validates function call schema.*

---

### `is-valid-openai-function-call`

```yaml
assert:
  - type: is-valid-openai-function-call
```

*Legacy: Validates OpenAI function schema.*

---

### `is-valid-openai-tools-call`

```yaml
assert:
  - type: is-valid-openai-tools-call
```

*Validates OpenAI tools/MCP tools.*

---

### `pi`

```yaml
assert:
  - type: pi
    value: "Does the output directly answer the user's question?"
    threshold: 0.7
```

*Scored by Pi Labs’ preference model.*

---

### `is-refusal`

```yaml
assert:
  - type: is-refusal
```

*Passes if output is a refusal (declines to answer).*

---

### `not-is-refusal`

```yaml
assert:
  - type: not-is-refusal
```

*Passes if output is NOT a refusal.*

---

### `starts-with`

```yaml
assert:
  - type: starts-with
    value: "Once upon a time"
```

*Passes if output starts with the given phrase.*

---

### `select-best`

```yaml
assert:
  - type: select-best
```

*Selects best output from multiple options.*

---

### `assert-set`

```yaml
assert:
  - type: assert-set
    value:
      threshold: 2
      assertions:
        - type: contains
          value: "foo"
        - type: contains
          value: "bar"
        - type: contains
          value: "baz"
```

*Passes if 2 or more contained assertions pass.*

---

## 📝 Tips

* **Classifier assertions** use [HuggingFace models](https://huggingface.co/models?pipeline_tag=text-classification).
* **LLM rubrics** can check for nuanced properties, like helpfulness or relevance.
* **Custom logic**: Use `javascript` or `python` assertions for advanced scenarios.
* For **semantic similarity**, `similar`, `rouge-n`, `bleu`, `gleu`, and `meteor` offer flexible, language-aware checks.

---