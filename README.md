# 🧹 Proceso de Limpieza y Preparación de Datos (Data Cleaning)

Esta sección describe los pasos realizados para inspeccionar, limpiar y preparar el conjunto de datos antes del análisis exploratorio o la modelización. El proceso se llevó a cabo utilizando la librería `pandas`.

## 1. Inspección Inicial del Dataset

Se realizó una revisión inicial de la estructura y el contenido del DataFrame.

### Estructura y Tipos de Datos (`df.info()`)

* **Tamaño:** 15 filas y 6 columnas.
* **Valores Nulos:** Se confirmó que todas las 15 filas en cada columna (`id`, `first_name`, `last_name`, `email`, `gender`, `ip_address`) eran **No Nulas**.
* **Tipos de Datos (Dtype):**
    * `id`: Entero (`int64`).
    * Otras columnas (`first_name`, `email`, etc.): Objeto (`object`), indicando cadenas de texto.
* **Conclusión:** El dataset es pequeño, completo y los tipos de datos son coherentes con el contenido.

### Estadísticas Descriptivas (`df.describe()`)

* Se aplicaron estadísticas descriptivas a la única columna numérica (`id`).
* **Hallazgo:** Los valores de `id` van de 1 a 15 de manera secuencial, confirmando un índice completo y consecutivo.

## 2. Validación de Integridad y Transformación

Se realizaron validaciones para asegurar la integridad de los datos y se aplicó una transformación para mejorar la legibilidad.

### 2.1. Manejo de Valores Nulos

* Se verificó la suma de valores nulos (`df.isnull().sum()`).
* **Resultado:** **Cero valores nulos** en todas las columnas. No fue necesario aplicar métodos de imputación (`fillna`) ni eliminación de filas (`dropna`), por lo que el número de filas se mantuvo en 15.

### 2.2. Manejo de Duplicados

* Se verificó la existencia de filas totalmente duplicadas.
* **Resultado:** **Cero filas duplicadas**. El tamaño del DataFrame se mantuvo en 15 filas.

### 2.3. Renombrado de Columnas

Se renombraron las columnas a términos más descriptivos y en español para mejorar la interpretabilidad del análisis:

| Nombre Original | Nombre Final |
| :--- | :--- |
| `id` | `ID` |
| `first_name` | `Nombre` |
| `last_name` | `Apellido` |
| `gender` | `Género` |
| `ip_address` | `IP` |

## 3. Identificación y Manejo de Valores Atípicos (Outliers)

Se aplicó el método del Rango Intercuartílico (IQR) a las columnas numéricas para identificar valores atípicos:

* **Proceso:** Se seleccionó la columna `ID` y se calcularon los cuartiles (Q1, Q3) y el IQR.
* **Resultado:** Dado que los `ID` son secuenciales (1 a 15), **no se identificaron valores atípicos**, por lo que el número de filas se mantuvo en 15.

**Conclusión del Proceso de Limpieza:** El conjunto de datos es extremadamente limpio y completo. Los pasos realizados aseguran la integridad de los datos y preparan el DataFrame para la siguiente fase de Análisis Exploratorio de Datos.
