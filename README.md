# Ecosistema de Automatización de IA Autónomo — "Nexo Contable"

**Entrega Final · Módulo 8 · Curso IA & Automatización (Coderhouse)**
Alumno: Alfredo Argañaraz

Pipeline de contenido de extremo a extremo con memoria RAG, validación humana (HITL), resiliencia ante fallos, salida multicanal y panel de control ejecutivo.

## Enlaces

- **Video demo (3 min):** https://drive.google.com/drive/folders/1qgNIxZhOw-AUUk_zkDRO5D-sT44OABnu?usp=sharing
- **Dashboard de control (público):** https://airtable.com/app9kqKH8btJO26m1/pagEB3CY4mV8wvIXq
- **Base de datos (modo lectura):** https://airtable.com/invite/l?inviteId=invTDwHPOMBZ631t6&inviteToken=98f17901690f6f8f91b353a0b8c496dc19a649ec89e302d85a9aa908afe929d9

## ¿Qué hace el sistema?

Transforma una "idea semilla" cargada en Airtable en una pieza de contenido publicada, de forma autónoma:

1. Interpreta la idea con IA (GPT-4o mini vía OpenRouter), apoyándose en una base de conocimiento privada (RAG).
2. Se detiene en un punto de validación humana obligatorio (HITL) antes de cualquier acción crítica.
3. Distribuye por dos canales en paralelo: Slack y Telegram.
4. Registra cada fallo o dato incompleto en una malla de resiliencia.
5. Todo el ciclo se monitorea desde un dashboard de control público.

## Stack tecnológico

| Capa | Herramienta |
|------|-------------|
| Orquestador | n8n (cloud) |
| Base de datos | Airtable (3 tablas vinculadas) |
| Procesamiento de IA | OpenRouter → GPT-4o mini (con RAG) |
| Canales de salida | Slack + Telegram |

## Contenido del repositorio

- `EntregaFinal_M8_Ecosistema_NexoContable.pdf` — Documento con los 5 entregables.
- Los 3 archivos `.json` — Blueprints de los workflows de n8n (Import from File).

## Los tres workflows

1. **Nexo - Generación de Contenido:** genera el borrador con IA + RAG, lo guarda y avisa por Slack y Telegram. Incluye una rama que detecta datos incompletos y los marca como Error.
2. **Nexo - Distribución (HITL):** publica solo cuando el humano aprobó (filtro de doble candado).
3. **Nexo - Manejo de Errores:** captura fallos, los registra en Airtable y alerta por Slack.

---

*Los blueprints no contienen claves de API. Las credenciales se gestionan cifradas dentro de n8n.*
