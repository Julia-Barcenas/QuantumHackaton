# QuantumHackaton

## Problema a tratar
Una empresa de reparto tiene una flota de camiones y un conjunto de clientes en diferentes lugares para entregar paquetes.
Debemos encontrar la longitud total de viaje más corta para todos los camiones para minimizar el costo/tiempo total. Para los cuales se utilizaron métodos de optimización combinatoria.

## Metodología
La **metodología** a seguir en la resolución de este código fue el siguiente:

1. Se creó un grafo con una distribución uniforme. Se definieron n nodos los cuales se distribuyeron de manera uniforme

2.  Se definió un solo centro de distribución definido por el centro de masas de todos los puntos, debido a que se utilizó una distribución uniforme este centro de distribución se encuentra bastante cerca del centro de todos los datos. Se trazaron los enlaces entre cada uno de los nodos

3. Se determinó el número de camiones a utilizar y se dividieron los clusters para asignarle cada uno a un camión distinto. Al momento de realizar los cluster no se tomó en consideración el centro de distribución ya que este punto pertenece a todos los cluster al mismo tiempo.

4. Estos clusters fueron separados para que fueran sus propios grafos individuales y poder aplicarles el tsp. Se graficaron cada uno de los clusters.

Dato: Es importante dividir la carga de trabajo en varios camiones debido a que por cada ciudad que se añade en el grafo la cantidad de operaciones aumenta significativamente. 

5. Se decidió tomar la aproximación de *VRP (Vehicle Routing Problem)*. La diferencia es que con esta técnica, en lugar de optimizar la ruta primero buscamos el conjunto de rutas más eficientes, esto se hizo al momento de separar los clusters.
Posteriormente, cada uno de los clusters se transformó de un dato de tipo networkx a uno de tsp para que cada uno de los clusters pueda ser resuelto como su propio TSP, donde se optimizaron cada una de las rutas, con la consideración de que todos los vehículos deben regresar al mismo centro de distribución.

![VRP](https://ingenieriaindustrialonline.com/wp-content/uploads/2021/07/VRP.png)

7. Se les asignó un costo relacionado con la distancia mínima que recorrió cada uno de los camiones. Específicamente se calculó que se utilizan 0.22 litros/km. Cada camión tiene un costo de $1509/día. Cada kilómetro cuesta $5.31 (suponiendo una velocidad constante de 60km/h)
