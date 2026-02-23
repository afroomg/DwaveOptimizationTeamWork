# Optimización del Diseño de Red Eléctrica con D-Wave

Este proyecto resuelve un problema de optimización combinatoria para el diseño de una red de distribución eléctrica jerarquizada. El objetivo es conectar una fuente de Alta Tensión (HV) con clientes industriales y domésticos minimizando el coste total de infraestructura y cableado.

## 🚀 Descripción del Proyecto
El problema se ha modelado utilizando una formulación **QUBO** (Quadratic Unconstrained Binary Optimization), compatible con los computadores cuánticos de **D-Wave**. 

El modelo considera:
- **CAPEX:** Coste de construcción de centros de Media Tensión (MV) y Baja Tensión (LV).
- **OPEX:** Coste de cableado basado en distancias euclidianas entre nodos.
- **Restricciones:** Unicidad de suministro por cliente, coherencia de existencia (no conectar a nodos no construidos) y flujo de potencia.

## 🛠️ Tecnologías Utilizadas
* **Python** (Pandas, NumPy, Matplotlib)
* **D-Wave Ocean SDK** (dimod, neal)
* **Simulated Annealing** para validación de resultados.

## 📊 Estructura de Datos (CSV)
El cuaderno está diseñado para leer un archivo `datos.csv` con una estructura específica. Para que el optimizador funcione correctamente, el CSV debe seguir este orden:

1. **Metadatos (Filas 0-3):** Cantidad de variables de tipo J (MV), K (LV), Industriales y Domésticos.
2. **Costes de cable (Filas 4-6):** Coste por unidad de longitud para HV, MV y LV.
3. **Datos de Nodos (Fila 7 en adelante):** Tabla con las columnas:
   - `Nombre`: Identificador (S, J1, K1, Ind1, Dom1...).
   - `Coord_X`, `Coord_Y`: Coordenadas geográficas del nodo.
   - `Cost`: Coste de inversión inicial (0 para clientes).
