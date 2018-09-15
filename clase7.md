# Clase 7

## Acerca de la tarea

## Autómatas finitos no determinísticos
Siempre encuentro una palabra, del producto cruz de un estado
y un símbolo, pero la diferencia es que no voy a un estado, las
transiciones van a un conjunto de estados, $n$ estados distintos.

## Función de transición extendida para un NDFA
*Esto viene en el examen*
$$
\delta Q \times \Sigma^{*} \to \mathbb{P}(Q)
$$
* Trabaja con los o más símbolos
### Función de transición extendida
1.
$$
\hat{\delta}(q_i, a) = \delta(q_i, a), \forall q_i \in Q \quad \hat{} \quad a \in \Sigma
$$

$$
\hat{\delta}(q_i, ax) = \cup \hat{\delta}(q_i, x); \quad \forall q_i \in \delta(q_i, a) 
$$

## Ejemplo 1
$$
\hat{\delta}(q_0, mnmm) = \emptyset
$$
No hay ninguna transición que dispare la $m$.

## Ejemplo 1
$$
\delta(q_0, m) = {q_1, q_2} \\
\delta(q_0, n)
$$
$$
\hat{\delta}(q_0, mnmm) = \hat{\delta}(q_1, nmm) \cup \hat{\delta}(q_2, nmm) \\
= {q_2} \cup {q_2, q_1}
$$
irá a ver la transición hasta llegar a los casos triviales.
No se acepta porque $q_3$ no está en el conjunto resultante.

Se acepta el conjunto de palabras que iniciando en un autómata
termine en un estado final, en este caso al menos uno de los
estados en el conjunto debe ser un estado final. El control
se queda en varios estados, en $n$ estados.

## Relación entre los DFA y NDFA
**Teorema**: sea $M$ un dfa $\to \exists$ un ndfa $M_2 / L(M) = L(M_2)$
Siempre existirá un determinístico que hará exactamente lo mismo.
Toda transición deltro del NDFA va a ser igual.
$$
\text{dfa} \\
\delta(q_0, 0) = q_1 \to \delta(q_0, 0) = {q_1} \\
\delta(q_0, 1) = q_2 \to \delta(q_0, 1) = {q_2} \\
$$
En el DFA la transición siempre será a un conjunto de un elemento.

¿Qué pasará con el otro lado de la historia?
**Teorema**: sea $M$ un ndfa $\to \exists$ un dfa $M_2 / L(M) = L(M_2)$
$$
\delta(q_0, 1) = \{q_0, q_1, q_2\} \\
\delta(q_1, 2) = \{q_0\} \\
\delta(q_2, 0) = \emptyset
$$

dfa:
* Estado 1: $\{q_0, q_1, q_2\}$
* Estado 2: $\{q_0, q_2\}$
* Estado 3: $\emptyset$
Nombramos estados como arreglos de conjuntos tengamos. Cada uno de esos va a ser un
estado.

¿Por qué salieron las máquinas de Turing no determinísticas?
Simplemente por la necesidad de ver qué tan potente podemos hacer el modelo. Es equivalente
al procesador.

## Lenguaje recursivo, recursivamente numerable
Es una pieza fundamental de clasificación de lenguajes para la computabilidad
### Lenguaje recursivo
Un lenguaje es recursivo sí y solo sí existe un algoritmo capaz de decir en tiempo finito
si dada cualquier palabra es o no es del lenguaje.

### Lenguaje recursivamente numerable
Un lenguaje es recursivamente numerable sí y solo sí existe un procedimiento que dada una
palabra es capaz de decir si la palabra pertenece a dicho lenguaje o no pertence, o no
es capaz de dar respuesta.

¿Todo lenguaje recursivo es aceptable por un DFA? **No**. No todo
lenguaje recursivo es aceptado por un autómata. Hay varios lenguajes
donde los autómatas no saben qué hacer.

#### Ejemplo:
$$
L = \{a^n b^n, \; \text{con} \; n \geq 0\}
$$
Es aceptado por ningún autómata. El autómata no tiene la capacidad
de contar.

**Todo lenguaje aceptado por un autómata es recursivo**

*¿Cuál es el campo de la computación?*
Son los lenguajes recursivamente numerables.

### Relación entre las expresiones regulares y los autómatas
Son equivalentes. Expresiones reguales y autómatas finitos en
general son equivalentes. Todo lo que pueden denotar expresiones regulares
lo pueden los autómatas. La cláusula de Kleen hace esta relación.

¿Cómo paso de una expresión regular a un autómata?
* nsd-$\xi$: se mueve con la palabra vacía.

$$
\circ{q_0} \to \xi \to \circ{q_1}
$$
Siempre pasará a $q_1$.

No es posible pasar a un dfa directamente, pero sí es fácil pasar a un
ndf-$\xi$.

**Las expresiones regulares están dentro de los lenguajes recursivos**

# Unidad 3
## Gramática formal
### Jerarquía de Chomsky
Nadie lograba clasificar los lenguajes para el área informática.
La gramática se compone de los siguientes 4 elementos:
* Conjunto de símbolos terminales.
* Conjunto de símbolos no terminales.
* Conjunto de reglas.
* Axioma de la gramática, símbolo inicial de la gramática, a fuerza no terminal.

Una gramática consiste en generar derivaciones, construir reglas, algo genera algo,
$P$ genera $Q$, etc. El algo que genera **debe** tener símbolos no terminales.
Una gramática termina de generar cuando tiene símbolos constantes. La única restricción
es: **no puedo generar a partir del vacio**. Simplemente se restrigieron la forma
de las producciones y con eso construyó distintos tipos de gramática, a tal grado
que las más restrigindas son las regulares. Estas son las gramáticas que generan todos
aquellos tipos de lenguaje que las expresiones regulares son capaces de denotar.

Las restricciones son las naturales, se relacionan con los lenguajes recursivamente
numerables. La computación trabaja sobre las gramáticas naturales, pero no siempre
tiene casos de éxito.

Sensibilidad al contexto: si $aXb \to 123$, se dice que $X$ está entre $a$ y $b$.
Por ejemplo:
$$
L = \{a^n b^n c^n, \; \text{con} \; n \geq 0\}
$$