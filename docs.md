```mermaid
graph TD
    A(Inicio Proyecto Río Paraná) --> B[Recolección de Datos<br>Alturas Hidrométricas<br>Caudales<br>Vientos, Temperaturas<br>Precipitaciones] %% Separé las líneas con <br> o nueva línea simple dentro del []

    subgraph Fase 1: Análisis y Preparación de Datos
        B --> C1[Análisis Exploratorio Inicial<br>(&#40;Correlaciones, Lags Fijos, etc.&#41;)]
        B --> C2[Segundo Análisis Exploratorio<br>(&#40;Foco 60 días, Cuencas Altas, Cascada&#41;)]
        C1 --> D[Ingeniería de Características<br>y Armado Base de Datos<br>(&#40;Lags Dinámicos, Acumulados Suavizados&#41;)]
        C2 --> D
    end

    subgraph Fase 2: Modelado y Predicción
        D --> E[Selección y Desarrollo Modelo ML<br>(&#40;Prophet Meta&#41;)]
        E --> F1[Aplicación Modelo<br>Predicción a 15 días]
        E --> F2[Aplicación Modelo<br>Estrategia Cascada para 60 días<br>(&#40;1. Predicción Regresoras: Corrientes, etc.&#41;)]
        F2 --> F3[Aplicación Modelo<br>Estrategia Cascada<br>(&#40;2. Predicción Altura Puntos Críticos&#41;)]
    end

    subgraph Fase 3: Evaluación y Objetivo
        F1 --> G1[Evaluación Resultados<br>(&#40;Horizonte 15 días&#41;)<br>MAE, R2]
        F3 --> G2[Evaluación Resultados<br>(&#40;Horizonte 60 días&#41;)<br>MAE, R2]
        G1 --> H[Predicción Obtenida<br>Altura Hidrométrica<br>(&#40;15 días&#41;)]
        G2 --> I[Predicción Obtenida<br>Altura Hidrométrica<br>(&#40;60 días&#41;)]
        H --> J[Cálculo Calado Máximo<br>(&#40;Usando Altura Predicha, Prof. Efectiva, Margen Seguridad&#41;)]
        I --> J
    end

    J --> K(Fin del Proyecto)

    classDef highlight fill:#f9f,stroke:#333,stroke-width:2px;
    class J highlight;
