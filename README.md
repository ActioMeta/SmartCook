
# Documentación Técnica de SmartCook
## 1. Visión General
SmartCook es una aplicación web que permite a los usuarios subir imágenes de ingredientes. A través de un modelo de inteligencia artificial (IA), la aplicación detecta los ingredientes y sus cantidades, y luego consulta una API externa (Spoonacular) para obtener recetas posibles y detalles culinarios adicionales.

## 2. Arquitectura General
**Frontend:** Django

**Backend IA:** FastAPI

**ML Pipeline:** Modelo de visión entrenado con imágenes de ingredientes

**Almacenamiento de Imágenes:** Sistema de archivos del servidor, organizado por usuario

**Base de Datos:** PostgreSQL (Dockerizado)

**API externa:** Spoonacular

## 3. Funcionalidades Clave
- Subida de imágenes por el usuario

- Identificación de ingredientes y cantidades (unidad, peso, número)

- Llamada a Spoonacular con los ingredientes detectados

-  Retorno de recetas con instrucciones

- Historial de búsquedas por usuario

## 4. Modelo de IA
**Tipo:** Modelo de detección de objetos (YOLOv8)

**Entrenamiento inicial:** Google Colab

**Futuro despliegue:** Servidor local con FastAPI

**Evaluación:** Accuracy, Precision, Recall, F1-Score

**Código fuente:** Privativo

## 5. Flujo de Trabajo
- El usuario sube una imagen desde la web.

- Django la almacena y envía la ruta a FastAPI.

- FastAPI llama al modelo IA.

El modelo retorna:

- Lista de ingredientes detectados

- Cantidades estimadas (de ser posible)

- FastAPI llama a Spoonacular y recibe recetas.

- La información se guarda y se muestra al usuario.

## 6. Pendiente por Definir
- Dataset(s) compatibles a fusionar (imagen, etiquetas, cantidades)

- Reglas de conversión entre unidades (ml a gramos, piezas, etc.)

- Entrenamiento y mejora iterativa del modelo con datos reales

- Posibles validaciones manuales para mejorar precisión

## 7. Seguridad y Privacidad
- Modelo cerrado, no se expondrá por API pública

- Las imágenes se almacenan en carpetas privadas por usuario

- Las credenciales del sistema se gestionan con .env
