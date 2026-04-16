# LLM Experiments — Prompt Engineering y Parámetros de Modelos

> 📓 **Nota:** Todos los notebooks están escritos en español.

Colección de experimentos prácticos con técnicas de prompt engineering y parametrización de modelos de lenguaje usando Azure AI Foundry y `gpt-4o`.

---

## ¿Qué contiene este repositorio?

Dos notebooks independientes que exploran cómo sacar el máximo partido a los modelos de lenguaje: el primero a través de las técnicas con las que se construyen los prompts, y el segundo a través de los parámetros que controlan el comportamiento del modelo.

## Contenido

```
llm-experiments/
├── parte1_prompt_engineering.ipynb    # 6 técnicas de prompting + 2 casos reales
├── parte2_parametros_modelo.ipynb     # Experimentación con temperature, top_p y penalties
└── README.md
```

---

## Parte 1 — Prompt Engineering

Exploración práctica de 6 técnicas de prompting con ejemplos ejecutables, análisis de resultados y aplicación a casos de uso reales.

### Técnicas cubiertas

| Técnica | Descripción |
|---------|-------------|
| **Zero-Shot** | Instrucción directa sin ejemplos |
| **Few-Shot** | Ejemplos input→output para fijar el patrón de respuesta |
| **Chain of Thought** | Razonamiento paso a paso para tareas complejas |
| **Role Prompting** | Asignación de rol para condicionar tono y vocabulario |
| **Output Formatting** | Forzar formato estructurado (JSON, listas, tablas) |
| **Iterative Refinement** | Ciclo de mejora progresiva sobre un borrador inicial |

### Casos de uso reales

1. **Extracción de datos de solicitudes hipotecarias** — combinación de Role Prompting + Output Formatting + Few-Shot para extraer datos estructurados en JSON directamente insertables en un CRM
2. **Redacción de email comercial** — aplicación de Iterative Refinement + Role Prompting para ajustar tono, longitud y llamada a la acción en varias iteraciones

---

## Parte 2 — Parámetros del Modelo

Experimentación comparativa con los parámetros que controlan el comportamiento de `gpt-4o`, con el mismo prompt ejecutado bajo diferentes configuraciones para observar el efecto de cada parámetro.

### Parámetros explorados

| Parámetro | Valores probados | Efecto principal |
|-----------|-----------------|-----------------|
| `temperature` | 0.0 / 0.5 / 1.0 | Aleatoriedad y creatividad de las respuestas |
| `top_p` | 0.1 / 0.5 / 0.9 / 1.0 | Amplitud del vocabulario candidato |
| `presence_penalty` | 0.0 / 0.6 / 1 | Diversidad de temas explorados |
| `frequency_penalty` | 0.0 / 0.8 | Reducción de repeticiones de palabras |

El notebook incluye también respuestas a las preguntas teóricas clave:
- ¿Cuál es la diferencia entre `top_p` y `temperature`?
- ¿Por qué no se recomienda ajustar ambos a la vez?
- ¿Cuál es la diferencia entre `presence_penalty` y `frequency_penalty`?

---

## Cómo ejecutarlo

### Requisitos previos

- Cuenta de Azure con un recurso de Azure OpenAI activo
- Deployment de `gpt-4o` activo en tu recurso
- Python 3.10+
- `openai>=1.40.0` instalado

### Configuración

En la celda de configuración de cada notebook, rellena tus credenciales:

```python
AZURE_ENDPOINT    = "https://TU-RECURSO.openai.azure.com/"
AZURE_API_KEY     = "TU_API_KEY"
AZURE_API_VERSION = "2024-02-01"
DEPLOYMENT_NAME   = "gpt-4o"  # nombre exacto de tu deployment en Azure
```

### Ejecución

Ambos notebooks son independientes y autocontenidos. Ejecuta las celdas en orden de arriba a abajo. No es necesario ejecutar la Parte 1 antes de la Parte 2.

---

## Stack

- Azure AI Foundry
- Azure OpenAI `gpt-4o`
- Python · `openai` SDK
