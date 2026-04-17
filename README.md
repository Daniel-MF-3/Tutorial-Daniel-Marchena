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
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/06817f65-9fa0-49f1-a435-d3d8ae090568" />
</p>
<p align="center">
Fig. 2. Ensamblaje del oscilador de anillo de 5 inversores.
</p>



<p align="center">
<img width="800" height="503" alt="image" src="https://github.com/user-attachments/assets/945ee588-f068-416f-a128-beb131284762" />
</p>
<p align="center">
Fig. 3. Onda obtenida del osciloscopio del oscilador de anillo de 5 inversores.
</p>

Como se puede observar la onda es lo esperado y los datos como la frecuencia de $10.7\mathrm{MHz}$ y el período de $94\mathrm{ns}$ son similares a los teóricos. Una de la razones de porque los valores teoricos y los experimentales no son iguales se debe a las varaciones en las codiciones de carga, capacitancias parásitas y efectos de interconexion, lo cual puede afectar el tiempo de propagación efectivo [3]. Al final se queda con tiempo de retraso de $9.4\mathrm{ns}$

### Caso de 3 inversores
Primero se mostrára la imagen del circuito en una protoboard y luego la onda que se consiguio en el osciloscopio:

<p align="center">
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/efeed98c-3ce8-46bb-8995-d4fa2ad2a9c2" />
</p>
<p align="center">
Fig. 4. Ensamblaje del oscilador de anillo de 3 inversores.
</p>


<p align="center">
<img width="800" height="503" alt="in3m" src="https://github.com/user-attachments/assets/09e18a67-7c96-4fc0-a18a-bf20551121fa" />
</p>
<p align="center">
Fig. 5. Onda obtenida del osciloscopio del oscilador de anillo de 3 inversores.
</p>

La onda se mantiene cuadrada, y los valores teoricos se acercan a lo esparado. La razón porque no son exactos, pasa lo mismo que el caso anterior. Sin embargo, se debe tomar en cuenta que al reducir el número de inversores, el período de oscilación baja proporcionalmente, ya que depende del número de inversores en uso y también aumenta la frecuencia [3]. Al final se queda con tiempo de retraso de $9.3\mathrm{ns}$

### Caso de 3 inversores con cable de un metro

Primero se mostrára la imagen del circuito en una protoboard y luego la onda que se consiguio en el osciloscopio:

<p align="center">
<img width="1599" height="741" alt="image" src="https://github.com/user-attachments/assets/d944e342-f436-4312-9dbd-0b61c478e580" />
<p align="center">
Fig. 6. Ensamblaje del oscilador de anillo de 3 inversores con un cable un metro.
</p>


<p align="center">
<img width="800" height="503" alt="in3ma" src="https://github.com/user-attachments/assets/372317cf-fbd1-48be-ab70-ae83ef59d950" />
</p>
<p align="center">
Fig. 7. Onda obtenida del osciloscopio del oscilador de anillo de 3 inversores con cable un metro.
</p>

Curiosamente con el cable de un metro da mejores resultados que uno normal, sin embargo es no quiere decir que con cable se soluciona los errores del caso anterior. Se debe que el cable proporciona un retardo adicional que reduce la frecuencia de oscilación y también afecta la estabilidad [4].

### Caso de 1 inversor

Primero se mostrára la imagen del circuito en una protoboard y luego la onda que se consiguio en el osciloscopio:

<p align="center">
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/04d68d36-890f-4f1c-952c-c5847670702d" />
Fig. 8. Ensamblaje del oscilador de anillo de 3 inversores con un cable un metro.
</p>


<p align="center">
<img width="800" height="503" alt="image" src="https://github.com/user-attachments/assets/f1e2bad2-f828-443f-9272-d83b7a63ac71" />

<p align="center">
Fig. 9. Onda obtenida del osciloscopio del oscilador de anillo de 3 inversores con cable un metro.
</p>

Resultados simalares a los teóricos y una onda cuadrada. Sin embargo un oscilador de anillo requiere un número impar mayor que uno de inversores para oscilar. Con un solo inversor, el sistema debería estabilizarse en un estado lógico fijo [3]. Estas oscilaciones no son estables ni confiables y suelen presentar frecuencias elevadas, como la observada experimentalmente [5].

[1] J. M. Rabaey, A. Chandrakasan and B. Nikolić, Digital Integrated Circuits: A Design Perspective, 2nd ed. Upper Saddle River, NJ, USA: Prentice Hall, 2003.

[2] Texas Instruments, “SN74LS04 Hex Inverters Datasheet”, 2016.

[3] J. M. Rabaey, A. Chandrakasan and B. Nikolić, Digital Integrated Circuits: A Design Perspective, 2nd ed. Upper Saddle River, NJ, USA: Prentice Hall, 2003.

[4] N. H. E. Weste and D. Harris, CMOS VLSI Design: A Circuits and Systems Perspective, 4th ed. Boston, MA, USA: Pearson, 2011.

[5] P. Horowitz and W. Hill, The Art of Electronics, 3rd ed. Cambridge, U.K.: Cambridge University Press, 2015.
