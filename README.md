## 5. Oscilador de Anillo


Un oscilador de anillo es un circuito que está compuesto por un número impar de inversores conectados en cascada que forman un lazo cerrado, por lo que cada salida del último inversor se retroalimenta a la entrada del primero [1]. Debido que el retardo de propagación finito de cada inversor, la señal no puede estabilizarse en un estado lógico fijo, lo que provoca una oscilación continua entre niveles alto y bajo [1].

En apartado se experimentara varios casos con 5 inversores, 3 inversores, 3 inversores con cable aproximadamente un 1 metro y 1 inversor. Primero se calcularán los valores teoricos para luego compararlo con los valores obtenidos en osciloscopio en laboratorio.

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

<img width="799" height="399" alt="image" src="https://github.com/user-attachments/assets/767b9c15-f845-4348-a139-e8374581f801" />
<p align="center">
1. Ensamblaje del oscilador de anillo de 5 inversores 
</p>




[1] J. M. Rabaey, A. Chandrakasan and B. Nikolić, Digital Integrated Circuits: A Design Perspective, 2nd ed. Upper Saddle River, NJ, USA: Prentice Hall, 2003.

[2] Texas Instruments, “SN74LS04 Hex Inverters Datasheet”, 2016.
