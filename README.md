# Simulaciones de Jubilación – jubilacionUNA

## 📊 Descripción general

Este proyecto tiene como objetivo analizar y comparar distintos **escenarios de jubilación** aplicables al personal de la UNA y funcionarios públicos paraguayos, mediante:

- **Modelos de carrera salarial** con crecimiento realista
- **Esquemas de inversión privada** (capitalización individual)
- **Regímenes actuariales públicos** con tasas de sustitución diferenciadas
- **Análisis de patrimonio** y evolución de fondos de pensión
- **Simulaciones demográficas y financieras** basadas en datos reales

El enfoque es cuantitativo y exploratorio, orientado a evaluar impactos relativos bajo diferentes supuestos de aportes, antigüedad y tasas de sustitución. El repositorio contiene 8 notebooks de simulación y análisis, datos procesados (de 2016-2025 y datos públicos del MEF) y herramientas para reproducir escenarios.

---

## 📁 Estructura del proyecto

### Archivos de datos principales
- **Datos/funcionarios_una_procesados.csv**  
  Dataset de entrada principal. Registros anonimizados de funcionarios UNA utilizados en simulaciones.

- **Datos/Bdd Jupe Jubilados Febrero 23.csv**  
  Base de datos de jubilados del sistema público (JUPE) - 2023.(Confidencial)

- **Datos/datosFuncionarios.csv** y **funcionarios_2023_2.csv**  
  Datos complementarios de funcionarios públicos.

- **Datos/ingresos_publicados_2023.json**  
  Datos de ingresos y gastos por sector (fuente: MEF).


### Notebooks

#### 📈 Análisis Exploratorio y Datos
- **0evolcuionPatrimoporcaja.ipynb**  
  Análisis de evolución del patrimonio acumulado según tasas de contribución (16%, 22%, 25%). Incluye proyecciones desde 2011 a 2030 y comparativas con tasas de interés variable.
  
- **5DatosFuncionarios2016-2025.ipynb**  
  Análisis temporal de datos de funcionarios 2016-2025. Distribuciones salariales por año, sector y tendencias demográficas con visualizaciones avanzadas.

#### 💰 Simulaciones de Capitalización
- **1SimulacionCapitalizacion.ipynb**  
  Simulación de acumulación de capital mediante contribuciones periódicas. Calcula años de pensión sostenible según capital acumulado y tasa de reemplazo.
  
- **2SimulacionCapitalizacionProbacion.ipynb**  
  Validación y pruebas de los modelos de capitalización. Incluye casos de prueba y verificación de coherencia.

#### 📊 Análisis de Datos Reales
- **3AnalisisDatosRealesUNA.ipynb**  
  Análisis integral con datos reales de UNA. Implementa correcciones estrictas de salarios, validación de antigüedad, y cálculo de jubilaciones bajo diferentes escenarios (tasas de sustitución 78%-100%, edades de retiro 57-62 años).
  
- **4DatosRealesTodo2023.ipynb**  
  Análisis completo de datos 2023 incluyendo todos los sectores (Administración Pública, Magisterio, Docentes, FFAA, Policía, Magistrados). Visualizaciones por sector, histogramas y estadísticas comparativas.

#### 🎓 Análisis Actuarial (En desarrollo)
- **6ActuarialV0Noterminado.ipynb** ⚠️ *Incompleto*  
  Sistema actuarial de precisión con parámetros exactos del informe MEF 2023. Incluye tasas de rotación por sector, esperanza de vida, y proyecciones de equilibrio actuarial hasta 2060. Clase `SistemaActuarialPreciso` con métodos para cálculo de pensiones.
  
- **7actuarialNewNoterminado.ipynb** ⚠️ *Incompleto*  
  Sistema de jubilación simplificado basado en datos 2023. Proyecciones de ingresos/gastos por sector y análisis de sostenibilidad del sistema actual vs. escenarios de reforma.

---

## 📈 Datos de entrada y validación

### Variables principales en datasets
Los archivos CSV principales contienen como mínimo:

- **edad**: edad actual del funcionario (años)
- **antiguedad**: años de servicio en la institución (años)
- **salario_total** o **devengado**: salario mensual en guaraníes (Gs)
- **sector** (cuando aplica): categoría laboral (DOCENTE, ADMIN, MAGISTRADO, etc.)
- **id_anonimo**: identificador anónimo del funcionario

### Procesamiento de datos
- **Normalización salarial**: conversión a salarios mínimos según año base
- **Correcciones automáticas**: detección y ajuste de valores extremos o inconsistentes  
- **Topes salariales diferenciados**: límites por sector y antigüedad (2-10 SM según parámetros)
- **Validación de antigüedad**: coherencia entre antigüedad reportada y nivel salarial
- **Filtrado de outliers**: eliminación de registros con supuestos económicos inviables
- **Proyección temporal**: generación de carrera salarial extrapolada futura

---

## 🎯 Escenarios de simulación

### Esquemas de inversión privada (capitalización)
**Contribuciones:**  
- 16% del salario (actual)
- 22% del salario (reforma propuesta)

**Horizontes de aporte:**
- 25 años de aportes
- 30 años de aportes

**Rentabilidad:**
- Tasa real de inversión (8% anual típico)
- Conversión a renta mensual vitalicia

### Sistemas públicos de pensiones
**Régimen actual (artículo 79):**
- Tasa de sustitución: 83% (fija)
- Edad mínima de retiro: variable por sector (57-62 años)
- Base de cálculo: 5 años o promedio similar

**Régimen reformado (propuesta):**
- Tasas de sustitución dinámicas: 78% a 100% según antigüedad (25-30 años)
- Edades mínimas diferenciadas: 57-62 años por sector
- Base de cálculo: 5 años completos previos

### Casos de análisis
Los escenarios se evalúan sobre el mismo conjunto de personas, permitiendo análisis comparativos:
- Diferencial de pensiones (régimen vs. capitalización)
- Sostenibilidad de fondos acumulados
- Cobertura por quintiles de ingreso
- Equidad intergeneracional

---

## ⚙️ Parámetros técnicos de simulación

### Parámetros configurables (en notebooks)
- **Salario mínimo base**: valor actualizado anualmente (2.8M Gs en 2024)
- **Rentabilidad de inversión**: tasa real anual típica 8%
- **Crecimiento salarial real**: 1-2% anual según hipótesis
- **Inflación supuesta**: 4% anual (para proyecciones)
- **Tipo de cambio**: 7,278 Gs/USD (base 2023)
- **Tasas de rotación**: por sector según datos MEF (0.08% - 2.55%)

### Restricciones y validación
- Máximo 10 salarios mínimos (tope absoluto)
- Máximo 30 años de antigüedad
- Coherencia edad-antigüedad (antigüedad ≤ edad - 20 años)
- Validación de carrera salarial realista
- Suavizado de series temporales

### Parámetros del sistema actuarial (MEF 2023)
- Esperanza de vida: 19 años (hombres, 60 años), 21.4 años (mujeres)
- Tasa de descuento (nominal): 9.2369%
- Tasas de rotación por sector: 0.08% - 2.55%
- Tasas de reemplazo base: 47% - 60% por sector

---

## 🚀 Cómo usar el proyecto

### Requisitos
- Python 3.8+
- Jupyter Notebook o JupyterLab
- Librerías: pandas, numpy, matplotlib, seaborn, scipy, scikit-learn

### Instalación de dependencias
```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

### Ejecución recomendada

**Opción 1: Exploración rápida **
1. Ejecutar **5DatosFuncionarios2016-2025.ipynb** → Visualización de tendencias históricas
2. Ejecutar **4DatosRealesTodo2023.ipynb** → Análisis integral de datos 2023

**Opción 2: Análisis de capitalización **
1. Ejecutar **1SimulacionCapitalizacion.ipynb** → Modelado de fondos por aportes
2. Ejecutar **0evolcuionPatrimoporcaja.ipynb** → Evolución de patrimonio acumulado

**Opción 3: Análisis completo con datos reales **
1. Ejecutar **3AnalisisDatosRealesUNA.ipynb** → Cálculo de jubilaciones por escenario
2. Ejecutar **4DatosRealesTodo2023.ipynb** → Validación con estadísticas de todos los sectores
3. Explorar notebooks actuariales (en desarrollo)



### Ajuste de parámetros
Todos los parámetros técnicos se modifican en las **primeras celdas** de cada notebook:
```python
SALARIO_MINIMO_BASE_2024 = 2_818_316  # Guaraníes
TASA_RENTABILIDAD_REAL = 0.08         # 8% anual
CRECIMIENTO_SALARIAL_REAL_ANUAL = 0.02  # 2% anual
```

---

## 📊 Salidas esperadas

### Por notebook
- **0evolcuionPatrimoporcaja.ipynb**  
  → Gráficos de evolución patrimonial, tablas de comparativa por tasa

- **1SimulacionCapitalizacion.ipynb**  
  → Tablas de capital acumulado, años de pensión sostenible

- **3AnalisisDatosRealesUNA.ipynb**  
  → Tabla de jubilaciones por persona, resumen estadístico, distribuciones

- **4DatosRealesTodo2023.ipynb**  
  → Boxplots por sector, histogramas, estadísticas agregadas, análisis de tendencias

- **5DatosFuncionarios2016-2025.ipynb**  
  → Series temporales, evolución demográfica, visualizaciones por sector

### Formatos de salida
- **Tablas CSV**: Resultados detallados para análisis posterior
- **Gráficos PNG**: Distribuciones, comparativas, series temporales
- **Reportes en consola**: Estadísticas, conteos, validaciones

---

```

---

## ⚠️ Limitaciones y consideraciones

### Supuestos modelados
- ✅ Carrera salarial con crecimiento realista
- ✅ Interés compuesto en capitalización
- ✅ Tasas de sustitución diferenciadas por antigüedad
- ✅ Validación de coherencia edad-antigüedad-salario

### Limitaciones reconocidas
- ❌ Se asume continuidad laboral (sin interrupciones ni desempleo)
- ❌ No se modela inflación explícita en proyecciones de largo plazo
- ❌ No se incluyen cambios normativos futuros
- ❌ Proyecciones demográficas simplificadas
- ❌ Tasas de rentabilidad constantes (no estocásticas)
- ❌ No se incluyen beneficios adicionales (pensión de viudez, invalidez, etc.)

### Metodología de validación
- Pruebas de coherencia en cada escenario
- Comparación con datos históricos reales (2016-2025)
- Validación de parámetros contra informe MEF 2023
- Controles de extremos en distribuciones salariales

---

## 🔍 Interpretación de resultados

### Resultados esperados
- **Jubilación estimada**: rango típico 40-80% del salario promedio según sistema
- **Capital acumulado**: valores 200M - 2,000M Gs según años de aporte
- **Cobertura**: % de funcionarios que alcanzan jubilación digna (≥2 salarios mínimos)

### Validación de resultados
- Verificar que jubilaciones oscilen entre 1-3 salarios promedio
- Confirmar que capital acumulado crece exponencialmente en años iniciales
- Revisar distribuciones para detectar sesgos (gráficos boxplot, histogramas)

---

## 📄 Datos y fuentes

### Datos utilizados
- **UNA interna**: Datos anonimizados de funcionarios
- **SFP Paraguay**: https://datos.sfp.gov.py/data/funcionarios/download
- **MEF**: Informe actuarial del sistema de pensiones (2023)
- **JUPE**: Base datos de jubilados (febrero 2023)

### Licencia de uso
Este proyecto es una herramienta de **análisis académico e institucional**. Los datos de funcionarios fueron anonimizados antes de su uso. Consultar con administración correspondiente antes de redistribuir.

---

## 📝 Notas de desarrollo

### Notebooks en desarrollo (⚠️)
- **6ActuarialV0Noterminado.ipynb**: Pendiente - clase `SistemaActuarialPreciso` con cálculos completos
- **7actuarialNewNoterminado.ipynb**: Pendiente - proyecciones de sostenibilidad a largo plazo

### Mejoras planeadas
- [ ] Validación cruzada con datos JUPE  
- [ ] Incorporación de tasas de rentabilidad estocásticas
- [ ] Módulo de análisis de sensibilidad automatizado
- [ ] Dashboard interactivo (Plotly/Streamlit)
- [ ] Exportación de reportes en PDF
- [ ] Cálculo de pensión de viudez e invalidez

---

## 👤 Autor y contacto

Proyecto desarrollado con fines de análisis académico e institucional en la Universidad Nacional de Asunción (UNA).

**Nota importante:** Este proyecto es una herramienta de simulación con fines educativos. Los valores estimados son **aproximaciones** basadas en supuestos y no garantizan resultados reales de jubilación. Consultar con especialistas actuariales y autoridades competentes antes de tomar decisiones de política pública.
