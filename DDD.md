# Diseño guiado por el dominio (DDD)

Enfoque que enlaza el modelado del dominio y el diseño del software.

Modelo del dominio rico que evoluciona por medio de múltiples interacciones.

El mayor desafío es entender el dominio del problema.

Los desarrolladores, cuando los proyectos son exitosos, saben perfectamente el dominio.

### El dominio
1. Área o actividad de interés.
2. Es el negocio.
3. Esfera del conocimiento.
4. Entorno de negocio o área de conocimiento especializado para la que desarrollamos el software.

> Importante aprender el lenguaje del negocio, aprender las reglas y procesos.

> Los proyectos fracasan cuando el conocimiento del negocio y la implementación no tienen ninguna conexión.

> Complejidad técnica: inherente a bases de datos, interfaces, distribución, que pueden ser complejas pero resultan manejables.

> Complejidad del dominio: subestimada, pero que puede ocasionar muchos problemas a largo plazo y se refiere a la complejidad del problema que el software intenta resolver.

### Promesa del modelo del dominio
1. El modelo sirve como lenguaje común entre los dos.
2. Guía el diseño de software de manera que el software expresa el conocimiento al dominio.
3. Facilita el aprendizaje continuo; se entiende el negocio y el modelo puede evolucionar.

## Capítulo 1: Destilando el conocimiento
> Desarrolladores y expertos del conocimiento trabajan en estrecha relación.
> En el proceso de destilación se debe encontrar todo el conocimiento que nos permita transformar el problema del negocio en herramientas para que el equipo pueda aprovechar y diseñar mejores soluciones de acuerdo al conocimiento.

### Elementos del proceso de destilación del conocimiento
* Conversaciones continuas entre desarrolladores y expertos (no son reuniones).
* Construcción de un modelo que capture el conocimiento del dominio que pueda expresarse en código.
* Ciclo rápido de retroalimentación: el modelo genera el código, el código genera preguntas y las preguntas generan más conocimientos.

### Aprendizaje continuo
El equipo nunca termina de aprender sobre el dominio. A veces los expertos no conocen todo el dominio sino hasta que ven el software funcionando.

### El proceso
1. El desarrollador hace preguntas sobre el negocio.
2. Los expertos responden con ejemplos concretos.
3. Se buscan patrones con esos ejemplos.
4. El desarrollador propone un modelo de captura de sus patrones.
5. El experto valida y corrige el modelo.
6. El ciclo vuelve a iniciar.

### Principio del capítulo
El conocimiento existe en la cabeza de los expertos, el desarrollador debe extraerlo, destilarlo y codificarlo. Hay una colaboración activa.

## Capítulo 2: Lenguaje Ubicuo
Comunicación y el uso del lenguaje.

### Cultivar un vocabulario común
El vocabulario debe usarse en todo (conversaciones, código, diagramas, documentación).

### El problema de los dos lenguajes
Existe un lenguaje técnico, que es el lenguaje que usan los desarrolladores, y un lenguaje de negocio, que es el que usan los expertos. Cuando se traduce el lenguaje de negocio directamente a lenguaje técnico se pierde información.

### Lenguaje común como solución
Es un lenguaje compartido por todos, basado en el modelo del dominio.

### Se usa en:
1. Conversaciones entre desarrolladores y expertos del dominio.
2. El nombre de clases, métodos y variables en el código.
3. Diagramas UML y documentación.
4. En los casos de uso y especificaciones de requerimientos.

> Si el lenguaje cambia, ese cambio también debe reflejarse en el código; renombrar una clase o un paquete es también un acto de modelado.

> No mezclar dos lenguajes, se debe usar el definitivo.

### Hablar el modelo en voz alta
Ayuda a afianzar el lenguaje y a corregir conceptos ambiguos; cimienta el vocabulario compartido.

### Un lenguaje, un equipo
El lenguaje debe ser uno solo, compartido por todos; un vocabulario del dominio central debe ser uno para todos.

### Documentos y diagramas
Los diagramas son útiles herramientas de documentación, pero no reflejan todo el negocio. Los documentos son necesarios para terminar de documentar todo el modelo.

## Capítulo 3: Diseño orientado al modelo
La idea central de este capítulo es que debe haber una correspondencia directa y literal entre el modelo del dominio y el código. No debe existir ninguna traducción entre el modelo y el diseño.

### El problema del modelo desconectado
El modelo en papel que no guía la implementación es inútil, y una implementación sin un modelo coherente es un laberinto. Debe haber una correspondencia en una implementación que permita la ejecución del código, y el código debe estar guiado por el modelo de diseño bien construido.

### El código es el modelo
El código debe ser una expresión directa del modelo; cada concepto importante en la vida debe tener una representación directa en el código: una clase, una interfaz, un método con ese nombre exacto.

Esto requiere dos cosas: el modelo debe ser práctico para implementar (o sea, no puede ser tan abstracto que no se pueda identificar directamente) y la implementación debe respetar el modelo. Cuando se refactoriza el código, se está refactorizando el modelo.

El modelo y el código son la misma cosa; un cambio en el código es un cambio en el modelo, y si se hace un desarrollo al modelo, se cambia el código.

### La analogía del astrolabio
El código del sistema bien diseñado no es una aproximación del modelo del dominio, es el modelo expresado en lenguaje de programación.

### Paradigma del modelado
Para que el diseño dirigido por el dominio funcione, se necesita un paradigma de programación que permita expresar el modelo directamente. Se usa mucho la programación orientada a objetos.

Los objetos corresponden directamente al concepto del modelo: cada clase es un concepto, cada asociación es una relación entre conceptos, cada método es un comportamiento del concepto.

El diseño orientado al modelo requiere que quienes modelan también codifiquen, y que quienes codifican entiendan el modelo. La separación total entre estas actividades destruye el valor del modelado.

## Capítulo 4: Arquitectura en capas
Arquitectura en capas como el mecanismo para lograr aislamiento.

### Las cuatro capas
Se divide en cuatro capas donde las dependencias solo fluyen hacia abajo.

1. **Capa de presentación:** muestra la interfaz del usuario, interpreta comandos.
2. **Capa de aplicación:** coordina las tareas del sistema (orquesta el trabajo de los objetos del dominio).
3. **Capa del dominio (modelo):** el corazón del software; contiene los conceptos del negocio, las reglas del negocio y el estado del negocio. Esta capa es donde vive el modelo; aquí están las entidades, los objetos de valor, los servicios del dominio y los agregados.
4. **Capa de infraestructura:** proporciona las capacidades técnicas que soportan a las capas superiores: mensajería, infraestructura de servicios, bases de datos, red.

### Patrón Smart UI
Este patrón se usa cuando las aplicaciones son simples y no necesitan la arquitectura en capas. Cuando la aplicación crece, es importante definir desde un inicio si se hace por este patrón, porque este crecimiento nos puede costar en la construcción de la aplicación; si se requiere una solución por capas, cuesta más invertir en la infraestructura y rehacer todo el código desde cero.

## Capítulo 5: Entidades y objetos de valor
Entidades, objetos de valor y servicios.

### Entidades
La entidad es la representación del mundo real, es la abstracción del objeto definido por su identidad. La entidad persiste a través del tiempo y puede cambiar sus atributos sin dejar de ser la misma cosa.

### Objetos de valor
Un objeto de valor es un objeto definido completamente por sus atributos; no tiene identidad. Los objetos de valor son inmutables; en lugar de modificar un objeto de valor existente, creas uno nuevo con los valores actualizados. Esto simplifica enormemente el razonamiento sobre el sistema; si el objeto no puede cambiar, no hay que preocuparse por efectos secundarios inesperados.

### Versus entre entidad y objetos de valor
¿Cuando dos instancias tienen los mismos atributos son la misma cosa? Si la respuesta es sí, es un objeto de valor. Si no (sin importar cuál instancia específica es), es una entidad.

### Diseño de asociaciones
Las relaciones entre objetos (asociaciones) son naturales en el modelado, pero peligrosas en el diseño. Se deben restringir las asociaciones bidireccionales tanto como sea posible.

Las asociaciones bidireccionales crean acoplamiento mutuo que hace difícil cambiar cualquiera de los dos objetos; en la implementación, son costosas de mantener. La dirección de la asociación a menudo refleja una comprensión más profunda del dominio.

### Servicios
Hay operaciones que no pertenecen naturalmente a ninguna entidad u objeto de valor; para estas operaciones se recomienda crear servicios. Un servicio al dominio es una operación sin estado que representa un concepto de dominio que no encaja naturalmente en un objeto de entidad o con atributos de valor. Los servicios:

1. No tienen estado propio entre llamados.
2. Operan sobre objetos del dominio (entidades y objetos de valor).
3. Expresan conceptos del dominio que no encajan naturalmente en ningún objeto.
4. Se nombran como verbos, no como sustantivos ("transferir fondos" en lugar de "transferencia de fondos").

### Módulos
Cuando un modelo crece, es necesaria una forma de organizar sus elementos en grupos cohesivos. Los módulos son la respuesta. Un buen módulo tiene cohesión interna y bajo acoplamiento externo; los objetos dentro del módulo tienen muchas relaciones entre sí y comparten un concepto coherente. Los módulos tienen pocas dependencias con otros módulos, o sea, pueden funcionar por sí solos.

Los nombres de los módulos deben ser parte del lenguaje ubicuo.

## Capítulo 6: Agregados, fábricas y repositorios

### Agregados
Los agregados son un clúster de objetos relacionados que se tratan como una unidad para operaciones de datos. Cada agregado tiene su raíz en una entidad específica que es el punto de entrada del agregado. El mundo exterior solo puede referenciar a la raíz, no a los objetos internos del agregado.

Reglas fundamentales de los agregados:
1. La raíz es la única con identidad global.
2. Solo la raíz puede ser obtenida directamente de la base de datos o repositorio.
3. Los objetos internos pueden tener identidad local dentro del agregado, pero no global.
4. Los objetos externos pueden tener referencias transitorias a objetos internos, pero no referencias persistentes.
5. Al final de una transacción, todos los invariantes del agregado deben ser satisfechos.

> Ejemplo: El coche es el Aggregate Root. Los neumáticos están dentro del Aggregate. Los bloques de motor (con número de serie) podrían ser raíz de su propio Aggregate.

Un agregado debe consistir en la raíz y quizás uno o dos objetos internos directamente necesarios para mantener los invariantes.

### Fábricas
Cuando la creación de un objeto complejo o un Aggregate entero revela demasiado de la estructura interna, o es una operación compleja en sí misma, se usa una Factory para encapsular esa creación.

La fábrica tiene dos formas principales:
1. Método fábrica en la raíz del agregado: cuando un agregado necesita crear objetos internos, el método en la raíz tiene el contexto necesario.
2. Fábrica independiente: para crear el agregado completo, una clase fábrica separada encapsula el proceso de creación. Esto es útil cuando la creación involucra configuración compleja o múltiples alternativas.

### Repositorios
Un repositorio proporciona una abstracción para obtener objetos persistentes (o sea, desde la base de datos hacia el objeto).

Los repositorios solo existen para las raíces del agregado; no hay repositorios para los objetos internos del agregado, esos siempre se acceden a través de la raíz.

Diferencia entre Repositorio y DAO (Data Access Object): un DAO es una abstracción técnica sobre una tabla de base de datos. Un Repositorio es una abstracción del dominio que representa una colección de objetos del dominio. El Repositorio pertenece al dominio; el DAO pertenece a la infraestructura.

> `Repositorio.findByCliente(clienteId)` // Dominio.
> `repositorio.executeQuery("SELECT * FROM orders WHERE client_id = ?", clienteId)` // No es dominio.

## Capítulo 10: Diseño flexible
Invita a ser cambiado y extendido.

1. **Interfaces que revelan intención:** El principio: nombrar clases y operaciones para describir su efecto y propósito, sin referencia a cómo lo hacen. Los nombres deben conformarse al Lenguaje Ubicuo.
2. **Funciones libres de efectos secundarios:** Las operaciones pueden dividirse en dos categorías: consultas (que obtienen información sin cambiar el estado) y comandos (que cambian el estado). Las funciones (operaciones que retornan resultados sin producir efectos secundarios) son mucho más seguras de usar y combinar. Los Objetos de Valor son la herramienta perfecta para esto. Como son inmutables, todas sus operaciones son funciones.
3. **Aserciones:** Una vez que tienes interfaces que revelan la intención y funciones libres de efectos secundarios, las aserciones son el siguiente paso: declarar explícitamente las postcondiciones de las operaciones y los invariantes de las clases.
4. **Contornos conceptuales:** Son las divisiones naturales del dominio que emergen del refactoring continuo. A medida que el equipo entiende mejor el dominio, refactoriza el modelo para que se alinee con las divisiones naturales del negocio.
5. **Clases independientes:** Una clase con muchas dependencias externas es difícil de entender y difícil de probar. El desarrollador tiene que entender no solo la clase, sino todas las clases de las que depende, y sus dependencias, y así sucesivamente.
6. **Clausura de operaciones:** Una técnica poderosa para diseñar interfaces ricas sin introducir dependencias externas: definir operaciones cuyos argumentos y valores de retorno son del mismo tipo que el implementador.

## Capítulo 14: Manteniendo la integridad del modelo
### Bounded Context (Contexto Delimitado)
Un Bounded Context es el patrón central para manejar múltiples modelos. Dentro del Bounded Context, el Lenguaje Ubicuo es coherente. Los mismos términos siempre significan lo mismo.
Definir un Bounded Context requiere:
1. Definir explícitamente los límites en términos de organización del equipo, partes de la aplicación y manifestaciones físicas (código, esquemas de base de datos).
2. Mantener el modelo estrictamente consistente dentro de esos límites.
3. No preocuparse por la consistencia fuera de esos límites.
4. Cuando dos Bounded Contexts necesitan comunicarse, definir explícitamente la traducción entre sus modelos.

### Integración continua dentro del Bounded Context
La integración continua es esencial para mantener la unidad del modelo. Los modelos se fragmentan cuando varias personas trabajan sobre ellos sin un proceso que detecte rápido las divergencias.
La integración continua opera en dos niveles: a nivel de modelo conceptual, mediante comunicación constante del equipo y uso del Lenguaje Ubicuo; y a nivel de implementación, mediante un proceso de merge, build y test automatizado que expone fragmentaciones rápidamente.

### Context Map
El Mapa de Contextos es una vista global de todos los modelos en un proyecto y sus relaciones. No solo ayuda a entender el sistema, es una herramienta de comunicación esencial para los equipos.
El Mapa de Contextos debe:
1. Identificar cada modelo en juego en el proyecto y su Bounded Context.
2. Nombrar cada Bounded Context (los nombres entran al Lenguaje Ubicuo).
3. Describir los puntos de contacto entre modelos, incluyendo las traducciones necesarias.
4. Representar la situación actual, no la ideal futura.

### Relaciones entre Bounded Contexts
* **Núcleo compartido:** Dos equipos acuerdan compartir un subconjunto del modelo. Ese subconjunto compartido no puede ser cambiado sin consultar con el otro equipo.
* **Cliente/Proveedor:** Un subsistema 'upstream' produce datos o servicios que otro 'downstream' consume. El equipo downstream expresa sus necesidades al upstream, y el upstream planifica para satisfacerlas. Requiere un proceso formal de comunicación de requisitos.
* **Conformista:** El equipo downstream se conforma con el modelo del upstream sin poder influir en él. Útil cuando el upstream es un sistema legado o externo sobre el que no se tiene control.
* **Capa Anticorrupción:** Cuando los modelos son muy diferentes o el upstream es de mala calidad, el equipo downstream crea una capa de traducción que convierte el modelo upstream al modelo propio. El dominio del equipo downstream permanece limpio e independiente.
* **Servicio de Acceso Abierto:** El upstream define un protocolo claro que permite al downstream acceder a sus funcionalidades como un conjunto de servicios. El protocolo está documentado y es estable.
* **Lenguaje Publicado:** Similar al Servicio de Acceso Abierto, pero el protocolo de comunicación es un lenguaje de dominio bien documentado que cualquier equipo puede consumir.
* **Caminos separados:** Cuando la integración entre dos contextos crea más problemas de los que resuelve, puede ser mejor que los equipos no compartan nada y desarrollen sus modelos completamente independientes.

## Capítulo 15: Destilación estratégica
### Core Domain (Dominio central)
Es el corazón del activo del negocio, es lo que diferencia a tu software de cualquier otro.

### Subdominios genéricos
Muchas partes del modelo son genéricas; necesarias pero no diferenciadoras: la contabilidad, el manejo de usuarios y permisos, el procesamiento de fechas con zonas horarias, el envío de notificaciones.

### Declaración de visión del dominio
Un documento de una página que describe el Core Domain y el valor que aporta. No intenta ser completo; se enfoca en los aspectos esenciales que distinguen al modelo.

### Core resaltado
Una vez que el Core Domain está identificado, necesita ser visible para todos en el equipo. El Highlighted Core es cualquier mecanismo que hace el Core Domain fácil de reconocer. Describe los conceptos centrales y sus interacciones. Puede ser un marcador en el código (un estereotipo UML, un comentario especial, una convención de nomenclatura).

### Mecanismos cohesivos
Un mecanismo cohesivo es una pieza del sistema que resuelve un problema computacional complejo y que puede ser separada del resto del modelo porque tiene una coherencia conceptual propia.

### Core segregado
El Core Segregado es una refactorización que separa físicamente (en módulos separados) los elementos del Core Domain de los elementos de soporte.

### Core abstracto
El Core Abstracto contiene las interfaces y clases abstractas que expresan los conceptos más fundamentales del dominio. Los módulos especializados dependen del Core Abstracto, pero no entre sí. Esto reduce el acoplamiento y hace el sistema más comprensible desde el nivel más alto.
