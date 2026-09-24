# Agentes de IA en el ciclo de vida del desarrollo de software

Deck de propuesta y entendimiento sobre la implementación de agentes de IA en el ciclo de vida del desarrollo de software (SDLC), del Laboratorio de Inteligencia Artificial de la Universidad Nacional de Colombia sede Manizales.

**Presentación en vivo: https://liaunal.github.io/AgentPt/**

Este repositorio es únicamente para `index.html`.

## Qué es

Un HTML independiente (HTML + CSS + JS, sin build ni dependencias), construido de forma incremental, que desarrolla la propuesta de adopción de agentes en el SDLC: motivación, evidencia con métricas citadas, riesgos y la respuesta metodológica, hasta el stack SPEC-WEAVER. 22 slides organizados en 6 módulos.

## Contenido

| # | Módulo | Tema |
|---|--------|------|
| 1 | Motivación | Ciclo de vida tradicional y su reconstrucción con IA |
| 2 | Perfiles en evolución | Perfiles tradicionales, PO/analistas de requerimientos y reparto IA/humano por etapa |
| 3 | Chat vs Agente | Diferencia chat/agente y benchmarks de agentes de código en el mercado (pagos y gratuitos) |
| 4 | Evidencia | Estadísticas citadas de productividad y adopción, matices de contexto, efecto amplificador de la IA y riesgos consolidados |
| 5 | La respuesta | Contexto amplio necesario, ingeniería aplicada a la IA, ecosistema de piezas y vínculo requisitos→código, con capturas reales del flujo brief→PRD→épicas→memoria |
| 6 | UN-SpecWeaver | El stack: qué herramientas ya se conectan y cuáles están en roadmap |

Cierra siempre con una diapositiva de **Fuentes**, con la cita completa de cada estadística usada en el deck.

## Navegación

| Acción | Teclas |
|--------|--------|
| Siguiente slide | `→`, `PageDown`, `Espacio` |
| Slide anterior | `←`, `PageUp` |
| Primer / último slide | `Home` / `End` |

También hay botones de flecha atrás/adelante y contador en la esquina inferior derecha, y una barra superior con los módulos.

En móvil y tablet: desliza el dedo a izquierda o derecha para cambiar de slide.

## Responsive

Se adapta a la resolución sin configuración extra:

- **Escritorio (≥1040px):** texto a la izquierda, diagrama a la derecha.
- **Portátil / tablet horizontal:** mismo layout con tipografía reducida.
- **Tablet vertical y móvil:** una sola columna (texto arriba, diagrama abajo) con scroll dentro del slide.
- **Móvil (≤560px):** los botones pasan a flechas, se oculta el running title y los logos se reducen.
- **Móvil horizontal (alto ≤520px):** modo compacto para no perder el cuerpo del slide.
- **Pantallas ≥1900px:** tipografía ampliada para proyección en sala.

## Ejecutar localmente

No requiere instalación ni build. Cualquier servidor estático sirve:

```bash
git clone https://github.com/GCPDSLAB/AgentPt.git
cd AgentPt
python3 -m http.server 8000
```

Abre http://localhost:8000/.

## Estructura

```
index.html             # Deck de la propuesta (22 slides, 6 modulos)
assets/css/styles.css  # Estilos y tema visual compartido
assets/js/app.js       # Navegacion, teclado y contador
assets/images/         # Logos, iconos y capturas usadas en las diapositivas
.github/workflows/     # Despliegue automatico a GitHub Pages
```

## Despliegue

Cada push a `main` dispara el workflow [`pages.yml`](.github/workflows/pages.yml), que publica el sitio estático de este repositorio en GitHub Pages.
