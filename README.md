# Clasificación y Triage de Leads Comerciales con IA

##  Descripción

Sistema de automatización para clasificar y priorizar leads comerciales utilizando Inteligencia Artificial.

El sistema recibe nuevos leads desde Airtable, analiza sus datos mediante OpenAI, determina una prioridad (Alta, Media o Baja), actualiza el registro y envía una notificación por Slack.

##  Herramientas

- Make — Automatización del flujo
- Airtable — Base de datos CRM
- OpenAI — Clasificación mediante IA
- Slack — Notificaciones comerciales

##  Objetivo

Automatizar el proceso de clasificación inicial de leads para que el equipo comercial pueda identificar rápidamente cuáles requieren mayor atención.

## Flujo principal

Airtable → OpenAI → Router → Airtable → Slack

El Router divide los leads en cuatro caminos:

- Alta
- Media
- Baja
- Error

## Clasificación

### Alta
Presupuesto igual o superior a $5.000.000.

### Media
Presupuesto entre $1.000.000 y $4.999.999.

### Baja
Presupuesto inferior a $1.000.000.

### Error
Se utiliza cuando faltan datos necesarios para realizar una clasificación válida.

## Aprobación humana (HITL)

Los leads que requieren aprobación quedan bloqueados hasta que una persona establezca `Aprobado = true`.

Solo después de esta aprobación el segundo escenario continúa y ejecuta la acción posterior.

## Manejo de errores

El flujo incorpora:

- Reintentos automáticos en OpenAI.
- Reintentos en las actualizaciones de Airtable.
- Reintentos en las notificaciones de Slack.
- Ruta específica para datos incompletos.

## Pruebas realizadas

Se probaron:

- Lead de prioridad Alta.
- Lead de prioridad Media.
- Lead de prioridad Baja.
- Lead con presupuesto vacío.
- Flujo de aprobación humana.

Las tres prioridades fueron procesadas correctamente y el dato incompleto fue enviado a la ruta de error.

## Archivos

- Blueprint: configuración del escenario de Make.
- Evidencias: capturas de las ejecuciones.
- Documentación: arquitectura y procedimientos.

## Base de datos

La información de los leads se almacena en la tabla `CRM IA` de Airtable.

##  Autor

David
Comisión 96910
Universidad de La Sabana

Link AirTable: https://airtable.com/invite/l?inviteId=invw9CfqV5mUrrxoQ&inviteToken=fafcb420248f8125fb4d038b42a8ad92ddd9f33d6c7e0de2f4ba8ed6d9b3ba88&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts
