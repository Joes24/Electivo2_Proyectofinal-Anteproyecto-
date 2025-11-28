#Proyecto Final: Super-Resolución de Imágenes 2D

##Entrega Parcial (Anteproyecto): Método Numérico Funcional

##Integrantes: José Gormaz, Octavio Marchant, Miguel Quispe, Steffany Urzúa.

Este repositorio contiene la implementación del método de **Descenso de Gradiente (GD)** para resolver un problema de Super-Resolución (SR) de imágenes, formulado como un problema inverso regularizado.


## 1. Formulación Matemática del Problema

El objetivo es encontrar la imagen de alta resolución $x$ que minimice la siguiente función de costo $J(x)$:

$$\min_{x}J(x)=\frac{1}{2}||Ax-b||^{2}+\lambda R(x)$$

* $||Ax-b||^{2}$: **Término de fidelidad** (Error cuadrático).
* $R(x)$: **Término de regularización** (Penaliza la falta de suavidad).
* $A$: **Operador de Degradación** (Desenfoque Gaussiano + Submuestreo).


## 2. Regularizadores Implementados

Los regularizadores operan sobre el gradiente de la imagen para imponer estabilidad:

### A. Regularización L2 del Gradiente (Tikhonov)
* **Clase:** `L2GradientRegularizer`
* **Gradiente ($\nabla R(x)$):** Proporcional al **Laplaciano** de la imagen.

### B. Regularización Huber del Gradiente (TV Suavizada)
* **Clase:** `HuberGradientRegularizer`
* **Ventaja:** Utiliza la función de Huber ($\phi_{\delta}$) para preservar bordes mejor que L2, ya que no penaliza gradientes grandes (bordes) tan severamente.


## 3. Estructura del Repositorio y Ejecución

### A. Estructura de Archivos

| Archivo / Carpeta | Propósito |
| :--- | :--- |
| `demo_parcial.py` | Script ejecutable para demostrar el método numérico. |
| `requirements.txt` | Lista de dependencias. |
| `superres/` | Módulo Python con todas las clases de optimización. |

### B. Instalación

1.  Clonar el repositorio.
2.  Crear un entorno virtual (opcional pero recomendado).
3.  Instalar las dependencias necesarias:
    ```bash
    pip install -r requirements.txt
    ```

### C. Ejecución de la Demo Numérica

Ejecute el script de prueba para generar la reconstrucción de la imagen sintética y el gráfico de convergencia:
```bash
python demo_parcial.py
