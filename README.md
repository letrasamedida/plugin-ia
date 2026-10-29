# Letras a Medida para Claude Code y Codex
<!-- SEO-TANDA-20261027-04 -->

Plugin de [Letras a Medida](https://letrasamedida.com) para **Claude Code** y **Codex**. Conecta tu agente con el
conector público de LAM (`https://mcp.letrasamedida.com/mcp`) y le enseña a aconsejarte un rótulo de letras corpóreas:
qué preguntarte, qué material encaja con tu uso, qué tamaño se lee bien a tu distancia y qué color pedir.

Al final te deja **un enlace que abre el Personalizador con tu diseño ya cargado**. Ahí lo revisas, ves el precio y lo
compras. El agente no puede hacer pedidos ni carritos, ni generar el archivo de producción: el conector es de solo
lectura y no pide inicio de sesión.

## Instalar en Claude Code

En una sesión de Claude Code:

```
/plugin marketplace add letrasamedida/plugin-ia
/plugin install letras-a-medida@letrasamedida
```

O desde la terminal:

```bash
claude plugin marketplace add letrasamedida/plugin-ia
claude plugin install letras-a-medida@letrasamedida
```

Abre una sesión nueva (o usa `/reload-plugins`) y pide tu rótulo, por ejemplo: «Quiero letras para la fachada de mi
cafetería». La skill también se puede lanzar a mano con `/letras-a-medida:disenar-rotulo`.

## Instalar en Codex

En la app (ChatGPT de escritorio, pestaña de Codex): **Plugins** → añadir el marketplace `letrasamedida/plugin-ia` → instalar
**Letras a Medida**, y abrir un chat nuevo.

Desde la terminal:

```bash
codex plugin marketplace add letrasamedida/plugin-ia
codex plugin add letras-a-medida@letrasamedida
```

(o `/plugins` dentro de Codex). Si se actualiza el plugin, vuelve a instalarlo: Codex trabaja con una copia.

## Qué hay dentro

```
.claude-plugin/marketplace.json        marketplace para Claude Code
.agents/plugins/marketplace.json       marketplace para Codex
plugins/letras-a-medida/
  .claude-plugin/plugin.json           manifiesto de Claude Code
  .mcp.json                            conector para Claude Code
  .codex-plugin/plugin.json            manifiesto de Codex
  codex.mcp.json                       conector para Codex
  skills/disenar-rotulo/SKILL.md       el oficio, común a los dos
  assets/icono.png                     icono
```

## Privacidad

El conector recibe solo los datos del rótulo (texto, medidas, material, tipografía y color). Para frenar abusos guarda
la dirección IP desde la que llega cada petición durante 30 días.
