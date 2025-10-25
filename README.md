
# 🌐 SGR-Java

**Simulador de una Red de Suministro Inteligente**

Un proyecto académico y personal desarrollado en Java que modela una red de servicios (como internet o fibra óptica) utilizando estructuras de datos. El sistema es capaz de simular fallas en la red y encontrar rutas alternativas de forma autónoma.

---

## 🎯 Objetivos del Proyecto

El objetivo principal es aplicar las estructuras de datos y algoritmos aprendidos en clase (pilas, colas, listas, grafos y árboles) en un proyecto práctico, robusto y con una finalidad visible.

* **Académico:** Implementar y conectar el funcionamiento de las principales estructuras de datos.
* **Funcional:** Crear un modelo de red que reaccione a fallas del mundo real.
* **Algoritmos Clave:**
    * Implementar **Dijkstra** para el re-ruteo de tráfico (encontrar la ruta más corta/barata).
    * Implementar **Prim** para la planificación y expansión de la red (encontrar el árbol de expansión mínima).
    * Implementar **DFS/BFS** para el análisis de la red (detectar nodos aislados tras una falla).
* **Interfaz:** Proveer una interfaz gráfica (GUI) que permita visualizar la red, sus estados y los eventos en tiempo real.

---

## 🛠️ Stack de Tecnologías (Planeado)

* **Lenguaje:** Java (visto en clase).
* **Estructuras de Datos:** Implementaciones propias y/o uso de Java Collections Framework.
    * Grafos (Listas de Adyacencia).
    * Colas de Prioridad (para Dijkstra y Prim).
    * Pilas (para DFS).
    * Colas (para BFS).
* **Interfaz Gráfica (GUI):** JavaFX o Swing.
* **IDE:** Visual Studio Code / Eclipse / IntelliJ IDEA.

---

## 🚀 Características Principales

* **Visualización del Grafo:** Dibujar la red en pantalla, mostrando nodos (routers, ciudades) y aristas (cables de fibra).
* **Simulación de Fallas:**
    * **Falla de Arista:** Permitir al usuario "romper" un cable. La GUI lo marcará en rojo.
    * **Falla de Vértice:** Permitir al usuario "apagar" un nodo. Todas sus conexiones se verán afectadas.
* **Sistema de Respuesta (Re-ruteo):**
    * Al detectar una falla, el sistema buscará automáticamente rutas alternativas usando Dijkstra para los nodos afectados.
    * La GUI mostrará la nueva ruta (ej. en color amarillo).
* **Sistema de Planeación:**
    * Permitir al usuario agregar un nuevo "nodo" (comunidad, cliente).
    * El sistema usará Prim para calcular y sugerir la conexión de menor costo para integrarlo a la red existente.
* **Log de Eventos:** Un panel de texto que mostrará en tiempo real lo que está sucediendo:
    * `[FALLA] Se detectó corte en Arista (Puebla-Atlixco).`
    * `[INFO] Nodos [Atlixco, Izúcar] quedaron aislados.`
    * `[INFO] Re-ruteando [Atlixco] por ruta (Puebla -> Cholula -> Atlixco).`
    * `[ALERTA] No se encontró ruta alternativa para [Izúcar]. Se requiere técnico.`

---

## 📋 Control de Progreso (To-Do List)

Esta es mi hoja de ruta personal para llevar control.

### Fase 1: El Núcleo (Backend)

* [ ] Definir clases base: `Nodo.java`, `Arista.java`.
* [ ] Definir la clase `Grafo.java` (implementada con Listas de Adyacencia).
* [ ] Implementar **Algoritmo de Dijkstra** (requiere una `PriorityQueue`).
* [ ] Implementar **Algoritmo de Prim** (requiere una `PriorityQueue`).
* [ ] Implementar **DFS** (Depth-First Search) con una `Pila` (Stack) para detectar nodos aislados.

### Fase 2: Lógica de Simulación

* [ ] Función `simularFallaArista(arista)` (cambia `arista.status` a `ROTO`).
* [ ] Función `simularFallaNodo(nodo)` (cambia `nodo.status` a `OFFLINE`).
* [ ] Función `responderAFalla()` (llama a DFS para encontrar huérfanos y luego a Dijkstra para reconectarlos).
* [ ] Función `planearNuevaConexion(nuevoNodo)` (llama a Prim).

### Fase 3: Interfaz Gráfica (Frontend)

* [ ] Configurar el proyecto con **JavaFX** (o Swing).
* [ ] Crear un "Canvas" (lienzo) para dibujar el grafo.
* [ ] Función `dibujarRed()` (itera el grafo y pinta círculos y líneas).
* [ ] Función `actualizarRed()` (repinta la red con colores según el estado: Verde=OK, Rojo=FALLA, Amarillo=RUTA_ALTERNA).
* [ ] Añadir botones de control ("Simular Falla", "Añadir Nodo").
* [ ] Implementar la interactividad (que se pueda hacer clic en una arista o nodo para simular su falla).
* [ ] Añadir un `TextArea` para el log de eventos.

---

## 🔮 Futuras Implementaciones (Ideas al Aire)

Cosas que podría implementar *después* de entregar el proyecto de clase, para hacerlo un proyecto personal más robusto.

* [ ] **Pesos Reales:** Usar pesos en las aristas que no solo sean "distancia", sino una combinación de **latencia, ancho de banda máximo y costo económico**.
* [ ] **Simular Congestión:** Que el "peso" de una arista aumente dinámicamente si tiene mucho tráfico.
* [ ] **Guardar/Cargar Red:** Usar archivos `JSON` o `XML` para guardar topologías de red y cargarlas en el simulador.
* [ ] **(Avanzado) API REST:** Separar la lógica (Backend) en un servidor (ej. con Spring Boot) y que la GUI (Frontend) solo sea un cliente.
* [ ] **(Avanzado) Endpoints:** Crear endpoints como `/api/network/fail/edge/{id}` que disparen la simulación desde un cliente externo (como Postman o un dashboard web).
