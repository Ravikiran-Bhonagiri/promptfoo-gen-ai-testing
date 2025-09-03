# Advanced Assertion Types in Promptfoo

---

## 🧑‍💻 Advanced Assertions: YAML Examples

### 1. `classifier`

```yaml
- vars:
    input: "You're so dumb!"
  assert:
    - type: classifier
      provider: huggingface:text-classification:facebook/roberta-hate-speech-dynabench-r4-target
      value: nothate
      threshold: 0.8
```

### 2. `not-classifier`

```yaml
- vars:
    input: "Say something inappropriate."
  assert:
    - type: not-classifier
      provider: huggingface:text-classification:facebook/roberta-hate-speech-dynabench-r4-target
      value: nothate
      threshold: 0.8
```

### 3. `llm-rubric`

```yaml
- vars:
    input: "Explain why plants are green."
  assert:
    - type: llm-rubric
      value: "Is the answer scientifically accurate and easy for a child to understand?"
```

### 4. `javascript`

```yaml
- vars:
    input: "Result: 42."
  assert:
    - type: javascript
      value: "output.startsWith('Result:') && output.includes('42')"
```

### 5. `python`

```yaml
- vars:
    input: "The total is 100."
  assert:
    - type: python
      value: |
        def check(output):
            return output.endswith('100.')
        check(output)
```

### 6. `similar`

```yaml
- vars:
    input: "The capital of Italy is Rome."
  assert:
    - type: similar
      value: "Rome is the capital of Italy."
      threshold: 0.7
```

### 7. `rouge-n`

```yaml
- vars:
    input: "Summarize the benefits of exercise."
  assert:
    - type: rouge-n
      value: "Exercise improves health."
      threshold: 0.6
```

### 8. `bleu`

```yaml
- vars:
    input: "Translate 'Good morning' to French."
  assert:
    - type: bleu
      value: "Bonjour"
      threshold: 0.5
```

### 9. `gleu`

```yaml
- vars:
    input: "Translate 'cat' to Spanish."
  assert:
    - type: gleu
      value: "gato"
      threshold: 0.7
```

### 10. `meteor`

```yaml
- vars:
    input: "Provide a synonym for 'happy'."
  assert:
    - type: meteor
      value: "joyful"
      threshold: 0.6
```

### 11. `f-score`

```yaml
# Requires derived metrics; see advanced Promptfoo docs for full setup.
```

### 12. `latency`

```yaml
- vars:
    input: "What's the time in Tokyo?"
  assert:
    - type: latency
      threshold: 1000
```

### 13. `cost`

```yaml
- vars:
    input: "Summarize this article."
  assert:
    - type: cost
      threshold: 0.002
```

### 14. `webhook`

```yaml
- vars:
    input: "Check if this is a greeting."
  assert:
    - type: webhook
      value: "https://your-webhook-server.com/validate"
```

### 15. `trace-span-count`

```yaml
- vars:
    input: "Trigger multiple calls."
  assert:
    - type: trace-span-count
      value:
        pattern: "*llm*"
        min: 1
        max: 3
```

### 16. `trace-span-duration`

```yaml
- vars:
    input: "Long-running operation."
  assert:
    - type: trace-span-duration
      value:
        max: 2000
```

### 17. `trace-error-spans`

```yaml
- vars:
    input: "Cause an error."
  assert:
    - type: trace-error-spans
      value:
        max_count: 0
```

### 18. `pi`

```yaml
- vars:
    input: "Respond politely."
  assert:
    - type: pi
      value: "Is the response polite and clear?"
      threshold: 0.8
```

### 19. `is-valid-function-call`

```yaml
- vars:
    input: '{"function":"getWeather","parameters":{"city":"London"}}'
  assert:
    - type: is-valid-function-call
```

---

### When to Use Advanced Assertions

* **Classifier/LLM rubrics**: To assess safety, quality, or nuanced aspects that aren’t simple keywords.
* **Similarity metrics**: To measure semantic similarity, translation quality, or summary coverage.
* **Code assertions (`javascript`, `python`)**: For custom or project-specific validation logic.
* **Performance/cost**: To guard against regressions in latency or API expense.
* **Trace/webhook**: For complex applications where you need external systems or observability data.
* **Function/tool call validation**: For advanced OpenAI/Google API integrations with function calling.

---

**Tip:**
You can chain multiple advanced assertions together for deep, multi-dimensional validation!

Let me know if you want YAML config examples for any advanced assertion.
