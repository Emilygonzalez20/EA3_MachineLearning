# Informe: Detección de Anomalías con Isolation Forest

## 1. Técnica Elegida
Se utilizó el algoritmo **Isolation Forest** para la detección de anomalías (Opción 2).
**Justificación:** En el contexto financiero, es crítico identificar comportamientos atípicos que puedan indicar fraude o errores de datos. Este método es eficiente para aislar estos casos sin necesidad de etiquetas previas.

## 2. Ejecución
* Se cargaron los datos de entrenamiento.
* Se imputaron valores nulos y se escalaron las variables.
* Se ejecutó Isolation Forest con una contaminación estimada del 5%.

## 3. Análisis de Resultados
El modelo logró separar exitosamente los datos en dos grupos:
* **Normales (1):** La gran mayoría de los clientes.
* **Anomalías (-1):** Un grupo pequeño con comportamientos numéricos extremos.
El gráfico de PCA generado en el notebook muestra claramente cómo estas anomalías se dispersan lejos del grupo central.

## 4. Conclusión
Se recomienda incorporar esta técnica en el pipeline del proyecto. Filtrar o tratar de forma diferenciada a estos clientes "anómalos" mejorará la robustez y precisión del modelo de scoring final.