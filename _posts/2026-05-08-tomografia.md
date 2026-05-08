---
layout: post
title: "Evaluación de Tomografía Eléctrica 2D"
date: 2026-05-08
---

Evaluación Comparativa de Procesamiento Geofísico: Implementación de Algoritmos en Python y Modelado en Golden Surfer para Tomografías Eléctricas 2D.

Autor:Patricio Cardenas

Resumen

El presente trabajo describe la caracterización geofísica del subsuelo somero en el sector este del Parque 9 de Julio (San Miguel de Tucumán, Argentina), mediante la aplicación de Tomografía de Resistividad Eléctrica (TRE) en 2D. El área de estudio se emplaza sobre depósitos cuaternarios del Río Salí, caracterizados por una secuencia sedimentaria granocreciente. Para el procesamiento de los datos brutos, se implementó un flujo de trabajo híbrido que integró algoritmos de validación en Python —utilizando bibliotecas de código abierto como Pandas, NumPy y Matplotlib— y el modelado final por interpolación Kriging en Golden Surfer. Los resultados permitieron identificar tres unidades geoeléctricas principales: una capa superficial conductiva (20-45 Ω X m) asociada a limos arcillosos, que transiciona a una unidad de alta resistividad (> 100 Ω X m) a partir de los 10 metros de profundidad, interpretada como el techo de la formación de gravas fluviales. La discusión técnica destaca que el uso de software libre, potenciado por la asistencia de Inteligencia Artificial (IA), permitió a un usuario sin experiencia previa en programación ejecutar análisis complejos y visualizaciones 3D con alta precisión científica. Se concluye que este enfoque no solo garantiza la fidelidad de los datos frente a la interpolación comercial, sino que democratiza el acceso a herramientas de prospección avanzada al eliminar la dependencia de licencias de alto costo.
Palabras clave: Geofísica 2D, Tomografía de Resistividad, Python, Software Libre, Parque 9 de Julio, Inteligencia Artificial. 

Antecedentes y Contexto Geológico

El área de estudio se localiza en el sector este de la ciudad de San Miguel de Tucumán (Argentina), en terrenos correspondientes a los niveles cuaternarios depositados por el Río Salí, principal colector de la provincia. Estratigráficamente, el subsuelo se caracteriza por una secuencia granocreciente en profundidad: los niveles superiores presentan limos arcillosos que conforman el suelo vegetal, los cuales transicionan hacia arenas medias a gruesas y, finalmente, hacia potentes depósitos de gravas medias a gruesas que se extienden hasta profundidades de 20 a 30 metros. 
Dada la relevancia urbana y ambiental del Parque 9 de Julio, se planteó la ejecución de una Tomografía de Resistividad Eléctrica (TRE) con una extensión de 48 metros y orientación Norte-Sur. El objetivo principal de esta prospección es caracterizar el subsuelo somero para generar información de base aplicable a estudios ambientales y geotécnicos

 Metodología
 
 Adquisición de Datos Geofísicos
Para la caracterización del subsuelo en el sector del Parque 9 de Julio, se empleó el método de Tomografía de Resistividad Eléctrica (ERT) en 2D. Esta técnica permite obtener una sección transversal de la resistividad eléctrica del terreno mediante la inyección de corriente y la medición del potencial resultante a través de un arreglo multielectródico. 
El dispositivo experimental consistió en:
•	Longitud del perfil: Un tendido total de 45 metros.
•	Configuración de Electrodos: Se utilizó un sistema de 46 electrodos con una separación base (a) de 1 metro.
•	Niveles de Investigación (n): La profundidad de investigación se controló mediante el incremento progresivo del espaciamiento entre los electrodos, abarcando desde el nivel L1 (profundidad de 1m) hasta el nivel L15 (profundidad máxima de 15m). 
•	Puntos de Medición: Se registraron múltiples puntos de dato, donde cada coordenada horizontal (X) se definió como el punto medio geométrico del arreglo de electrodos activo en cada medición. 
 Procesamiento y Modelado Numérico
El flujo de trabajo para el procesamiento de los datos brutos se dividió en tres etapas principales para garantizar la trazabilidad y calidad del modelo final:
Pre-procesamiento (Control de Calidad): Se organizaron los datos de campo (voltaje, corriente y factor geométrico K) en una estructura de niveles de profundidad teórica (p). Se eliminaron registros con ruido instrumental excesivo o valores de resistividad físicamente incoherentes. 
El procesamiento numérico en entorno Python se diseñó como un filtro de validación y análisis estadístico previo al modelado final, iniciando con la estructuración de una matriz de coordenadas espaciales (X, Y, Z) mediante las bibliotecas Pandas y NumPy para automatizar el cálculo del punto medio geométrico en cada nivel de investigación (n). Posteriormente, se empleó una Triangulación de Delaunay para conectar los puntos de medición vecinos en una red de triángulos, garantizando una representación fiel de la densidad real de datos y evitando la generación de valores ficticios en los bordes, técnica que culmina con el uso de la función tricontourf de Matplotlib para generar una pseudosección de resistividades que permite la identificación crítica de ruidos o lecturas erróneas antes del refinamiento final en Surfer. Para obtener una perspectiva volumétrica del subsuelo del Parque 9 de Julio, se generó un modelo de capas apiladas (Stacked Layers). Este método permite visualizar cómo cambia la resistividad en cada nivel de profundidad de forma independiente pero integrada en un solo bloque.
•	Lógica del Modelo: Se proyectaron los niveles de investigación (L1, L3, L6, L9, L12, L15) como planos horizontales paralelos en un espacio tridimensional.
 Refinamiento y Post-procesamiento en Golden Surfer: Los datos procesados se exportaron en formato ASCII Grid (DSAA) para su modelado final. Se aplicó el método de interpolación de Kriging para obtener una superficie continua de isolíneas de resistividad. Finalmente, se realizó un proceso de Blanking (recorte) para eliminar las áreas de extrapolación sin soporte físico fuera del área de influencia de las líneas de corriente. 

Los datos obtenidos son los siguientes 
TOMOGRAFIA ELECTRICAS: Una (1) con dispositivo Wenner con aperturas crecientes de AB, de 3, 9, 18, 27, 36 y 45 m, ubicadas en un perfil NS a 45 m de longitud.
Protocolo de Procesamiento: Tomografía Eléctrica
Paso 1: Preparación de Datos (Excel)
Antes de tocar cualquier software, el Excel debe estar limpio.
•	Columnas Obligatorias: Distancia (X), Profundidad (Y), Resistividad (Z) y Nivel (L).
Lo valores de profundidad y resistencia se obtiene de los datos de campo y  el cálculo de la distancia se describe a continuación 
El cálculo de la Distancia (X)
La distancia horizontal se calcula buscando el centro exacto entre los electrodos externos A y B. La fórmula es:
  X=(A+B)/2

•	Limpieza: Eliminar valores negativos de resistividad (ruido de campo) y verificar que las profundidades sean negativas (eje Y descendente).
 
Resultados y Visualización

A continuación se presentan los perfiles de resistividad obtenidos:
![Descripción corta](/Geologia_Digital/imaganes/tomo.1.png)
Figura 1. Sección de resistividad eléctrica procesada en Python. Se observa la distribución discreta de los puntos de medición.
![Descripción corta](/Geologia_Digital/imaganes/tomo2.png)
Figura 2: Modelo de contornos suavizado en Surfer. 
Fue necesario recortar el modelo final para restringir la visualización únicamente al dominio donde existió información de campo efectiva
![Descripción corta](/Geologia_Digital/imaganes/tomo3.png)
Figura3. Tomografía eléctrica con surfer después de aplicar el protocolo de recorte (blanking)

 Interpretación de Unidades Geofísicas
 
De acuerdo a los valores de resistividad (Ω x m) observados, se identifican tres unidades principales:
1.	Capa Superior Conductiva (20 - 45 Ω X m): Ubicada en los primeros 4 metros de profundidad hacia el sector Este (derecha del perfil). Esta baja resistividad sugiere suelos con mayor contenido de humedad o presencia de limos arcillosos. 
2.	Cuerpo de Resistividad Intermedia (50 - 80 Ω X m): Predomina en la zona central y superficial. Corresponde probablemente a suelos franco-arenosos con compactación moderada. 
3.	Anomalía de Alta Resistividad (> 100 Ω X m): Se detecta un cuerpo prominente en la base del perfil, entre las progresivas 20 y 30 metros, a una profundidad de -10 a -15 metros.
o	Interpretación: Esta zona (colores rojos intensos) indica un material mucho más resistivo. Podría tratarse de un nivel de gravas secas, restos de estructuras antiguas o una variación litológica hacia materiales más gruesos y menos porosos
![Descripción corta](/Geologia_Digital/imaganes/tomo.5.png)
Figura 4. Visualización 3D mediante planos de resistividad apilada. Se observa la arquitectura interna de las capas de limos y gravas.

Esta visualización permite identificar la continuidad vertical de las unidades. Por ejemplo, se observa cómo la unidad conductiva superficial disminuye su espesor hacia el Oeste, mientras que el cuerpo de alta resistividad (gravas) gana potencia en los niveles basales.

Discusión
   
¿Por qué el triángulo en Python no es "perfecto"?

En tu gráfico de Python (Figura 1), los bordes se ven escalonados o ligeramente irregulares por dos motivos:
•	Discretización de los datos: Como se observa en la tabla de datos, el nivel L1 tiene 45 puntos, pero el L15 tiene solo 1 punto. Python (usando librerías como Matplotlib) intenta dibujar el contorno uniendo esos puntos específicos. Al no haber datos en las diagonales exactas, el algoritmo de interpolación genera ese borde "serruchado" o irregular. 
•	Densidad variable: Al tener muchos puntos arriba y casi ninguno abajo, la malla de interpolación se vuelve más "tosca" a medida que profundizas. El software "estira" los colores hasta donde encuentra el último dato real, y si los datos no terminan en una línea recta perfecta en el espacio X, Y, el borde reflejará esa irregularidad. 

 ¿Por qué en Surfer hay que recortarla (Blanking)?
 
Surfer funciona de una manera distinta a los scripts típicos de Python:
•	Extrapolación por defecto: Surfer es un programa de interpolación "rectangular". Cuando le das tus datos, él crea una rejilla (grid) que cubre desde el X mínimo al X máximo, y desde el Y mínimo al Y máximo. 
•	El problema del "Inventado": Como Surfer ve un espacio vacío en las esquinas superiores e inferiores fuera del triángulo de datos, intenta "predecir" qué valores habría ahí basándose en los puntos cercanos. Esto genera colores en zonas donde nunca mediste nada. 
•	El archivo de recorte (.bln): Para que el mapa sea científicamente válido, debes aplicar un proceso de Blanking (recorte). Esto le dice al programa: "Aunque calculaste valores para toda el área, por favor borra o vuelve invisibles las zonas donde no hubo paso de corriente eléctrica". 
![Descripción corta](/Geologia_Digital/imaganes/tomo6.png)

Este trabajo destaca la transición hacia flujos de trabajo basados en software libre, utilizando Python para romper la dependencia de licencias comerciales costosas y garantizar la reproducibilidad científica. La implementación de estos algoritmos fue posible gracias a la Inteligencia Artificial (IA), que actuó como un puente técnico para traducir la lógica geológica en scripts funcionales sin requerir experiencia previa en programación. Esta sinergia entre código abierto e IA potencia la autonomía del geólogo, permitiendo generar visualizaciones avanzadas de alta calidad técnica con una inversión económica mínima.


Conclusiones

•	Caracterización del Subsuelo: El estudio permitió identificar con éxito la arquitectura sedimentaria del subsuelo somero en el sector este del Parque 9 de Julio. Se confirmó la presencia de una secuencia granocreciente en profundidad, compuesta por una capa superficial limo-arcillosa de baja resistividad (20-45Ωxm) que transiciona hacia un nivel de arenas y gravas altamente resistivas (> 100 Ωxm) a partir de los 10 metros de profundidad. 
•	Alcance del Método Eléctrico: La Tomografía de Resistividad Eléctrica (TRE) con un tendido de 48 metros demostró ser una herramienta eficaz para la prospección ambiental y geotécnica, logrando una profundidad de investigación efectiva de aproximadamente 15 metros, suficiente para detectar el techo de la unidad de gravas fluviales del Río Salí. 
•	Validación Metodológica: La comparación entre el procesamiento en Python y Golden Surfer reveló que, si bien Surfer ofrece una estética suavizada ideal para la presentación final, el uso de scripts en Python permite una validación más rigurosa y fiel a la densidad real de los datos brutos, evitando extrapolaciones sin sustento físico en las zonas de borde. 
•	Innovación y Autonomía: Se demostró que la integración de software libre y herramientas de Inteligencia Artificial reduce significativamente los costos operativos y permite que profesionales sin experiencia avanzada en programación ejecuten análisis complejos y visualizaciones 3D de alta precisión. Este flujo de trabajo garantiza la reproducibilidad de los resultados y democratiza el acceso a tecnología geofísica de punta

Referencias
García, J. W. y D'Urso, C. H. (2015). Guía de Trabajos Prácticos: Métodos Geoeléctricos. Cátedra de Hidrogeología, Facultad de Ciencias Naturales e Instituto Miguel Lillo, Universidad Nacional de Tucumán.
<script src="https://utteranc.es/client.js"
        repo="patriciocardenasgon-svg/Geologia_Digital"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
<br>
<hr>
<div style="text-align: center; margin-top: 20px; margin-bottom: 50px;">
  <a href="https://patriciocardenasgon-svg.github.io/Geologia_Digital/" 
     style="padding: 12px 25px; 
            background-color: #333; 
            color: white; 
            text-decoration: none; 
            border-radius: 8px; 
            font-weight: bold; 
            display: inline-block;">
     ← Volver al Inicio
  </a>
</div>
