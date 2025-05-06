```mermaid
graph TD
    A(Inicio Proyecto Río Paraná) --> B[Recolección Integrada de Datos<br><ul><li>Alturas Hidrométricas</li><li>Caudales</li><li>Factores Climáticos (Viento, Temp, Precipitaciones)</li><li>Datos de Represas, Cuencas</li></ul>]

    B --> C[Análisis Exploratorio Detallado<br><ul><li>Identificación de Variables Relevantes</li><li>Análisis de Correlaciones y Lags</li><li>Comprensión de la Dinámica del Río</li></ul>]

    C --> D[Ingeniería de Características<br>y Preparación de la Base de Datos<br>(Creación de Lags Dinámicos, Acumulados, etc.)]

    D --> E[Selección y Desarrollo del Modelo ML<br>(Prophet Meta)]

    %% Bifurcación para los distintos horizontes
    E --> F_15[Aplicación del Modelo<br>para Predicción Directa<br>a 15 días]
    E --> F_60_1[Estrategia para 60 días:<br>Paso 1: Predicción de Regresoras Clave<br>(Altura Corrientes, Precipitaciones Cuenca Norte, etc.)]

    F_15 --> G_15[Evaluación y Ajuste<br>Resultados 15 días<br>(MAE, R2)]
    F_60_1 --> F_60_2[Estrategia para 60 días:<br>Paso 2: Predicción de Altura Puntos Críticos<br>Usando Regresoras Predichas en Paso 1]

    F_60_2 --> G_60[Evaluación y Ajuste<br>Resultados 60 días<br>(MAE, R2)]

    G_15 --> H[Predicción Validada<br>Altura Hidrométrica<br>(Horizonte 15 días)]
    G_60 --> I[Predicción Validada<br>Altura Hidrométrica<br>(Horizonte 60 días)]

    %% Convergencia hacia el objetivo final
    H --> J[Cálculo del Calado Máximo<br>(OBJETIVO Principal del Proyecto)<br>Usando Altura Predicha + Profundidad Efectiva + Margen Seguridad]
    I --> J

    J --> K(Fin del Proyecto)

    classDef highlight fill:#f9f,stroke:#333,stroke-width:2px;
    class J highlight;
