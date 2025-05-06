```mermaid
graph TD
    A(Pronóstico a 60 días) -->
    B[Foco en Corrientes<br>- Análisis aguas arriba y su influencia en Corriente]

    B --> C[Afluentes importantes<br>- Rio Parana Brasil<br>- Río Paraguay]
    C --> G2[Analisis de Alturas hidrométricas Pilcomayo <br> Rio Paraguay]
    C --> G3[Analisis de Caudal en Yacyreta <br> Río Paraná Brasil/Represas]

    C[Análisis aguas arriba<br>- Influencia en Corrientes<br>- Río Paraguay Alturas/Caudales<br>- Río Paraná Brasil/Represas<br>- Precipitaciones Cuencas Paraguay/Brasil]

    F[Input: Pronósticos<br>Precipitaciones 3 meses]

    B --> C[Desarrollo Modelos Predictivos<br>para Puntos Clave Aguas Arriba]

    C --> G1[Modelo/Predicción Altura<br>Pilcomayo - Río Paraguay]
    C --> G2[Modelo/Predicción Altura<br>Yacyreta - Río Paraná]
    C --> G3[Modelo/Predicción Altura<br>Corrientes - Horizonte 45 días]

    F --> G1
    F --> G2
    F --> G3

    subgraph Estrategia de Predicción Final Cascada
        H[Inputs para Modelo Final:<br>Predicciones de Pilcomayo,<br>Yacyreta, Corrientes]
        G1 --> H
        G2 --> H
        G3 --> H
        H --> I[Modelo/Predicción Altura Puntos Críticos<br>San Lorenzo, Rosario, Ramallo, San Pedro<br>para 60 días]
    end

    I --> J(Objetivo de Pronóstico a 60 días Cumplido<br>para Cálculo de Calado Máximo)

    classDef highlight fill:#f9f,stroke:#333,stroke-width:2px;
    class J highlight;
