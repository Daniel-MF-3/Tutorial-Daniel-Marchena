## 5. Oscilador de Anillo


Un oscilador de anillo es un circuito que está compuesto por un número impar de inversores conectados en cascada que forman un lazo cerrado, por lo que cada salida del último inversor se retroalimenta a la entrada del primero [1]. Debido que el retardo de propagación finito de cada inversor, la señal no puede estabilizarse en un estado lógico fijo, lo que provoca una oscilación continua entre niveles alto y bajo [1].

En apartado se experimentara varios casos con 5 inversores, 3 inversores, 3 inversores con cable aproximadamente un 1 metro y 1 inversor. Primero se calcularán los valores teoricos para luego compararlo con los valores obtenidos en osciloscopio en laboratorio. En la siguiente imagen, se vera como se debe construir un oscilador de anillo:

<p align="center">
<img width="515" height="107" alt="image" src="https://github.com/user-attachments/assets/eb3dcf77-0a43-4b77-a648-a8087c9102f7" />
</p>
<p align="center">
Oscilador de anillo basado en 74LS04.
</p>


## Valores teoricos.

Se desmostrarán los calculos del periodo y frecuencia. Según la hoja de datos, un el inversor **74LS04** tiene como $t_d \approx 10\mathrm{ns}$ [2]. Con este dato se puede aplicar la siguiente formula:

$$
T= 2\times n \times t_d 
$$

Donde:

$T$ = Periodo
$n$ = número de inversores 
$t_d$ = tiempo de retardo de un inversor
<

Al obtener el periodo se puede obtener la frecuencia : 

$$
f = \frac{1}{T}
$$ 

### Caso de 5 inversores

El periodo: 

$$
T= 2\times 5 \times 10\mathrm{ns}
$$

$$
T= 100\mathrm{ns}
$$ 

Frecuencia:

$$
f = \frac{1}{100\mathrm{ns}}
$$
$$
f = 10\mathrm{MHz}
$$

### Caso de 3 inversores

El periodo: 

$$
T= 2\times 3 \times 10\mathrm{ns}
$$
$$
T= 60\mathrm{ns}
$$


Frecuencia:

$$
f = \frac{1}{60\mathrm{ns}}
$$
$$
f = 16.7\mathrm{MHz}
$$

El caso de 1 metro de cable no cambia a ser estos valores ideales, por lo que sería lo mismo que el caso de 3 inversores.

### Caso de 1 inversor

El periodo: 

$$
T= 2\times 1 \times 10\mathrm{ns}
$$
$$
T= 20\mathrm{ns}
$$


Frecuencia:

$$
f = \frac{1}{20\mathrm{ns}}
$$
$$
f = 50\mathrm{MHz}
$$


## Experimentos

Está parte se mostraran las imagenes de las ondas y datos que se obtuvieron del osciloscopio en cada caso y comparalos con los valores teoricos.

### Caso de 5 inversores

Primero se mostrára la imagen del circuito en una protoboard y luego la onda que se consiguio en el osciloscopio:
<p align="center">
<img width="799" height="399" alt="image" src="https://github.com/user-attachments/assets/767b9c15-f845-4348-a139-e8374581f801" />
</p>
<p align="center">
Fig. 2. Ensamblaje del oscilador de anillo de 5 inversores.
</p>



<p align="center">
<img width="800" height="480" alt="l3" src="https://github.com/user-attachments/assets/3b14d5c4-bab7-42e7-8148-f14ab5c4c57b" />
</p>
<p align="center">
Fig. 3. Onda obtenida del osciloscopio del oscilador de anillo de 5 inversores.
</p>

Como se puede observar la onda no es lo esperado, sin embargo los datos como la frecuencia $10.1\mathrm{MHz}$ y el periodo $T= 95\mathrm{ns}$ son similares a los teóricos. Una de las razones porque hay distorción y ruido son por las características no ideales de los inevrsores TTL [2]. Los tiempos de propagación de los inversores no son constantes y hay diferentes transiciones entre la subida y bajada, por lo que genera deformaciones [2]. También se debe el modelo 74ls04 se introduce ruido interno debido a sus corrientes de comutación y acoplamientos internos que afecatan la estabilidad de la señal de salida [3] 


[1] J. M. Rabaey, A. Chandrakasan and B. Nikolić, Digital Integrated Circuits: A Design Perspective, 2nd ed. Upper Saddle River, NJ, USA: Prentice Hall, 2003.
[2] Texas Instruments, “SN74LS04 Hex Inverters Datasheet”, 2016.
[3] P. Horowitz and W. Hill, The Art of Electronics, 3rd ed. Cambridge, U.K.: Cambridge University Press, 2015.
[2] Texas Instruments, “SN74LS04 Hex Inverters Datasheet”, 2016.
