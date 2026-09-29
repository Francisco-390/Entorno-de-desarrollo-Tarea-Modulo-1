# Tarea Módulo 1: Reconocimiento de Elementos en el Desarrollo de un Programa Informático

**Asignatura:** Entornos de Desarrollo  
**Alumno:** Francisco Martínez  
**Curso:** 1º Formación Profesional (Grado Superior)  
**Módulo:** Módulo 1 - Reconocimiento de Elementos en el Desarrollo de Software  
**Palabra clave:** Compañeros

---

## 📌 Descripción de la Tarea

Esta actividad tiene como objetivo evaluar la capacidad para reconocer los elementos y herramientas clave que intervienen en el ciclo de vida del desarrollo de software. A lo largo de la práctica se diferencian conceptual y prácticamente el **código fuente**, el **código objeto** y el **código ejecutable**, además de analizar el proceso de traducción/compilación y la clasificación de lenguajes de programación según su nivel de abstracción y paradigma.

---

## 🎯 Objetivos de Aprendizaje

- **RA1:** Reconoce los elementos y herramientas que intervienen en el desarrollo de un programa informático, analizando sus características y las fases en las que actúan hasta llegar a su puesta en funcionamiento.
  - **Criterio c):** Diferenciación clara entre código fuente, código objeto y ejecutable.
  - **Criterio e):** Clasificación sistemática de los lenguajes de programación.

---

## 📄 Parte 1: Análisis Teórico de Conceptos

### 1. Explicación de los Conceptos Básicos

#### A. Definiciones
* **Código Fuente:** Es el conjunto de instrucciones escritas por el programador en un lenguaje de alto o medio nivel (por ejemplo, C, Java o Python). Es legible por los seres humanos, pero no puede ser ejecutado directamente por la CPU.
* **Código Objeto:** Es el resultado de traducir (compilar) el código fuente a lenguaje máquina o código de bajo nivel. Aunque está compuesto por instrucciones binarias entendibles por el procesador, **aún no es ejecutable** de forma directa porque carece de las vinculaciones con librerías o dependencias externas.
* **Código Ejecutable:** Es el archivo binario final (por ejemplo, extensión `.exe` en Windows o sin extensión con permisos de ejecución en UNIX/Linux). Ha pasado por el proceso de enlazado (*linking*), incorporando las librerías necesarias para ejecutarse directamente en el procesador y el sistema operativo.

---

#### B. Fases por las que pasa un programa hasta su ejecución

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Código Fuente  │ ──► │   Compilador    │ ──► │  Código Objeto  │ ──► │    Enlazador    │ ──► Código Ejecutable
└─────────────────┘     └─────────────────┘     └─────────────────┘     └─────────────────┘
```

1. **Análisis Léxico:** El compilador lee el código fuente carácter por carácter y lo agrupa en **tokens** (palabras clave, identificadores, operadores, literales). Se eliminan espacios en blanco y comentarios.
2. **Análisis Sintáctico:** Verifica que los tokens sigan las reglas gramaticales del lenguaje, construyendo un Árbol de Sintaxis Abstracta (AST).
3. **Análisis Semántico:** Comprueba la coherencia lógica y de tipos (por ejemplo, verificar que no se sume un `String` con un `Int` si el lenguaje no lo permite, o que las variables estén declaradas).
4. **Generación de Código Intermedio:** Traduce el AST a una representación intermedia independiente de la arquitectura.
5. **Optimización de Código:** Mejora el código intermedio para reducir consumo de memoria o tiempo de CPU.
6. **Generación de Código Objeto:** Traduce el código optimizado al lenguaje de máquina de la arquitectura destino (`.o` o `.obj`).
7. **Enlazado (*Linking*):** El *linker* combina uno o varios archivos objeto con las bibliotecas estándar y del sistema para generar el archivo **Ejecutable**.
8. **Carga y Ejecución:** El cargador (*loader*) del sistema operativo ubica el código ejecutable en la memoria RAM y traslada el control a la CPU.

---

### 2. Clasificación de Lenguajes de Programación

#### A. Según el Nivel de Abstracción

| Nivel de Abstracción | Descripción | Ejemplos | Justificación |
| :--- | :--- | :--- | :--- |
| **Bajo Nivel** | Directamente vinculado con el hardware. Sin abstracción de memoria o registros. | **Lenguaje Ensamblador**, **Código Máquina** | Utiliza mnemónicos (`MOV`, `ADD`) o binario/hexadecimal directo. Depende totalmente de la arquitectura del procesador. |
| **Medio Nivel** | Permite abstracción de alto nivel pero conserva acceso directo a punteros y gestión de memoria. | **C**, **C++** | Permiten estructuras de control complejas y a la vez manipulación directa de memoria mediante punteros y aritmética de direcciones. |
| **Alto Nivel** | Gran distancia del hardware. Sintaxis cercana al lenguaje humano o matemático; gestión de memoria automática. | **Python**, **Java** | Ocultan detalles de la máquina (recolección de basura, gestión de memoria) y se enfocan en la resolución lógica del problema. |

#### B. Según el Paradigma de Programación

| Paradigma | Enfoque Principal | Ejemplos | Justificación |
| :--- | :--- | :--- | :--- |
| **Imperativo** | Especifica **cómo** se debe realizar una tarea mediante instrucciones secuenciales y cambios de estado. | **C**, **Java** | Utilizan estructuras como bucles (`for`, `while`), condicionales (`if`) y asignación explícita de variables para modificar el estado paso a paso. |
| **Declarativo** | Especifica **qué** resultado se desea obtener sin detallar el control de flujo explícito. | **SQL**, **Prolog** | En SQL se define el conjunto de datos deseado (`SELECT... WHERE...`) y el gestor de BD decide el plan de ejecución óptimo. Prolog evalúa reglas lógicas. |

---

## 🛠️ Parte 2: Actividad Práctica y de Análisis

### 1. Identificación de Paradigmas a partir de Fragmentos

* **Fragmento 1:** *Un programa recorre una lista de números sumándolos uno por uno hasta obtener el total.*
  * **Paradigma:** **Imperativo**
  * **Justificación:** Describe el algoritmo detallado paso a paso (*cómo* realizar el cómputo), utilizando una iteración y acumulación del estado para obtener la suma.

* **Fragmento 2:** *Una consulta a una base de datos busca empleados mayores de 30 años y devuelve solo sus nombres.*
  * **Paradigma:** **Declarativo**
  * **Justificación:** Expresa el resultado deseado (*qué* recuperar: nombres de empleados con edad $> 30$) sin especificar algoritmos de búsqueda, recorridos de memoria o índices a utilizar.

* **Fragmento 3:** *Un programa que calcula el factorial de un número $n$ definiendo que el factorial de $0$ es $1$ y, para números mayores, multiplicando el número por el factorial del número anterior ($n! = n \times (n-1)!$).*
  * **Paradigma:** **Declarativo (Funcional / Lógico)**
  * **Justificación:** Se apoya en la definición matemática y recursiva de la propiedad del factorial. Describe qué es la relación del factorial de un número en lugar de detallar una secuencia de bucles y modificaciones de variables acumuladoras.

* **Fragmento 4:** *Un programa filtra productos con precios superiores a 10 dólares recorriendo una lista y comprobando cada producto uno por uno.*
  * **Paradigma:** **Imperativo**
  * **Justificación:** Se detalla explícitamente el flujo de control y el mecanismo de verificación manual uno a uno sobre la lista.

---

### 2. Actividad en Grupo (Equipo Unipersonal): Comparación Cotidiana

#### Actividad Elegida: *Preparar un Café con Leche*

##### A. Descripción Imperativa
1. Camina hacia la cocina y coge una taza limpia del armario.
2. Llena la tetera con 200 ml de agua.
3. Enciende el fuego e introduce la tetera hasta que el agua hierva ($100^\circ\text{C}$).
4. Agrega una cucharada de café molido en la taza.
5. Vierte el agua hirviendo en la taza y remueve durante 10 segundos.
6. Abre el frigorífico, toma la botella de leche y añade 50 ml a la taza.
7. Remueve nuevamente con la cuchara y sirve en la mesa.

##### B. Descripción Declarativa
> Deseo obtener una taza de café caliente con leche, dulce, a una temperatura aproximada de $60^\circ\text{C}$ y lista para consumir en la mesa.

##### C. Análisis Comparativo: Ventajas y Desventajas

| Enfoque | Ventajas | Desventajas |
| :--- | :--- | :--- |
| **Imperativo** | - Control total sobre el proceso.<br>- Facilidad para depurar o modificar un paso específico.<br>- Predicibilidad paso a paso. | - Código/descripción más extenso y verboso.<br>- Mayor propensión a errores si falla un paso intermedio. |
| **Declarativo** | - Concisión y claridad en el objetivo final.<br>- Alta abstracción que permite optimización automática.<br>- Enfocado en la lógica del negocio. | - Menor control fino sobre la ejecución interna.<br>- Requiere un motor/intérprete subyacente que entienda cómo resolver la petición. |

---

## 📊 Formato de Entrega y Presentación

El trabajo está preparado para ser presentado en formato de presentación/informe de **5 a 10 páginas** estructurado de la siguiente forma:

1. **Portada:** Título de la práctica, datos del estudiante y módulo.
2. **Sección I:** Explicación teórica de Código Fuente, Objeto y Ejecutable + Fases de compilación.
3. **Sección II:** Clasificación de lenguajes (Niveles de abstracción y Paradigmas).
4. **Sección III:** Análisis y resolución de los 4 fragmentos de código.
5. **Sección IV:** Ejercicio práctico cotidiano (Café con leche) y tabla comparativa Imperativo vs. Declarativo.
6. **Conclusión y Bibliografía.**

---

## 📑 Criterios de Evaluación Cubiertos

- [x] **RA1.c:** Se han diferenciado claramente los conceptos de código fuente, objeto y ejecutable.
- [x] **RA1.e:** Se han clasificado adecuadamente los lenguajes de programación según sus características y paradigmas.