```mermaid
graph TD
    A(Inicio Proyecto Río Paraná) --> B[Recolección de Datos<br>Alturas Hidrométricas<br>Caudales<br>Vientos, Temperaturas<br>Precipitaciones]

    subgraph Fase 1: Análisis y Preparación de Datos
        B --> C1[Análisis Exploratorio Inicial<br>Correlaciones, Lags Fijos, etc.]
        B --> C2[Segundo Análisis Exploratorio<br>Foco 60 días, Cuencas Altas, Cascada]
        C1 --> D[Ingeniería de Características<br>y Armado Base de Datos<br>Lags Dinámicos, Acumulados Suavizados]
        C2 --> D
    end

    subgraph Fase 2: Modelado y Predicción
        D --> E[Selección y Desarrollo Modelo ML<br>Prophet Meta]
        E --> F1[Aplicación Modelo<br>Predicción a 15 días]
        E --> F2[Aplicación Modelo<br>Estrategia Cascada para 60 días<br>1. Predicción Regresoras]
        F2 --> F3[Aplicación Modelo<br>Estrategia Cascada<br>2. Predicción Altura Puntos Críticos]
    end

    subgraph Fase 3: Evaluación y Objetivo
        F1 --> G1[Evaluación Resultados<br>Horizonte 15 días<br>MAE, R2]
        F3 --> G2[Evaluación Resultados<br>Horizonte 60 días<br>MAE, R2]
        G1 --> H[Predicción Obtenida<br>Altura Hidrométrica<br>15 días]
        G2 --> I[Predicción Obtenida<br>Altura Hidrométrica<br>60 días]
        H --> J[Cálculo Calado Máximo<br>Usando Altura Predicha<br>Prof. Efectiva, Margen Seguridad]
        I --> J
    end

    J --> K(Fin del Proyecto)

    classDef highlight fill:#f9f,stroke:#333,stroke-width:2px;
    class J highlight;
