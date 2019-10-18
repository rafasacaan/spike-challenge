# Desafío Spike Octubre 2019 - Predicción de caudales extremos en Chile

Algunos puntos importantes a considerar:
- Este desafío no te debiera tomar más de 5 horas de tu tiempo. Por lo mismo, no esperamos respuestas muy pulidas ni perfectas.
- Las preguntas irán aumentando en dificultad, por lo que intenta responder hasta donde puedas. Si por algún motivo hay alguna parte que no lograste completar, no hay problema.
- Tendrás hasta el Jueves 17  de Octubre a las 23:59 para enviar tus respuestas al desafío.
- Solo se aceptarán Jupyter notebook (recomendado), R Markdown o R Notebook como formatos de entrega y solamente python o R. La idea es sea fácil para nosotros correr lo que ustedes escribieron (que sea reproducible).
- ¡Lee bien las instrucciones!


## Motivación

Nota: este segmento de motivación es para que entiendan un poco más del problema y por qué es relevante. No es necesario que entiendan todo, el resto del desafío los irá guiando en las cosas específicas que deben hacer. En otras palabras: lean esto rápido y luego concéntrense en las preguntas e instrucciones del desafío.

Las olas de calor son eventos meteorológicos extremos (temperaturas extremas), que pueden generar impactos negativos en nuestro ecosistema. Estos impactos van desde días de verano muy calurosos, deshidratación, hasta aumento del riesgo de incendios y riesgo de aluviones por crecidas de los ríos (por derretimiento de nieve o lluvias líquidas en zonas altas de la cordillera).
Dado que las olas de calor responden a patrones de circulación atmosférica que pueden ser detectadas con días e incluso semanas de anticipación, existe una oportunidad sin precedentes de intentar predecir la ocurrencia de algunos de los impactos negativos asociados a estos eventos extremos. Esto es clave en el contexto de calentamiento global, en donde la frecuencia a escala global de este tipo de eventos extremos ha aumentado en el último siglo (https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2012GL053361).
Para explorar esta potencial predictibilidad de los impactos asociados a las olas de calor, en particular los eventos de peakflows (crecidas de ríos, los que en casos extremos pueden llegar a desbordar el cauce), en Chile contamos con una amplia red de monitoreo de variables hidro-meteorológicas. Las estaciones meteorológicas que miden temperatura y precipitación son mantenidas por la Dirección General de Aguas (DGA) y la Dirección Meteorológica de Chile. Para potenciar el uso y la generación de conocimiento en base a estos datos públicos, el Centro de Ciencia del Clima y la Resiliencia (CR2) desarrolló un explorador climático (http://explorador.cr2.cl), desde el cual se pueden visualizar y descargar estos registros.

En el explorador climático se encuentran también los datos de caudal de las estaciones fluviométricas de la DGA, los que representan el agua total que aporta una cuenca hidrográfica a una sección de río. En el CR2 también se generó una base de datos de cuencas, que provee una serie de atributos de cada área aportante a las estaciones fluviométricas (http://camels.cr2.cl), además de series meteorológicas de temperatura y caudal promediadas dentro de la cuenca (es decir, no son datos de estaciones puntuales, sino que agregados espacialmente sobre el polígono de cada cuenca). 

Algunas de las preguntas claves que en Chile debemos responder son:
- ¿Ha aumentado la frecuencia de olas de calor en Chile? Para esto se deben analizar las estaciones de temperatura.
- ¿Existe una relación entre olas de calor y eventos extremos de caudal? 
- De existir una relación entre olas de calor y eventos extremos de caudal, ¿se puede explicar este evento extremo por las características de la cuenca en donde ocurre el peakflow?


## Instrucciones

Como dice el título, vamos a predecir los caudales extremos para cuencas en Chile. Para eso armamos un dataset usando datos públicos y reales de estaciones metereológicas.

Cada fila representa una medida de caudal diaria en una estación medidora. La medición de caudal estará asociada a características de la cuenca (fijas) y a mediciones diarias de temperatura y precipitación de estaciones cercanas.

El archivo caudal_extra.csv contiene todos los datos que van a necesitar para este desafío. Esta base la produjimos en Spike y sintetiza información de caudal, precipitación y temperatura.

*Nota sobre la producción de la base*: Las estaciones que miden el caudal y las que miden la temperatura y la precipitación no están en el mismo lugar. Para construir esta base, tomamos el polígono de la cuenca aguas arriba que corresponde a la estación de caudal y luego identificamos las estaciones de temperatura y precipitación que se encuentran en ese polígono. En muchos casos hay más de una estación, así que, por simpleza, tomamos el promedio de todas esas estaciones. De esta manera, cada día de medición de caudal va a estar asociada a una única medición de temperatura y de precipitación relevante (aunque puede haber cuencas sin estaciones de temperatura o precipitación).

La base pesa 256 megas. Si tienen problemas de RAM, tomen un subconjunto de las estaciones y continúen con el desafío.
Esta base tiene las siguientes variables:

- codigo_estacion: el código de la estación de medición de caudal.
- nombre: nombre del lugar en la cuenca donde está la estación.
- fecha: día de medición.
- caudal: medición de caudal de ese día.
- gauge_id: id de la cuenca.
- precip_promedio: precipitación promedio de ese día en la cuenca.
- temp_max_promedio: temperatura máxima  promedio de ese día en la cuenca.

Hemos creado además un canal en Gitter para que todos puedan colaborar entre sí. Ingresa en https://gitter.im/desafioSpike (se requiere cuenta github o gitlab).

## Desafío
Puedes ver el desafío desde en el siguiente link: https://github.com/SpikeLab-CL/desafio_spike_cuencas/raw/master/Spike%20Challenge%20-%20Caudales%20Extremos%20en%20Chile.pdf
