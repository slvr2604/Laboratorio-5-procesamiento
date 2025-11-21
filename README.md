# Laboratorio-5-procesamiento
En el presente laboratorio se realizó el procesamiento y análisis de una señal electrocardiográfica (ECG) con el propósito de estudiar la variabilidad de la frecuencia cardíaca (HRV) y comprender cómo cambia la actividad del sistema nervioso autónomo en diferentes condiciones fisiológicas. Para ello, se trabajó con una señal ECG de cuatro minutos de duración, la cual fue filtrada mediante un filtro IIR pasa banda de 1–40 Hz y un filtro Notch de 60 Hz, con el fin de eliminar el ruido muscular y la interferencia eléctrica.  

Posteriormente, la señal filtrada se dividió en dos segmentos: los primeros dos minutos durante los cuales la persona se encontraba en reposo y los siguientes dos minutos correspondientes a la lectura en voz alta. En cada segmento se identificaron los picos R mediante técnicas de detección basadas en las características morfológicas del ECG, y se calcularon los intervalos R-R, los cuales constituyen la base para el análisis de la HRV.     

Asimismo, se construyó el diagrama de Poincaré para cada segmento, del cual se obtuvieron los índices SD1, SD2, CVI y CSI, los cuales permiten evaluar de manera separada la actividad parasimpática y simpática del sistema nervioso autónomo. Este análisis permitió comparar de manera cuantitativa y visual cómo la carga cognitiva durante la lectura modifica el ritmo cardíaco y su variabilidad.  

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


# PARTE B   
c. Pre-procesamiento de la señal  
# PARTE C  


# REFERENCIAS 


-Berntson, G. G., et al. (1997). Heart rate variability: Origins, methods, and interpretive caveats. Psychophysiology.


-Brennan, M., Palaniswami, M., & Kamen, P. (2001). Do existing measures of Poincaré plot geometry reflect nonlinear features of HRV? IEEE TBME.


-Guyton, A. & Hall, J. (2021). Textbook of Medical Physiology. Elsevier.


-Kamen, P., & Tonkin, A. (1995). Application of the Poincaré plot to heart rate variability. IEEE Eng Med Biol.


-Klabunde, R. (2011). Cardiovascular Physiology Concepts.


-Laborde, S., Mosley, E., & Thayer, J. (2017). Heart rate variability and self-regulation. Frontiers in Psychology.


-Shaffer, F., & Ginsberg, J. P. (2017). An overview of HRV metrics and norms. Frontiers in Public Health.


-Task Force of the ESC. (1996). Heart rate variability: Standards of measurement, physiological interpretation, and clinical use. Circulation.


-Thayer, J., et al. (2012). A meta-analysis of HRV and autonomic function. Neuroscience & Biobehavioral Reviews.


-Tulppo, M., et al. (1996). Quantitative beat-to-beat analysis of heart rate dynamics. Am J Physiol.


