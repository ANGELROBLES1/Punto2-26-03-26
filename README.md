# Punto2-26-03-26
# Comparacion de Analisis Sintactico: CYK vs ANTLR

## Requerimientos

### 1. Archivos necesarios

El programa requiere los siguientes archivos organizados en la carpeta `Punto2`:
``
Punto2/
│
├── cyk.py
├── medir.py
├── resultados.txt
│
├── antlr_parser/
│ ├── Simple.g4
│ ├── pruebas.py
│ ├── SimpleLexer.py
│ ├── SimpleParser.py
│ ├── (demas archivos generados por ANTLR)
``
- `cyk.py`: Implementacion del algoritmo CYK con complejidad O(n^3)
- `medir.py`: Script que ejecuta y compara ambos algoritmos
- `resultados.txt`: Archivo con los tiempos obtenidos
- `antlr_parser/`: Contiene la gramatica y el parser generado con ANTLR

---

### 2. Abrir la terminal
---

### 3. Navegar hasta la carpeta del programa
---

### 4. Ejecutar programa
`python3 medir.py`
Se ejecuta:
- El algoritmo CYK
- El parser generado con ANTLR
- Mide los tiempos de ejecucion para diferentes tamanos de entrada
---
### 5. Salida del programa
<img width="741" height="183" alt="image" src="https://github.com/user-attachments/assets/1e383a89-5f65-4cb1-a854-7b7fa7d2de12" />
- n es el tamano de la cadena
- CYK es el tiempo del algoritmo cubico
- ANTLR es el tiempo del parser lineal
---
### Analisis
### Algoritmo CYK

Entrada:
Cadenas generadas automaticamente de tipo a^n b^n

Resultado:
Se observa que el tiempo de ejecucion aumenta de forma acelerada a medida que crece el tamano de la cadena. Para valores pequenos de n el tiempo es bajo, pero al incrementar n, el tiempo crece de manera significativa

Analisis:
El algoritmo CYK construye una tabla bidimensional de tamano n x n, donde cada celda almacena posibles derivaciones. Para cada subcadena, evalua todas las particiones posibles, lo que implica un numero elevado de operaciones

Este comportamiento provoca que el tiempo de ejecucion no crezca de forma lineal ni cuadratica, sino cubica

Conclusion:
Los resultados experimentales confirman que CYK presenta una complejidad O(n^3), lo cual lo hace costoso para entradas grandes.

Imagen sugerida:
<img width="197" height="155" alt="image" src="https://github.com/user-attachments/assets/2404d2fe-d626-4741-8984-20e7d3b6d320" />


---

### Parser con ANTLR

Entrada:
Las mismas cadenas utilizadas en el algoritmo CYK

Resultado:
El tiempo de ejecucion se mantiene bajo y con variaciones minimas, incluso cuando el tamano de la entrada aumenta.

Analisis:
El parser generado con ANTLR utiliza tecnicas de analisis sintactico descendente optimizadas, basadas en estrategias tipo LL. Estas tecnicas permiten procesar la cadena en una sola pasada, sin necesidad de evaluar multiples particiones como en CYK.

Debido a esto, el numero de operaciones crece de forma proporcional al tamano de la entrada.

Conclusion:
El comportamiento observado es cercano a O(n), lo que hace que este tipo de parser sea eficiente y adecuado para aplicaciones reales.

Imagen sugerida:
<img width="209" height="157" alt="image" src="https://github.com/user-attachments/assets/3f2805b6-bf74-409d-80f9-be11d7b9d0f9" />

---

## Comparacion

Los resultados obtenidos permiten establecer una diferencia clara entre ambos enfoques de analisis sintactico:

- El algoritmo CYK son todas las posibles combinaciones de la cadena, lo que genera un crecimiento cubico en el tiempo de ejecucion
- El parser con ANTLR procesa la entrada de forma secuencial, lo que produce un crecimiento lineal

A medida que aumenta el tamano de la entrada, la diferencia entre ambos algoritmos se vuelve mas evidente. Mientras CYK incrementa rapidamente su tiempo de ejecucion, ANTLR mantiene tiempos bajos y estables.

Esto demuestra que, aunque CYK es un algoritmo mas general y aplicable a cualquier gramatica en forma normal de Chomsky, su costo computacional es considerablemente mayor en comparacion con parsers modernos.

Conclusion general:
Los resultados experimentales validan la teoria de complejidad, evidenciando que los parsers optimizados como ANTLR son significativamente mas eficientes que el algoritmo CYK para el analisis sintactico.










