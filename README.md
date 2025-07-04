Análisis de Tiendas - Alura Store Latam
Descripción del Proyecto
Este proyecto tiene como objetivo analizar los datos de ventas de las 4 tiendas de la cadena Alura Store y recomendar al Sr. Juan cuál tienda debería vender para iniciar un nuevo emprendimiento.
El análisis considera facturación total, categorías más vendidas, calificación promedio de los clientes, productos más y menos vendidos, y costos promedio de envío.

Importación de Datos

import pandas as pd
import matplotlib.pyplot as plt

# URLs de los datasets
url = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_1%20.csv"
url2 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_2.csv"
url3 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_3.csv"
url4 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_4.csv"

# Lectura de los datos
tienda1 = pd.read_csv(url)
tienda2 = pd.read_csv(url2)
tienda3 = pd.read_csv(url3)
tienda4 = pd.read_csv(url4)

tienda1.head()

Análisis de Facturación
Se sumaron los ingresos de cada tienda:

facturacion = {
    'Tienda 1': tienda1['Precio'].sum(),
    'Tienda 2': tienda2['Precio'].sum(),
    'Tienda 3': tienda3['Precio'].sum(),
    'Tienda 4': tienda4['Precio'].sum(),
}

Resultados:

Tienda 2 tiene la facturación más alta.

Tienda 1 tiene la facturación más baja.

Ventas por Categoría

categorias = tienda1['Categoría del Producto'].value_counts()
categorias.plot.pie(autopct='%1.1f%%', startangle=90, cmap='Pastel1')

Conclusión:
La categoría más vendida en todas las tiendas es Muebles, pero la Tienda 1 muestra menos diversidad de productos vendidos.

Calificación Promedio de la Tienda

calificaciones = {
    'Tienda 1': tienda1['Calificación'].mean(),
    'Tienda 2': tienda2['Calificación'].mean(),
    'Tienda 3': tienda3['Calificación'].mean(),
    'Tienda 4': tienda4['Calificación'].mean(),
}
Resultados:

Tienda 3 y Tienda 2 tienen calificaciones superiores a 4.0.

Tienda 1 tiene la calificación promedio más baja, lo que refleja menor satisfacción del cliente.

Productos Más y Menos Vendidos
mas_vendido = tienda1['Producto'].value_counts().idxmax()
menos_vendido = tienda1['Producto'].value_counts().idxmin()

Tienda 1 muestra bajo rendimiento tanto en productos populares como en los menos vendidos.

Envío Promedio por Tienda
envios = {
    'Tienda 1': tienda1['Costo de envío'].mean(),
    'Tienda 2': tienda2['Costo de envío'].mean(),
    'Tienda 3': tienda3['Costo de envío'].mean(),
    'Tienda 4': tienda4['Costo de envío'].mean(),
}
Aunque la Tienda 1 tiene el costo de envío más bajo, esto no mejora su facturación ni su calificación general.

Conclusión y Recomendación
Después de analizar todos los datos:

Tienda 1 tiene la facturación más baja.

Tiene la peor calificación promedio, lo que indica problemas en el servicio o productos.

Sus categorías y productos no son tan competitivos como los de las otras tiendas.

Aunque el envío es económico, no logra compensar el bajo desempeño general.

➡️ Recomendación Final:
El Sr. Juan debería vender la Tienda 1, y enfocarse en sus otras tiendas, que son más rentables y mejor evaluadas por los clientes.
