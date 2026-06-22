# Polar Training Agent 🏃‍♀️

App de análisis de sesiones Polar Flow con IA para Paola Arenas — Bogotá Half Marathon 2026.

---

## Despliegue en Vercel (10 minutos, gratis)

### Paso 1 — Consigue tu API Key de Anthropic
1. Ve a https://console.anthropic.com
2. Settings → API Keys → Create Key
3. Cópiala (empieza con `sk-ant-...`)

### Paso 2 — Sube el proyecto a GitHub
1. Ve a https://github.com/new
2. Crea un repositorio nuevo (ej: `polar-agent`), privado
3. Sube estos archivos manteniendo la estructura:
```
polar-agent/
├── api/
│   └── analyze.js
├── public/
│   └── index.html
├── package.json
└── vercel.json
```

**Opción fácil — arrastrar y soltar en GitHub:**
- En el repo recién creado, haz clic en "uploading an existing file"
- Primero crea la carpeta `api`: sube `analyze.js` y en el path escribe `api/analyze.js`
- Luego crea `public`: sube `index.html` y escribe `public/index.html`
- Sube `package.json` y `vercel.json` en la raíz

### Paso 3 — Conecta con Vercel
1. Ve a https://vercel.com → Sign up con tu cuenta de GitHub (gratis)
2. Click en "Add New Project"
3. Selecciona tu repositorio `polar-agent`
4. En **Environment Variables** agrega:
   - Key: `ANTHROPIC_API_KEY`
   - Value: tu clave `sk-ant-...`
5. Click **Deploy**

### Paso 4 — Listo
Vercel te dará una URL tipo `https://polar-agent-xxx.vercel.app`
Ábrela, sube los CSV de Polar Flow y haz clic en "Analizar con IA".

---

## Uso local (opcional)

Si quieres correrlo en tu computador:

```bash
npm install -g vercel
cd polar-agent
ANTHROPIC_API_KEY=sk-ant-... vercel dev
```

Luego abre http://localhost:3000

---

## Cómo exportar CSV desde Polar Flow

1. Entra a https://flow.polar.com
2. Ve a **Training** → selecciona una sesión
3. Haz clic en el ícono de exportar (⬇) → **Export CSV**
4. Descarga el archivo y súbelo a la app

Puedes subir múltiples sesiones a la vez (una semana completa).

---

## Qué analiza la app

- **Distribución de zonas FC** usando el método Karvonen calibrado con la FC de reposo y máxima de Paola
- **Diagnóstico de fatiga** basado en Training Load acumulado, Running Index y tendencias de FC
- **Eficiencia metabólica** — relación FC vs ritmo a lo largo del bloque
- **Plan semanal** enfocado en resolver el colapso de ritmo en km 17-21
- **Feedback personalizado** listo para enviarle a Paola directamente

---

## Estructura del proyecto

```
api/analyze.js      → Backend Vercel: proxy seguro a Anthropic API
public/index.html   → Frontend completo (parser CSV + UI + gráficos)
package.json        → Configuración del proyecto
vercel.json         → Routing de Vercel
```
