### Definiciones de Términos empleados en clase:

**Token**
Unidad mínima en la que el modelo divide el texto. No es una palabra: según el tokenizador puede ser una palabra, una sub-palabra, un carácter o incluso bytes. Por eso *llueve* se parte en `ll` + `ueve` y *escampa* en `Esc` + `ampa`. Cada token tiene asociado un ID entero. El modelo nunca "ve" letras: opera siempre sobre secuencias de tokens.

**Vocabulario**
Conjunto finito y cerrado de todos los tokens que el modelo conoce, cada uno con un ID único. Su tamaño $V$ es fijo (típicamente ~30.000–200.000). Define a la vez la entrada (todo texto se codifica con tokens de este conjunto) y la salida (el modelo solo puede emitir tokens que existan en el vocabulario). Es el "alfabeto" del modelo.

**Embedding**
Vector denso de dimensión $D$ que representa a cada token en un espacio continuo. La capa de embedding es una matriz $V \times D$: dado el ID del token, devuelve su fila correspondiente. Convierte un identificador discreto y sin significado numérico en un vector cuyas componentes capturan relaciones semánticas y sintácticas aprendidas durante el entrenamiento (tokens parecidos quedan cerca en ese espacio). Es lo que aparece como `[0.52, -0.31, 0.87 …]` en el diagrama.

**Logits**
Salida cruda (sin normalizar) de la última capa lineal del modelo: un vector de tamaño $V$, una puntuación por cada token del vocabulario. Se obtienen proyectando el estado oculto final $h$ sobre el vocabulario, $z = h\,W^\top$. Son números reales arbitrarios (pueden ser negativos) y **no** son probabilidades todavía. El de mayor valor es el token más favorecido como siguiente.

**Softmax de la capa de salida (con temperatura T)**
Transforma los logits $z$ en una distribución de probabilidad sobre todo el vocabulario (todo positivo y suma 1). Con temperatura $T$:

$$p_i = \frac{e^{\,z_i / T}}{\displaystyle\sum_{j=1}^{V} e^{\,z_j / T}}$$

La temperatura $T>0$ escala los logits **antes** de exponenciar y controla cuán "picuda" o "plana" queda la distribución:

- $T = 1$: softmax estándar.
- $T \to 0$: la masa se concentra casi toda en el logit máximo → comportamiento determinista (equivale a *greedy* / argmax).
- $T < 1$: agudiza la distribución → más conservador y repetitivo.
- $T > 1$: aplana la distribución → más aleatorio, diverso y "creativo" (también más errores).

**Top-k (en el muestreo)**
Antes de muestrear, se conservan solo los $k$ tokens con mayor probabilidad y se descarta el resto (probabilidad 0). Se renormaliza el softmax sobre esos $k$ y se muestrea de ahí. El corte es por **número fijo** de candidatos (p. ej. $k=40$): siempre se consideran 40, sea cual sea la forma de la distribución.

**Top-p / nucleus sampling**
Se ordenan los tokens por probabilidad descendente y se toma el conjunto más pequeño cuya probabilidad **acumulada** alcanza el umbral $p$ (p. ej. $p=0.9$). Se renormaliza sobre ese "núcleo" y se muestrea. El corte es por **masa de probabilidad**, no por cantidad: el tamaño del núcleo se adapta solo —pocos candidatos cuando el modelo está muy seguro, muchos cuando duda.

La diferencia clave: *top-k* fija **cuántos** candidatos; *top-p* fija **cuánta probabilidad** acumulas. En la práctica se combinan con la temperatura (primero $T$ deforma la distribución, luego top-k/top-p la recortan, después se muestrea).

Si quieres, puedo añadir un sexto recuadro al diagrama mostrando el paso `logits → softmax(T) → top-k/top-p → muestreo`, que es justo el eslabón que ahora queda implícito entre "mayor logit" y el token elegido.