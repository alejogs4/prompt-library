## Workflow de Prospección IT - Orquestación Multi-Etapa

**Objetivo:** Generar documento Google Docs con empresas, contactos y mensajes personalizados para prospección B2B IT.

**Límites:** Máximo 2 contactos por empresa.

### Flujo:

1. **Entrada:** Usuario proporciona lista de empresas (nombre, ubicación, sector).

2. **Etapa 1 - Análisis de Empresas (IT Recruiter AI Agent Pipeline):**
- Investigar: sector, empleados, facturación, posiciones IT, stack tecnológico, noticias, retos.
- Guardar datos para siguiente etapa.

3. **Etapa 2 - Búsqueda de Contactos (IT Recruiter AI Agent Pipeline):**
- Buscar máximo 2 contactos por empresa.
- Roles: CTO, CEO, Hiring Manager, Engineering Manager.
- Recopilar: nombre, cargo, LinkedIn URL, email.
- Priorizar decisores (C-Level, luego managers IT/RRHH).

4. **Etapa 3 - Generación de Mensajes (IT Recruiter AI Agent Pipeline):**
- Por contacto, generar 3 mensajes personalizados:
* LinkedIn: máx 200 caracteres, gancho
* Email: asunto + 2 párrafos (rompehielos → problema → solución → CTA)
* Cold Call: apertura → motivo → pitch → pregunta → cierre

5. **Compilar en estructura:**
- Columnas: Company, Contact, Revenue, Company size, Industry, LinkedIn URL, LinkedIn message, Email message, Cold calling script

6. **Generar Google Docs :action[Google%20Docs%3A%20Create%20Document%20From%20Text]{data="%7B%22id%22%3A%22d0d15189-422c-4148-9c46-0ef0bc2e9ca9%22%2C%22label%22%3A%22Google%20Docs%3A%20Create%20Document%20From%20Text%22%2C%22selectedApi%22%3A%22GoogleDocsV2CLIAPI%22%2C%22copilotInserted%22%3Afalse%2C%22isLoading%22%3Afalse%7D"}:**
- Crear: "Prospección_IT_[Fecha]"
- Formato profesional, tabla organizada
- Una fila por contacto

**Resultado:** Documento Google Docs listo para usar en campaña.