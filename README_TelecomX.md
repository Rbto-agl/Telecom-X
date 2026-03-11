# 📡 TelecomX LATAM — Análisis de Evasión de Clientes (Churn)

## 📌 Descripción

Este proyecto forma parte del **Challenge 2 de Data Science** de Alura LATAM. Telecom X enfrenta una alta tasa de cancelaciones y necesita comprender qué factores llevan a la pérdida de clientes.

El análisis aplica un pipeline **ETL completo** sobre datos de más de 7,000 clientes para extraer insights accionables que permitan al equipo de Data Science desarrollar modelos predictivos y estrategias de retención.

---

## 🎯 Objetivos

- ✅ Importar y manipular datos desde una API en formato JSON
- ✅ Aplicar ETL (Extracción, Transformación y Carga)
- ✅ Realizar un Análisis Exploratorio de Datos (EDA) completo
- ✅ Crear visualizaciones estratégicas para identificar patrones de churn
- ✅ Generar un informe con insights y recomendaciones

---

## 📁 Estructura del Proyecto

```
telecomx-latam/
│
├── TelecomX_LATAM_Completo.ipynb   # Notebook principal con ETL + EDA + Informe
├── TelecomX_diccionario.md          # Diccionario de datos
├── README.md                        # Este archivo
└── datos/
    └── TelecomX_Data.json           # Dataset original
```

---

## 🔄 Pipeline ETL

### 📌 Extracción
- Carga directa desde API GitHub en formato JSON
- Normalización de estructura anidada con `pd.json_normalize`

### 🔧 Transformación
| Tarea | Método |
|---|---|
| Renombre de columnas | Traducción al español |
| `Cargo_Total` string → float | `pd.to_numeric` |
| Variables Yes/No → 1/0 | `.map()` |
| Nulos imputados | Mediana de `Cargo_Total` |
| Nueva variable `Cuentas_Diarias` | `Cargo_Mensual / 30` |
| Nueva variable `Num_Servicios` | Suma de servicios activos |
| Duplicados eliminados | `.drop_duplicates()` |

### 📊 Carga y Análisis
- Estadísticas descriptivas completas
- Visualizaciones de distribución de churn
- Análisis por variables categóricas y numéricas
- Matriz de correlación

---

## 📈 Visualizaciones Incluidas

1. **Torta + Barras** — Distribución global de Churn
2. **Barras agrupadas** — Churn por género, adulto mayor, tipo de contrato, método de pago, internet y factura electrónica
3. **Histogramas** — Distribución de meses, cargo mensual y total por grupo Churn
4. **Boxplots** — Comparación de variables numéricas Churn vs No Churn
5. **Línea** — Tasa de churn según número de servicios contratados
6. **Heatmap** — Matriz de correlación entre todas las variables

---

## 🚀 Cómo Ejecutar el Proyecto

### Opción 1 — Google Colab (recomendado)
1. Abre [Google Colab](https://colab.research.google.com)
2. Ve a **Archivo → Subir notebook**
3. Selecciona `TelecomX_LATAM_Completo.ipynb`
4. Ejecuta todas las celdas: `Runtime → Run all`

> Los datos se cargan automáticamente desde la API, no es necesario subir el JSON.

### Opción 2 — Local
```bash
# Clonar el repositorio
git clone https://github.com/tu-usuario/telecomx-latam.git
cd telecomx-latam

# Instalar dependencias
pip install pandas numpy matplotlib

# Abrir el notebook
jupyter notebook TelecomX_LATAM_Completo.ipynb
```

---

## 🧰 Tecnologías Utilizadas

| Herramienta | Uso |
|---|---|
| **Python 3** | Lenguaje principal |
| **Pandas** | Manipulación y limpieza de datos |
| **NumPy** | Operaciones numéricas |
| **Matplotlib** | Visualización de datos |
| **Google Colab** | Entorno de desarrollo |

---

## 🔍 Principales Hallazgos

| Factor | Impacto en Churn |
|---|---|
| Contrato mes a mes | 🔴 Alto riesgo (~3x más churn) |
| Pocos meses de antigüedad | 🔴 Clientes nuevos evaden más |
| Internet por Fibra óptica | 🔴 Mayor churn que DSL |
| Pago por cheque electrónico | 🔴 Mayor tasa de evasión |
| Adulto mayor | 🟠 Riesgo moderado-alto |
| Cargo mensual alto | 🟠 Correlación positiva con churn |
| Género | 🟢 Sin diferencia significativa |

---

## ✅ Recomendaciones Estratégicas

- 🎯 Incentivar contratos anuales con descuentos
- 🚀 Programa de onboarding intensivo en los primeros 3 meses
- 💰 Revisar precio/valor percibido del servicio de Fibra óptica
- 📲 Migrar clientes a métodos de pago automático
- 👴 Crear planes y soporte diferenciado para adultos mayores
- 📦 Ofrecer bundles de servicios con beneficios por fidelidad

---

## 👤 Autor

Desarrollado como parte del **Challenge 2 — Data Science Alura LATAM**

---

*📅 2025 — TelecomX LATAM Churn Analysis*
