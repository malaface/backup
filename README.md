# Sistema RAG de Nutrición con n8n

Este repositorio contiene los flujos de trabajo y la base de conocimiento para un sistema de RAG (Retrieval-Augmented Generation) enfocado en nutrición, implementado en n8n.

## Estructura del Proyecto

```
/n8n/backup/
├── rag/
│   └── nutriologo/
│       ├── Cuerpo balanceado y salud.txt
│       ├── Guia completa de Nutrientes.txt
│       ├── planificación alimentaria y nutricion completa.txt
│       ├── dietas, sueño y comidas.txt
│       ├── Nutrición para Mejorar el Rendimiento Deportivo.txt
│       ├── Nutrición Clínica y Aplicada.txt
│       └── Nutrición para Pacientes Cardiacos.txt
└── workflows/
    ├── Local_RAG_Nutriologo.json
    ├── Asistente_RAG.json
    └── AI_Agent.json
```

## Configuración de los Flujos de Trabajo

### 1. Local_RAG_Nutriologo.json
Este flujo de trabajo maneja la base de conocimiento local para el asistente de nutrición.

**Configuración de nodos principales:**
- **File Read Node**: Configurado para leer archivos de la carpeta `/n8n/backup/rag/nutriologo/`
- **Text Processing Node**: Procesa el contenido de los archivos para la base de datos RAG
- **Vector Store Node**: Almacena los embeddings de los documentos procesados

### 2. Asistente_RAG.json
Este flujo implementa el asistente virtual de nutrición.

**Configuración de nodos principales:**
- **HTTP Trigger Node**: Configurado para recibir consultas
- **RAG Query Node**: Conectado a la base de datos vectorial
- **LLM Node**: Configurado con el modelo de lenguaje preferido
- **HTTP Response Node**: Devuelve las respuestas generadas

### 3. AI_Agent.json
Este flujo maneja la lógica del agente de IA.

**Configuración de nodos principales:**
- **Webhook Node**: Para recibir solicitudes
- **Function Node**: Contiene la lógica de procesamiento
- **Condition Node**: Para tomar decisiones basadas en la entrada
- **Set Node**: Para manipular datos

## Base de Conocimiento

Los archivos de texto en `/n8n/backup/rag/nutriologo/` contienen la información que alimenta la base de datos RAG. Estos archivos incluyen:
- Guías nutricionales
- Información clínica
- Planes de alimentación
- Recomendaciones deportivas
- Información sobre dietas y sueño

## Actualización de la Base de Conocimiento

Para actualizar la información de la base de datos RAG:

1. Coloca los nuevos archivos de texto en la carpeta `/n8n/backup/rag/nutriologo/`
2. Asegúrate de que los archivos mantengan el formato .txt
3. Ejecuta el flujo de trabajo `Local_RAG_Nutriologo.json` para procesar los nuevos documentos

**Nota importante**: Los archivos DEBEN estar ubicados en la ruta exacta `/n8n/backup/` y sus subcarpetas correspondientes para que el sistema funcione correctamente. Cualquier cambio en la estructura de carpetas requerirá actualizar las configuraciones de los nodos en los flujos de trabajo.

## Requisitos del Sistema

- n8n instalado y configurado
- Acceso a un modelo de lenguaje (LLM)
- Espacio suficiente para almacenar la base de datos vectorial
- Permisos de lectura/escritura en la carpeta `/n8n/backup/` 