# Reconstrucción de Secuencia de ADN usando Grafos de Bruijn

Este programa permite la reconstrucción de una secuencia de ADN utilizando un grafo de Bruijn. A partir de fragmentos de ADN (k-mers), el programa construye el grafo y busca un camino o ciclo Euleriano para ensamblar la secuencia original. También maneja errores en las secuencias y verifica la conectividad del grafo.

## Características

1. **Construcción del Grafo de Bruijn**:
   - A partir de fragmentos de ADN, se construye un grafo de Bruijn en el cual los nodos representan los prefijos y sufijos de cada fragmento, y las aristas representan las conexiones entre ellos.

2. **Determinación de un Camino o Ciclo Euleriano**:
   - Verifica las condiciones para la existencia de un camino o ciclo Euleriano.
   - Si es un ciclo Euleriano: todos los nodos deben tener la misma cantidad de aristas de entrada y salida.
   - Si es un camino Euleriano: todos los nodos excepto dos deben tener igual número de aristas de entrada y salida, y se deben identificar nodos específicos de inicio y fin.

3. **Reconstrucción de la Secuencia de ADN**:
   - Usa el camino o ciclo Euleriano para reconstruir la secuencia de ADN original.
   - Maneja errores en caso de inconsistencias en el grafo, como falta de conectividad o grados de entrada/salida incorrectos, e identifica fragmentos conflictivos.
   
## Uso del Código
Este programa implementa una clase DeBruijnGraph para construir, visualizar y analizar un grafo de Bruijn a partir de fragmentos de ADN, con el objetivo de ensamblar la secuencia original. A continuación, se explican los pasos detallados para el uso del código.

1. **Inicialización**:

Primero, crea una instancia de la clase DeBruijnGraph, pasando una lista de fragmentos de ADN en el formato de tuplas (fragmento, prefijo, sufijo). Cada fragmento representa una sección de la secuencia de ADN, donde:
  
  - Fragmento: Es una cadena que representa el fragmento de ADN en sí.
  - Prefijo: Son los primeros nucleótidos del fragmento.
  - Sufijo: Son los últimos nucleótidos del fragmento.

2. **Construcción y Visualización del Grafo**:

Para visualizar el grafo de Bruijn construido, llama al método visualize_graph(). Este método representa el grafo, donde cada nodo es un prefijo o sufijo de los fragmentos, y cada arista representa una transición entre ellos.

3. **Ensamblado de la Secuencia**:

Para ensamblar la secuencia original de ADN, llama al método assemble_sequence(). Este método realiza los siguientes pasos:

  - Verifica la conectividad del grafo mediante el método is_weakly_connected().
  - Evalúa si el grafo tiene un camino o ciclo Euleriano utilizando el método check_eulerian_conditions(). Esto implica revisar que el grafo cumpla las condiciones de grado necesarias para que exista un camino (si tiene nodos de entrada y salida distintos) o un ciclo (si todos los nodos tienen el mismo grado de entrada y salida).
  - Ensambla la secuencia de ADN original siguiendo el camino o ciclo Euleriano en el grafo, uniendo los fragmentos en el orden que se recorren en el grafo.

4. **Manejo de Errores**:

Si el grafo no cumple con las condiciones para un camino o ciclo Euleriano (lo que puede suceder si las secuencias de ADN tienen errores o están incompletas), el programa identifica y muestra los fragmentos conflictivos, es decir, aquellos nodos cuyos grados de entrada y salida no cumplen con las condiciones.
También, explica por qué el ensamblado de la secuencia original no es posible, indicando los problemas de conectividad o de grado en el grafo.
Propone soluciones, como la identificación de nodos iniciales y finales sugeridos, para facilitar una posible corrección o completar la secuencia de forma manual.
