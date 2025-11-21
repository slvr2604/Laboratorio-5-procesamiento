# Laboratorio-5-procesamiento
En el presente laboratorio se realizó el procesamiento y análisis de una señal electrocardiográfica (ECG) con el propósito de estudiar la variabilidad de la frecuencia cardíaca (HRV) y comprender cómo cambia la actividad del sistema nervioso autónomo en diferentes condiciones fisiológicas. Para ello, se trabajó con una señal ECG de cuatro minutos de duración, la cual fue filtrada mediante un filtro IIR pasa banda de 1–40 Hz y un filtro Notch de 60 Hz, con el fin de eliminar el ruido muscular y la interferencia eléctrica.  

Posteriormente, la señal filtrada se dividió en dos segmentos: los primeros dos minutos durante los cuales la persona se encontraba en reposo y los siguientes dos minutos correspondientes a la lectura en voz alta. En cada segmento se identificaron los picos R mediante técnicas de detección basadas en las características morfológicas del ECG, y se calcularon los intervalos R-R, los cuales constituyen la base para el análisis de la HRV.     

Asimismo, se construyó el diagrama de Poincaré para cada segmento, del cual se obtuvieron los índices SD1, SD2, CVI y CSI, los cuales permiten evaluar de manera separada la actividad parasimpática y simpática del sistema nervioso autónomo. Este análisis permitió comparar de manera cuantitativa y visual cómo la carga cognitiva durante la lectura modifica el ritmo cardíaco y su variabilidad.  

## Diagrama de flujo  
Como primera etapa, se elaboró un diagrama de flujo que permitió estructurar tanto la programación como el procedimiento general del análisis. Esta herramienta facilitó la organización lógica de las tareas, definiendo el orden de ejecución, las funciones necesarias y los criterios de procesamiento aplicados.

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

HRV alta → más control vagal → organismo en un estado flexible y tranquilo.

HRV baja → más control simpático → organismo en alerta o en mayor exigencia.

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
Inicialmente se graficó el ECG sin filtrar, que dio como resultado:  
<img width="1006" height="470" alt="image" src="https://github.com/user-attachments/assets/fd8c0479-bfa6-4db7-879e-c8fcbfbb9a30" />  
<img width="1020" height="470" alt="image" src="https://github.com/user-attachments/assets/a3c16acf-c4a9-45b2-a002-b7a2e894a91a" />  

Inicialmente se intentó implementar un filtro IIR pasabanda, pero los cálculos requeridos presentaban un alto nivel de complejidad, especialmente al justificar manualmente los coeficientes y garantizar la estabilidad del sistema. Por esta razón, se optó por una estrategia alternativa: aplicar un filtro FIR pasaalto para eliminar la deriva de baja frecuencia, seguido de un filtro IIR pasabajo para atenuar el ruido de alta frecuencia.

Sin embargo, durante la implementación del filtro IIR pasabajo aparecía una línea recta, lo cual indicaba una posible saturación e incluso cierta inestabilidad que pudo ser numérica o se le atribuye a errores en la inicialización del filtro. Por otro lado, el filtro FIR pasaalto generó coeficientes excesivamente largos, lo que dificultó su cálculo manual y su validación. Esto evidenció la necesidad de utilizar funciones para el la implementacón del mismo.  
**PEGAR CALCULOSSS**  
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

# DESDE ACAAAA
Luego, se identificaron los picos R en cada uno de los segmentos y se calcularon los intervalos R-R 






## d. Análisis de la HRV en el dominio del tiempo  

# PARTE C  
## e. Construcción del diagrama de Poincaré   


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


