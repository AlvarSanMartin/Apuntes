#greco
innarima -> consultora

# TODO
- [ ] 
# 1. Resumen general
- Aparicion de chatgtp
- Consumo de agua/electricidad en el entrenamiento de modelos
- ¿Cómo podemos cambiar esta tendencia y hacer que los sistemas inteligentes sean más eficientes y respetuosos con el medioambiente? !!
- Integrar consideraciones de eficiencia y sostenibilidad desde las
etapas iniciales

>El objetivo principal de GRECO “Transformación de la ingeniería de sistemas IA para mejorar la eficiencia y el impacto medioambiental a través de GREenCOmputing” es maximizar la eficiencia económica y minimizar el impacto medioambiental de los sistemas inteligentes buscando el equilibrio entre el rendimiento, la calidad y la sostenibilidad de estos sistemas. GRECO permitirá a la industria vasca que implementa o integra cualquier componente de inteligencia artificial optimizar la vida útil de sus sistemas y __reducir el consumo energético reduciendo los altos tiempos de integración__ y el alto impacto medioambiental que actualmente tienen estos sistemas.

- Objetivo 1: Incrementar la **eficiencia económica** de los sistemas inteligentes en las diferentes fases del ciclo de vida (relacionado con el paquete de trabajo 1)
- Objetivo 2: Implementar **nuevas arquitecturas** que reduzcan el impacto medioambiental de los sistemas inteligentes sin perjudicar su rendimiento (relacionado con el paquete de trabajo 2)
- Objetivo 3: Optimizar la **vida útil** de los sistemas IA haciéndolos eficientes desde el diseño (relacionado con el paquete de trabajo 3)
- Objetivo 4: Capacitar a los sistemas inteligentes de técnicas para adaptarse a diferentes **escenarios** en base a indicadores de coste e impacto medioambiental (relacionado con el paquete de trabajo 4)
- Objetivo 5: **Aplicar e integrar** los avances y resultados desarrollados en el proyecto en diferentes dominios industriales

#### PCTI 2030
- IA y big data -> componentes con algo de *IA* o *Big data* que sean mas económicas
- Materiales y procesos -> casos de uso industrial

# 2. Estado del arte
- Inquietud sobre el impacto medioambiental de la IA 
- Temas de lo que contamina entrenar la IA y el agua que usa etc.
- Los modelos quedan obsoletos rápidamente (solo se mencionan los LLM)
- *No es una investigación de la IA como tecnología ni una investigación en metodologías para una IA confiable*
## Áreas de GRECO
### [2.1.1] Mejora de la eficiencia económica de sistemas inteligentes
- Confiabilidad y eficiencia -> párrafo sobre los coches autónomos, supervisores en tiempo de ejecución
- Ley de IA
- Degradación de modelos -> monitorización del modelo
### [2.1.2] Mejora de la sostenibilidad medioambiental de sistemas inteligentes
- Otra vez el impacto ambiental 
- Almacenamiento de grandes volumenes
> El LCA es una metodología ampliamente reconocida para la evaluación del impacto ambiental, con normas ISO (ISO 14040 y 14044) y una norma metodológica específica para las TIC del ETSI/UIT
- Herramientas para evaluar consumos y emisiones

### [2.1.3] Ingeniería de sistemas IA eficientes y sostenibles
- Aprendizaje por refuerzo 
- Zero o Few Shot Learning
- garantizar, no solo que las inferencias son buenas, sino también que los modelos son  eficientes, sostenibles y que son soluciones costo-efectivas

---
# A completar
### [1.2] ***Interés Dominon (p6)***
> Dominion es una multinacional que trabaja en el impulso de la industria 5.0 en plantas de producción de varios países. En el desarrollo de estas labores se ha desarrollado software mediante el cual ha sido posible manejar grandes cantidades cantidades de datos en tiempo real, que son vitales a la hora de entender los procesos de estas empresas y como aplicar la IA de una forma eficaz y sostenible. Dominion puede aportar conocimientos y técnicas aplicadas directamente en el centro de producción, la obtención de datos para el entrenamiento de los modelos, software para implementar los resultados en un entorno real y monitorización extensiva de el impacto de la IA en la productividad, la degradación que pueda sufrir a lo largo del tiempo y el impacto ambiental que tiene en cada etapa de su ciclo de vida. GRECO es una oportunidad para mejorar el software industrial de Dominion incluyendo herramientas inteligentes que ayuden a nuestros clientes en la toma de decisiones a la hora de reducir su huella de carbono.

Propuestas:
- Recopilación / tratamiento de datos desde la fuente
- Implementación y despliegue de los sistemas inteligentes en los centros
- Obtención de métricas de eficiencia en el uso practico
- Monitorización de uso de recursos y ahorro en proyectos
- Monitorización de productividad
- Monitorización de la degradación de modelos

### [3.1.1] Caso de uso de Industria Inteligente (p46)
Propuesta: Experiencia de Lynx en monitorización de uso de recursos e implementación en las plantas, texto sobre como ayudaría a predecir consumos o controlar emisiones
>La actividad de Dominon se lleva a cabo a nivel de planta, los datos se recogen directamente desde cada sensor y son almacenados y tratados según los objetivos de cada cliente, que pueden ir desde la gestión de la energía consumida desde varias fuentes o el control del estado de los equipos de producción. 
>En el proceso de monitorización se generan cantidades de datos que no siempre son útiles en su totalidad y debemos trabajar en técnicas que nos ayuden a minimizar el muestreo de tal forma que se reduzcan los costes de procesamiento y almacenamiento.
>En el área del hardware estamos buscando soluciones que nos permitan procesar la mayor cantidad de datos con el mínimo consumo, para lo que se investiga en la aplicación de arquitecturas que han demostrado un menor consumo como ARM o RISC-V tanto en dispositivos edge, como en servidores para la nube. Es especialmente importante considerar aquellos equipos que van a ser usados para la inferencia de datos por medio de algoritmos de ML.
>Capa superior a la IA??
### [5] Nivel de cooperación e integración entre agentes del sistema ciencia-tecnología (p69)
> Identificación y tipología de los participantes en el proyecto y los elementos esenciales de su posicionamiento incluyendo antecedentes y experiencia previa, y estrategia a futuro dentro del ámbito científico-tecnológico abordado en el proyecto.

Propuesta: Lo que puede aportar Dominion al proyecto en cuanto a conocimientos / personal 
> Dominion es una compañía global con actividad en 35 país, su principal actividad es ayudar en la transición de los negocios hacia modelos mas eficiente y respetuosos con el medio ambiente mediante la aplicación tecnológica en sus procesos. En el desarrollo de esta labor Dominion desarrolla infraestructuras inteligentes para la transmisión y almacenamiento de datos de grandes dimensiones.
> Dominion aporta conocimientos en extracción de datos de la planta y métodos para su almacenamiento de una manera estructurada y practica para su futuro consumo por parte de los clientes, que en el caso de GRECO podrían ser los modelos de ML que buscamos entrenar.
> La participación en el proyecto GRECO supone una oportunidad de llevar a nuestros clientes la IA sin que suponga un coste energético excesivo, lo que consolidaría a Dominion como una empresa referente en la industria 5.0 y en especial en su compromiso por la reducción del impacto ambiental de la industria globalmente.
### [5.2.1] Papel y complementariedad de los participantes (p73)
- **Conocimiento que aporta al proyecto**: [Propuesta]: Recolección de datos, monitorización, funcionamiento de fabricas y equipos industriales, datos en tiempo real por Lynx, despliegue de IA en producción.
>[En la tabla] Conocimiento de extracción y tratamiento de datos directamente de la plantas, pudiendo aplicarse tanto a la elaboración de conjuntos para los entrenamientos como para obtener mediciones del impacto de las técnicas desarrolladas aplicadas en entornos reales.
### [6.2] Lista de personal investigador (p82)
- Incluir a los participantes


### [6.3] Justificar la dimensión y equilibrio del equipo de proyecto en términos de masa crítica necesaria para las actividades y objetivos propuestos, perfiles y categorías de investigadores y sus niveles de dedicación, etc. (p84)
- Justificación de dedicación en porcentaje por cada miembro y participación en las tareas
El equipo de DOMINION I+D lo conforman 3 investigadores dirigidos por *Iñaki Aizpurua Olano*  ingeniero superior de telecomunicación con mas de 20 años de experiencia laboral dirigiendo proyectos de  I+D en el área TIC. *Xabier Barandiaran Landín*, doctor en ciencias biológicas  con mas de 33 años de experiencia laboral en los campos de medioambiente y biotecnología, los 4 últimos ha dirigido su actividad hacia proyectos de I+D en el área TIC, especializándose en Inteligencia Artificial. *Iker Garcia Londrin* es graduado en matemáticas por la UPV-EHU con experiencia investigadora en analítica avanzada, Big-Data e inteligencia artificial.

- [ ] Hablar con alexander eguia 664003872  alexander.eguia@tecnalia.com
### [7.5] Justificación de otros gastos incurridos, en especial todos aquellos que tengan una dimensión relevante (registro de propiedad intelectual, gastos de auditoría,…) (p86)
Se incluyen gastos de auditoria por valor de 1000€ anuales para cada uno de los dos ejercicios dando un total de 2000€ para todo el proyecto.

### [8.3] Posibles acuerdos de transferencia de resultados con empresas. Transferencia directa de know-how (nº empresas con las que se prevé realizaractuaciones de I+D) (p88)
[Propuesta] Parrafo generico sobre como la participación serviría para mejorar los conocimientos para la aplicacion en el software de monitorizacion de energia y la implementacion de IA en este.


>Trabajar en GRECO supone un salto importante en cuanto a la aplicación de la IA en técnicas para mejorar la procesos de producción, lo que tendría un gran impacto en los proyectos en los que Dominion trabaja a nivel mundial. También ofrece una oportunidad para la mejora de la eficiencia energética de la infraestructura que ya ha sido construida alrededor de todo el proceso que implica la extracción y almacenamiento de datos. GRECO puede suponer un salto importante en cuanto sofisticación tecnológica de nuestras soluciones y en el impacto ambiental positivo que estas aportan.

- (p89) Completar el número de agentes participantes
