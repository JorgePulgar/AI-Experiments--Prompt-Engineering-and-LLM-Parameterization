# LLM Experiments — Prompt Engineering & Model Parameters

> 🌐 [Versión en español](README_ES.md)  
> 📓 **Note:** All notebooks are written in Spanish.

A collection of practical experiments with prompt engineering techniques and language model parameter tuning using Azure AI Foundry and `gpt-4o`.

---

## What's in this repository?

Two independent notebooks that explore how to get the most out of language models: the first through prompting techniques, the second through the parameters that control model behavior.

## Repository structure

```
llm-experiments/
├── parte1_prompt_engineering.ipynb    # 6 prompting techniques + 2 real use cases
├── parte2_parametros_modelo.ipynb     # Experiments with temperature, top_p and penalties
└── README.md
```

---

## Part 1 — Prompt Engineering

Practical exploration of 6 prompting techniques with executable examples, result analysis, and application to real use cases.

### Techniques covered

| Technique | Description |
|-----------|-------------|
| **Zero-Shot** | Direct instruction with no examples |
| **Few-Shot** | Input→output examples to fix the response pattern |
| **Chain of Thought** | Step-by-step reasoning for complex tasks |
| **Role Prompting** | Role assignment to condition tone and vocabulary |
| **Output Formatting** | Forcing structured output (JSON, lists, tables) |
| **Iterative Refinement** | Progressive improvement cycle over an initial draft |

### Real use cases

1. **Structured data extraction from mortgage applications** — combining Role Prompting + Output Formatting + Few-Shot to extract JSON-structured data directly insertable into a CRM
2. **Commercial email drafting** — applying Iterative Refinement + Role Prompting to adjust tone, length, and call to action across multiple iterations

---

## Part 2 — Model Parameters

Comparative experiments with the parameters that control `gpt-4o` behavior, running the same prompt under different configurations to observe the effect of each parameter.

### Parameters explored

| Parameter | Values tested | Main effect |
|-----------|--------------|-------------|
| `temperature` | 0.0 / 0.5 / 1.0 / 1.5 | Randomness and creativity of responses |
| `top_p` | 0.1 / 0.5 / 0.9 / 1.0 | Breadth of candidate vocabulary |
| `presence_penalty` | 0.0 / 0.6 / 1.5 | Diversity of topics explored |
| `frequency_penalty` | 0.0 / 0.8 | Reduction of word repetition |

The notebook also includes answers to key theoretical questions:
- What is the difference between `top_p` and `temperature`?
- Why is it not recommended to adjust both at the same time?
- What is the difference between `presence_penalty` and `frequency_penalty`?

---

## How to run it

### Prerequisites

- Azure account with an active Azure OpenAI resource
- Active `gpt-4o` deployment in your resource
- Python 3.10+
- `openai>=1.40.0` installed

### Configuration

In the configuration cell of each notebook, fill in your credentials:

```python
AZURE_ENDPOINT    = "https://YOUR-RESOURCE.openai.azure.com/"
AZURE_API_KEY     = "YOUR_API_KEY"
AZURE_API_VERSION = "2024-02-01"
DEPLOYMENT_NAME   = "gpt-4o"  # exact name of your deployment in Azure
```

### Execution

Both notebooks are independent and self-contained. Run cells top to bottom. There is no need to run Part 1 before Part 2.

---

## Stack

- Azure AI Foundry
- Azure OpenAI `gpt-4o`
- Python · `openai` SDK
