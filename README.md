# PEP2_DAG
# Proyecto: Búsqueda de Predio Óptimo para Canchas de Fútbol

Este repositorio contiene un script Python y un conjunto de herramientas para identificar predios óptimos para la instalación de canchas de fútbol. El análisis se realiza utilizando datos espaciales y atributos relevantes almacenados en una base de datos PostgreSQL/PostGIS.

---

## 🔧 **Estructura del Proyecto**

El proyecto incluye los siguientes componentes principales:

### 1. Descomprimir el zip "PEP2_DAG.zip" para acceder a **Carpetas y Archivos**
- **Entradas/**: Contiene archivos como shapefiles (predios, manzanas, vías) necesarios para el procesamiento.
- **sql_queries/**: Archivos SQL utilizados para geoprocesos y cálculos en la base de datos.
- **config/**: Archivos de configuración, incluyendo `config.json`.
- **pep_dag.py**: Script principal de Python que conecta, procesa y almacena los datos en la base de datos PostgreSQL/PostGIS.
- **Procedimiento DAG**: Documento con los pasos y especificaciones de los procesos implementados.

---

## ✅ **Requisitos**

### **Herramientas Necesarias**
- **PostgreSQL/PostGIS**: Base de datos espacial para almacenar y procesar datos geográficos.
- **Python 3.x**: Lenguaje de programación utilizado para la automatización.
- **Bibliotecas de Python**:
  - `pandas`
  - `geopandas`
  - `sqlalchemy`
  - `shapely`
  - `psycopg2`
  - `geoalchemy2`

### **Instalación de Dependencias**

1. Clona el repositorio:
   ```bash
   git clone https://github.com/JoaquinGeoUsach/PEP2_DAG.git
   cd PEP2_DAG
   ```

2. Configura un entorno virtual y activa:
   ```bash
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   ```

3. Instala las dependencias desde `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

---

## 🔄 **Procesamiento de la Información**

### **1. Crear Esquemas en la Base de Datos**
El script crea dos esquemas principales:
- **`entradas`**: Para almacenar los datos de entrada (predios, manzanas, vías, etc.).
- **`salidas`**: Para almacenar los resultados del análisis (predio óptimo y cálculos relacionados).

### **2. Poblar los Datos de Entrada**
Se cargan shapefiles desde la carpeta `Entradas/` a la base de datos PostgreSQL en el esquema `entradas`.

### **3. Procesamiento y Geoprocesos**
El script ejecuta los siguientes pasos:

#### **a. Procesamiento de Vías Cercanas**
- Cuenta el número de vías que se encuentran dentro de un radio de 20 metros de cada predio.

#### **b. Densidad Poblacional**
- Calcula la densidad poblacional promedio en un radio de 500 metros alrededor de cada predio.

#### **c. Índice Final**
- Calcula un índice basado en la cantidad de vías y la densidad poblacional para identificar el predio óptimo.

### **4. Resultados en el Esquema `salidas`**
La tabla final **`salidas.predios_normados_con_indice`** contiene:
- ID del predio
- Cantidad de vías cercanas
- Densidad poblacional promedio
- Índice calculado

---

## 🌐 **Cómo Ejecutar el Proyecto**

1. **Configurar el archivo de conexión**:
   - Edita `config/config.json` para incluir las credenciales de tu base de datos PostgreSQL.

2. **Ejecutar el script principal**:
   ```bash
   python pep_dag.py
   ```

3. **Cargar los resultados en QGIS**:
   - Conecta QGIS a tu base de datos PostgreSQL.
   - Agrega la tabla `salidas.predios_normados_con_indice` al lienzo para visualizar los resultados.

---

## 📚 **Documentación Adicional**

Consulta el archivo **`Procedimiento DAG`** para obtener detalles técnicos y explicaciones completas de los procesos implementados.

---

## 📊 **Estructura del Repositorio**

```
├── Entradas/               # Archivos de entrada (shapefiles de predios, manzanas, vías)
├── sql_queries/            # Consultas SQL para geoprocesos
├── config/                 # Archivos de configuración (JSON, etc.)
├── pep_dag.py              # Script principal para procesamiento y carga
├── Procedimiento DAG       # Documentación de procesos
└── README.md               # Instrucciones del proyecto
```

---


## 📢 **Contacto**

Para dudas o comentarios, contáctanos:
- **Email:** joaquin.bravo.v@usach.cl
- **GitHub Issues:** [Abrir un issue](https://github.com/JoaquinGeoUsach/PEP2_DAG/issues)

---

Gracias por tu interés en este proyecto. ¡Esperamos que sea útil y claro! 🏆

