# Informe: Segmentación de Clientes con K-Means

## 1. Técnica Elegida y Justificación
Se seleccionó el algoritmo de agrupamiento **K-Means** (Opción 1 del enunciado).
**Justificación:** En el scoring crediticio, no todos los clientes riesgosos son iguales. K-Means nos permite segmentar la cartera en grupos homogéneos para identificar perfiles de riesgo diferenciados que el modelo supervisado global podría pasar por alto. Esto cumple con el objetivo de identificar subpoblaciones con comportamientos financieros específicos.

## 2. Instrucciones de Ejecución
1. Asegurarse de tener el archivo `X_train.csv` en el directorio raíz (se utilizaron solo datos de entrenamiento para evitar data leakage).
2. Ejecutar el notebook `entrega_ea3.ipynb`.
3. El script realizará automáticamente la imputación de nulos, escalado de datos (StandardScaler) y la ejecución del modelo con k=3 (seleccionado mediante el método del codo).

## 3. Análisis e Interpretación de Resultados
El algoritmo identificó 3 clusters con comportamientos financieros muy marcados:

* **Cluster 0 (Riesgo Alto):** Clientes de ingresos medios-bajos y menor antigüedad laboral. Este grupo coincide con las tasas de morosidad más altas detectadas en el análisis exploratorio.
* **Cluster 1 (Perfil Medio):** Clientes estándar con estabilidad financiera promedio.
* **Cluster 2 (Clientes Premium):** Caracterizados por altos ingresos (promedio ~$64k) y alta antigüedad laboral. Presentan el menor riesgo histórico.

El gráfico de PCA adjunto en el notebook valida visualmente la separación clara de estos tres perfiles.

## 4. Discusión y Aplicabilidad al Proyecto Final
**Conclusión: SÍ se recomienda incorporar al proyecto.**
La variable "Cluster" generada aporta valor predictivo adicional. Al agregar esta etiqueta como un *feature* nuevo al modelo supervisado, permitimos que el modelo de scoring ajuste sus umbrales dependiendo de si el cliente es "Premium" o "Riesgoso", mejorando la precisión y permitiendo estrategias de negocio diferenciadas (ej: ofrecer tasas preferenciales al Cluster 2).
