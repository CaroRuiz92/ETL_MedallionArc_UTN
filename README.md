# Data Engineering - Pipeline con CoinGecko

Trabajo final integrador del curso Data Engineering (UTN BA). Implementa un 
pipeline completo de ingeniería de datos sobre criptomonedas, cubriendo extracción, 
almacenamiento y procesamiento.

## Descripción

El proyecto extrae datos de la API de CoinGecko, los almacena en formato Delta Lake 
siguiendo la arquitectura Medallion (bronze / silver / gold) y aplica tareas de 
limpieza y enriquecimiento con Pandas.

- **Datos temporales** (`/coins/markets`): precios de mercado, extracción incremental.
- **Datos estáticos** (`/coins/{id}`): metadatos de cada moneda, extracción full.

## Estructura

- `CarolinaRuiz_TP1.ipynb` — Extracción y almacenamiento de datos crudos (capa bronze).
- `CarolinaRuiz_TP2.ipynb` — Procesamiento y transformación (capas silver y gold).

## Capas del data lake

- **Bronze:** datos crudos tal como llegan de la API.
- **Silver:** datos limpios y enriquecidos (fechas convertidas, nulos tratados, 
  columna derivada, JOIN entre precios y metadata).
- **Gold:** datos agregados listos para consumo (top 10 por market cap).

## Requisitos

- Python 3 con las librerías `requests`, `pandas`, `deltalake` y `python-dotenv`.
- Una API key gratuita de CoinGecko (plan Demo).

## Configuración

Crear un archivo `.env` en la raíz del proyecto con la variable:

​```
COINGECKO_KEY=tu_api_key
​```

Se incluye `.env.example` como referencia.

## Ejecución

Ejecutar primero `CarolinaRuiz_TP1.ipynb` (genera la capa bronze) y luego 
`CarolinaRuiz_TP2.ipynb` (lee de bronze y produce silver y gold).
