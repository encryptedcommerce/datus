Esta es una traducción al español de 
[Covid-19, your community, and you — a data science perspective](https://www.fast.ai/2020/03/09/coronavirus/),
escrito por [Jeremy Howard](https://twitter.com/jeremyphoward) y [Rachel Thomas](https://twitter.com/math_rachel), y traducido por [Leonardo González](https://twitter.com/archimagos).

# Covid-19, su comunidad y usted: una perspectiva de ciencia de datos

> Somos científicos de datos, es decir, nuestro trabajo es comprender cómo analizar e interpretar los datos. Cuando analizamos los datos en torno a covid-19, estamos muy preocupados. Las partes más vulnerables de la sociedad, los ancianos y los pobres, están en mayor riesgo, pero controlar la propagación y el impacto de la enfermedad requiere que todos cambiemos nuestro comportamiento. Lávese las manos minuciosa y regularmente, evite grupos y multitudes, cancele eventos y toque la cara. En esta publicación, explicamos porqué estamos preocupados, y porqué usted también debería estarlo. Para obtener un excelente resumen de la información clave que necesita saber, lea [Coronavirus en resumen](https://docs.google.com/document/u/1/d/1vumYWoiV7NlVoc27rMQvmVkVu5cOAbnaW_RKkq2RMaQ/mobilebasic?fbclid=IwAR0If1zzDDldgAy3DZmFhaxAmP046-dwAE_LCj3l9su2XLYpZe2By8mCj1A) de Ethan Alley (presidente de una organización sin ánimo de lucro que desarrolla tecnologías para reducir los riesgos de pandemias).

## Traducciones
Cualquiera puede traducir este artículo para ayudar a sus comunidades locales a comprender estos problemas. 
Vuelva a vincular aquí con el crédito apropiado. Háganos saber en [Twitter](https://twitter.com/jeremyphoward) 
para que podamos agregar su traducción a esta lista.
* [francés](https://medium.com/@xrb/covid-19-votre-communaut%C3%A9-et-vous-3e5f127910bc)
* [español](https://datus.encryptedcommerce.net/2020/03/09/Covid-19-datascience-translation.html)

## Contenido
* [Necesitamos un sistema médico que funcione](#necesitamos-un-sistema-médico-que-funcione)
* [Esto no es como la gripe](#esto-no-es-como-la-gripe)
* [“No entre en pánico. Mantenga la calma.” no ayuda](#no-entre-en-pánico-mantenga-la-calma-no-ayuda)
* [No se trata solo de usted](#no-se-trata-solo-de-usted)
* [Necesitamos aplanar la curva](#necesitamos-aplanar-la-curva)
* [La reacción de una comunidad marca la diferencia](#la-reacción-de-una-comunidad-marca-la-diferencia)
* [No tenemos buena información en los Estados Unidos](#no-tenemos-buena-información-en-los-estados-unidos)
* [En conclusión](#en-conclusión)

## Necesitamos un sistema médico que funcione
Hace poco más de 2 años, uno de nosotros (Rachel) sufrió una infección cerebral que mata a aproximadamente 1/4 de las 
personas que la padecen y deja a 1/3 con un deterioro cognitivo permanente. Muchos otros terminan con daños permanentes en 
la vista y la audición. Rachel estaba delirando cuando se arrastró por el estacionamiento del hospital. Ella tuvo la suerte 
de recibir atención inmediata, diagnóstico y tratamiento. Hasta poco antes de este evento, Rachel estaba muy bien de salud. 
Tener acceso rápido a la sala de urgencias casi seguramente le salvó la vida.

Ahora, hablemos de covid-19 y de lo que podría pasarle a la gente en la situación de Rachel en las próximas semanas y meses. 
El número de personas infectadas con covid-19 se duplica cada 3 a 6 días. Con una tasa de duplicación de tres días, eso 
significa que la cantidad de personas infectadas puede aumentar 100 veces en tres semanas (en realidad no es tan simple, 
pero no nos distraigamos con detalles técnicos). Una de cada 10 personas infectadas requiere hospitalización durante muchas 
semanas, y la mayoría de ellas requieren oxígeno. Aunque es muy temprano para este virus, ya hay regiones donde los 
hospitales están completamente desbordados, y las personas ya no pueden obtener el tratamiento que requieren (no solo para 
covid-19, sino también para cualquier otra cosa, como el cuidado para salvar vidas que Rachel necesitaba). Por ejemplo, en 
Italia, donde hace solo una semana los funcionarios decían que todo estaba bien, ahora dieciséis millones de personas han 
sido bloqueadas ( actualización: 6 horas después de publicar esto, Italia puso a todo el país en bloqueo ), y carpas como 
esta se están configurando para ayudar a manejar la afluencia de pacientes:
![Una carpa médica utilizada en Italia](https://www.fast.ai/images/coronavirus/image1.jpeg "Una carpa médica utilizada en Italia")

*Una carpa médica utilizada en Italia*

El Dr. Antonio Pesenti, jefe de la unidad regional de respuesta a la crisis en una zona muy afectada de Italia, 
[dijo](https://www.reuters.com/article/us-health-coronavirus-italy/alarmed-italy-locks-down-north-to-prevent-spread-of-coronavirus-idUSKBN20V06R) :
“Ahora nos vemos obligados a establecer tratamientos de cuidados intensivos en corredores, quirófanos, salas de recuperación... 
Uno de los mejores sistemas de salud del mundo, en Lombardía está a un paso del colapso”.

## Esto no es como la gripe

La gripe tiene una tasa de mortalidad de alrededor del 0,1% de las infecciones. Marc Lipsitch, director del 
[Centro de Dinámica de Enfermedades Transmisibles](https://ccdd.hsph.harvard.edu/) de Harvard, estima que [para covid-19 es 
entre el 1% al 2%](https://www.washingtonpost.com/opinions/2020/03/06/why-its-so-hard-pin-down-risk-dying-coronavirus/).
El último modelo epedemiológico encontró una tasa de 1,6% en China en febrero, dieciséis veces más alta 
que la gripe [^1] (sin embargo, este podría ser un número bastante conservador, porque las tasas aumentan mucho cuando el 
sistema de salud no da a basto). Las mejores estimaciones actuales esperan que covid-19 matará 10 veces más personas 
este año que la gripe (y [los modelos de Elena Grewal](https://docs.google.com/spreadsheets/d/1ktSfdDrX_uJsdM08azBflVOm4Z5ZVE75nA0lGygNgaA/edit?usp=sharing), ex directora de ciencia de datos en Airbnb, muestra que podría ser 
100 veces más, en el peor de los casos). Esto es antes de tener en cuenta el gran impacto en el sistema médico, como el 
descrito anteriormente. Es comprensible que algunas personas estén tratando de convencerse de que esto no es nada nuevo, 
una enfermedad muy parecida a la gripe, porque es muy incómodo aceptar la realidad de que esto no es para nada familiar.

Tratar de comprender intuitivamente un crecimiento exponencial en el número de personas infectadas no es algo que nuestros 
cerebros estén diseñados para manejar. Entonces tenemos que analizar esto como científicos, no utilizando nuestra intuición.
![¿En qué estará esto en 2 semanas? ¿2 meses?](https://www.fast.ai/images/coronavirus/image2.png)

*¿En qué estará esto en 2 semanas? ¿2 meses?*

Por cada persona que tiene gripe, en promedio, infectan a otras 1,3 personas. Eso se llama “R0” para la gripe. Si R0 es 
menor que 1.0, entonces una infección deja de propagarse y desaparece. Si está por encima de 1,0 se extiende. R0 
actualmente es 2-3 para covid-19 fuera de China. La diferencia puede sonar pequeña, pero después de 20 "generaciones" de 
personas infectadas que transmiten su infección, un R0 de 1,3 daría como resultado 146 infecciones, ¡pero un R0 de 2,5 daría 
como resultado 36 millones de infecciones! (Esto es, por supuesto, una generalización e ignora muchos impactos del mundo real, 
pero es una ilustración razonable de la diferencia _relativa_ entre covid-19 y la gripe, todas las demás cosas siendo iguales).

Tenga en cuenta que R0 no es una propiedad fundamental de una enfermedad. Depende en gran medida de la respuesta pública, y puede 
cambiar con el tiempo [^2] . En particular, en China, R0 para covid-19 ha bajado mucho y ahora se acerca a 1,0. ¿Cómo, preguntas?
Poniendo en práctica medidas a una escala que sería difícil de imaginar en un país como los Estados Unidos -- por ejemplo, bloqueando 
por completo muchas ciudades gigantes y desarrollando un proceso de pruebas que permite administrar la prueba a más de un millón de 
personas por semana.

Una cosa que surge mucho en las redes sociales (incluso de cuentas muy seguidas como Elon Musk) es un malentendido de la 
diferencia entre el crecimiento _logístico_ y _exponencial_. El crecimiento “logístico” se refiere al patrón de crecimiento 
“en forma de s” de propagación epidémica en la práctica. Obviamente, el crecimiento exponencial no puede continuar para 
siempre, ya que de lo contrario habría más personas infectadas que personas en el mundo. Por lo tanto, eventualmente, las 
tasas de infección siempre deben disminuir, lo que resulta en una tasa de crecimiento en forma de S (conocida como _sigmoidea_)
con el tiempo. Sin embargo, el crecimiento decreciente solo ocurre por una razón -- no es magia. Las razones principales son:

* Respuesta comunitaria masiva y efectiva, o
* Un porcentaje tan grande de personas infectadas que hay menos personas no infectadas para contagiarse.

Por lo tanto, no tiene sentido lógico confiar en el patrón de crecimiento logístico como una forma de “controlar” una 
pandemia.

Otra cosa que dificulta la comprensión intuitiva del impacto de covid-19 en su comunidad local es que hay un retraso muy 
significativo entre la infección y la hospitalización, generalmente alrededor de 11 días. Esto puede no parecer mucho tiempo, 
pero cuando se compara con la cantidad de personas infectadas durante ese tiempo, significa que cuando se note que las camas 
de hospital estén llenas, la infección de la comunidad ya estará a un nivel en el que habrán 5-10 veces más personas con que lidiar.

Tenga en cuenta que hay algunas señales tempranas de que el impacto en su área local puede ser al menos algo dependiente del 
clima. El artículo [análisis de temperatura y latitud para predecir la propagación potencial y la estacionalidad para covid-19](https://poseidon01.ssrn.com/delivery.php?ID=091071099092098096101097074089104068104013035023062021010031112088025099126064001093097030102106046016114116082016095089113023126034089078012119081090111118122007110026000085123071022022127025026080005029001020025126022000066075021086079031101116126112&EXT=pdf)
señala que la enfermedad se ha propagado hasta ahora en climas templados (desafortunadamente para nosotros, el rango de 
temperatura en San Francisco, donde vivimos, está en ese rango; también cubre los principales centros de población de
Europa, incluido Londres.)

## “No entre en pánico. Mantenga la calma.” no ayuda

Una respuesta común que hemos visto en las redes sociales a las personas que señalan las razones para preocuparse es 
“no se asuste” o “mantenga la calma”. Esto, por decir lo menos, no ayuda. Nadie sugiere que el pánico sea una respuesta 
apropiada. Sin embargo, por alguna razón, "mantener la calma" es una reacción muy popular en ciertos círculos (pero no entre 
los epidemiólogos, cuyo trabajo es rastrear estas cosas). Quizás “mantener la calma” ayuda a algunas personas a sentirse 
mejor acerca de su propia inacción, o las hace sentir de alguna manera superiores a las personas que imaginan que corren 
como gallinas decapitadas.

Pero “mantener la calma” puede conducir fácilmente a una falta de preparación y respuesta. En China, pusieron a decenas de 
millones de personas en cuarentena y se construyeron dos nuevos hospitales cuando llegaron a las estadísticas que ahora tiene 
los Estados Unidos. Italia 
esperó demasiado, y solo en el domingo 8 de marzo informaron 1492 nuevos casos y 133 nuevas muertes, a pesar de encerrar a 
16 millones de personas. Con base en la mejor información que podemos determinar en esta etapa, hace solo 2-3 semanas Italia 
estaba en la misma posición en la que se encuentran los Estados Unidos y el Reino Unido actualmente (en términos de 
estadísticas de infección).

Tenga en cuenta que casi todo lo relacionado con covid-19 en esta etapa está indefinido. Realmente no conocemos la 
velocidad o la mortalidad de la infección, no sabemos cuánto tiempo permanece activo en las superficies, y no sabemos si 
sobrevive y se propaga en condiciones cálidas. Todo lo que tenemos son las mejores conjeturas actuales basadas en la mejor 
información que las personas pueden reunir. Y recuerde, la gran mayoría de esta información está en China, en chino. 
Actualmente, la mejor manera de entender la experiencia china hasta ahora es leer el excelente 
[Informe de la Misión Conjunta OMS-China sobre la Enfermedad por Coronavirus 2019](https://www.who.int/docs/default-source/coronaviruse/who-china-joint-mission-on-covid-19-final-report.pdf),
basado en una misión conjunta de 25 expertos nacionales e internacionales de China, Alemania, Japón, Corea, Nigeria, Rusia, 
Singapur, los Estados Unidos de América y la Organización Mundial de la Salud (OMS).

Cuando hay cierta incertidumbre, que tal vez esto no sea una pandemia global, y tal vez todo pueda pasar sin que el sistema 
hospitalario se derrumbe, eso no significa que la respuesta correcta sea no hacer nada. Eso sería enormemente especulativo 
y no una respuesta óptima en cualquier escenario de modelo de amenazas. También parece extremadamente improbable que países 
como Italia y China efectivamente cierren gran parte de su economía sin una buena razón. Tampoco es coherente con los 
impactos reales que estamos viendo en el terreno en las áreas infectadas, donde el sistema de salud no puede dar a basto 
(por ejemplo, Italia está utilizando 462 carpas para “pre-triaje”, y todavía tiene que [mover a los pacientes de 
la UCI de áreas infectadas](https://www.repubblica.it/cronaca/2020/03/08/news/coronavirus_situazione_italia-250665818/?ref=RHPPTP-BH-I250661466-C12-P5-S1.12-T1)).

En cambio, la respuesta razonable y razonable es seguir los pasos recomendados por los expertos para evitar la propagación 
de infecciones:

* Evite grupos grandes y multitudes.
* Cancelar eventos
* Trabajar desde casa, si es posible
* Lávese las manos cuando vaya y venga de casa, y con frecuencia cuando salga
* Evite tocarse la cara, especialmente cuando esté fuera de su casa (¡no es fácil!)
* Desinfecte las superficies y los paquetes (es posible que el virus permanezca activo durante 9 días en las superficies, aunque esto no se sabe con certeza).

## No se trata solo de usted

Si tiene menos de 50 años y no tiene factores de riesgo como un sistema inmune comprometido, enfermedad cardiovascular, 
antecedentes de tabaquismo previo u otras enfermedades crónicas, puede estar tranquilo de que es poco probable que covid-19 
lo mate. Pero cómo responde aún importa mucho. Aún tiene la misma probabilidad de infectarse y, si lo hace, la misma 
probabilidad de infectar a otros. En promedio, cada persona infectada está infectando a más de dos personas más, y se 
vuelven infecciosas antes de mostrar síntomas. Si tienes padres que te importan, o abuelos, y planeas pasar tiempo con ellos, 
y luego descubres que eres responsable de infectarlos con covid-19, sería una carga pesada con que vivir.

Incluso si no está en contacto con personas mayores de 50 años, es probable que tenga más compañeros de trabajo y conocidos 
con enfermedades crónicas de lo que cree. La investigación muestra que [pocas personas revelan sus condiciones de salud](https://www.talentinnovation.org/_private/assets/DisabilitiesInclusion_KeyFindings-CTI.pdf) 
en el lugar de trabajo si pueden evitarlo, [por temor a la discriminación](https://medium.com/@racheltho/the-tech-industry-is-failing-people-with-disabilities-and-chronic-illnesses-8e8aa17937f3). 
Ambos estamos en categorías de alto riesgo, pero muchas personas con las que interactuamos regularmente pueden no haberlo sabido.

Además, por supuesto, no se trata solo de las personas que te rodean inmediatamente. Este es un problema ético muy 
significativo. Cada persona que hace todo lo posible para contribuir a controlar la propagación del virus está ayudando a 
toda su comunidad a reducir la tasa de infección. Como Zeynep Tufekci [escribió en Scientific American](https://blogs.scientificamerican.com/observations/preparing-for-coronavirus-to-strike-the-u-s/): 
“Prepararse para la propagación mundial casi inevitable de este virus... es una de las cosas más pro-sociales y altruistas 
que puedes hacer”. Ella continúa:

> Debemos prepararnos, no porque podamos sentirnos personalmente en riesgo, sino para que podamos ayudar a disminuir el riesgo para todos. Debemos prepararnos no porque nos enfrentamos a un escenario del fin del mundo fuera de nuestro control, sino porque podemos alterar todos los aspectos de este riesgo que enfrentamos como sociedad. Así es, usted debe prepararse porque sus vecinos necesitan que se prepare, especialmente sus vecinos mayores, sus vecinos que trabajan en hospitales, sus vecinos con enfermedades crónicas y sus vecinos que pueden no tener los medios o el tiempo para prepararse debido a la falta de recursos o tiempo.

Esto nos ha impactado personalmente. El curso más grande e importante que hemos creado en fast.ai, que representa la 
culminación de años de trabajo para nosotros, estaba programado para comenzar en la Universidad de San Francisco en una 
semana. El miércoles pasado (4 de marzo), tomamos la decisión de [mover todo en línea](https://twitter.com/jeremyphoward/status/1236088745251581952). Fuimos uno de los primeros cursos 
grandes para movernos en línea. ¿Por qué lo hicimos? Debido a que nos dimos cuenta a principios de la semana pasada de que 
si realizábamos este curso, alentamos implícitamente a cientos de personas a reunirse en un espacio cerrado, varias veces 
durante un período de varias semanas. Reunir grupos en espacios cerrados es lo peor que se puede hacer. Nos sentimos 
éticamente obligados a garantizar que, al menos en este caso, esto no sucediera. Fue una decisión desgarradora. Nuestro 
tiempo dedicado a trabajar directamente con nuestros estudiantes ha sido uno de los grandes placeres y períodos más 
productivos de cada año. Y teníamos estudiantes planeando viajar desde todo el mundo, a quienes realmente no queríamos 
decepcionar [^3].

Sin embargo, sabíamos que era lo correcto, porque de lo contrario estaríamos aumentando la propagación de la enfermedad en 
nuestra comunidad [^4].

## Necesitamos aplanar la curva

Esto es extremadamente importante, porque si podemos reducir la tasa de infección en una comunidad, entonces les damos a los 
hospitales de esa comunidad tiempo para tratar con los pacientes infectados y con la carga regular de pacientes que necesitan 
manejar. Esto se describe como “aplanamiento de la curva”, y se muestra claramente en este gráfico ilustrativo:
![Permanecer debajo de esa línea punteada significa todo](https://www.fast.ai/images/coronavirus/image3.jpeg "Permanecer debajo de esa línea punteada significa todo")

*Permanecer debajo de esa línea punteada significa todo*

Farzad Mostashari, el ex Coordinador Nacional de TI de Salud, explicó: “Todos los días se identifican nuevos casos que no 
tienen un historial de viaje o conexión con un caso conocido, _y sabemos que estos son solo la punta del iceberg_ debido a la 
retrasos en las pruebas. Eso significa que en las próximas dos semanas el número de casos diagnosticados explotará... Tratar 
de contener la situación cuando hay una extensión exponencial de la comunidad es como enfocarse en apagar chispas cuando la 
casa está en llamas. Cuando eso suceda, debemos cambiar las estrategias a la mitigación: tomar medidas de protección para 
reducir la propagación y reducir el impacto máximo en la atención médica”. Si podemos mantener la propagación de la 
enfermedad lo suficientemente baja como para que nuestros hospitales puedan manejar la carga, entonces las personas podrán 
acceder al tratamiento. Pero si los casos llegan demasiado rápido, aquellos que necesitan hospitalización no la recibirán.

Así es como se verían las matemáticas, [según Liz Specht](https://twitter.com/LizSpecht/status/1236095186737852416):

> Estados Unidos tiene alrededor de 2,8 camas de hospital por cada 1000 personas. Con una población de 330 millones, esto es ~ 1 millón de camas. En cualquier momento, el 65% de esas camas ya están ocupadas. Eso deja alrededor de 330k camas disponibles en todo el país (quizás un poco menos en esta época del año con la temporada de gripe regular, etc.). Confiemos en los números de Italia y supongamos que alrededor del 10% de los casos son lo suficientemente graves como para requerir hospitalización. (Tenga en cuenta que para muchos pacientes, la hospitalización dura semanas , en otras palabras, la rotación será muy lenta a medida que las camas se llenen de pacientes con COVID19). Según esta estimación, aproximadamente el 8 de mayo, se llenarán todas las camas de hospital abiertas en los EE. UU. (Por supuesto, esto no dice nada acerca de si estas camas son adecuadas para el aislamiento de pacientes con un virus altamente infeccioso). Si nos equivocamos por un factor de dos con respecto a la fracción de casos graves, eso solo cambia la línea de tiempo de la saturación de la cama por 6 días en cualquier dirección. Si el 20% de los casos requieren hospitalización, nos quedamos sin camas antes del ~ 2 de mayo. Si solo el 5% de los casos lo requieren, podemos llegar hasta el ~ 14 de mayo. El 2.5% nos lleva al 20 de mayo. Esto, por supuesto, supone que no hay un aumento en la demanda de camas por otras causas (no COVID19), lo que parece una suposición dudosa. A medida que el sistema de salud se vuelve cada vez más pesado, la escasez de Rx, etc., las personas con afecciones crónicas que normalmente se manejan bien pueden verse sumidas en estados graves de angustia médica que requieren cuidados intensivos y hospitalización.

## La reacción de una comunidad marca la diferencia

Como hemos discutido, esta matemática no es una certeza: China ya ha demostrado que es posible reducir la propagación 
tomando medidas extremas. Otro gran ejemplo de una respuesta exitosa es Vietnam, donde, entre otras cosas, una campaña 
publicitaria a nivel nacional (¡incluyendo una canción que se popularizó!) movilizó rápidamente la respuesta de la comunidad 
y aseguró que las personas ajustaran su comportamiento de manera apropiada.

Esta no es solo una situación hipotética: se mostró claramente en la pandemia de gripe de 1918. En los Estados Unidos, dos 
ciudades mostraron reacciones muy diferentes a la pandemia: Filadelfia siguió adelante con un desfile gigante de 200.000 
personas para ayudar a recaudar dinero para la guerra. Pero St. Louis puso en marcha procesos cuidadosamente diseñados para 
minimizar los contactos sociales a fin de disminuir la propagación del virus, junto con la cancelación de todos los grandes 
eventos. Este es el aspecto de la cantidad de muertes en cada ciudad, como se muestra en las 
[Actas de la Academia Nacional de Ciencias](https://www.pnas.org/content/104/18/7582):
![Impacto de las diferentes respuestas a la pandemia de gripe de 1918](https://www.fast.ai/images/coronavirus/image4.jpeg "Impacto de las diferentes respuestas a la pandemia de gripe de 1918")

*Impacto de las diferentes respuestas a la pandemia de gripe de 1918*

La situación en Filadelfia se volvió extremadamente grave, llegando incluso a un punto donde 
[no había suficientes ataúdes fúnebres o morgues](https://www.history.com/news/spanish-flu-pandemic-dead) para manejar la 
gran cantidad de muertos por la gripe.

Richard Besser, quien fue director interino de los Centros para el Control y la Prevención de Enfermedades durante la 
pandemia de H1N1 de 2009, dice que en los Estados Unidos “el riesgo de exposición y la capacidad de protegerse a uno mismo 
y a su familia dependen de los ingresos, el acceso a la atención médica y estado migratorio, entre otros factores”. Él 
nota:

> Los ancianos y los discapacitados corren un riesgo particular cuando su vida cotidiana y sus sistemas de apoyo se ven afectados. Aquellos que no tienen fácil acceso a la atención médica, incluidas las comunidades rurales y nativas, pueden enfrentar enormes distancias en momentos de necesidad. Las personas que viven en lugares cerrados, ya sea en viviendas públicas, hogares de ancianos, cárceles, refugios o incluso las personas sin hogar en las calles, pueden sufrir olas, como ya hemos visto en el estado de Washington. Y las vulnerabilidades de la economía de trabajo de bajos salarios, con trabajadores no asalariados y horarios de trabajo precarios, estarán expuestos para que todos lo vean durante esta crisis. Pregúntele al 60 por ciento de la fuerza laboral estadounidense que recibe un pago por hora qué fácil es tomarse un tiempo libre en un momento de necesidad.

La Oficina de Estadísticas Laborales de los Estados Unidos Muestra que menos de un tercio de los que se encuentran en la 
banda de ingresos más bajos tienen acceso a licencia por enfermedad remunerada:
![La mayoría de los estadounidenses pobres no tienen licencia por enfermedad, por lo que tienen que ir a trabajar.](https://www.fast.ai/images/coronavirus/image5.png "La mayoría de los estadounidenses pobres no tienen licencia por enfermedad, por lo que tienen que ir a trabajar.")

*La mayoría de los estadounidenses pobres no tienen licencia por enfermedad, por lo que tienen que ir a trabajar.*

## No tenemos buena información en los Estados Unidos

Uno de los grandes problemas en los Estados unidos es que se están realizando muy pocas pruebas y los resultados de las pruebas no 
se comparten correctamente, lo que significa que no sabemos qué está sucediendo realmente. Scott Gottlieb, el anterior 
comisionado de la FDA, explicó que en Seattle se han realizado mejores pruebas, y estamos viendo infecciones allí: 
“La razón por la que supimos temprano sobre el brote de covid-19 en Seattle fue debido al trabajo de vigilancia centinela 
realizado por científicos independientes. Tal vigilancia nunca se puso en marcha totalmente en otras ciudades. Por lo tanto, 
es posible que otros puntos calientes de los Estados Unidos aún no se detecten por completo”. 
Según [The Atlantic](https://www.theatlantic.com/health/archive/2020/03/how-many-americans-have-been-tested-coronavirus/607597/), 
el vicepresidente Mike Pence prometió que “aproximadamente 1.5 millones de pruebas” estarían disponibles esta semana, pero 
hasta ahora se han realizado pruebas a menos de 2.000 personas en todo el páis. Basándose en el trabajo del 
[Proyecto de Seguimiento COVID](https://docs.google.com/spreadsheets/u/1/d/e/2PACX-1vRwAqp96T9sYYq2-i7Tj0pvTf6XVHjDSMIKBdZHXiCGGdNC0ypEU9NbngS8mxea55JuCFuua1MUeOj5/pubhtml), 
Robinson Meyer y Alexis Madrigal de The Atlantic, dijeron:

> Las cifras que reunimos sugieren que la respuesta estadounidense al covid-19 y la enfermedad que causa, COVID-19, ha sido sorprendentemente lenta, especialmente en comparación con la de otros países desarrollados. El CDC confirmó hace ocho días que el virus estaba en transmisión comunitaria en los Estados Unidos: que estaba infectando a estadounidenses que no habían viajado al extranjero ni estaban en contacto con otros que sí. En Corea del Sur, más de 66.650 personas fueron evaluadas dentro de una semana de su primer caso de transmisión comunitaria, y rápidamente pudo evaluar a 10.000 personas por día.

Parte del problema es que esto se ha convertido en un problema político. En particular, el presidente Donald Trump ha dejado 
claro que quiere ver que “los números” (es decir, el número de personas infectadas en los Estados Unidos) se mantenga bajo. 
Este es un ejemplo de dónde la optimización de las métricas interfiere con la obtención de buenos resultados en la práctica. 
(Para obtener más información sobre este tema, consulte el artículo de Ética de la Ciencia de Datos: 
[El problema con las métricas es un problema fundamental para la IA](https://arxiv.org/abs/2002.08512)). El jefe de 
inteligencia artificial de Google, Jeff Dean, [tuiteó su preocupación](https://twitter.com/JeffDean/status/1236489084870119427) 
por los problemas de desinformación politizada:

> Cuando trabajaba en la OMS, formaba parte del Programa Mundial sobre el SIDA (ahora ONUSIDA), creado para ayudar al mundo a combatir la pandemia del VIH / SIDA. El personal allí era médicos y científicos dedicados que se enfocaban intensamente en ayudar a abordar esa crisis. En tiempos de crisis, la información clara y precisa es vital para ayudar a todos a tomar decisiones adecuadas e informadas sobre cómo responder (gobiernos de países, estados y locales, empresas, ONG, escuelas, familias e individuos). Con la información y las políticas adecuadas para escuchar a los mejores expertos médicos y científicos, todos enfrentaremos desafíos como los presentados por el VIH / SIDA o COVID-19. Con la desinformación impulsada por intereses políticos, existe un riesgo real de empeorar las cosas al no actuar de manera rápida y decisiva frente a una pandemia cada vez mayor, y al alentar activamente comportamientos que realmente propagarán la enfermedad más rápidamente. Toda esta situación es increíblemente dolorosa de ver desarrollarse.

No parece que haya voluntad política para cambiar las cosas cuando se trata de transparencia. El secretario de Salud y 
Servicios Humanos, Alex Azar, según Wired , “comenzó a hablar sobre las pruebas que los trabajadores de la salud usan para 
determinar si alguien está infectado con el nuevo coronavirus. La falta de esos kits ha significado una peligrosa falta de 
información epidemiológica sobre la propagación y la gravedad de la enfermedad en los Estados Unidos, exacerbada por la 
opacidad por parte del gobierno. Azar intentó decir que había más pruebas en camino, a la espera del control de calidad”.
Pero ellos continuaron:

> Entonces Trump cortó a Azar. “Pero creo que, lo que es más importante, cualquiera, en este momento y ayer, que necesita una prueba, se hace una prueba. Están allí, tienen las pruebas y las pruebas son hermosas. Cualquiera que necesite una prueba se hace una prueba ”, dijo Trump. Esto no es cierto. El vicepresidente Pence dijo a los periodistas el jueves que Estados Unidos no tenía suficientes kits de prueba para satisfacer la demanda.

Otros países están reaccionando mucho más rápido y significativamente que los Estados Unidos. Muchos países en el sudeste 
asiático están mostrando excelentes resultados, incluidos Taiwán, donde R0 ahora se ha reducido a 0.3, y Singapur, que se 
propone como [El modelo para la respuesta COVID-19](https://www.medpagetoday.com/infectiousdisease/covid19/85254). Sin 
embargo, no es solo en Asia; en Francia, por ejemplo, está prohibida cualquier reunión de más de 1000 personas, y las 
escuelas ahora están cerradas en tres distritos.

## En conclusión

Covid-19 es un problema social importante y todos podemos y debemos trabajar para disminuir la propagación de la enfermedad. 
Esto significa:

* Evitar grandes grupos y multitudes
* Cancelar eventos
* Trabajar desde casa, si es posible
* Lavarse las manos cuando vaya y venga de casa, y con frecuencia cuando esté fuera
* Evitar tocarse la cara, especialmente cuando esté fuera de su casa

_Nota: debido a la urgencia de sacar esto a la luz, no hemos sido tan cuidadosos como normalmente nos gustaría ser sobre citar y acreditar el trabajo en el que confiamos. Por favor, háganos saber si nos hemos perdido algo.

Gracias a Sylvain Gugger y Alexis Gallagher por sus comentarios._

### Notas al pie

[^1]: Los _epidemiólogos_ son personas que estudian la propagación de la enfermedad. Resulta que estimar cosas como la 
mortalidad y la R0 en realidad son bastante desafiantes, por lo que hay un campo completo que se especializa en hacerlo bien. 
Desconfie de las personas que usan índices y estadísticas simples para decirle cómo se comporta covid-19. En cambio, mire los 
modelos realizado por epidemiólogos.

[^2]: Bueno, técnicamente no es cierto. “R0” estrictamente hablando se refiere a la tasa de infección en ausencia de respuesta.
Pero dado que eso no es lo que realmente nos importa, nos dejaremos ser un poco descuidados con nuestras definiciones aquí.

[^3]: Desde esa decisión, hemos trabajado duro para encontrar una manera de ejecutar un curso virtual que esperamos sea 
incluso mejor que la versión en persona. Hemos podido abrirlo a cualquier persona en el mundo y ejecutaremos grupos de 
estudio y proyectos virtuales todos los días.

[^4]: También hemos realizado muchos otros cambios menores en nuestro estilo de vida, como hacer ejercicio en casa en lugar 
de ir al gimnasio, trasladar todas nuestras reuniones a una videoconferencia y omitir eventos nocturnos que habíamos estado 
esperando.
