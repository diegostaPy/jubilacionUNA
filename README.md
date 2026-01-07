# Simulaciones de Jubilación – jubilacionUNA

## 📊 Descripción general

Este proyecto tiene como objetivo analizar y comparar distintos **escenarios de jubilación** aplicables al personal universitario, combinando **modelos de carrera salarial**, **esquemas de inversión privada** y **regímenes públicos de pensiones**.  
El enfoque es cuantitativo y exploratorio, orientado a evaluar impactos relativos bajo diferentes supuestos de aportes, antigüedad y tasas de sustitución.

El repositorio contiene notebooks de simulación, datos procesados y resultados agregados que permiten reproducir y analizar los escenarios planteados.

---

## 📁 Estructura del proyecto

### Archivos de datos
- **funcionarios_una_procesados.csv**  
  Dataset de entrada principal. Contiene registros anonimizados y depurados de funcionarios, utilizados como base para todas las simulaciones.

### Notebooks
- **Simulacion1.ipynb**  
  Análisis exploratorio inicial y simulaciones preliminares. Incluye gráficos diagnósticos de edad, antigüedad y salarios.
  
- **Simulacion2DatosReales.ipynb**  
  Notebook central del proyecto. Realiza la carga de datos reales, correcciones y topes, construcción del modelo de carrera salarial y ejecución de los escenarios de jubilación.
  
- **Simulacion3Simulada.ipynb**  
  Notebook auxiliar para pruebas con datos sintéticos o escenarios completamente simulados.

### Salidas generadas
- **resumen_estadistico_completo.csv**  
  Resultados agregados por escenario (medias, medianas, percentiles).
- **resultados_detallados_inversion_docentes.csv**  
  Resultados a nivel individual (cuando corresponde).
- Gráficos comparativos en formatos PNG o PDF.

---

## 📈 Datos de entrada

El archivo `funcionarios_una_procesados.csv` contiene, como mínimo, las siguientes variables:

- **edad**: edad actual del funcionario.
- **antiguedad**: años de servicio en la institución.
- **salario_total**: salario mensual expresado en guaraníes.
- **cargo** (opcional): categoría laboral (por ejemplo: DOCENTE, AUXILIAR, ADMINISTRATIVO).

### Características y tratamiento de los datos
- Los salarios se normalizan en salarios mínimos vigentes.
- Se aplican correcciones automáticas para valores extremos o inconsistentes.
- Se utilizan topes salariales diferenciados por categoría.
- Se controla la coherencia entre antigüedad y nivel salarial antes de simular.

---

## 🎯 Escenarios simulados

### Esquemas de inversión privada
- Aportes del **16%** y **22%** del salario.
- Horizontes de **25** y **30 años** de aporte.
- Capitalización con interés compuesto y conversión a renta mensual estimada.

### Sistemas públicos de pensiones
- Régimen actual con tasa de sustitución basada en el promedio salarial.
- Escenarios con **25 y 30 años** de aporte.
- Escenarios bajo un sistema nuevo, diferenciando jubilación ordinaria y extraordinaria.

Cada escenario se evalúa de forma comparable sobre el mismo conjunto de personas, permitiendo analizar diferencias relativas entre alternativas.

---

## ⚙️ Parámetros principales de simulación

- Salario mínimo: valor configurable al inicio del notebook.
- Rentabilidad anual de inversión: supuesto constante.
- Tasa de sustitución del sistema público: definida según el régimen simulado.
- Topes salariales por categoría laboral.
- Restricciones máximas de antigüedad y salario para evitar extrapolaciones irreales.

Todos estos parámetros pueden ajustarse fácilmente desde las primeras celdas del notebook principal.

---

## 🚀 Ejecución

Las simulaciones se ejecutan directamente desde los notebooks con Jupyter Notebook o JupyterLab.  
Se recomienda comenzar por **Simulacion2DatosReales.ipynb** y ejecutar las celdas en orden, ya que allí se concentra la lógica principal del modelo.

Es necesario que el archivo `funcionarios_una_procesados.csv` se encuentre en la raíz del proyecto o en la ruta configurada dentro del notebook.

---

## 📊 Resultados esperados

- Tablas comparativas de jubilaciones estimadas por escenario.
- Estadísticas descriptivas agregadas.
- Gráficos de distribución y comparación entre sistemas.
- Archivos CSV listos para análisis posterior o informes institucionales.

---

## ⚠️ Consideraciones y limitaciones

- Los resultados dependen fuertemente de los supuestos adoptados.
- No se modelan cambios futuros de normativa ni inflación explícita.
- Se asume continuidad laboral sin interrupciones.

---

## 📄 Uso de datos y licencia

Se usaron datos publicos de https://datos.sfp.gov.py/data/funcionarios/download
---

## 👤 Autor 

Proyecto desarrollado y mantenido localmente por el autor del repositorio, con fines de análisis académico e institucional.

**Nota:** Este proyecto es una herramienta de simulación. Los valores obtenidos son estimaciones y no garantizan resultados reales de jubilación.
