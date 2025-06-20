
## Consideraciones

Para realizar las pruebas de carga se tuvieron en cuenta las siguientes consideraciones:

1. La tasa de servicio del servidor es 𝜇=10 como parametro de la distribucion exponencial. Definido en el archivo [server.py](./coding/implementacion_py.md/#servidor-de-respuestas-a-peticiones-http).
2. La tasa de arrivo 𝜆 se varia aumentando la carga en cada una de las pruebas.
3. La utilización del sistema 𝜌= 𝜆/𝜇 será el valor que se desea obtener en
las pruebas.
4. El tiempo de respuesta por solicitud T=1/(𝜇-𝜆), el cual se va a utilizar para comprar los valores teoricos y los obtenidos en la practica, para mas de un pod se calcula como T=1/(𝜇*k-𝜆).

### Tabla I: Resultados de las mediciones

## Tiempo medio en el sistema

| PODs (SVs) | ρ teórico      | λ [1/s] | λ medido [1/s] | μ medido [1/s] | Teórico [s]     | Medido [s]       | ρ medido |
|:-----------|:----------------|:--------|:----------------|:----------------|:----------------|:----------------|:-----------|
| **1**     | 0.1            | 1      | 1.04           | 9.45           | 0.1111111111   | 0.1188989953   | 0.11      |
|           | 0.3            | 3      | 3.08           | 9.56           | 0.1428571429   | 0.1542809889   | 0.322     |
|           | 0.6            | 6      | 6.01           | 9.55           | 0.25           | 0.2830055186   | 0.63      |
|           | 0.9            | 9      | 8.66           | 9.84           | 1              | 0.8468834688   | 0.88      |
|           | 1              | 10     | 9.7            | 9.8            | Inf            | 10.20408163    | 0.99      |
|           | 1.2            | 12     | 10.01          | 10.01          | Inf            | Inf            | 1         |
|           | 1.5            | 15     | 12.51          | 15.25          | Inf            | 0.364298725    | 0.82      |
| **2**     | 0.25           | 5      | 4.83           | 9.5            | 0.06666666667  | 0.07055171441  | 0.254     |
|           | 0.45           | 9      | 8.72           | 10.13          | 0.09090909091  | 0.08659358168  | 0.43      |
|           | 0.65           | 13     | 12.57          | 9.57           | 0.1428571429   | 0.1583230423   | 0.67      |
|           | 0.75           | 15     | 15.07          | 9.78           | 0.2            | 0.2222814973   | 0.77      |
|           | 0.95           | 19     | 19.93          | 10.48947368    | 1              | 0.264815744    | 0.82      |
|           | 1              | 20     | 19.46          | 9.45           | Inf            | -1.76366843    | 1.03      |
| **3**     | 0.2            | 6      | 5.92           | 8.97           | 0.04166666667  | 0.04764218811  | 0.22      |
|           | 0.4            | 12     | 12.09          | 9.83           | 0.05555555556  | 0.05747423717  | 0.41      |
|           | 0.6            | 18     | 17.69          | 10             | 0.08333333333  | 0.08130081301  | 0.59      |
|           | 0.8            | 24     | 23.8           | 9.91           | 0.1666666667   | 0.1681802893   | 0.8       |
|           | 0.9666666667   | 29     | 28.2           | 9.85           | 1              | 0.7405021345   | 0.9543    |
|           | 1.166666667    | 35     | 31.85          | 10.87          | -0.2           | 1.533272002    | 0.98      |
| **4**     | 0.2            | 8      | 7.97           | 9.5            | 0.03125        | 0.03329848092  | 0.2097    |
|           | 0.375          | 15     | 14.42          | 10.09          | 0.04           | 0.0385334478   | 0.357     |
|           | 0.6            | 24     | 23.49          | 9.8            | 0.0625         | 0.0637755102   | 0.6       |
|           | 0.75           | 30     | 29.36          | 9.91           | 0.1            | 0.09702708996  | 0.74      |
|           | 0.95           | 38     | 36.87          | 10.02          | 0.5            | 0.3118762475   | 0.92      |
|           | 1              | 40     | 38.65          | 9.38           | Inf            | 0.02665245203  |           |
|           | 1.05           | 42     | 39.51          | 9.877          | -0.5           | Inf            | 1         |
| **6**     | 0.3333333333   | 20     | 19.91          | 9.5            | 0.025          | 0.026106934    | 0.328     |
|           | 0.4333333333   | 26     | 25.73          | 10.09          | 0.02941176471  | 0.02919406968  | 0.4342    |
|           | 0.5333333333   | 32     | 30.76          | 9.8            | 0.03571428571  | 0.03513802215  | 0.516     |
|           | 0.6666666667   | 40     | 39             | 9.91           | 0.05           | 0.04692530393  | 0.6416    |
|           | 0.8666666667   | 52     | 50.6           | 10.02          | 0.125          | 0.1039587492   | 0.84      |
|           | 0.9666666667   | 58     | 55.35          | 9.38           | 0.5            | 0.1184553423   | 0.85      |
|           | 1              | 60     | 56.94          | 9.86           | Inf            | 0.4471775939   | 0.9622    |


En la Tabla 1 se presentan los distintos escenarios diseñados para analizar el comportamiento del sistema. El ensayo consistió en realizar 28 pruebas distintas, en las cuales se modificaron diferentes parámetros con el objetivo de evaluar los resultados obtenidos en cada caso. Durante las pruebas, se varió la cantidad de pods en el clúster y, para cada configuración, se ajustaron los valores teóricos de λ (tasa de llegada de solicitudes) en función de la carga del sistema ρ que se deseaba analizar.

En la práctica, se observó el comportamiento real de los pods y se calculó el promedio de utilización de milicores en el clúster. Con este valor, se obtuvo el ρ práctico, lo que permitió determinar el μ práctico basándose en la ecuación del sistema para un modelo M/M/C, donde el número de servidores C corresponde a la cantidad de pods configurados en el clúster.



## Ecuaciones utilizadas para modelar el sistema

![Modelo](img/figura7.png)

Donde *k* son la cantidad de PODS.
***

## **Tiempos de Respuesta del sistema en funcion de la tasa de arribo:**

Para valores bajo de carga del sistema ρ, el tiempo de respuesta es pequeño y estable, pero cuando se acerca a 1 o lo que es lo mismo cuando  λ se acerca demasiado a μ, el tiempo de respuesta crece rápidamente y el pod ya no puede manejar la carga de trabajo de manera efectiva lo que indica congestion y demoras altas.

![Modelo](img/trespuesta_vs_rho.png)



## **Numero de tareas en el sistema en funcion de la tasa de arribo:** 

Para valores bajos de λ, el numero esperado de tareas en el sistema crece de manera controlado, pero a medida que la tasa de arrivos se acerca a la capacidad del sistema (kμ), L se dispara, indicando sobrecarga y congestion. Cuando λ supera la capacidad del sistema, L tiende a infinito, y el sistema es inestable

![Modelo](img/Numero_Tareas_vs_Lambda.png)



## **Consumo de CPU en el cluster en funcion de la tasa de arribo:**

El consumo de CPU en el cluster para los valores de lambda tomados crece en porcentaje a medida que se incrementa la tasa de arrivos, la utilidad en el sistema aumenta por lo tanto es mayor el consumo de recursos de hardware.

![Modelo](img/Cpu_vs_Lambda.png)


## Uso de CPU en la maquina anfitriona con el cluster corriendo en reposo y realizando una prueba de carga:

![Modelo](img/cluster_en_reposo.png)
![Modelo](img/uso_cpu_6podsl50.png)




## **Tasa de perdida en funcion de la tasa de arribo:**

Al aumentar la tasa de arribo λ, el sistema tiende a saturarse, lo que provoca un aumento en el tiempo de respuesta, una mayor tasa de pérdida de solicitudes y una alta utilización de recursos.

![Modelo](img/Loss_Rate_vs_Lambda.png)

&nbsp;

## *Respuesta del sistema en funcion de la cantidad de servidores en ejecucion para un lambda=15 1/s y mu=10 1/s*

![Modelo](img/Tiempo_Respuesta_vs_Pods.png)


[*Scripts para graficar*](./coding/implementacion_py.md/#scripts-de-graficas).

&nbsp;


## **Tiempo de respuesta promedio en funcion del factor de utilidad para los valores medidos variando la cantidad de pods:**

![Modelo](img/curvas_respuesta_carga.png)

Se observa que a medida que se incrementan la cantidad de servidores disponibles, la curva de tiempo de respuesta en el sistema es menor.

## Uso del Horizontal Pod Autoescaler

### Caso 1: 1 Pod, λ=30
![Modelo](img/t_respuestal30_1pod (1).png)

Configurando el HPA para que escale hasta un maximo de 6 pods cuando el uso promedio del CPU exceda el 25%, para este caso con una tasa de arribo igual a 30 1/s y para un pod en ejecucion el sistema se estabiliza aproximadamente a las 7000 solicitudes alcanzando el escalado maximo de 6 replicas.

### Caso 2: 2 Pod, λ=30

![Modelo](img/t_respuesta_l302pods.png)

### Caso 3: 2 Pod, λ=40

![Modelo](img/t_respuesta_l402pods.png)

[*Horizontal Pod Autoescaler*](./coding/implementacion_yml.md/#horizontal-pod-autoescaler)
