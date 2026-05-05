# Parcial 2
- Sergio Esteban Alarcón Valbuena

## 1. Parte conceptual
### La diferencia entre un latch y un flip flop
Un latch es un dispositivo de almacenamiento que cambia su salida de manera inmediata cuando cambian sus entradas, es decir, es sensible al nivel de la señal de control. En cambio, un flip-flop es un dispositivo síncrono que solo cambia su estado en un instante específico, generalmente en el flanco de subida o bajada de una señal de reloj. Por esta razón, los flip-flops son más utilizados en sistemas digitales secuenciales controlados por reloj, ya que ofrecen mayor estabilidad y control.

### Tipos de latch y flip flops.
#### Tipos de latch
<img width="504" height="249" alt="image" src="https://github.com/user-attachments/assets/86040039-d25d-4020-bb18-e7ce51d5e277" />

1. SR Latch (Set-Reset)
Entradas: S (Set) y R (Reset)
Funcionamiento:
- S = 1, R = 0 → Q = 1
- S = 0, R = 1 → Q = 0
- S = 0, R = 0 → mantiene estado
- S = 1, R = 1 → estado inválido

2. D Latch (Data Latch)
- Entrada: D (dato) + señal de habilitación
- Evita el estado inválido del SR.

Cuando está habilitado:
- Q = D

Cuando no:
- Mantiene el valor

#### Tipos de Flip-Flop
<img width="474" height="108" alt="image" src="https://github.com/user-attachments/assets/2b89bb75-83e0-441e-a5e3-bcfa522d5848" />

1. SR Flip-Flop
- Igual al latch SR pero controlado por reloj.
- Cambia solo en el flanco del reloj.
- Problema: estado inválido (S=R=1).

2. D Flip-Flop
- Entrada: D
- Salida sigue a D en el flanco del reloj.
- Muy usado en registros.

3. JK Flip-Flop
- Mejora del SR.
- Entradas: J y K

Funcionamiento:
- J=0, K=0 → mantiene
- J=1, K=0 → pone 1
- J=0, K=1 → pone 0
- J=1, K=1 → cambia (toggle)

4. T Flip-Flop (Toggle)
- Entrada: T
- Si T = 1 → cambia estado
- Si T = 0 → mantiene estado
- Muy usado en contadores

### Diferencia entre un multiplexor y un demultiplexor
Un multiplexor (MUX) es un circuito que permite seleccionar una de varias entradas y enviarla a una única salida, dependiendo de las líneas de selección. Por otro lado, un demultiplexor (DEMUX) realiza la función inversa: toma una sola entrada y la dirige hacia una de varias salidas, también según las líneas de selección. En resumen, el multiplexor concentra señales y el demultiplexor las distribuye.

### Qué es un sumador completo
Un sumador completo es un circuito digital que realiza la suma de tres bits: dos bits principales y un acarreo de entrada. Como resultado, genera dos salidas: la suma y el acarreo de salida. Este tipo de sumador es fundamental en sistemas digitales porque permite realizar operaciones aritméticas más complejas al encadenar varios sumadores completos.

### Qué es un mapa de karnaugh
Un mapa de Karnaugh es una herramienta gráfica utilizada para simplificar funciones booleanas. Consiste en una tabla organizada de manera que facilita la agrupación de términos semejantes. Su principal objetivo es reducir la cantidad de compuertas lógicas necesarias en un circuito, lo que permite diseñar sistemas más eficientes, económicos y fáciles de implementar.


## 2. Parte de Diseño
### 2.a  $X = \left[ A \overline{B} \left( (C + BD) + \overline{A}\,\overline{B} \right) \right] C$

- 1. Simplificacion:

Observa que toda la expresión está multiplicada por $C$:

$$
X = A \cdot \overline{B} \cdot C \left( C + BD + \overline{A}\cdot \overline{B} \right)
$$

Aplicamos propiedad booleana:

$$
C(C + \text{algo}) = C
$$

Entonces:

$$
X = A \cdot \overline{B} \cdot C
$$

- 2. Tabla de Verdad
Variables :A, B y C

| A | B | C | X = A·B̅·C |
| - | - | - | ---------- |
| 0 | 0 | 0 | 0          |
| 0 | 0 | 1 | 0          |
| 0 | 1 | 0 | 0          |
| 0 | 1 | 1 | 0          |
| 1 | 0 | 0 | 0          |
| 1 | 0 | 1 | 1          |
| 1 | 1 | 0 | 0          |
| 1 | 1 | 1 | 0          |

- 3. Circuito logico
<img width="1652" height="356" alt="punto 2a" src="https://github.com/user-attachments/assets/d5f2a88c-fe37-4188-a492-43d47ffc03a9" />

### 2.b  $$X = A \cdot \overline{B}C \cdot BD + CDE + AC$$

1.  Simplificación

Observa el primer término:

$$
A \cdot \overline{B}C \cdot BD
$$

Aquí aparece:

$$
\overline{B} \cdot B = 0
$$

Entonces todo ese término es:

$$
0
$$

- Sustituyendo:

$$
X = 0 + CDE + AC
$$

$$
X = CDE + AC
$$

- Factor común:

$$
X = C(DE + A)
$$

- Resultado simplificado final:

$$
X = C(A + DE)
$$

2. Tabla de verdad

Variables: A, B, C, D, E

| A | B | C | D | E | X |
| - | - | - | - | - | - |
| 0 | - | 0 | 0 | 0 | 0 |
| 0 | - | 0 | 0 | 1 | 0 |
| 0 | - | 0 | 1 | 0 | 0 |
| 0 | - | 0 | 1 | 1 | 0 |
| 0 | - | 1 | 0 | 0 | 0 |
| 0 | - | 1 | 0 | 1 | 0 |
| 0 | - | 1 | 1 | 0 | 0 |
| 0 | - | 1 | 1 | 1 | 1 |
| 1 | - | 0 | 0 | 0 | 0 |
| 1 | - | 0 | 0 | 1 | 0 |
| 1 | - | 0 | 1 | 0 | 0 |
| 1 | - | 0 | 1 | 1 | 0 |
| 1 | - | 1 | 0 | 0 | 1 |
| 1 | - | 1 | 0 | 1 | 1 |
| 1 | - | 1 | 1 | 0 | 1 |
| 1 | - | 1 | 1 | 1 | 1 |

3. Circuito logico
<img width="1780" height="548" alt="punto 2b" src="https://github.com/user-attachments/assets/3e9573bc-94dc-4d5f-a786-f8eb36beec76" />


## 3. Parte Empirica
ChatBot: https://colab.research.google.com/drive/1IprHP06nufNmR9BlaXISgPNGTsDuoUMY?usp=sharing
### Descripcion del proyecto
Este proyecto consiste en el desarrollo de un chatbot interactivo enfocado en el análisis de los sistemas digitales y la industria de los semiconductores en el año 2026. El objetivo principal es proporcionar respuestas claras, estructuradas y educativas sobre temas clave vistos en clase, integrando tanto conocimientos teóricos como tendencias actuales del sector tecnológico.

<img width="1703" height="217" alt="image" src="https://github.com/user-attachments/assets/f3a6a247-b988-4696-81c9-d9cfc678182f" />

El chatbot fue diseñado para funcionar en un entorno interactivo, permitiendo al usuario realizar preguntas relacionadas con electrónica digital, lógica booleana, circuitos secuenciales y el impacto de los semiconductores en la tecnología moderna.

Funcionamiento del chatbot

El sistema opera mediante dos mecanismos principales:

Respuestas locales:
El chatbot contiene una base de conocimientos interna con definiciones y explicaciones sobre temas fundamentales como compuertas lógicas, flip-flops, mapas de Karnaugh y contadores.
Integración con API:
Para preguntas más complejas o relacionadas con el contexto actual (como semiconductores en 2026, empresas tecnológicas o tendencias futuras), el chatbot utiliza una API externa que permite generar respuestas más avanzadas y actualizadas.

Además, el sistema incluye un filtro de validación que asegura que las preguntas estén relacionadas con temas de sistemas digitales, evitando respuestas fuera del contexto del proyecto.

### Temáticas abordadas
El chatbot está diseñado para responder sobre los siguientes temas:

Sistemas digitales y lógica booleana
Compuertas lógicas (AND, OR, XOR, etc.)
Flip-flops y circuitos secuenciales
Mapas de Karnaugh
Multiplexores y demultiplexores
Contadores y registros
Semiconductores en el contexto actual (2026)
Empresas líderes del sector tecnológico
Innovación en la educación
Proyectos tecnológicos educativos
Futuro de los sistemas digitales

### Semiconductores y sistemas digitales en 2026

El chatbot analiza cómo la industria de los semiconductores se ha convertido en un pilar fundamental del desarrollo tecnológico. Se destacan avances como la fabricación de chips de alta eficiencia, el crecimiento de la inteligencia artificial y la optimización del rendimiento en sistemas digitales.

También se establece la relación entre estos avances y su impacto en áreas como la computación, la automatización y los sistemas embebidos.

### Empresas relevantes del sector
El sistema identifica y analiza el papel de empresas líderes en la industria, explicando su impacto en el desarrollo de los sistemas digitales. Estas compañías impulsan la innovación tecnológica mediante el diseño y fabricación de procesadores, memorias y soluciones avanzadas.

### Aplicación en la educación
El chatbot incluye respuestas orientadas a la educación, destacando:

Innovación en el aprendizaje mediante herramientas digitales
Uso de simuladores y plataformas interactivas
Desarrollo de proyectos prácticos con tecnologías como microcontroladores

Esto permite evidenciar cómo los sistemas digitales están transformando la enseñanza y facilitando el aprendizaje técnico.

### Proyección futura
Finalmente, el chatbot aborda el futuro de los sistemas digitales, resaltando tendencias como:

Inteligencia artificial
Internet de las Cosas (IoT)
Computación avanzada
Nuevas arquitecturas de hardware

Estos elementos reflejan la importancia de los sistemas digitales en la evolución tecnológica global.

### Conclusión

El desarrollo de este chatbot permite integrar conocimientos teóricos con aplicaciones prácticas, facilitando la comprensión de los sistemas digitales y su relación con la industria de los semiconductores. Además, demuestra el uso de herramientas modernas como APIs para enriquecer la interacción y mejorar la calidad de las respuestas.
