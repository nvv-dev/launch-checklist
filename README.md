# launch-checklist

> Lanzar sabiendo cómo medirlo y cómo volver atrás.

**Checklist de lanzamiento** · Skill para agentes de código de la comunidad [nvvdev](https://github.com/nvv-dev). Funciona en Claude Code como plugin o como skill suelta, y en cualquier agente compatible con el formato abierto [`SKILL.md`](https://agentskills.io).

*English summary at the end.*

## Qué hace

Revisa con evidencia, antes de lanzar, la medición (meta, línea base, evento), las páginas legales, la ficha de la tienda y las páginas, el anuncio, el canal de comentarios y el plan de vuelta atrás. Después del lanzamiento repasa la misma lista: métrica contra la meta, lo que reportaron los usuarios, lo que falló y los aprendizajes, que guarda en el contexto del producto. Un fallo en medición, páginas legales o vuelta atrás es bloqueante.

## Objetivo

Que ningún lanzamiento salga sin forma de saber si funcionó ni forma de deshacerlo.

## Cuándo usarla

- Antes de lanzar un producto, una app, una funcionalidad o un sitio
- En la revisión del día 1, 7 y 30 después del lanzamiento

## Cuándo no

- Despliegues técnicos sin anuncio: usa pre-deploy-audit
- Para publicar el anuncio: la skill revisa, no publica

## Ejemplo

```text
/launch-checklist para la salida de Widget Studio a producción el 15 de noviembre.
```

## Cómo se activa

Esta skill **solo se activa a mano** (`disable-model-invocation: true`): no ocupa contexto en cada sesión y la invocas cuando la necesitas:

- Instalada como plugin: `/launch-checklist:launch-checklist`
- Copiada a `.claude/skills/`: `/launch-checklist`

## Instalación

### Opción 1: Claude Code, como plugin (recomendada)

Dentro de Claude Code:

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install launch-checklist@nvvdev
```

La primera línea agrega el catálogo de nvvdev una sola vez; la segunda instala esta skill. Si prefieres el paquete completo, instala `growth-workflow@nvvdev` en su lugar (incluye esta skill y las demás de [growth-workflow](https://github.com/nvv-dev/growth-workflow)); no instales los dos a la vez.

### Opción 2: Claude Code, copiando la skill

Para un solo proyecto (se comparte con tu equipo por git):

```bash
git clone --depth 1 https://github.com/nvv-dev/launch-checklist.git /tmp/launch-checklist
mkdir -p .claude/skills
cp -R /tmp/launch-checklist/skills/launch-checklist .claude/skills/
```

Para todos tus proyectos, cópiala en `~/.claude/skills/` en lugar de `.claude/skills/`.

### Opción 3: otros agentes

Copia la carpeta `skills/launch-checklist/` en la carpeta de skills de tu agente (cada agente documenta la suya). Con la CLI [skills](https://github.com/vercel-labs/skills) de Vercel Labs:

```bash
DISABLE_TELEMETRY=1 npx skills add nvv-dev/launch-checklist
```

### Verificar

Abre una sesión nueva y pregunta "¿qué skills tienes disponibles?"; `launch-checklist` debe aparecer. Con el plugin, `/plugin` la muestra como instalada.

### Actualizar o desinstalar

- Plugin: `/plugin marketplace update nvvdev` para actualizar; `/plugin uninstall launch-checklist@nvvdev` para quitarla.
- Copia manual: repite la copia para actualizar, o borra la carpeta `.claude/skills/launch-checklist`.

Antes de instalar cualquier skill, incluida esta, conviene leerla: es un solo archivo, [`skills/launch-checklist/SKILL.md`](skills/launch-checklist/SKILL.md). Ver [vetting-external-skills](https://github.com/nvv-dev/vetting-external-skills).

## Contenido

| Ruta | Qué es |
|---|---|
| `skills/launch-checklist/SKILL.md` | La skill: instrucciones en inglés para que los escáneres de seguridad las analicen completas; el agente responde en tu idioma |
| `.claude-plugin/plugin.json` | Manifiesto para instalarla como plugin |
| `.github/workflows/` | Validación de estructura y escaneo con SkillSpector en cada cambio |

## Contribuir

Este repo se **genera** desde [nvv-dev/growth-workflow](https://github.com/nvv-dev/growth-workflow), donde vive la versión canónica. Abre issues y PRs allí. La mejor contribución es un caso real en la sección *Known failures* de la skill, con la regla que lo evita.

## Origen

Escrita desde cero por nvvdev. Inspirada en: [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (launch).

## Licencia

MIT.

---

## English

**launch-checklist** — Before and after a launch: measurement, legal pages, store listing, announcement, feedback channel and rollback plan, with evidence for every item.

Install in Claude Code with `/plugin marketplace add nvv-dev/claude-plugins` and `/plugin install launch-checklist@nvvdev`, or copy `skills/launch-checklist/` into `.claude/skills/` (project) or `~/.claude/skills/` (personal). Other agents: copy the folder into their skills directory, or run `DISABLE_TELEMETRY=1 npx skills add nvv-dev/launch-checklist`. Manual-only skill: invoke it with `/launch-checklist:launch-checklist` (plugin) or `/launch-checklist` (copied). Canonical source: [nvv-dev/growth-workflow](https://github.com/nvv-dev/growth-workflow). License: MIT.
