## 11. Ejercicios

En este apartado, se realizarán 2 ejercicios sobre 2 circuitos, el primero es sobre contadores sincrónicos y el segundo es un cerrojo Set-Reset con compuertas NAND.


## Contadores sincrónicos
 El 74LS163 es un contador cargable sincrónico de 4 bits, con un reset sincrónico. Entonces se toma la siguiente imagen para armar el circuito:


<p align="center">
<img width="558" height="242" alt="image" src="https://github.com/user-attachments/assets/8c24ca7a-7b80-4ac5-a385-020d66c47e0c" />
</p>
<p align="center">
Fig 1. Contadores sincrónicos en cascada.
</p>

Lo primero que se hará es una simulación en multisim para verificar cual es la respueta que se está buscando y cual es el comportamiento de las ondas, para luego compararlo con la respuesta final obtenida en el osciloscopio.

### Simulación

En la siguiente imagen, se mostrar como se implemento el circuito en multisim: 

<p align="center">
<img width="802" height="431" alt="image" src="https://github.com/user-attachments/assets/754c1b16-1eff-48eb-8237-46b17f687a98" />
</p>
<p align="center">
Fig 2. Circuito de contadores sincrónicos en cascada en multisim.
</p>

En est caso se unos modelos de 74LS163 que no son necesarios conectarlos una fuente de alimentación y tierra para más comodidad en el simulador, como también poner el reloj en $1\mathrm{kHz}$
(en práctica si debe tomar en cuenta). El primer canal D0, tomará la señal del reloj, el segundo canal D1 sería la salida de QD del primer 74LS163, el tercer canal D2 sería la salida del QD del segundo 74LS163 y el cuarto canal D3 sería RCO del 74LS163 primer. En la siguiente imagen se obtiene el resultado obtenido de la simulación:

<p align="center">
<img width="931" height="526" alt="image" src="https://github.com/user-attachments/assets/083e10dd-319d-40e9-8aa9-e44291e32020" />
</p>
<p align="center">
Fig 3. Resultado del circuito de contadores sincrónicos en cascada en multisim.
</p>

Luego se explicará porque estos comportamientos coherentes y es lo que busca.

### Resultado obtenido en el Osciloscopio.

En la siguiente imagen se muestra lo que se obtuvo oscilospocio, donde los canales son los mismos que utilizaron en la simulación:

<p align="center">
<img width="1448" height="913" alt="image" src="https://github.com/user-attachments/assets/5ada5999-1b5d-480b-8175-de7032c9a687" />
</p>
<p align="center">
Fig 4. Resultado obtenido del osciloscopio  del circuito de contadores sincrónicos en cascada 
</p>

En la señal del Reloj (D0) es una onda cuadrada periodica que está aproximadamente de $1.79\mathrm{MHz}$, un valor cercano al que estaba solicitando.

La señal de salidoa QD del primer comtador (D1), presenta una frencuancia de $114.3\mathrm{kHz}$. Cumple con el funcionamiento del 74LS163, ya que cada salida divide progresivamente la frecuencia de entrada entre potencias de dos [1].

$$
f = \frac{f_{CLK}}{16}
$$ 

$$
f = \frac{1.79\mathrm{MHz}}{16}
$$ 

$$
f = 112\mathrm{kHz}
$$

Cercano al valor obtenido en el osciloscopio.

La señal de salida de QD del segundo contador (D2) es más lenta que le primer contador, esto se debe porque  este contador va incremnetar cuando el primer contador alcance $1111_2$ y la señal RCO habilita la entrada ENT, por lo que el segundo contador divide nuevamente la frecuencia, produciendo una señal considerablemente más lenta [1].

Por último la señal RCO del primer contador (D3), tiene pulsos estrechos, porque se debe que se actica cuando el contador alcance $1111_2$ y las entradas de habilitación están activas [1]. El 74LS163 incorpora lógica de carry look-ahead, que permite implementar conteos síncronicos de alta velocidad y evitando retardos acumalativos [1].

La razón de porque el RCO y T están conectados entre los dos contadores es para implementar una conexión en cascada entres ambos dipositivos [1]. Una expliación de como funciona que el primer contador incrementa su valor con cada flanco positivo del reloj, cuando alcanza $1111_2$, la salida RCO se activa, por lo habilita temporalmente la entrada T del segundo contador y en el siguinete flanco positivo del reloj, en el segundo contador imcrementa.

Si observamos la hoja de datos del 74LS163, tiene 2 entradas que serían T (ENT) y P (ENP) [1]. Lo que realiza la entreda P es habilitar el conteo interno del contador, para que eso pase debe estar en un nivel alto [2]. Para la entrada E que aparte de hablitar el conteo, también controla la generación de la señal RCO y por está razón se utiliza para la conexión en cascada entre contadores [1].

Para saber que uno flip-flops cambie estad, luego de un flanco positivo del reloj correponde al tiempo de propagación entre el flanco posoyivo del reloj y el cambio d eetados de las salidas Q [1]. En la hoja de datos del 74LS163, Su tiempo de progación del reloj es de una aproximación de $14\mathrm{ns}$ [1]. Este retardo se se puede debe a capacitacias parásitas, frecuancia de operción y carga conectada al circuito [3].

Por ultimo, se debe tomar la importacia de cuál bit de salida se escoja para el osciloscopio, porque cada una posee una frecuencia distinta, en la hoja de datos dice que QD va ser la frecuencia más baja [1].Por eso en este caso si utliza QD para facilitar la observación temporal de la señales.


## Cerrojo Set-Reset con compuertas NAND 

Este circuito corresponde un cerrojo SR sincronizado mendiante una señal de reloj y constituido con compuestas NAND. Este tipo de circuitos secuenciales tiene la capcidad de almacenar un bit de información utilizando realimentación entre las compuestas lógicas [4]. Se divide en dos etapas: 1. Habilitación mediante reloh¿j. 2. Etapa de memoria.

En la etapa de habilitación de reloj esta conformada por 2 NAND que recibe las señales de entradas S R y el reloj (CLK), sus salidas se pueden definir:

$$
X = (S \cdot CLK)'
$$

$$
Y = (R \cdot CLK)'
$$

En el caso que reloj este en bajo las salidas tomarán un valor alto, entonces el latch se bloequea y conserva el estado almacenado previamente sin importar los cambios de las entradas S y R [5]. En el  caso que el reloj este en alto, las entradas pueden modificar el estado del lacth [5].

En la etapa de memoria también hay 2 compuertas NAND están conectadas en  realimentación cruzada:

$$
Q = \overline{X \cdot\overline{Q}}
$$

$$
\overline{Q}  = \overline{Y\cdot Q}
$$

Esta realimenración permite que el circuito conserve el último esatdo almacenado aun cuando las entradas regresen a cero [5]. 

Si está en el caso que $S = 1$ , $R = 0$ y $CLK = 1$, es el estado de SET por lo que $Q = 1$ y $\overline{Q} = 0$.

Si está en el caso que $S = 0$ , $R = 0$ y $CLK = 1$, es el estado de HOLD por lo que $Q = 1$ y $\overline{Q} = 0$. Donde las salidas mantienen el mismo valor previo.

Si está en el caso que $S = 0$ , $R = 1$ y $CLK = 1$, es el estado de HOLD por lo que $Q = 0$ y $\overline{Q} = 1$.

Si está n el caso que $S = 1$ , $R = 1$ y $CLK = 1$, es el estado de inválido por lo que $Q = 1$ y $\overline{Q} = 1$. Se concidera inválido poruqe puede generar resultados impredecibles por los retardos internos de propagación [6]. 

Se toma la siguiente imagen para armar el circuito:

<p align="center">
<img width="490" height="268" alt="image" src="https://github.com/user-attachments/assets/d6e73ada-4fc1-45a4-80a2-939b480fc2ad" />
</p>
<p align="center">
Fig 5. Circuito de prueba de un cerrojo SR.
</p>

Se hará lo mismo que el ejericio anterior, una simulación en multisim para verificar cual es la respueta que se está buscando y cual es el comportamiento de las ondas, para luego compararlo con la respuesta final obtenida en el osciloscopio y también ver si cumple con teoría antes establecida.

### Simulación

En la siguiente imagen, se mostrar como se implemento el circuito en multisim: 

<p align="center">
<img width="1293" height="527" alt="image" src="https://github.com/user-attachments/assets/721d9d95-3c3f-4e5c-adc3-526c2ede9291" />
</p>
<p align="center">
Fig 6. Circuito de prueba de un cerrojo SR en multisim. 
</p>

En este caso en el simulador se está utilizando un 74LS00D al no tener un 74CHOO en el simulador, sin embargo es una opción alternativa al tener las mismas funciones. También se utiliza un reloj en $1\mathrm{kHz}$ para más comodidad. El primer canal D0 tomará la señal del reloj, el segundo canal D1 tomará la señal de S, el tercer canal D2 será R, el cuarto canal D3 sera la salida de Q y el quinto canal será la salida de Q'.

En la siguientes imagenes se observarán los resultados de cada caso en la simulación:

Caso S = 1 y R = 0:

<p align="center">
<img width="938" height="528" alt="image" src="https://github.com/user-attachments/assets/64b598ba-b902-4151-ae85-30a181ccbf7d" />
</p>
<p align="center">
Fig 7. Resultado de la simulación del cerrojo de S = 1 y R = 0.
</p>


Caso S = 0 y R = 0:

<p align="center">
<img width="937" height="530" alt="image" src="https://github.com/user-attachments/assets/6e94f315-b868-4cce-af54-1def613924b7" />
</p>
<p align="center">
Fig 8. Resultado de la simulación del cerrojo de S = 0 y R = 0.
</p>


Caso S = 0 y R = 1:

<p align="center">
<img width="935" height="528" alt="image" src="https://github.com/user-attachments/assets/a871bd51-ed33-42f0-a4a8-e81903101ca8" />
</p>
<p align="center">
Fig 9. Resultado de la simulación del cerrojo de S = 0 y R = 1.
</p>


Caso S = 1 y R = 1:

<p align="center">
<img width="947" height="531" alt="image" src="https://github.com/user-attachments/assets/30a0a1a5-801e-49ef-b542-85d9d5174684" />
</p>
<p align="center">
Fig 9. Resultado de la simulación del cerrojo de S = 1 y R = 1.
</p>

### Resultado obtenido en el Osciloscopio.

En la siguienteS imagenes se muestra lo que se obtuvo oscilospocio, donde los canales son los mismos que utilizaron en la simulación:

Caso S = 1 y R = 0:

<p align="center">
<img width="1442" height="915" alt="image" src="https://github.com/user-attachments/assets/f9b02e79-d5f0-45ea-b805-1de91f54ecd6" />
</p>
<p align="center">
Fig 10. Resultado del osciloscopio del cerrojo de S = 1 y R = 0.
</p>


Caso S = 0 y R = 0:

<p align="center">
<img width="1447" height="912" alt="image" src="https://github.com/user-attachments/assets/93a89553-1d8f-4d23-afac-92a507a8b2ce" />
</p>
<p align="center">
Fig 11. Resultado del osciloscopio del cerrojo de S = 0 y R = 0.
</p>

Caso S = 0 y R = 1:

<p align="center">
 <img width="1446" height="917" alt="image" src="https://github.com/user-attachments/assets/d4e85903-c24c-4963-87e4-bfb46fce46c2" />
</p>
<p align="center">
Fig 12. Resultado del osciloscopio del cerrojo de S = 0 y R = 1.
</p>

Caso S = 1 y R = 1:

<p align="center">
<img width="1446" height="922" alt="image" src="https://github.com/user-attachments/assets/df4b9392-09ed-4a58-a97d-fb199a03dedd" />
</p>
<p align="center">
Fig 9. Resultado del osciloscopio del cerrojo de S = 1 y R = 1.
</p>

Como puede observar los resultados cumplen lo establecido anteriormente y también es similar a lo obtenido en la simulación.

Su tabla de verdad es la siguiente:

<p align="center">
Tabla 1. Tabla de verdad del cerrojo.
</p>

<p align="center">
<img width="753" height="157" alt="image" src="https://github.com/user-attachments/assets/aa5df3d7-967b-43c0-b6a4-416bea4fbaae" />
</p>



## Referencias bibliográficas

[1] Fairchild Semiconductor, “DM74LS163A Synchronous 4-Bit Binary Counters,” Datasheet, 2000.

[2] Datasheet Hub, “74LS163 Fully Synchronous 4-Bit Counter,” 2023. [Online]. Available: https://www.datasheethub.com/74ls163-fully-synchronous-4-bit-counter/

[3] ON Semiconductor, “74LS163 Binary Counter Datasheet,” Datasheet, 2004.

[4] C. Garaipoom, “SR Latch Explained: Circuit Variants, Truth Table, and Operation,” ElecCircuit, Feb. 2026. [Online]. Available: https://www.eleccircuit.com/how-sr-latch-works/

[5] “SR Latch Circuit,” ChipVerify. [Online]. Available: https://www.chipverify.com/digital-fundamentals/sr-latch-circuit

[6] SR NAND latch,” Electronics-Course. [Online]. Available: https://electronics-course.com/sr-nand-latch
