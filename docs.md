```mermaid
graph TD
    A(Inicio Proyecto Río Paraná) --> B[Recolección Integrada de Datos<br>Alturas Hidrométricas<br>Caudales<br>Factores Climáticos<br>Datos de Represas y Cuencas]

    B --> C[Análisis Exploratorio Detallado<br>Identificación Variables Relevantes<br>Correlaciones y Lags<br>Dinámica del Río]

    C --> D[Ingeniería de Características<br>y Preparación Base de Datos<br>Creación Lags Dinámicos, Acumulados]

    D --> E[Selección y Desarrollo Modelo ML<br>Prophet Meta]

    %% Bifurcación para los distintos horizontes
    E --> F_15[Aplicación del Modelo<br>Predicción Directa<br>a 15 días]
    E --> F_60_1[Estrategia Cascada 60 días:<br>Paso 1: Predicción de Regresoras Clave]

    F_15 --> G_15[Evaluación Resultados<br>Horizonte 15 días]
    F_60_1 --> F_60_2[Estrategia Cascada 60 días:<br>Paso 2: Predicción Altura Target<br>Usando Regresoras Predichas]

    F_60_2 --> G_60[Evaluación Resultados<br>Horizonte 60 días]

    G_15 --> H[Predicción Validada<br>Altura Hidrométrica<br>15 días]
    G_60 --> I[Predicción Validada<br>Altura Hidrométrica<br>60 días]

    %% Convergencia hacia el objetivo final
    H --> J[Cálculo del Calado Máximo<br>OBJETIVO Principal<br>Usando Altura Predicha<br>Profundidad y Margen Seguridad]
    I --> J

    J --> K(Fin del Proyecto)

    classDef highlight fill:#f9f,stroke:#333,stroke-width:2px;
    class J highlight;
