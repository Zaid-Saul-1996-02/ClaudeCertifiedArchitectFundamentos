# Claude Certified Architect — Curso del Agent SDK de Anthropic

Material de clases en notebooks (`.ipynb`) para aprender a construir **soluciones agénticas** con el
**[Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk)** y la **API de Anthropic**.

El contenido está orientado a la preparación de la certificación **Claude Certified Architect /
Engineer**: cubre desde los fundamentos de cómo funciona un LLM hasta el diseño de loops agénticos,
subagentes, hooks, diseño de herramientas e integración con MCP.

---

## Contenido

| Clase | Notebook | Temas |
|-------|----------|-------|
| **Clase 1** | [clases/clase_1/clase_1.ipynb](clases/clase_1/clase_1.ipynb) | Qué es un LLM · Agentic loops y el ciclo `tool_use` · ReAct · `stop_reason` como señal de control · anti-patterns del loop · subagentes y patrón *coordinator* · spawning paralelo con la tool `Task` · workflows multi-step, hooks y *handoffs* |
| **Clase 2** | [clases/clase_2/clase_2.ipynb](clases/clase_2/clase_2.ipynb) | Tools predefinidas · diseño de tools efectivos y descriptions · overlap ambiguo y misrouting · conexión con herramientas externas vía **MCP** · scoping de servidores MCP · `isError` y errores estructurados · `tool_choice` (`auto` / `any` / forced) |

### Material de apoyo

- [clases/clase_1/terminos.md](clases/clase_1/terminos.md) — glosario: token, vocabulario, embedding,
  logits, softmax con temperatura, top-k y top-p.
- [clases/repaso-mas-falladas-d1-d2.md](clases/repaso-mas-falladas-d1-d2.md) — repaso de las preguntas
  más falladas de los días 1 y 2.

---

## Requisitos previos

- **Python 3.13+** (definido en [.python-version](.python-version)).
- **[uv](https://docs.astral.sh/uv/)** como gestor de dependencias y entornos (recomendado).
- Una **API key de Anthropic** ([consola de Anthropic](https://console.anthropic.com/)).
- Para la parte de MCP de la Clase 2, **Node.js** instalado (varios servidores MCP se ejecutan con
  `npx`).

---

## Instalación

### 1. Clonar el repositorio

```bash
git clone <url-del-repo>
cd ClaudeCertifiedArchitect
```

### 2. Instalar `uv` (si no lo tienes)

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# o con Homebrew
brew install uv
```

### 3. Crear el entorno e instalar dependencias

`uv` lee [pyproject.toml](pyproject.toml) y [uv.lock](uv.lock) y reproduce el entorno exacto:

```bash
uv sync
```

Esto crea `.venv/` con las dependencias del proyecto:

- `anthropic` — SDK oficial de la API de Anthropic.
- `claude-agent-sdk` — SDK de agentes de Claude.
- `ipykernel` — kernel para ejecutar los notebooks.

### 4. Configurar la API key

Crea un archivo `.env` en la raíz del proyecto:

```bash
ANTHROPIC_API_KEY=sk-ant-...
```

> El archivo `.env` no debe subirse al repositorio. Asegúrate de mantener tu key privada.

---

## Cómo correr el proyecto

### Opción A — VS Code / Cursor (recomendado)

1. Abre la carpeta del proyecto.
2. Abre cualquier notebook en [clases/](clases/).
3. Selecciona el kernel del entorno `.venv` (Python 3.13).
4. Ejecuta las celdas en orden.

### Opción B — Jupyter en el navegador

```bash
uv run jupyter lab
# o
uv run jupyter notebook
```

Abre el notebook deseado y selecciona el kernel del proyecto.

### Verificar la instalación

```bash
uv run python main.py
# -> Hello from claudecertifiedarchitect!
```

---

## Estructura del proyecto

```
ClaudeCertifiedArchitect/
├── clases/
│   ├── clase_1/
│   │   ├── clase_1.ipynb        # Agentic loops y tool_use
│   │   ├── terminos.md          # Glosario de fundamentos
│   │   └── img/                 # Diagramas (pipeline LLM, tool use)
│   ├── clase_2/
│   │   └── clase_2.ipynb        # Diseño de tools e integración MCP
│   └── repaso-mas-falladas-d1-d2.md
├── extras/
├── main.py                      # Script de verificación
├── pyproject.toml               # Dependencias del proyecto
├── uv.lock                      # Lockfile reproducible
├── .python-version              # Python 3.13
└── .env                         # ANTHROPIC_API_KEY (no versionar)
```

---

## Recomendaciones de uso

- Ejecuta las celdas **en orden**: cada notebook construye los conceptos de forma incremental.
- Cada llamada a la API consume tokens y tiene coste. Revisa los
  [precios de Anthropic](https://www.anthropic.com/pricing) antes de ejecutar loops largos.
- Si una celda falla con un error de autenticación, confirma que el `.env` está cargado y que la key
  es válida.

---

## Recursos

- [Documentación del Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk)
- [Documentación de la API de Anthropic](https://docs.claude.com/en/api)
- [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)
- [Consola de Anthropic](https://console.anthropic.com/)
