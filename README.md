# Laboratorio-5-procesamiento
En el presente laboratorio se realizó el procesamiento y análisis de una señal electrocardiográfica (ECG) con el propósito de estudiar la variabilidad de la frecuencia cardíaca (HRV) y comprender cómo cambia la actividad del sistema nervioso autónomo en diferentes condiciones fisiológicas. Para ello, se trabajó con una señal ECG de cuatro minutos de duración, la cual fue filtrada mediante un filtro IIR pasa banda de 1–40 Hz y un filtro Notch de 60 Hz, con el fin de eliminar el ruido muscular y la interferencia eléctrica.  

Posteriormente, la señal filtrada se dividió en dos segmentos: los primeros dos minutos durante los cuales la persona se encontraba en reposo y los siguientes dos minutos correspondientes a la lectura en voz alta. En cada segmento se identificaron los picos R mediante técnicas de detección basadas en las características morfológicas del ECG, y se calcularon los intervalos R-R, los cuales constituyen la base para el análisis de la HRV.     

Asimismo, se construyó el diagrama de Poincaré para cada segmento, del cual se obtuvieron los índices SD1, SD2, CVI y CSI, los cuales permiten evaluar de manera separada la actividad parasimpática y simpática del sistema nervioso autónomo. Este análisis permitió comparar de manera cuantitativa y visual cómo la carga cognitiva durante la lectura modifica el ritmo cardíaco y su variabilidad.  

## Diagrama de flujo  
Como primera etapa, se elaboró un diagrama de flujo que permitió estructurar tanto la programación como el procedimiento general del análisis. Esta herramienta facilitó la organización lógica de las tareas, definiendo el orden de ejecución, las funciones necesarias y los criterios de procesamiento aplicados.

<img width="1280" height="863" alt="image" src="https://github.com/user-attachments/assets/ea38eaa8-b10e-4b6a-acff-06e5cacaa77a" />



# PARTE A  

## a. Fundamento teórico 


### -Actividad simpática y parasimpática del sistema nervioso autónomo.

El corazón no late por sí solo; su funcionamiento es dependiente del sistema nervioso autónomo. Este sistema tiene dos partes que actúan como un acelerador y un freno.

Primero, la parte simpática es la que se activa cuando el cuerpo necesita una reacción rápida: como situaciones de estrés, ejercicio, o cualquier estímulo que necesite más energía de lo normal. Cuando el simpático aumenta su actividad, el corazón late más rápido, la presión sube y el cuerpo se prepara para dar una respuesta al estímulo.

Por otro lado, el sistema parasimpático hace todo lo contrario. Está más presente en momentos de calma, descanso o relajación. Su respuesta disminuye la frecuencia cardíaca y genera un ritmo más flexible. La parte parasimpática actúa inicialmente por medio del nervio vago que tiene una influencia muy marcada sobre el control fino del ritmo cardíaco. (Berntson et al., 1997)

Estas dos partes están activas todo el tiempo y se van equilibrando según lo que el cuerpo necesite en cada momento.


### -Efecto de la actividad simpática y parasimpática en la frecuencia cardíaca.

El nodo sinusal, que es el marcapasos natural del corazón, responde a la combinación del simpático y del parasimpático.
Cuando domina el simpático, el nodo sinusal se despolariza más rápido y por eso la frecuencia cardíaca aumenta. Además, el ritmo tiende a volverse más uniforme, con menos variación entre un latido y otro.
Cuando domina el parasimpático, la despolarización del nodo sinusal se hace más lenta. Esto baja la frecuencia cardíaca y genera más variación entre latidos consecutivos. Es por eso que, en reposo, la frecuencia cardíaca suele ser más irregular pero de forma saludable. (Berntson et al., 1997)

En pocas palabras:
más simpático = corazón rápido y menos variable

más parasimpático = corazón lento y más variable.



### -Variabilidad de la frecuencia cardíaca (HRV) obtenida a partir de la señal electrocardiográfica (ECG).

La variabilidad de la frecuencia cardíaca  mide qué tanto cambia el tiempo entre un latido y el siguiente. Para obtenerla, se toma la señal ECG, se localizan los picos R de cada complejo QRS y se calcula cuánto tiempo pasa entre un R y el siguiente. Esta secuencia de intervalos es la que se usa para analizar la variabilidad de la frecuencia cardiaca.

La variabilidad de la frecuencia cardiaca no es ruido ni error, es una característica normal del corazón sano. Un organismo que se adapta bien a los estímulos suele tener una variabilidad de la frecuencia cardiaca más alta, porque el parasimpático puede modular el ritmo con rapidez. Por el contrario, cuando predomina el simpático o hay estrés físico o emocional, la variabilidad de la frecuencia cardiaca tiende a disminuir ya que el ritmo se vuelve más rígido.(Laborde, Mosley & Thayer, 2017)

En la práctica de laboratorio, comparar los intervalos R-R en reposo y durante la lectura en voz alta permite observar cómo cambia el balance autonómico entre una actividad tranquila y otra que exige más control respiratorio y cognitivo.


### -Diagrama de Poincaré como herramienta de análisis de la serie R-R. Variabilidad de la frecuencia cardíaca (HRV) y balance autonómico 
  
El diagrama de Poincaré es una forma visual de entender cómo está variando la frecuencia cardíaca de un latido al siguiente. Para crearlo, se toma cada intervalo R-R de la señal ECG y se compara con el que viene justo después; es decir, se grafica 𝑅𝑅𝑛 en el eje horizontal y
𝑅𝑅𝑛+1 en el vertical. Lo que se obtiene es una nube de puntos que describe el “comportamiento” del ritmo cardíaco.

La forma de esa nube dice mucho sobre el estado del sistema nervioso autónomo.

Cuando los puntos se dispersan de manera amplia y un poco redonda, significa que el ritmo cardíaco cambia bastante entre un latido y otro. Eso suele interpretarse como un mayor predominio parasimpático, ya que el sistema vagal introduce variaciones rápidas en el ritmo.(Tulppo et al., 1996)

En cambio, cuando los puntos se alinean en una forma más alargada y estrecha, la variación entre latidos disminuye. Esto se relaciona con un aumento del tono simpático, que vuelve el ritmo más rígido y más rápido.

Además de lo visual, del diagrama se obtienen medidas como SD1 (que refleja la variabilidad a corto plazo, relacionada con el parasimpático) y SD2 (que representa la variabilidad a largo plazo, más influenciada por mecanismos simpáticos). Estas dos medidas permiten calcular otros índices, como el CVI y el CSI, que ayudan a expresar de manera numérica la relación entre ambas ramas del sistema autónomo.

En resumen, el diagrama de Poincaré convierte los intervalos R-R en una representación muy intuitiva, donde la forma de la nube de puntos revela si el corazón está bajo una influencia más relajada (parasimpática) o más activada (simpática).


La variabilidad de la frecuencia cardíaca, o HRV, se refiere a los cambios naturales que existen entre un latido y el siguiente. Aunque solemos pensar que el corazón late como un metrónomo, en realidad los intervalos entre latidos siempre están cambiando. Esa variación no es un error: es una señal importante del estado del sistema nervioso autónomo.(Thayer et al., 2012)

Cuando la actividad parasimpática predomina (por ejemplo, en reposo, respiración tranquila o relajación), la frecuencia cardíaca se vuelve más variable. Los intervalos R-R aumentan y disminuyen de forma más libre, lo cual indica que el cuerpo tiene buena capacidad de adaptación fisiológica.

Por el contrario, cuando la actividad simpática aumenta (como durante estrés, esfuerzo o una actividad que exige concentración), los intervalos R-R se parecen más entre sí y la variabilidad disminuye. Esto ocurre porque el simpático tiende a acelerar y estabilizar el ritmo para preparar al cuerpo ante una demanda mayor.

Por esa razón, la HRV se utiliza como una herramienta para evaluar el balance autonómico:

HRV alta = más control vagal = organismo en un estado flexible y tranquilo.

HRV baja = más control simpático = organismo en alerta o en mayor exigencia.

En el contexto del laboratorio, comparar la HRV durante los primeros dos minutos (reposo) con la HRV de los dos minutos de lectura permite observar cómo cambia este equilibrio. Como hablar en voz alta requiere coordinación respiratoria y atención, lo normal es que la actividad simpática aumente y la variabilidad disminuye.

De manera conjunta, la HRV y el diagrama de Poincaré permiten comprender no sólo cuánto varían los intervalos R-R, sino también cómo se distribuyen esas variaciones, lo que ofrece una visión mucho más completa del estado del sistema nervioso autónomo.(Shaffer & Ginsberg, 2017)

### -Al realizar este análisis, deberán formular el plan de acción para cumplir con el objetivo de la práctica y formularlo como un diagrama de flujo. 

<img width="850" height="1280" alt="image" src="https://github.com/user-attachments/assets/3a531400-7888-49e8-8b09-d820d1460511" />  

## b. Adquisición de la señal ECG   
Para la adquisición de la señal ECG se utilizó el mismo código en Python previamente implementado durante el laboratorio de EMG, el cual permite obtener datos en tiempo real y descargar la señal para su posterior análisis. La única modificación realizada fue en la frecuencia de muestreo, que se ajustó considerando un rango de interés de 0.05 Hz a 250 Hz, acorde con los estándares internacionales para señales electrocardiográficas de alta resolución.  

Según el teorema de Nyquist, para evitar aliasing es necesario muestrear al menos al doble de la frecuencia máxima presente en la señal, lo que en este caso corresponde a 500 Hz. Sin embargo, se optó por una frecuencia de muestreo de 2000 Hz, es decir, cuatro veces la frecuencia de Nyquist, con el fin de garantizar una mayor fidelidad en la reconstrucción digital, mejorar la precisión en la detección de eventos rápidos como los picos R, y facilitar el análisis espectral detallado sin distorsión.  

         import nidaqmx
         from nidaqmx.constants import AcquisitionType
         import numpy as np
         import matplotlib.pyplot as plt
         import time  

         frecuencia_muestreo = 2000       
         canal_daq = "Dev5/ai0"           
         muestras_por_bloque = 500        
         tiempo_buffer = 5                 

         datos_capturados = []        
         inicio = time.time()    

    with nidaqmx.Task() as tarea:
       tarea.ai_channels.add_ai_voltage_chan(canal_daq)
       tarea.timing.cfg_samp_clk_timing(
        freq=frecuencia_muestreo,
        sample_mode=AcquisitionType.CONTINUOUS
    )
    tarea.in_stream.input_buf_size = int(frecuencia_muestreo * tiempo_buffer)

    print("Iniciando adquisición continua... (Ctrl + C para finalizar)")
    try:
        while True:
            bloque = tarea.read(number_of_samples_per_channel=muestras_por_bloque)
            datos_capturados.extend(bloque)
    except KeyboardInterrupt:
        print("\nAdquisición interrumpida por el usuario.")
    finally:
        tiempo_total = time.time() - inicio
        print(f"Tiempo total de adquisición: {tiempo_total:.2f} segundos") .


         datos_capturados = np.array(datos_capturados)
         tiempo = np.arange(0, len(datos_capturados)) / frecuencia_muestreo

         plt.figure(figsize=(10, 5))
         plt.plot(tiempo, datos_capturados, color='steelblue')
         plt.xlabel("Tiempo [s]")
         plt.ylabel("Amplitud [V]")
         plt.title("Registro EMG")
         plt.grid(True)
         plt.show()  

         ruta_guardado = f"C:/Users/carlo/.spyder-py3/RegistroEMG_{frecuencia_muestreo}.txt"
         np.savetxt(ruta_guardado, datos_capturados)
         print(f"Archivo guardado en: {ruta_guardado}")  
    

# PARTE B   
## c. Pre-procesamiento de la señal   
Se importaron las librerías necesarias para el procesamiento de la señal y se descargó el ECG. Fue cargado en el Drive de Colab, lo que permitió su manipulación directa desde el notebook. A partir de los datos obtenidos, se realizó la visualización inicial de la señal sin aplicar ningún tipo de filtrado. La primera gráfica muestra la señal ECG original completa, mientras que la segunda tiene zoom, con el fin de observar con mayor detalle la morfología del complejo PQRST y evaluar la calidad de la señal antes del procesamiento.  

     fs = 2000
     t = np.arange(len(senal)) / fs
     plt.figure(figsize=(12,5))
     plt.plot(t, senal, color='purple', linewidth=1)
     plt.title('Señal ECG')
     plt.xlabel('Tiempo [s]')
     plt.ylabel('Amplitud [V]')
     plt.grid(True)
     plt.show()

<img width="1006" height="470" alt="image" src="https://github.com/user-attachments/assets/fd8c0479-bfa6-4db7-879e-c8fcbfbb9a30" />  
<img width="1020" height="470" alt="image" src="https://github.com/user-attachments/assets/a3c16acf-c4a9-45b2-a002-b7a2e894a91a" />  

Inicialmente se intentó implementar un filtro IIR pasabanda, pero los cálculos requeridos presentaban un alto nivel de complejidad, especialmente al justificar manualmente los coeficientes y garantizar la estabilidad del sistema. Por esta razón, se optó por una estrategia alternativa: aplicar un filtro FIR pasaalto para eliminar la deriva de baja frecuencia, seguido de un filtro IIR pasabajo para atenuar el ruido de alta frecuencia.

Sin embargo, durante la implementación del filtro IIR pasabajo aparecía una línea recta, lo cual indicaba una posible saturación e incluso cierta inestabilidad que pudo ser numérica o se le atribuye a errores en la inicialización del filtro. Por otro lado, el filtro FIR pasaalto generó coeficientes excesivamente largos, lo que dificultó su cálculo manual y su validación. Esto evidenció la necesidad de utilizar funciones para el la implementacón del mismo.  
![Imagen de WhatsApp 2025-11-21 a las 10 29 03_1994c26d](https://github.com/user-attachments/assets/ce942203-9bbe-4f2e-940f-5a0dbab302be)
![Imagen de WhatsApp 2025-11-21 a las 10 29 05_ae08a882](https://github.com/user-attachments/assets/a830c488-0fdc-4ba5-a94b-69cb4767ae4b)
![Imagen de WhatsApp 2025-11-21 a las 10 53 24_0d7cf9ad](https://github.com/user-attachments/assets/a805e05a-f586-4e68-b2d8-9c638ab8a68d)



Al final se optó por hacerlo con un pasabanda con funciones de phyton, tambien se ingreso la ecuación en diferencias para que alobtener los coeficientes computacionalmente se reemplazaran alli


       frecuencia_corte_baja_hz = 1.0
       frecuencia_corte_alta_hz = 40.0

       frecuencia_normalizada_baja = frecuencia_corte_baja_hz / (fs / 2)
       frecuencia_normalizada_alta = frecuencia_corte_alta_hz / (fs / 2)

       coeficientes_b_pasabanda, coeficientes_a_pasabanda = butter(
           4,
           [frecuencia_normalizada_baja, frecuencia_normalizada_alta],
           btype='bandpass'
       )


       coeficientes_b_rechaza_60hz, coeficientes_a_rechaza_60hz = iirnotch(60 / (fs / 2),
       30
       )

       print("Coeficientes del filtro pasa banda:")
       print("b =", coeficientes_b_pasabanda)
       print("a =", coeficientes_a_pasabanda)

       print("\nCoeficientes del filtro Notch 60 Hz:")
       print("b =", coeficientes_b_rechaza_60hz)
       print("a =", coeficientes_a_rechaza_60hz)



       def filtro_IIR_simple(x, b, a):
           y = np.zeros(len(x))
           for n in range(len(x)):
               y[n] = sum(b[k] * x[n-k] for k in range(len(b)) if n-k >= 0) \
                    - sum(a[k] * y[n-k] for k in range(1, len(a)) if n-k >= 0)
           return y


       senal_filtrada_pasabanda_manual = filtro_IIR_simple(
           senal, 
           coeficientes_b_pasabanda, 
           coeficientes_a_pasabanda
       )

       senal_filtrada_total_manual = filtro_IIR_simple(
           senal_filtrada_pasabanda_manual,
           coeficientes_b_rechaza_60hz,
           coeficientes_a_rechaza_60hz
       )


       senal_ecg_filtrada = filtfilt(coeficientes_b_pasabanda, coeficientes_a_pasabanda, senal)
       senal_ecg_filtrada = filtfilt(coeficientes_b_rechaza_60hz, coeficientes_a_rechaza_60hz, senal_ecg_filtrada)

<img width="1012" height="470" alt="image" src="https://github.com/user-attachments/assets/2bdca0f4-7627-453a-8f1a-8d5ccdfcde30" />

<img width="1032" height="470" alt="image" src="https://github.com/user-attachments/assets/e31b8a13-4a2f-4ef1-a7c9-9cee05d4f2b6" />  

Después se dividió la señal filtrada en dos segmentos, los primeros 2 minutos donde la persona estaba en resposo y los otros en los que permanecía hablando.

       duracion_segundos = 120              # duración de cada segmento
       muestras_segmento = duracion_segundos * fs   # 120 s × fs Hz

       senal_segmento1 = senal_ecg_filtrada[:muestras_segmento]

       senal_segmento2 = senal_ecg_filtrada[muestras_segmento : 2 * muestras_segmento]

       t_segmento1 = np.arange(len(senal_segmento1)) / fs
       t_segmento2 = np.arange(len(senal_segmento2)) / fs + 120 

Luego se graficaron en su forma original y también con zoom:  

       plt.figure(figsize=(12,4))
       plt.plot(t_segmento1, senal_segmento1, color='purple')
       plt.title("Segmento 1 — Reposo (0–120 s)")
       plt.xlabel("Tiempo [s]")
       plt.ylabel("Amplitud [V]")
       plt.grid(True)
       plt.show()

**Segmento 1 (Reposo)**  
<img width="1012" height="393" alt="image" src="https://github.com/user-attachments/assets/fa197875-c004-41d6-8315-2f03f2166cfb" />
<img width="1002" height="374" alt="image" src="https://github.com/user-attachments/assets/4a3f8def-dd34-4436-9247-ce1cbd09b953" />

**Segmento 2 (Leyendo)**  
<img width="1012" height="393" alt="image" src="https://github.com/user-attachments/assets/6ac1714f-aa76-4a78-af28-f6375a450c8a" />
<img width="1006" height="374" alt="image" src="https://github.com/user-attachments/assets/7d8a419c-5aba-45e4-b949-4e9400bee643" />



## d. Análisis de la HRV en el dominio del tiempo  
Luego, se identificaron los picos R en cada uno de los segmentos y se calcularon los intervalos R-R 
```
picos_R_reposo, _ = find_peaks(
    senal_segmento1,
    distance=int(0.25 * fs)    # separación mínima de 250 ms
)

picos_R_lectura, _ = find_peaks(senal_segmento2, distance=int(0.25 * fs))
```
Este código utiliza la función `find_peaks()` de `scipy.signal` para detectar picos R en dos segmentos de señal ECG:
La `senal_segmento1` representa el ECG en reposo (0–120 s).
Y la `senal_segmento2` representa el ECG en lectura (120–240 s).
Los picos R son los puntos más altos del complejo QRS y son esenciales para calcular los intervalos RR y posteriormente la HRV.
Y para el cálculo de los picos R-R:

```
intervalos_RR_reposo = np.diff(picos_R_reposo) / fs
intervalos_RR_lectura = np.diff(picos_R_lectura) / fs

print("Primeros intervalos RR (reposo):", intervalos_RR_reposo[:10])
print("Primeros intervalos RR (lectura):", intervalos_RR_lectura[:10])
```
Donde:

`np.diff(picos_R)`	Calcula la distancia entre picos R consecutivos (en muestras)
`/ fs`	Convierte esa distancia de muestras a segundos
`intervalos_RR` es el	vector de intervalos RR listos para análisis HRV
`print(...[:10])`	Muestra los primeros 10 intervalos para ver si son correctos

Luego se calcula la serie temporal RR con el siguiente código:
```
# Construcción de tiempo RR para graficar (se escala a 120 s)
tiempo_RR_reposo = np.linspace(0, 120, len(intervalos_RR_reposo))
tiempo_RR_lectura = np.linspace(120, 240, len(intervalos_RR_lectura))
```
Donde:
`tiempo_RR_reposo = np.linspace(0, 120, len(intervalos_RR_reposo))` se encarga de generar un vector de tiempo entre 0 y 120 segundos, con tantos puntos como intervalos RR en reposo. 
`tiempo_RR_lectura = np.linspace(120, 240, len(intervalos_RR_lectura))` y genera un vector de tiempo entre 120 y 240 segundos, con tantos puntos como intervalos RR durante la lectura. lo que nos permite graficar este segundo segmento a continuación del primero sin superposición.

Y se generan las gráficas:

<img width="1012" height="393" alt="image" src="https://github.com/user-attachments/assets/b6a28f28-45f7-483e-8602-3dd85dc72bf7" />
<img width="1012" height="393" alt="image" src="https://github.com/user-attachments/assets/03eef450-aa02-43b7-8eaf-08553e26697f" />
Y adicionalemte se arrojan los primeros intervalos de las gráficas: 
Primeros intervalos RR (reposo): [0.25   0.2535 0.425  0.303  0.4465 0.275  0.423  0.277  0.4385 0.2635]
Primeros intervalos RR (lectura): [0.4445 0.298  0.425  0.281  0.447  0.256  0.4535 0.2605 0.399  0.318 ]
<img width="1010" height="393" alt="image" src="https://github.com/user-attachments/assets/5f8b2c3b-1d97-4270-be2f-2d3a2d5f621b" />
Y observamos la serie de intervalos tanto en reposo como durante la lectura.
<img width="1010" height="393" alt="image" src="https://github.com/user-attachments/assets/4284b71c-38e4-49b5-8cc4-a410faace381" />

Los intervalos RR oscilan aproximadamente entre 0.25 s y 0.55 s, con algunos picos aislados hasta ~0.65 s.
Esto corresponde a una frecuencia cardiaca aproximada de:

100 a 270 latidos por minuto. Un resultado bastante alto para ser medido en una persona que se encuentra en reposo, aunque podría verse relacionado con la medición de doble latido, un error que es común cuando se hace una medición de ECG.
Por otro lado, cuando observamos la gráfica de intervalos de la lectura encontramos muestra un patrón típico de actividad autonómica aumentada durante la lectura en voz alta. Se mantiene una frecuencia elevada y estable, hay una reducción  de variabilidad cardiaca, las fluctuaciones rapidas las asociamos al control ventilatorio cuando la persona estudiada hablaba. A su vez los picos son compatibles con las pausas respiratorias o artefactos naturales que ocurren al habla.

Finalmente calculamos el HRV en dominio del tiempo.
Con el siguiente código:
```
# Media de intervalos RR
media_RR_reposo = np.mean(intervalos_RR_reposo)
media_RR_lectura = np.mean(intervalos_RR_lectura)

# Desviación estándar de intervalos RR (SDNN)
sdnn_reposo = np.std(intervalos_RR_reposo)
sdnn_lectura = np.std(intervalos_RR_lectura)
```
En reposo la media RR es de 0.3679 s y durante la lectura es de 0.3262 s. En el SDNN en reposo es de 0.0965s y en lectura es de 0.0640s.

En la media RR encontramos que es mayor en reposo, lo cual significa que la frecuencia cardíaca es menor, como es fisiológico.
Durante la lectura, la media RR disminuye por lo que la frecuencia cardíaca aumenta, haciendo referencia a una mayor activación.
Por otro lado, el SDNN representa la variabilidad total, controlada por simpático y parasimpático.
Cuando está en reposo nos da un valor de 0.0965 s lo que es mayor que en la lectura que es de 0.0640 s, lo que nos indica una mayor variabilidad cardiaca en reposo.
Es decir que el comportamiento es coherente, cuando hay reposo hay una mayor variabilidad, lo que inidica más fluencia vagal y cuando se hace una lectura, hay menor variabilidad, lo que indica más control simpático.


# Parte C.
## e. Comparación del diagrama de Poincaré.
Costruimos el diagrama de Poincaré con el siguiente código:
```
plt.figure(figsize=(6,6))
plt.scatter(intervalos_RR_reposo[:-1], intervalos_RR_reposo[1:],
            color='purple', s=10)
plt.title("Diagrama de Poincaré — Reposo (0–2 min)")
plt.xlabel("RR(n) [s]")
plt.ylabel("RR(n+1) [s]")
plt.grid(True)
plt.show()

plt.figure(figsize=(6,6))
plt.scatter(intervalos_RR_lectura[:-1], intervalos_RR_lectura[1:],
            color='green', s=10)
plt.title("Diagrama de Poincaré — Lectura (2–4 min)")
plt.xlabel("RR(n) [s]")
plt.ylabel("RR(n+1) [s]")
plt.grid(True)
plt.show()
```
El cual arrojó las siguientes gráficas:
<img width="546" height="548" alt="image" src="https://github.com/user-attachments/assets/a02cf251-4d7a-40cd-bb19-85969e1bacbf" />
<img width="545" height="548" alt="image" src="https://github.com/user-attachments/assets/0719ae34-697c-44a6-b437-a3a6bae26cdd" />

Cuando está en reposo hay una nube de puntos más dispersión, especialmente en el eje transversal (SD1), a su vez hay mayor variabilidad latido a latido. También se observan sub-clusters que indican respiración sinusal.
Ahora, durante la lectura la nube es más compacta y hay menor dispersión trasnversal en SD1 y longitudinal en SD2. Es decir que cuando está en reposo hay mayor dispersión, por lo que hay un mayor tono vagal. Y cuando está leyendo la dispersión se reduce por lo que hay mayor tónico.

Luego hicimos el cálculo de SD1 y SD2, y de CVI y CSI con el siguiente código:

```
def calcular_SD1_SD2(intervalos_RR):
    # diferencias consecutivas
    diferencia_RR = intervalos_RR[1:] - intervalos_RR[:-1]

    SD1 = np.sqrt(0.5) * np.std(diferencia_RR)
    SD2 = np.sqrt(2*(np.std(intervalos_RR)**2) - SD1**2)

    return SD1, SD2

SD1_reposo, SD2_reposo = calcular_SD1_SD2(intervalos_RR_reposo)
SD1_lectura, SD2_lectura = calcular_SD1_SD2(intervalos_RR_lectura)
```
Y el de CVI y CSI:

```
def calcular_CVI_CSI(SD1, SD2):
    CVI = np.log10(SD1 * SD2)
    CSI = SD2 / SD1
    return CVI, CSI

CVI_reposo, CSI_reposo = calcular_CVI_CSI(SD1_reposo, SD2_reposo)
CVI_lectura, CSI_lectura = calcular_CVI_CSI(SD1_lectura, SD2_lectura)
```
La función `calcular_SD1_SD2` se encarga de obtiener SD1 y SD2 a través de funciones como  `np.std()`, `np.sqrt()`. Y `calcular_CVI_CSI` obtiene CVI y CSI a través de funciones como `np.log10()` para las operaciones matemáticas.

Interpretando los datos obtenidos en el SD1 Y SD2.
### SD1.
El reposo es de 0.1289 s y en lectura es de 0.0821 s.
Es decir que SD1 disminuye notablemente durante la lectura, lo que indica una reducción de la actividad parasimpática.
Esto es coherente con una mayor demanda cognitiva ya que el cuerpo atenúa la relajación para permitir mayor atención.

### SD2.
En reposo es de 0.0448s y cuando lee es de 0.0380s. Por lo que aunque SD2 también disminuye en lectura, lo hace en menor medida que SD1.
Esto sugiere que la variabilidad total se reduce, pero lo más afectado es el componente parasimpático (SD1), lo que indica un desplazamiento hacia mayor actividad simpática.
En el Índice CVI es decir la actividad vagal, el reposo se ubica en –2.2390 mientras en la lectura se encuentra en –2.5061
Lo que nos indica que un CVI menos negativo representa mayor influencia vagal. Por tanto, el CVI es mayor en reposo, confirmando que la actividad parasimpática domina cuando no hay exigencia cognitiva.
Y durante la lectura, el CVI disminuye, indicando supresión vagal típica del estado de concentración.

3. Índice CSI (actividad simpática)​
En reposo se encuentra en: 0.3474.
Y en lectura en 0.4620.
Por lo que los valores más altos indican mayor actividad simpática, asociada a alerta, estrés o tareas cognitivas.
A su vez el CSI aumenta durante la lectura indicando mayor tono simpático y el aumento no es extremo, lo que indica una activación fisiológica moderada, consistente con una tarea de lectura, no con estrés intenso.

Es decir que este comportamiento tiene sentido con la componente autonómico ya que tiene dominancia en reposo, la dominancia en lectura es parasimpático.
Tiene alta variabilidad rápida y actividad vagal predominante.
Y en la lectura de los 2–4 minutos hay una reducción marcada de SD1 lo que indica una disminución parasimpática.
Al aumento del CSI hay una mayor actividad simpática, lo que refleja una activación compatible con concentración y atención cognitiva.

# REFERENCIAS 

- Berntson, G. G., et al. (1997). Heart rate variability: Origins, methods, and interpretive caveats. Psychophysiology.


- Brennan, M., Palaniswami, M., & Kamen, P. (2001). Do existing measures of Poincaré plot geometry reflect nonlinear features of HRV? IEEE TBME.


- Guyton, A. & Hall, J. (2021). Textbook of Medical Physiology. Elsevier.


- Kamen, P., & Tonkin, A. (1995). Application of the Poincaré plot to heart rate variability. IEEE Eng Med Biol.


- Klabunde, R. (2011). Cardiovascular Physiology Concepts.


- Laborde, S., Mosley, E., & Thayer, J. (2017). Heart rate variability and self-regulation. Frontiers in Psychology.


- Shaffer, F., & Ginsberg, J. P. (2017). An overview of HRV metrics and norms. Frontiers in Public Health.


- Task Force of the ESC. (1996). Heart rate variability: Standards of measurement, physiological interpretation, and clinical use. Circulation.


- Thayer, J., et al. (2012). A meta-analysis of HRV and autonomic function. Neuroscience & Biobehavioral Reviews.


- Tulppo, M., et al. (1996). Quantitative beat-to-beat analysis of heart rate dynamics. Am J Physiol.

- Bistel Esquivel, R. A., & Fajardo Márquez, A. (2015). Diseño de un sistema de adquisición y procesamiento de la señal de ECG basado en instrumentación virtual. Ingeniería Electrónica, Automática y Comunicaciones, 36(1).


