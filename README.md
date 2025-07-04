### Importación de datos



import pandas as pd
import matplotlib.pyplot as plt

url = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_1%20.csv"
url2 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_2.csv"
url3 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_3.csv"
url4 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_4.csv"

tienda1 = pd.read_csv(url)
tienda2 = pd.read_csv(url2)
tienda3 = pd.read_csv(url3)
tienda4 = pd.read_csv(url4)

tienda1.head()


#1. Análisis de facturación



facturacion = {
    'Tienda 1': tienda1['Precio'].sum(),
    'Tienda 2': tienda2['Precio'].sum(),
    'Tienda 3': tienda3['Precio'].sum(),
    'Tienda 4': tienda4['Precio'].sum(),
}

print("Facturación total por tienda:")
for tienda, total in facturacion.items():
    print(f"{tienda}: {total}")

import matplotlib.pyplot as plt

plt.figure(figsize=(8,5))
plt.bar(facturacion.keys(), facturacion.values(), color=['#4CAF50', '#2196F3', '#FF9800', '#F44336'])
plt.title('Facturación por tienda')
plt.ylabel('Total de Ventas ($)')
plt.show()

# 2. Ventas por categoría

categorias = tienda1['Categoría del Producto'].value_counts()

print("Ventas por categoría (Tienda 1):")
print(categorias)

plt.figure(figsize=(7,7))
categorias.plot.pie(autopct='%1.1f%%', startangle=90, cmap='Pastel1')
plt.title('Ventas por Categoría - Tienda 1')
plt.ylabel('')
plt.show()

# 3. Calificación promedio de la tienda


calificaciones = {
    'Tienda 1': tienda1['Calificación'].mean(),
    'Tienda 2': tienda2['Calificación'].mean(),
    'Tienda 3': tienda3['Calificación'].mean(),
    'Tienda 4': tienda4['Calificación'].mean(),
}

print("Calificación promedio por tienda:")
for tienda, calif in calificaciones.items():
    print(f"{tienda}: {round(calif, 2)}")

plt.figure(figsize=(8,5))
plt.bar(calificaciones.keys(), calificaciones.values(), color=['#4CAF50', '#2196F3', '#FF9800', '#F44336'])
plt.title('Calificación promedio por tienda')
plt.ylabel('Calificación')
plt.show()

# 4. Productos más y menos vendidos

mas_vendido = tienda1['Producto'].value_counts().idxmax()
menos_vendido = tienda1['Producto'].value_counts().idxmin()


print(f"Producto más vendido Tienda 1: {mas_vendido}")
print(f"Producto menos vendido Tienda 1: {menos_vendido}")

# 5. Envío promedio por tienda

envios = {
    'Tienda 1': tienda1['Costo de envío'].mean(),
    'Tienda 2': tienda2['Costo de envío'].mean(),
    'Tienda 3': tienda3['Costo de envío'].mean(),
    'Tienda 4': tienda4['Costo de envío'].mean(),
}

print("Costo promedio de envío por tienda:")
for tienda, costo in envios.items():
    print(f"{tienda}: {round(costo, 2)}")

plt.figure(figsize=(8,5))
plt.bar(envios.keys(), envios.values(), color=['#4CAF50', '#2196F3', '#FF9800', '#F44336'])
plt.title('Costo promedio de envío por tienda')
plt.ylabel('Costo de Envío ($)')
plt.show()



# Informe Final: Recomendación sobre la venta de una tienda de Alura Store

El presente informe tiene como objetivo analizar el rendimiento de las 4 tiendas de la cadena Alura Store, con el fin de recomendar cuál tienda debería vender el Sr. Juan para enfocarse en un nuevo emprendimiento.
El análisis se basó en métricas clave: facturación total, categorías más vendidas, calificación promedio de los clientes, productos más y menos vendidos y costos promedio de envío.
Además, se crearon visualizaciones que facilitaron la interpretación de los datos.

1. Facturación Total
Tienda 2 presentó la facturación más alta, seguida de Tienda 3 y Tienda 4.

Tienda 1 tuvo la facturación más baja, indicando menores ingresos globales.

2. Ventas por Categoría
Las 4 tiendas tienen como principal categoría de ventas “Muebles”.

Sin embargo, Tienda 1 tiene un volumen más bajo en categorías secundarias como Electrónica y Juguetes, reduciendo su diversidad de ventas.

3. Calificación Promedio de Clientes
Tienda 3 y Tienda 2 destacaron con calificaciones promedio superiores a 4.0.

Tienda 4 mantuvo un promedio aceptable cercano a 4.0.

Tienda 1, en cambio, presentó la calificación promedio más baja, lo cual refleja problemas en la experiencia del cliente o en la calidad del servicio.

4. Productos más y menos vendidos
Tienda 2 y Tienda 3 tienen productos más vendidos con alta rotación.

Tienda 1 tiene un bajo rendimiento tanto en sus productos más vendidos como en los menos vendidos, lo que indica poca demanda general.

5. Costo Promedio de Envío
Tienda 1 tiene el costo de envío promedio más bajo, pero este ahorro no logra compensar su baja facturación y baja calificación.

Tiendas con costos de envío más altos (Tienda 2 y 3) mantienen mejores resultados globales.

Conclusión y Recomendación
Después de analizar todos los factores, la recomendación es que el Sr. Juan debería vender Tienda 1, ya que es la menos eficiente:

Tiene la facturación más baja, por lo tanto genera menos ingresos.

Posee la calificación promedio más baja, indicando una menor satisfacción del cliente.

Su oferta de productos y categorías no logra igualar el rendimiento de las otras tiendas.

Aunque su costo de envío es bajo, esto no genera un impacto positivo suficiente en ventas ni en experiencia del cliente.

*➡️ Por estas razones, Tienda 1 es la mejor opción para vender, permitiendo que el Sr. Juan conserve las tiendas con mejores resultados para enfocarse en su nuevo emprendimiento.*
