---
layout: post
title: "Modelamiento Geológico 3D y Determinación de Recursos"
date: 2026-06-21 14:00:00 -0300
---

# MODELAMIENTO GEOLÓGICO 3D Y DETERMINACIÓN DE RECURSOS DE UNA CANTERA DE YESO UTILIZANDO EL SOFTWARE LIBRE RECMIN

**Cárdenas González P., Horta, L.R., Lazarte J. E.**
*Facultad de Ciencias Naturales e I.M.L., U.N.T., Instituto Superior de Correlación Geológica (INSUGEO-CONICET).*
Contacto: pocardenas20@alumnos.csnat.unt.edu.ar

El modelamiento geológico de yacimientos mineros se sustenta tradicionalmente en software comercial de alto costo. Esta barrera económica limita el acceso de los alumnos e instituciones educacionales a herramientas clave para la formación profesional. Esta limitación se subsana con la adopción de RecMin (Recursos Mineros), un software libre que ofrece funcionalidades comparables a los paquetes comerciales y está diseñado como un paquete completo para la gestión de proyectos de exploración y explotación.

La metodología implementada en este trabajo para el modelamiento de la cantera de yeso se fundamenta en la capacidad integral de RecMin para procesar datos de exploración y generar un modelo estimativo; específicamente, la gestión de datos críticos se realiza mediante el módulo RMedit para la edición de sondeos. En nuestro caso particular, dado que la cantera presenta una naturaleza subhorizontal y casi superficial y, por lo tanto, no se dispone de datos de sondeos profundos, se optó por adecuar la entrada de datos: las profundidades de las capas de yeso se tomaron a partir de las capas aflorantes visibles en el frente de la cantera, lo que permitió definir la extensión y las características del cuerpo de yeso dentro de las formaciones sedimentarias. Posteriormente, se procedió al Modelado Geológico 3D a través del módulo RMdraw, generando las superficies trianguladas que definen los límites del cuerpo mineralizado.

Basado en el modelo geológico 3D, se aplicó el **método de secciones transversales**, el cual permite cuantificar con precisión el volumen del cuerpo mineralizado mediante la interpolación de áreas. Al integrar la densidad y los parámetros del yacimiento a este cálculo, se logra una estimación de recursos con alta confianza técnica. La herramienta RecMin no solo facilita esta cubicación, sino que resulta fundamental para definir los límites de explotación y el diseño de la cantera, asegurando una planificación minera eficiente, segura y adaptada a la morfología real del depósito.

La adaptación exitosa de RecMin para el cálculo de reservas en una cantera de yeso demuestra la flexibilidad y el poder analítico de este software libre. Al proveer una plataforma robusta y accesible, RecMin se establece como una herramienta fundamental para la investigación y la consultoría en el sector geológico-minero.

**Palabras claves:**
*Modelado Geológico. RecMin. Reservas Mineras. Software Libre. Secciones transversales*

---

## 1. Introducción

**Modelado Geológico: Un Pilar Esencial con una Barrera de Acceso**

El modelamiento geológico de yacimientos mineros es una competencia crítica en la formación y práctica profesional. Tradicionalmente, este campo se ha sustentado en software comercial de alto costo. Esta barrera económica limita significativamente el acceso de alumnos, instituciones educacionales y consultores independientes a herramientas clave, para la formación profesional y consultorías. 

RecMin (Recursos Mineros) emerge para subsanar esta limitación. Es un software libre que ofrece un paquete completo para la gestión de proyectos de exploración y explotación, con funcionalidades comparables a las herramientas comerciales. Este trabajo describe el proceso integral en RecMin para la estimación de recursos en un yacimiento real, desde la gestión de datos hasta el modelado.

El presente estudio tuvo como objetivo integrar datos geológicos en un entorno 3D para cuantificar el volumen del yacimiento mediante el método de secciones, estableciendo una base sólida para la estimación de recursos y el análisis de factibilidad del proyecto minero.

## 2. Metodología de Trabajo en RecMin

RecMin opera como un sistema integrado de módulos especializados (Figura 1). Esta estructura permite un flujo de trabajo multidimensional que garantiza la trazabilidad desde la carga de datos crudos hasta la obtención de volúmenes finales.

![Módulos de RecMin](/Geologia_Digital/imaganes/modelo/figura1.png)
*Figura 1. Módulos de RecMin*

### Gestión de la Base de Datos Geológica

Para la construcción de la base de datos en RecMin, se integraron cinco archivos en formato cvs o txt los que se cargan en el módulo de yacimientos, estos archivos son fundamentales:

*   **Collar (sondajes):** Coordenadas (X, Y, Z) de los sondeos.
*   **Survey:** Trayectoria espacial (Azimut e Inclinación) de cada perforación.
*   **Litología:** Intervalos de profundidad y códigos de las unidades rocosas.
*   **Ensayos:** Datos de leyes o calidad asociados a cada tramo muestreado.
*   **Topografía:** Datos de puntos o curvas de nivel necesarios para generar la superficie de control que limita el modelo hacia arriba.

En este trabajo, para la confección del archivo de sondajes, las profundidades se determinaron a partir de los niveles de yeso aflorantes en el frente de explotación, cuya disposición subhorizontal facilitó la proyección del cuerpo mineralizado dentro de la secuencia sedimentaria. En cuanto a los datos técnicos, se generó un archivo de desviaciones con valores nulos (0°) dada la verticalidad de los puntos de control, mientras que el archivo de litología se simplificó en dos unidades principales: el horizonte económico de yeso y su cobertura de limoarcilla (Figura 2). Finalmente, se prescindió de un archivo de composición química detallado debido a la baja variabilidad del yacimiento, el cual mantiene una pureza constante y elevada, con rangos que oscilan entre el 80% y 96%.

![Método aplicado para generar los archivos de sondaje](/Geologia_Digital/imaganes/modelo/figura2.png)
*Figura 2. Método aplicado para generar los archivos de sondaje.*

La **Figura 2** ilustra esquemáticamente el procedimiento de generación de archivos base para la construcción del modelo tridimensional. En este sector específico, se modeló una unidad de yeso con potencias variables entre **0,90 m y 2,00 m**, protegida por un horizonte de encape cuyos espesores oscilan entre **1,50 m y 2,50 m**. Esta variabilidad geométrica fue capturada mediante el relevamiento de frentes y puntos de control, permitiendo una representación fiel de las irregularidades del depósito. Por su parte, en la **Figura 3** se detalla el flujo de procesamiento de la información, desde la obtención de los datos brutos de campo hasta la confección de las tablas normalizadas que requiere RecMin. Este proceso de estructuración de datos permite que el software procese las coordenadas y profundidades para generar, como resultado final, los archivos de sondajes que visualizan con precisión los espesores de yeso y las capas de sobrecarga en el entorno 3D.

![Construcción de base de datos](/Geologia_Digital/imaganes/modelo/figura3.png)
*Figura 3. Construcción de base de datos*

Una vez importados los datos de collares, desviaciones y litologías, el módulo de dibujo de RecMin (RMdraw) permite visualizar los sondeos en su correcta posición y orientación en el espacio 3D (Figura 4).

![Visualización de sondeos en su correcta posición](/Geologia_Digital/imaganes/modelo/figura4.png)
*Figura 4. Visualización de sondeos en su correcta posición y orientación en el espacio 3D.*

El siguiente paso es interpretar y conectar los intervalos de interés (Yeso) entre los diferentes sondeos para crear un modelo sólido 3D del cuerpo mineralizado. En RecMin, esto se logra generando superficies trianguladas (Figura 5).

![Intervalos de yeso conectados](/Geologia_Digital/imaganes/modelo/Figura5.png)
*Figura 5. Intervalos de yeso conectados mediante superficies trianguladas T3*

Tras la generación del **sólido tridimensional**, se procedió a la cuantificación del recurso utilizando el **método de secciones transversales**. Este procedimiento consiste en realizar cortes verticales paralelos a lo largo del cuerpo modelado a intervalos regulares. En cada sección, el software calcula el área del perfil del yacimiento y, mediante la **fórmula del prismoide** o de las **áreas medias**, interpola el volumen contenido entre planos sucesivos.

Una vez obtenido el **volumen geométrico total (m³)**, se aplicó el factor de **densidad aparente** (2.11 tn/m³) para transformar dicha magnitud en masa. Este paso final permitió determinar las **toneladas de yeso** contenidas en el sólido, proporcionando una base cuantitativa precisa para evaluar el potencial extractivo y la planificación minera del sector.

## 3. Resultados

![Modelo 3D de la capa yeso](/Geologia_Digital/imaganes/modelo/figura6.png)
*Figura 6. Modelo 3D de la capa yeso.*

![Métodos de los perfiles transversales para cálculo de volumen](/Geologia_Digital/imaganes/modelo/figura7.png)
*Figura 7. Métodos de los perfiles transversales para cálculo de volumen*

Como se aprecia en la **Figura 6**, la aplicación del método de secciones en RecMin permite realizar una disección del sólido 3D en planos paralelos. Las secciones actúan como un control de calidad del modelo; si hay una variación brusca en el espesor entre una sección y otra, el software lo detecta en el perfil. Además, RecMin genera un reporte detallado que desglosa el cálculo volumétrico sección por sección. En la Tabla 1 se aprecian las siguientes columnas clave que validan el rigor del cálculo:

*   **Sección:** Identifica cada plano de corte realizado a lo largo del yacimiento.
*   **Área (m²):** Representa la superficie del banco de yeso interpretada en cada perfil.
*   **Distancia (m):** El intervalo de separación entre secciones sucesivas utilizado para la interpolación.
*   **Volumen Parcial (m³):** El resultado de aplicar el método de las áreas medias entre dos secciones contiguas.
*   **Volumen Acumulado:** La sumatoria progresiva que arroja el volumen total del sólido modelado.

### Tabla 1. Cálculo detallado de volúmenes parciales y acumulados mediante el software RecMin

| Sección | Area | Paso | Parcial | Total |
| :--- | :--- | :--- | :--- | :--- |
| 275.513,50 | 0,00 | | | |
| 275.518,50 | 4,13 | 5,00 | 10,33 | 10,33 |
| 275.523,50 | 4,44 | 5,00 | 21,43 | 31,76 |
| 275.528,50 | 4,41 | 5,00 | 22,12 | 53,88 |
| ... | ... | ... | ... | ... |
| 275.728,50 | 2,61 | 5,00 | 12,90 | 677,77 |
| 275.732,50 | 0,00 | 4,00 | 5,22 | 682,99 |

Como se observa en la Tabla 1, el volumen total acumulado para el cuerpo de yeso modelado asciende a **682,99 m³**. Para la conversión de volumen a masa, se aplicó una densidad media de **2,11 tn/m³**, representativa del yeso de este yacimiento. De esta operación se desprende que el sector evaluado contiene un recurso estimado de **1.441,11 toneladas**.

## 4. Discusión

La delimitación del modelo geológico hacia el oeste se estableció bajo un criterio de **factibilidad económica**. Se observó que, en dicha dirección, el espesor del encape (limoarcillas) aumenta de manera abrupta, superando rápidamente la relación estéril/mineral (S: R) considerada rentable para una operación de pequeña a mediana escala. Este incremento del estéril impactaría directamente en los costos operativos, desplazando el límite del diseño de la cantera.

Sin embargo, debido a que el banco de yeso mantiene una potencia significativa y una alta pureza en ese sector, se optó por realizar una cubicación específica de una franja de **3 metros de ancho**. El objetivo de este análisis adicional fue cuantificar el recurso disponible bajo estas condiciones críticas de sobrecarga.

Si bien el software RecMin permite la implementación de modelos de bloques para la estimación de recursos, se optó por descartar esta metodología en favor del **método de secciones transversales**. Esta decisión técnica se fundamentó en dos factores críticos:

1.  **Morfología del Yacimiento:** El depósito presenta una geometría tabular con potencias (espesores) reducidas y subhorizontales. Las dimensiones de estas capas no satisfacen los requisitos mínimos de discretización para un modelo de bloques eficaz, ya que el tamaño del bloque necesario para representar fielmente el espesor del yeso comprometería la eficiencia computacional o generaría un error de "dilución" geométrica.
2.  **Continuidad Química:** La variabilidad de la pureza en el horizonte de yeso es mínima, manteniéndose en rangos constantes de alta calidad. Dado que no existen gradientes de ley complejos que requieran una interpolación geoestadística (como *Kriging* o Inverso de la Distancia), el método de secciones transversales resulta más eficiente y preciso para cuantificar un recurso de estas características.

Los resultados obtenidos (1.441,11 toneladas) quedan sujetos a la evaluación de la administración de la cantera. Corresponderá a los responsables de la explotación determinar si el valor del mineral recuperado compensa los costos de remoción del encape excedente, o si este sector debe ser clasificado como un recurso marginal bajo el esquema actual de costos.

Como se resume en el diagrama de flujo de la **Figura 8**, la confiabilidad de la estimación de recursos en este estudio reside en la integración sistemática de los datos. El proceso se inicia con la normalización de los **Datos en Bruto** (coordenadas, perfiles de frente y espesores), los cuales son transformados en **Sondeos 3D** dentro del entorno de RecMin. Esta base de datos permite la construcción de un **Modelo Geológico** tridimensional que respeta la geometría real del yacimiento. Finalmente, la aplicación del método de secciones sobre este modelo genera un **Informe de Recursos** automatizado, que en este sector específico arrojó un total de **1.441 t**.

![Flujo de trabajo con RecMin](/Geologia_Digital/imaganes/modelo/figura8.png)
*Figura 8. Flujo de trabajo con RecMin*

## 5. Conclusiones

*   RecMin no necesita de otros programas complementarios. Se realizó todo el proceso de modelado, desde la importación de datos hasta la estimación de recursos, dentro de un único ecosistema de software.
*   La metodología se adaptó a datos no convencionales (afloramientos en lugar de sondeos), probando la versatilidad de la herramienta.
*   Se generó un modelo 3D y una estimación de recursos de yeso, proporcionando datos valiosos para la toma de decisiones.
*   RecMin se establece como una herramienta fundamental y accesible para la investigación, la docencia y la consultoría en el sector geológico-minero, eliminando las barreras económicas sin sacrificar la capacidad técnica.

## 6. Referencias

RECMIN. (2024). *Manual de usuario y guía de procedimientos técnicos* (ver. 2.0).
https://www.recmin.com/manual
