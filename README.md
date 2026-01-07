# Simulaciones de Jubilación - jubilacionUNA

Proyecto para analizar simulaciones de retiro y comparar escenarios de inversión y sistemas públicos, usando datos procesados de personal.

**Contenido**
- **`funcionarios_una_procesados.csv`**: dataset de entrada (registros procesados de funcionarios).
- **Simulacion1.ipynb**: Notebook principal de simulación (escenarios y visualizaciones).
- **Simulacion2DatosReales.ipynb**: Notebook con carga y corrección de datos reales, modelo de carrera y simulador (usa `funcionarios_una_procesados.csv`).
- **Simulacion3Simulada.ipynb**: Notebook auxiliar / plantilla para simulaciones simuladas.
- **resumen_estadistico_completo.csv** y **resultados_detallados_inversion_docentes.csv**: salidas generadas por las simulaciones (cuando corresponda).

**Requisitos**
- Python 3.9+ (recomendado)
- Paquetes principales: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy`, `scikit-learn`

Instalar dependencias (ejemplo usando pip):

```
pip install numpy pandas matplotlib seaborn scipy scikit-learn
```

**Cómo ejecutar**
- Ejecutar los notebooks con JupyterLab/Notebook: abrir `Simulacion2DatosReales.ipynb` o `Simulacion1.ipynb` y ejecutar las celdas en orden.
- Alternativamente, ejecutar el script principal si se exporta a `.py`. Asegurarse de que `funcionarios_una_procesados.csv` esté en la raíz del proyecto.

**Notas importantes**
- Los notebooks aplican correcciones estrictas y topes razonables antes de simular; revisar las funciones de limpieza en `Simulacion2DatosReales.ipynb`.
- Los resultados pueden depender de supuestos (salario mínimo, tasa de rentabilidad, topes por antigüedad). Revisar y ajustar las constantes al inicio del notebook.

**Salida esperada**
- Tablas resumidas y archivos CSV con estadísticas por escenario.
- Gráficos comparativos de retiros y pensiones.

**Licencia y datos**
- Verificar restricciones sobre el uso de `funcionarios_una_procesados.csv` antes de compartir. Este repositorio no incluye una licencia explícita; añadir una si se desea compartir públicamente.

**Contacto / Autor**
- Proyecto mantenido localmente por el autor del repositorio.

Si quieres, agrego un `requirements.txt` y un script Python ejecutable para correr la simulación desde la línea de comandos.
