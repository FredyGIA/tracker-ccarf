# Tracker CCAR-F

Aplicación de un solo archivo para preparar el examen **Claude Certified Architect – Foundations** (60 preguntas, 120 minutos, 720 sobre una escala de 100–1000).

Abre `tracker-ccarf.html` con doble clic o publícalo como sitio estático. No tiene build, ni dependencias, ni CDN: funciona sin conexión salvo los enlaces a la documentación.

## Qué incluye

| Sección | Contenido |
|---|---|
| Avance | Cobertura ponderada por el peso real de cada dominio (27/20/20/18/15), calculada sobre minutos completados |
| Ejercicios | 39 ejercicios ejecutables de tipo BUILD, DECIDE, DIAGNOSE y RECALL, con criterio de aceptación y pista colapsable |
| Quiz | Las 8 preguntas del quiz del curso *Claude Code in Action*, con la explicación de las 4 opciones |
| Simulacros | Dos exámenes de 60 preguntas cronometrados a 120 minutos, con revisión completa |
| Miss log | Registro de preguntas falladas con el porqué de cada distractor |
| Estoy listo | Checklist de cierre antes de reservar el examen |

Todo el contenido está en **español e inglés**: el examen real se presenta en inglés.

## Sobre las preguntas

Las 8 del Quiz provienen del quiz público del curso Claude Code in Action de Anthropic Academy. **Las 120 de los simulacros son propias**, construidas sobre el blueprint del examen y la documentación vigente: no son preguntas oficiales de Anthropic ni reproducen el examen real.

## Dónde se guarda el progreso

En `localStorage`, bajo la clave `ccarf-tracker-v1`, **solo en el navegador donde lo usas**. Nunca viaja a este repositorio ni a ningún servidor.

Consecuencias prácticas:

- El PC y el celular son **dos progresos distintos**, aunque abras la misma URL.
- Limpiar los datos del navegador borra el avance. Copia o exporta con frecuencia.
- Abierto como archivo local (`file://`), Safari bloquea el almacenamiento. Si aparece la barra roja de aviso, ese navegador no está guardando nada: úsalo publicado o cámbiate a Chrome o Edge.

## Llevar el progreso a otro dispositivo

La sección **Sincronizar y analizar** tiene lo necesario:

| Botón | Para qué |
|---|---|
| Copiar progreso | Pone todo el estado como JSON en el portapapeles. Pésalo en kilobytes, no en megas: con un simulacro completo ronda los 2 KB, así que cabe en un mensaje de WhatsApp o en una nota. |
| Pegar progreso | Abre un cuadro donde pegas ese JSON. Pide confirmación y **reemplaza** el progreso local, no lo fusiona. |
| Copiar informe para análisis | Genera un resumen en Markdown (cobertura por dominio, fallos del quiz y de los simulacros con su anti-patrón, miss log y checklist) pensado para pegarlo en un chat y pedir un plan de refuerzo. |
| Descargar JSON | La copia de seguridad en archivo, igual que el botón de la cabecera. |

Flujo típico: terminas un simulacro en el PC, **Copiar progreso**, te lo envías por mensaje, lo abres en el celular y **Pegar progreso**. Para pedir análisis, **Copiar informe** y pégalo en el chat.

Si el navegador no permite copiar solo, el texto aparece en un cuadro para seleccionarlo a mano.

> **No subas tu progreso a este repositorio.** Es público y el miss log contiene tus puntos débiles. `.gitignore` ya excluye `ccarf-progreso-*.json`. Si quieres guardarlo en GitHub, usa un **gist secreto**: pega ahí el JSON y, desde el otro dispositivo, cópialo del gist y úsalo en «Pegar progreso». Un gist secreto no es privado de verdad —cualquiera con el enlace lo ve— pero no aparece en búsquedas ni en tu perfil.

## Publicarlo

El repositorio ya está listo para cualquier hosting estático. `index.html` solo redirige a `tracker-ccarf.html`, y `.nojekyll` evita que GitHub Pages procese los archivos.

**GitHub Pages:** Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`. Queda en `https://<usuario>.github.io/<repo>/`.

**Cloudflare Pages:** conecta el repositorio, deja el comando de build vacío y el directorio de salida en `/`. Para cerrarlo con contraseña, añade una política de Cloudflare Access sobre el dominio.

**Netlify:** arrastra la carpeta o conecta el repositorio, sin comando de build. La protección por contraseña es una función de pago.

> Un repositorio privado **no** hace privado el sitio: en los planes Pro y Team de GitHub, Pages se publica abierto a internet aunque el repositorio esté oculto. Para un sitio con control de acceso real hace falta GitHub Enterprise Cloud, o poner Cloudflare Access o Netlify delante.

## Archivos

```
index.html          redirección a la app
tracker-ccarf.html  la aplicación completa
.nojekyll           desactiva el procesado Jekyll en GitHub Pages
```

El material de estudio personal (plan, notas del curso, guía en PDF) está excluido en `.gitignore`.
