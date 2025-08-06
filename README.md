# Vision‑Transformers‑Segment‑Anything  
**De las Convoluciones a la Atención**  

Una exploración profunda del cambio de paradigma en Visión por Computador: desde las clásicas redes convolucionales (CNN) hasta las arquitecturas basadas en Transformers, a través de tres pilares recientes en este campo:

- **Vision Transformers (ViT)**  
- **Segment Anything Model (SAM)** de Meta  
- **DETR** (DEtection TRansformer) para detección de objetos  

---

## 🧠 Introducción

Durante casi una década, las **CNNs** dominaron tareas de clasificación, detección y segmentación visual gracias a su habilidad para extraer patrones locales con filtros convolucionales. Sin embargo, pensadas para captar contexto local, requerían redes muy profundas para modelar relaciones globales.

La llegada del Transformer en NLP en 2017 cambió el juego: su mecanismo de **auto-atención global** permitió procesar y comprender dependencias a largo plazo en una sola pasada.

Este repositorio muestra cómo esa evolución llegó a visión: **ViT**, **SAM** y **DETR** reescribieron las reglas del juego.

---

## 📘 Contenido del repositorio

- `notebooks/`: cuadernos con ejemplos funcionales para ViT, SAM y DETR.
- `scripts/`: scripts de entrenamiento o inferencia en PyTorch.
- `README.md`: explicación técnica y conceptual del enfoque general.

---

## 📚 Pilares Tecnológicos

### Vision Transformers (ViT)

- **Inspiración**: Transformers de NLP adaptados a visión (imagen = secuencia de parches).  
- **Proceso**: divide la imagen en parches (16×16 px), los embebe y aplica atención global.  
- **Ventajas**:
  - Alcance global desde la primera capa.
  - Escalabilidad con datos masivos.
  - Excelente transferencia de aprendizaje desde Backbones preentrenados.

**Ejemplo**: Fine‑tuning de ViT con PyTorch sobre CIFAR‑10. El notebook `notebooks/vit_finetune.ipynb` muestra cómo cargar, entrenar y guardar un ViT personalizado.

---

### Segment Anything Model (SAM) de Meta

- Modelo universal de segmentación capaz de aislar *cualquier objeto* con prompts interactivos (puntos, bounding boxes o texto).
- **Arquitectura**:
  - Codificador de imagen (ViT pretrained)
  - Codificador de prompts
  - Decodificador de máscaras dinámicas
- **Capacitado con más de mil millones de máscaras generadas automáticamente en 11M imágenes**
- **Usos**: edición visual, robótica, medicina, etiquetado semiautomático y más.

Ejemplo en `notebooks/sam_interactive.ipynb`: muestra cómo cargar SAM, definir un punto de input y obtener múltiples máscaras con score.

---

### DETR – Detección de Objetos con Transformers

- Replantea la detección: **modelo end‑to‑end sin anchor boxes ni NMS manual**.
- Combina un backbone CNN con varias queries de Transformer.
- Utiliza bipartite matching para asignar predicciones a ground truth.
- Simplifica pipeline y reduce hiperparámetros.

Ejemplo en `notebooks/detr_detection.ipynb`: detección visual con bounding boxes sobre imágenes propias, usando modelos preentrenados en COCO.

---

## 🔍 Comparativa: CNNs vs Transformers en visión

| Aspecto                  | CNNs                                 | Transformers (ViT / DETR / SAM)       |
|--------------------------|---------------------------------------|---------------------------------------|
| Procesamiento            | Local (kernels)                      | Global (auto-atención)                |
| Contexto visual          | Limitado a receptive field local      | Aborda relaciones a gran escala       |
| Interpretabilidad        | Filtros y pooling                    | Atención explicable entre parches     |
| Pipeline (detección)     | Anchor‑boxes, NMS                    | Predicciones directas con queries     |
| Segmentación             | Por clase                             | Interactiva, independiente de clase   |
| Escalabilidad            | Costosa en profundidad                | Escalable con más datos y heads       |

---

## 🚀 Requisitos y uso

1. Clona el repositorio:
```
   git clone https://github.com/Orliluq/Vision-Transformers-Segment-Anything.git
   cd Vision-Transformers-Segment-Anything
```

2. Crea un entorno virtual (recomendado):
```
  python -m venv venv
  source venv/bin/activate
```

3. Instala dependencias:
```
pip install torch torchvision timm segment-anything opencv-python matplotlib
```

4. Explora los notebooks o scripts:

- `notebooks/vit_finetune.ipynb`
- `notebooks/sam_interactive.ipynb`
- `notebooks/detr_detection.ipynb`

5. Cada notebook explica cómo subir imágenes, cargar modelos, hacer inferencia y visualizar resultados.

---

## ✨ Conclusión
Este repositorio muestra cómo la visión por computadora está dando el gran salto desde la detección local con filtros hasta una comprensión global basada en atención:
- **ViT** rompe con el paradigma local al tratar imágenes como texto (secuencia de parches).
- **SAM** democratiza la segmentación interactiva sin clases predeterminadas.
- **DETR** elimina pasos manuales en detección, simplificando el diseño.

Este es solo el inicio de una nueva era: modelos híbridos que combinen las fortalezas de los CNNs y los Transformers están abriendo un futuro más flexible, eficiente y humano en Visión por Computador.

---

## 📌 Créditos
- Autora: Orli
- Código basado en papers de Google Research (ViT), Meta AI (SAM y DETR)
- Ejemplos de implementación con frameworks timm, transformers y torchvision.

### ¡Gracias por explorar esta evolución conmigo! 🌟
