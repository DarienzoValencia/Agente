🧠 Cesantías-POC
Prueba de Concepto — Agente Inteligente para Consultas de Cesantías y Empresa

Este proyecto construye una prueba de concepto (POC), donde un usuario puede realizar preguntas que serán interpretadas por un agente inteligente basado en un modelo de lenguaje (LLM).
El agente decide dinámicamente entre dos acciones posibles:

Responder con conocimiento general de la empresa (a través de un sistema de búsqueda semántica basado en embeddings y FAISS).

Consultar información de cesantías causadas en una base local (archivo Excel) y devolver el resultado exacto.

🚀 Objetivo

Desarrollar un agente conversacional con capacidad de:

Comprender el contexto y la intención del usuario.

Determinar si la pregunta requiere conocimiento institucional o datos de cesant[ias.

Responder usando herramientas específicas (tools) para cada caso.

Mantener contexto y razonamiento controlado con LangGraph.

🧩 Arquitectura General

Componentes principales:

LangGraph Agent: Define la lógica de conversación y la toma de decisiones del LLM.

Tools (funciones externas):

validardoc: consulta información de cesantías en un archivo Excel.

vector_search: realiza búsqueda semántica con embeddings y FAISS para preguntas sobre la empresa.

Modelo LLM: Configurado en models_llm.py, responsable del razonamiento y la generación de respuestas.

Prompts personalizados: Definidos en prompts.py para guiar el comportamiento del agente según el contexto corporativo.

Memoria y Control de Estado: Manejados con MemorySaver de LangGraph.

```
🗂️ Estructura del Proyecto
Cesantías-POC/
│
├── app.py                  # Punto de entrada principal del agente
├── models_llm.py           # Configuración del modelo LLM y bindings
├── prompts.py              # Prompts usados por el agente
├── tools.py                # Tools (funciones) usadas por el agente
├── vector_search.py        # Proceso de retrieval y búsqueda semántica
├── teoria_.pdf             # Documento teórico con sustento conceptual
├── requirements.txt        # Dependencias del proyecto
└── README.md               # Este archivo
```

⚙️ Instalación y Ejecución Local
1️⃣ Clonar el repositorio
git clone https://github.com/tu_usuario/Cesantias-POC.git
cd Cesantias-POC

2️⃣ Crear entorno virtual
python -m venv .venv
source .venv/Scripts/activate  # En Windows

3️⃣ Instalar dependencias
pip install -r requirements.txt

4️⃣ Ejecutar la aplicación
python app.py


Luego puedes escribir preguntas directamente en la consola, por ejemplo:

> ¿Cuánto tengo ahorrado en mis cesantías?
> ¿Qué beneficios ofrece la empresa?

🧮 Funcionamiento del Agente

El flujo del agente sigue esta lógica:

El usuario realiza una pregunta.

El modelo LLM, desplegado mediante LangGraph, analiza la intención.

Si la pregunta contiene datos sobre cesantías → usa la tool validardoc.

Si se relaciona con información de la empresa → usa la tool vector_search.

Retorna la respuesta final estructurada en JSON, junto con su proceso interno de decisión.

🧠 Modelos y Embeddings

Embeddings: Se deja espresado un modelo de open-ai

Vector Store: FAISS (faiss-cpu) para almacenar y buscar los 10 resultados más similares por similitud del coseno.

LLM: Modelo configurable, compatible con OpenAI o alternativas locales (por ejemplo, gpt-4o-mini, Llama-3, etc.).

📄 Entregables

app.py: flujo principal del agente.

🧰 Tecnologías Utilizadas
Tipo	Tecnología
Lenguaje	Python 3.11
Framework IA	LangGraph / LangChain
Almacenamiento vectorial	FAISS
Formato de Respuestas	JSON estructurado
