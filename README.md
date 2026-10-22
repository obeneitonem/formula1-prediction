# Análisis Estadístico: Predicción de Puntos en Fórmula 1

Proyecto académico enfocado en el análisis de datos históricos de Fórmula 1 para identificar las variables clave que influyen en los puntos obtenidos por los pilotos y predecir la temporada 2024.

## Problema
Identificar qué factores (clima, circuito, piloto, constructor) tienen mayor impacto en el rendimiento y construir un modelo estadístico capaz de predecir los puntos de una carrera.

## Herramientas Utilizadas
- **Lenguaje:** R
- **Librerías:** ggplot2, dplyr, stats (Regresión polinomial)
- **Análisis:** Modelado estadístico, Análisis Exploratorio de Datos (EDA).

## Resultados
- Se construyó un modelo de regresión polinomial con un **R² ajustado de 0.707**.
- El modelo logró predecir con éxito los resultados de la temporada 2024.

## Estructura de los Datos
El dataset relacional cuenta con las siguientes tablas y claves:

```mermaid
erDiagram
    QUALIFYING {
        int RaceId FK
        int DriverId FK
        int ConstructorID FK
        int Number
        int Position_qualy
        string Q1
        string Q2
        string Q3
    }

    RESULTS {
        int ResultsID PK
        int RaceId FK
        int DriverID FK
        int ConstructorID FK
        int Number
        int Grid
        int Position
        string PositionText
        int PositionOrder
        float Points
        int Laps
        string Time
        int Milliseconds
        int Rank
        string FastestLapTime
        float FastestLapSpeed
        int StatusID FK
    }

    STATUS {
        int StatusID PK
        string Status
    }

    DRIVERS {
        int DriverID PK
        string DriverRef
    }

    CONSTRUCTORS {
        int ConstructorID PK
        string Name_constructor
    }

    RACES {
        int RaceId PK
        int Year
        date Date
        int CircuitID FK
    }

    CIRCUITS {
        int CircuitID PK
        string CircuitRef
    }

    RESULTS }o--|| RACES : "RaceId"
    RESULTS }o--|| DRIVERS : "DriverID"
    RESULTS }o--|| CONSTRUCTORS : "ConstructorID"
    RESULTS }o--|| STATUS : "StatusID"

    QUALIFYING }o--|| RACES : "RaceId"
    QUALIFYING }o--|| DRIVERS : "DriverID"
    QUALIFYING }o--|| CONSTRUCTORS : "ConstructorID"

    RACES }o--|| CIRCUITS : "CircuitID"
