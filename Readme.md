# Limpieza de datos geográficos del módulo sitios

El presente documento detalla el proceso de limpieza para la consulta generada a partir del módulo sitios.

El proceso genera tres salidas como se puede apreciar en el siguiente diagrama.

`<br><br>`

```mermaid
graph LR;
    id1[(sitios.txt)]-->id2[sitios_clean.ipynb];
    id2[sitios_clean.ipynb]-->polygons.geojson;
    id2[sitios_clean.ipynb]-->points.geojson;
    id2[sitios_clean.ipynb]-->errors.csv;
```

`<br><br>`

Para el script de **limpieza**, **transformación de datos a tipo georreferenciado** toma el supuesto de que la información de coordenadas son del tipo **decimal**. La información ingresada al sistema es a través de una proyección es del tipo CRS84 la cual es exportada a formato GeoJSON.

Las salidas son de acuerdo al tipo de geometría encontrada en función de la longitud de los pares ordenados (coordenadas).

En este caso para *puntos* esta formada por un par, para *polígonos* deben ser al menos 3 pares ordenados.

En *errores* se descartan aquellos con una longitud menor a 2 datos. Al igual de aquellos registros que no cumpla con el supuesto de información del tipo coordenadas decimales.
