---
title: "Ejercicios de Prácticas: Regresión Logística"
format:
  html:
    theme: flatly           # Puedes cambiar por: cerulean, cosmo, journal, lumen, united
    highlight: tango        # Estilo de resaltado de código
    toc: true               # Muestra tabla de contenido
    toc-depth: 3            # Profundidad máxima del TOC
    toc-location: left      # Posición del TOC flotante
    toc_float: true         # Tabla de contenido flotante
    number-sections: true   # Numeración de secciones
    df-print: paged         # Tablas paginadas si son largas
    fig-cap-location: bottom # Para leyendas bajo gráficos
    code-fold: true         # Opción para mostrar los código
    keep-md: true           # Guarda el markdown intermedio
---



2025-05-16

::: {style="text-align: center;"}
<p>*Zamora, T. Jesús D*\[\^a\]. [info.thowinsson\@gmail.com](mailto:info.thowinsson@gmail.com){.email}</p>

<p>Barranquilla-Colombia.</p>
:::

```{=html}
<style>
  #TOC::before {
    content: "";
    display: block;
    width: 100%;
    background-image: url('Imagen_portada.png');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    margin-bottom: 20px;
    border-radius: 10px;
    height: 350px; /* Ajusta la altura según tu imagen */
  }
</style>
```

::: {#toc-imagen-container}
<img src="Portada2.jpg" alt="Ejercicios de Practicas" id="imagen-toc"/>
:::


# Cargar Datos

## Paso 1: Carga de los datos y exploración inicial


::: {.cell layout-align="center"}

```{.r .cell-code}
# Cargar paquete necesario
library(lsm)

# Cargar datos
datos <- pros
attach(datos)

# Visualizar estructura de los datos
str(datos)
```

::: {.cell-output .cell-output-stdout}

```
tibble [380 × 9] (S3: tbl_df/tbl/data.frame)
 $ ID     : num [1:380] 1 2 3 4 5 6 7 8 9 10 ...
 $ CAPSULE: num [1:380] 0 0 0 0 0 1 0 0 0 0 ...
 $ AGE    : num [1:380] 65 72 70 76 69 71 68 61 69 68 ...
 $ RACE   : num [1:380] 1 1 1 2 1 1 2 2 1 2 ...
 $ DPROS  : num [1:380] 2 3 1 2 1 3 4 4 1 1 ...
 $ DCAPS  : num [1:380] 1 2 2 1 1 2 2 2 1 2 ...
 $ PSA    : num [1:380] 1.4 6.7 4.9 51.2 12.3 3.3 31.9 66.7 3.9 13 ...
 $ VOL    : num [1:380] 0 0 0 20 55.9 0 0 27.2 24 0 ...
 $ GLEASON: num [1:380] 6 7 6 7 6 8 7 7 7 6 ...
```


:::
:::


### Explicación:

-   Primero cargamos los datos del paquete lsm y usamos attach() para acceder directamente a las variables.

-   La función str() nos muestra la estructura de los datos: tipos de variables, dimensiones y primeras observaciones.

-   Esto nos permite verificar que $CAPSULE$ sea binaria (0/1) y $VOL$ sea numérica.