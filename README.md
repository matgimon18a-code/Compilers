# Tarea 1 – Función de Falla (Algoritmo KMP)

## Autores
- Matias Gil Montoya  
- Samuel Quintero  

---

## Sistema Operativo y Herramientas Utilizadas

- Sistema Operativo: Windows 10 / Linux / macOS  
- Lenguaje de Programación: Python 3.10 o superior  
- Entorno de ejecución: Google Colab / Jupyter Notebook  
- Control de versiones: Git y GitHub  

---

## Descripción del Proyecto

Este proyecto implementa la **Función de Falla** descrita en la Sección 3.4.5 del libro (Figura 3.19).

La función de falla es parte fundamental del algoritmo **Knuth-Morris-Pratt (KMP)**, utilizado en análisis léxico para el reconocimiento eficiente de tokens dentro de un texto.

---

## ¿Qué hace la Función de Falla?

Dado un patrón `b1 b2 ... bn`, la función de falla `f(s)` calcula:

La longitud del prefijo propio más largo del substring `b1...bs`
que también es sufijo de `b1...bs`.

En otras palabras, para cada posición del patrón, indica cuánto podemos retroceder sin perder información cuando ocurre un fallo en la comparación.

---

## ¿Para qué se utiliza?

La función de falla se utiliza en:

- Búsqueda eficiente de cadenas
- Análisis léxico
- Reconocimiento de tokens
- Construcción de compiladores
- Algoritmo KMP

Su principal ventaja es que evita comparaciones innecesarias, garantizando un tiempo de ejecución lineal.

---

## Explicación Lógica del Algoritmo

1. Inicialización:
   - `f[0] = 0`
   - `t = 0` (longitud del prefijo coincidente actual)

2. Para cada posición `s` desde 1 hasta n-1:
   - Mientras haya un desajuste y `t > 0`,
     se actualiza:
     `t = f[t-1]`
   - Si los caracteres coinciden:
     - se incrementa `t`
     - se asigna `f[s] = t`
   - Si no coinciden:
     - se asigna `f[s] = 0`

### Idea fundamental

Cuando ocurre un fallo, el algoritmo no vuelve al inicio del patrón.
En su lugar, reutiliza información previamente calculada.

Esto evita repeticiones innecesarias y garantiza eficiencia.

---

## Complejidad Temporal

El algoritmo tiene complejidad:

O(n)

Donde `n` es la longitud del patrón.

Cada carácter se procesa como máximo dos veces, lo que garantiza eficiencia lineal.

---

## Cómo Ejecutar el Programa

1. Abrir Google Colab
2. Crear un nuevo Notebook
3. Copiar y pegar el código en una celda
4. Ejecutar la celda

El programa calculará la función de falla para:

- abababaab
- aaaaaa
- abbaabb

---

## Ejemplo de Salida

Patrón: abababaab  
Función de Falla: [0, 0, 1, 2, 3, 4, 5, 1, 2]

Patrón: aaaaaa  
Función de Falla: [0, 1, 2, 3, 4, 5]

Patrón: abbaabb  
Función de Falla: [0, 0, 0, 1, 1, 2, 3]

---

## Conclusión

La función de falla es un componente esencial del algoritmo KMP.
Permite realizar búsquedas de patrones de manera eficiente,
reduciendo comparaciones innecesarias y garantizando un tiempo de ejecución lineal.

Este proyecto implementa correctamente el algoritmo descrito en la Figura 3.19
y resuelve el Ejercicio 3.4.3.
