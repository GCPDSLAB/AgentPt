# specweaver

Deck del seminario **"Principios de IA agéntica para el desarrollo de software"**, del Laboratorio de Inteligencia Artificial de la Universidad Nacional de Colombia sede Manizales.

**Presentación en vivo: https://amalvarezme.github.io/specweaver/**

Autor: A.M Álvarez-Meza, PhD — Seminario de Investigación, UNAL Manizales.

## Qué es

Una presentación estática (HTML + CSS + JS, sin build ni dependencias) de 61 slides organizados en 12 módulos, más una serie de guías de demo en vivo.

## Contenido

| # | Módulo | Tema |
|---|--------|------|
| 1 | IA → Software | Ciclo de vida tradicional, reconstruido por IA, y reparto IA/humano |
| 2 | Forward Deployed Engineer | Perfiles clásicos, roles de IA y el cruce que define al FDE |
| 3 | IA Generativa | Qué es y qué no es un LLM |
| 4 | Context Window | Attention decay y compactación |
| 5 | Chat vs Agente | Tools y capacidad de acción |
| 6 | Evolución del Contexto | AGENTS.md → Skills → sub-agentes |
| 7 | God Agent | Por qué degrada un agente monolítico |
| 8 | SDD Orchestrator | Spec-Driven Development y el DAG de fases |
| 9 | Engram | Memoria persistente entre sesiones |
| 10 | Skills Registry | Progressive disclosure de instrucciones |
| 11 | Stack y Bibliotecas | gentle-ai y ecosistema |
| 12 | SetUp y cierre | El stack, por qué CLI, GentlemanDots y cierre |

## Demos en vivo

Guías paso a paso en [`demos/`](demos/):

- [`01-engram.md`](demos/01-engram.md) — Memoria persistente para agentes
- [`02-agentes-paralelos.md`](demos/02-agentes-paralelos.md) — Sub-agentes en paralelo
- [`03-skills.md`](demos/03-skills.md) — Contexto preciso bajo demanda
- [`04-sdd.md`](demos/04-sdd.md) — De idea a dashboard con SDD

## Navegación

| Acción | Teclas |
|--------|--------|
| Siguiente slide | `→`, `PageDown`, `Espacio` |
| Slide anterior | `←`, `PageUp` |
| Primer / último slide | `Home` / `End` |

También hay botones de flecha atrás/adelante y contador en la esquina inferior derecha, y una barra superior con los módulos.

En móvil y tablet: desliza el dedo a izquierda o derecha para cambiar de slide.

## Responsive

El deck se adapta a la resolución sin configuración extra:

- **Escritorio (≥1040px):** texto a la izquierda, diagrama a la derecha.
- **Portátil / tablet horizontal:** mismo layout con tipografía reducida.
- **Tablet vertical y móvil:** una sola columna (texto arriba, diagrama abajo) con scroll dentro del slide.
- **Móvil (≤560px):** los botones pasan a flechas, se oculta el running title y los logos se reducen.
- **Móvil horizontal (alto ≤520px):** modo compacto para no perder el cuerpo del slide.
- **Pantallas ≥1900px:** tipografía ampliada para proyección en sala.

## Ejecutar localmente

No requiere instalación ni build. Cualquier servidor estático sirve:

```bash
git clone https://github.com/amalvarezme/specweaver.git
cd specweaver
python3 -m http.server 8000
```

Abre http://localhost:8000.

## Estructura

```
index.html            # Deck completo (todos los slides)
assets/css/styles.css # Estilos y tema visual LIA-UNAL
assets/js/app.js      # Navegación, teclado y contador
assets/images/        # Logo, diagramas y códigos QR
demos/                # Guías de demo en vivo
.github/workflows/    # Despliegue automático a GitHub Pages
```

## Despliegue

Cada push a `main` dispara el workflow [`pages.yml`](.github/workflows/pages.yml), que publica el sitio estático en GitHub Pages.
