## 5. Ejercicios

En este aparrado, se realizarán 2 ejercicios sobre 2 circuitos, el primero es sobre contadores sincrónicos y el segundo es un cerrojo Set-Reset con compuertas NAND.


## Contadores sincrónicos
 El 74LS163 es un contador cargable sincrónico de 4 bits, con un reset sincrónico. Entonces se toma la siguiente imagen para armar el circuito:


<p align="center">
<img width="558" height="242" alt="image" src="https://github.com/user-attachments/assets/8c24ca7a-7b80-4ac5-a385-020d66c47e0c" />
</p>
<p align="center">
Fig 1. Contadores sincrónicos en cascada.
</p>

Lo primero que se hará es una simulación en multisim para verificar cual es la respueta que se está buscando y cual es el comportamientos de las ondas, para luego compararlo con la respuesta final obtenida en el osciloscopio.

### Simulación

En la siguiente imagen, se mostrar como se implemento el circuito en multisim: 

<p align="center">
<img width="802" height="431" alt="image" src="https://github.com/user-attachments/assets/754c1b16-1eff-48eb-8237-46b17f687a98" />
</p>
<p align="center">
Fig 2. Circuito de contadores sincrónicos en cascada en multisim.
</p>

En est caso se unos modelos de 74LS163 que no son necesarios conectarlos una fuente de alimentación y tierra para más comodidad en el simulador, como tambén poner el reloj en $1\mathrm{kHz}$
(en práctica si debe tomar en cuenta). El primer canal D0, tomará la señal del reloj, el segundo canal D1 sería la salida de QD del primer 74LS163, el tercer canal D2 sería la salida del QD del segundo 74LS163 y el cuarto canal D3 sería RCO del 74LS163 primer. En la siguiente imagen se obtiene el resultado obtenido de la simulación:

<p align="center">
<img width="931" height="526" alt="image" src="https://github.com/user-attachments/assets/083e10dd-319d-40e9-8aa9-e44291e32020" />
</p>
<p align="center">
Fig 3. Resultado del circuito de contadores sincrónicos en cascada en multisim.
</p>

Luego se explicará porque estos comportamientos coherentes y es lo que busca.

### Resultado obtenido en el Osciloscopio.

En la siguiente imagen se muestra lo que se obtuvo oscilospocio, donde los canales son los mismo que utilizaron en la simualción:

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

Por último la señal RCO del primer contador (D3), tiene pulsos estrechos, porque se debe que se actica cuando el contador alcance $1111_2$ y las entradas de habilitación están activas [1].

[1] Fairchild Semiconductor, “DM74LS163A Synchronous 4-Bit Binary Counters,” Datasheet, 2000.

[2] 

[3] 
[4] 

[5] 
