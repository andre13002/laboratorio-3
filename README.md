Para la practica de este laboratorio lo primero que realizamos fue la adquisición de la señal, para esto colocamos los electrodos en el antebrazo para analizar el músculo cubital posterior, y colocamos una tierra cercana a iniciar la palma de la mano como se muestra en la siguiente figura, utilizamos un amplificador AD8232 y para gráficar la señal utilizamos la tarjeta de Arduino.

Luego le pedimos al sujeto de prueba que realizara una contracción
del musculo hasta llegar a la fatiga con una pesa de 10kg, en total tuvimos 7 repeticiones. 
Con la señal capturada la pasamos a Spyder para empezar a realizar su análisis, para esto lo primero que hicimos fue limpiar un poco la señal eliminado el ruido en ella mediante el codigo, aplicamos un filtro pasa altas para deshacer los componentes de baja frecuencia, como el movimiento que podia tener la persona que o a la linea de base. Y un filtro pasa bajas para eliminar frecuencias altas no deseadas, como el ruido electromagnético o de interferencia de alta frecuencia.


Aplicamos un aventamiento a la señal, en cada contracción ya que es una función que se aplica multiplicativamente sobre una señal para limitarla o suavizarla en su dominio de tiempo o espacio. La señal completa se "ventanea", lo que significa que la señal original se multiplica por la función de ventana en cada punto, normalmente antes de hacer un análisis en el dominio de la frecuencia.
El aventanamiento que utilizamos fue la hanning, que es una técnica usada comúnmente en el procesamiento de señales y análisis espectral. Se aplica para suavizar una señal y reducir los efectos de las discontinuidades en los bordes de la señal cuando se realiza una Transformada de Fourier (FFT), esta tiene una forma de campana que esta diseñada para reducir las discontinuidades en los extremos de la señal.
La utilizamos debido a que cuando se trabaja con señales finitas como señales electromiográficas,  a menudo tenemos que analizar pequeños fragmentos de la señal, y las discontinuidades o saltos bruscos en los extremos de estos fragmentos pueden generar artefactos no deseados al realizar la transformada de Fourier (FFT), lo que se conoce como fugas espectrales.
* Fugas espectrales: Esto ocurre cuando una señal discontinua en el dominio del tiempo introduce componentes de alta frecuencia no presentes originalmente en la señal. La ventana Hanning suaviza estos extremos, reduciendo las fugas espectrales, lo que resulta en un espectro de frecuencias más preciso y más limpio.
Cuando aplicamos la ventana Hanning, los valores en los extremos de la señal son multiplicados por 0 (o casi 0), mientras que los valores en el centro son multiplicados por 1 o por valores cercanos a 1. Esto produce una señal suavizada que tiende a tener valores pequeños en los bordes y se comporta de manera más gradual a lo largo del tiempo o del espacio.


Luego realizamos la transformada de Fourier para obtener el espectro de frecuencias en las contracciones de la señal EMG.


Con estas dos cosas, calculamos los valores estadísticos de la señal que fueron: 
Media: El valor promedio 
Mediana: Es el valor que divide la señal en dos partes iguales.

Varianza: Mide la dispersión de los valores respecto a la media.
Desviación estándar: Es la raíz cuadrada de la varianza, y representa la magnitud promedio de las desviaciones respecto a la media.
Potencia: Es la energía promedio por unidad de tiempo.
SNR: Mide la relación entre la potencia de la señal útil y la potencia del ruido presente.
Cada una de estos valores nos proporcionaron una visión diferente de las características de la señal y es útil para el análisis de la misma.
