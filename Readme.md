# Resumen Final Orga2

# Tecnología de integración

### Escenario actual

- Queremos achicar los nanómetros que ocupa un transistor
- En 2012 teníamos 22nm
- Actualmente se trabaja en lograr 7 y 5nm.
- **Y luego? Violamos las leyes de la física. No podemos achicar más.**

### Ley de Moore

El número de transistores que incorporemos en un chip aproximadamente se duplicará cada 24 meses.

### Evolución tecnológica

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled.png)

Los progresos en scaling muchas veces obedecen a mejoras en el proceso de fabricación, pero cada tanto se produce algún salto cuántico en esto, que es cuando aparecen tecnologías de fabricación de semiconductores disruptivas.

- Strained Silicon
- High-k Metal Gate
- Tri-Gate:

    Ademas del scaling, disminuye mucho el consumo. En 2011 el consumo de energía es una preocupación muy fuerte.

**Velocidad de conmutación:** Es la velocidad que tarda en la que un transistor pasa de 0 a 1. **Evoluciona en función del scaling: cuanto más chico es el transistor, más alta es la velocidad de conmutación.**

### Tendencias tecnológicas

La tarea de un diseñador está inevitablemente influida por el rumbo de las tecnologías.

1. La densidad de transistores por unidad de superficie aumenta 35% por año en promedio (Ley de Moore alternativa)
2. El tamaño del die (disco con circuitos integrados) aumenta de 10 a 20% por año. Esto deriva en un crecimiento en la cantidad de transistores de entre 40% y 55% de un año a otro.
3. La velocidad de clock ya no crece, Parecería haber alcanzado un techo en los 3 GHz aproximadamente.
4. La capacidad de almacenamiento de las memorias DRAM crece a razón de un 40% por año.
5. Los discos rígidos aumentan su capacidad 25% a 30% por año. Su costo por bit de almacenamiento se mantiene entre 50 y 100 veces por debajo del costo de un bit de memoria DRAM.

# Arquitectura de Computadores

## Arquitectura vs Microarquitectura

### Arquitectura

Es el conjunto de recursos que nosotros tenemos como programadores para poder trabajar y poder desarrollar programas. **Se mantiene constante de un modelo a otro (en general).**

- Registros
- Set de instrucciones
- Estructuras de memoria (descriptores de segmento y de página)

### Micro Arquitectura

Es la implementación es el silicio de la arquitectura. Lo que está detrás del set de instrucciones. Determina de qué manera se ejecutan las instrucciones, cuán rápido o no. Cuestiones que están relacionadas a electrónica, tecnología, materiales, etc. Un procesador con una misma arquitectura tenga una estructura muy sólida, robusta, performante, y otro procesador con la misma arquitectura pero con una organización o microarquitectura diferente por debajo sea un procesador menos performante, más econónico, más lento, que consuma menos. **Cambian de un modelo a otro. Es "levantar el capó y ver qué hay debajo de la arquitectura".**

IA-32 es una **arquitectura**. Se inicia con el procesador 80386 en 1985 y llega hasta los procesadores Intel Core i7, i5, i3, ATOM y Xeon.

En el camino han pasado diferentes generaciones de **Microarquitectura** para más de 25 modelos de procesadores.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%201.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%201.png)

**Microarquitectura = Organización + Hardware**

## Organización

Se refiere a los detalles de implementación de la ISA (Instruction Set Architecture).

- Organización e interconexión de la memoria.
- Diseño de los diferentes bloques de la CPU que van a ejecutar la ISA. Qué características van a tener. Qué grado de paralelismo va a tener. Puede ejecutar varias instrucciones a la vez, o no? Puede ejecutar instrucciones fuera de orden o no?
- Implementación de paralelismo a nivel de instrucciones, y/o de datos.
- Podemos encontrar procesadores que poseen la misma arquitectura pero organización diferente **(ejemplo: AMD FX e Intel Core i7 tienen la misma ISA, pero su organización es completamente diferente).**

## Hardware

Se refiere a cosas todavía más "de abajo".

- Diseño lógico y tecnología de fabricación.
- Se pueden tener procesadores que tengan la misma ISA, la misma organización y distinto hardware.

## Por qué necesitamos saber todo esto?

- Comprender qué hay debajo del software.
- Comprender cómo el diseño de un hardware en particular impacta nuestra tareas como programadores.

# ________________________________________________________________________________________

# Sistema de Memoria

## Jerarquías de Memorias

### **Baja latencia o alta capacidad**

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%202.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%202.png)

- Cuanto más cerca de la cúspide estás, tenés memorias más veloces pero a la vez de menor capacidad, porque su costo por bit aumenta a medida que subimos.
- Queremos que nuestros datos estén lo más cerca posible de la CPU.
- Lo que tenemos más cercano al procesador son los registros.

## Principio de Vecindad o Localidad

### Principio de funcionamiento

El comportamiento de los algoritmos de software que se emplean habitualmente, es el que rige cómo y para qué se diseña el hardware. Muchas de las cosas que se diseña en hardware no son inventos, son simplemente observaciones de cómo se comportamiento y, entonces, buscar soluciones para agilizar ese comportamiento.

**Principio de vecindad temporal**

Una dirección de memoria que está siendo accedida actualmente tiene muy alta probabilidad de seguir siendo accedida en el futuro inmediato.

**Principio de vecindad espacial**

Si se está accediendo a una dirección determinada de memoria actualmente, la probabilidad de que esta dirección y sus direcciones vecinas sean accedidas en el futuro inmediato es muy alta.

# Tecnologías de Memoria

## Clasificación de memorias

### **Memorias No Volátiles (ROM)**

- Retienen la información almacenada cuando se les desconecta la alimentación.
- Han evolucionado tecnológicamente, desde ROM que se grababan en la fabrica hasta ROMs borrables y reprogramables eléctricamente.

### **Memorias Volátiles (RAM)**

- Pierden la información almacenada cuando se les desconecta la alimentación.
- Pueden almacenar mayores cantidades de información y modificarla en tiempo real mucho más rápido que las No Volátiles.
- Se clasifican, de acuerdo con la tecnología y diseño interno, en dinámicas (DRAM) y estáticas (SRAM).

### **Uso en un computador**

- La memoria no volátil se usa fundamentalmente para almacenar el programa de arranque de cualquier sistema.
- Se conectan en un espacio de direcciones determinado por el propio microprocesador de acuerdo a la dirección en la que éste irá a buscar la primer instrucción luego de encender el equipo.
- El resto es RAM y allí el sistema copia incluso buena parte del código de arranque para que se ejecute más rápido (recordemos que las memorias volátiles tienen menor tiempo de acceso)

### **Memorias RAM dinámicas (DRAM)**

Tenemos una celda de memoria representada por un transistor y un capacitor.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%203.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%203.png)

- Almacena la información en forma de estado de carga en un capacitor y la sostiene durante un breve lapso con la ayuda de un transistor.
- Una celda (un bit) se implementa con un sólo transistor → máxima capacidad de almacenamiento por CI.
- Ese transistor está generalmente en estado de Corte. Consume mínima energía.
- Al leer el bit, se descarga la capacidad (lectura destructiva), con lo cual necesita regenerar la carga cada vez que se la lee.
- Se descargan solas por las corrientes de fuga de los transistores, con lo cual hay que refrescarlas manualmente periodicamente. La recarga se hace haciendo una lectura "dummy" de toda una fila a la vez.

### **Memorias RAM estáticas (SRAM)**

- Tienen 6 transistores por cada bit. Es decir, la densidad es peor que en la RAM dinámica.
- 3 de los 6 transistores están cerrados, con lo cual consumen mucha corriente, con lo cual cada celda consume mucha energía.
- No se destruye la información al leer un bit.
- La velocidad de lectura es casi instantánea.

## Memorias y velocidad del Procesador

### **Conexion básica (Según Von Newmann)**

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%204.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%204.png)

Intel presenta su arquitectura muy parecida a la de Von Neumann. El 8088 tenía una línea de control llamada `Ready` que servía para saber cuándo una memoria estaba lista para leer o escribir un dato. Cuando los procesadores aumentaron su velocidad, las RAM se quedaron atrás.

El problema consiste en decidir qué tipo de RAM usar en el sistema. Hay dos opciones:

- **RAM dinámica (DRAM)**
    - Consumo mínimo.
    - Capacidad de almacenamiento comparativamente alta (1 transistor por bit).
    - Costo por bit bajo.
    - Tiempo de acceso alto (lento), debido al circuito de regeneración de carga.
- **RAM estática (SRAM)**
    - Alto consumo relativo.
    - Capacidad de almacenamiento comparativamente baja (6 transistores por bit).
    - Costo por bit alto (por ser menos densa).
    - Tiempo de acceso bajo (es más rápida).

**Conclusión:**

No podemos poner un banco de RAM estática porque el costo y consumo es muy elevado. Entonces, elegimos usar RAM dinámica, aunque al ser lentas no podemos aprovechar la velocidad superior del procesador (cuello de botella). **Esto último se resolvió con la memoria cache.**

# Memoria Cache

## Principio de Funcionamiento

Es un banco de **RAM estática** que contiene una copia de los datos e instrucciones que están en la memoria principal y el procesador necesita en este momento. La dificultad está en lograr que esta copia esté disponible justo cuando el procesador la necesita permitiéndole acceder a estos ítems sin utilizar *wait states*.

Este banco de RAM estática tiene que ser pequeño para no comprometer el costo y consumo de nuestro sistema (mismo problema de antes), pero a la vez tiene que ser suficientemente grande para contener siempre lo que el procesador necesita.

Esta memoria cache de pequeño tamaño combinada con una gran cantidad de memoria DRAM donde almacenemos el resto de las cosas resuelve el problema mediante una típica solución de compromiso.

Quién se encarga de que las cosas que están en la DRAM que el procesador va a utilizar estén en la cache? Esto cuesta hardware. Tiene que haber un controlador que intermedie entre el procesador y las dos memorias para asegurar que eso esté completamente funcional en el momento que el procesador lo necesite. **A este se lo denomina Controlador cache.**

### Características y métricas

**Se maneja con los principios de vecindad.** Al principio el cache esta vacío y el sistema es ineficiente porque tiene que ir a buscar todo a la RAM. Cuando se va a buscar algo a la RAM, el controlador la guarda también en la cache. Si se va a buscar una instrucción, el controlador busca esa instrucción y más, ya que seguro se van a utilizar las siguientes instrucciones.

Para medir la eficiencia de esto, se establecieron métricas. La operación de memoria es un **hit** o un **miss** según encuentre o no encuentre lo que busca en el cache (cuando lo encuentra es un **hit**, y cuando no lo encuentra es un **miss**). El **hitrate** se mide con la relación entre la **cantidad de hit** sobre la **cantidad de accesos totales**.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%205.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%205.png)

**Queremos que el hitrate tienda a 1.**

## Controlador de cache

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%206.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%206.png)

Quien maneja el BUS de control es quien maneja el BUS del sistema. **Este BUS ahora es manejado por el Controlador de Cache. El Controlador de Cache es el master del BUS de control. La idea es que intercepta los pedidos del procesador y se los manda o bien a la Memoria cache o bien a la memoria RAM según haya un hit o miss.**

El BUS de control es un bus con líneas de control del tipo **Read**, **Write**, etc.

### Operación de acceso a memoria para lectura

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%207.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%207.png)

1. El procesador inicia un ciclo de lectura. Pone la dirección de memoria en el BUS de address y **activa la línea Memory Read en el BUS de control**.
2. El controlador de Cache toma la línea de `Memory Read` (pues maneja el BUS de control) y dice, "Ok, el procesador quiere leer". También le llega el BUS de address y entonces puede saber qué dirección quiere leer. El controlador de Cache mira si la dirección de memoria está guardada en la cache (usa el directorio interno). **Sabe si tiene un hit o un miss.**

    a. Si tiene un **hit**, le manda el `Memory Read` a la cache en vez de enviarselo a la memoria RAM. La cache responde el dato por el BUS de data y el procesador lo lee. **Fin.**

    b.

    1. Si tiene un **miss**, le manda el `Memory Read` a la RAM. La memoria RAM se toma su tiempo para acceder al dato y luego mete el dato en el BUS de datos.
    2. Además, el controlador de cache le dice a la memoria cache que un dato va a ser escrito (seteando la linea `Memory Write` en su BUS de control) y le manda la misma data que devolvió la RAM en el punto anterior. Este dato lo guarda para honrar el principio de vecindad temporal.
    3. Luego, el controlador de cache actualiza la dirección en su directorio de cache.
    4. Por último, el mismo controlador de caché le devuelve el dato al procesador.

## Organización de un cache

### Líneas

El controlador caché no ve a la memoria principal como una sucesión de bytes, sino como una sucesión de líneas. **La mínima unidad de memoria para un controlador cache es la línea.** La línea está compuesta de una cantidad *b* de bytes. **Esto está pensado así para aprovechar el principio de vecindad espacial.** El controlador de caché se trae una línea completa en vez de un único byte.

**Tag**

A cada línea dentro del caché se le asigna una etiqueta (tag). El tag indica la posición de memoria, en la DRAM, en la cual comienza la línea. Dentro del cache las líneas no necesariamente están en el mismo orden en el que aparecen en memoria.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%208.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%208.png)

### Sistema Cache de Mapeo Directo

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%209.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%209.png)

- La DRAM se divide en bloques del mismo tamaño de la cache, los cuales se referencian con los bits más significativos de la dirección.
- Cada bloque se divide en sets.
- Cada set se divide en líneas. Generalmente 8 líneas.
- El directorio cache almacena, para cada set, el número de bloque (tag) que está guardado en la cache. Además tiene un bit de validez general del tag y un bit de validez individual de la línea.

**Funcionamiento:**

1. Particiono la dirección.

    ![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2010.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2010.png)

2. Accedo al número de set en el Directorio Cache.
3. Comparo el número de banco en la dirección con el tag almacenado en la entrada del directorio cache.
    - **Si el tag del directorio cache NO coincide con el número de banco de la dirección, miss.**
4. **Si el bit de validez general del tag está apagado, miss.**
5. Accedo al bit de validez individual de la línea.
    1. **Si el bit de validez de la línea está apagado, miss.**
6. **Devuelvo hit.**

**Problema:** **El mapeo directo es el menos eficiente de todos.** Para que sea eficiente, todas las líneas del set deben ser del mismo banco.

**Solución:** Sistema de Cache asociativo de n vías

### Sistema Cache Asociativo de 2 Vías

Este es el que se usa en la práctica.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2011.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2011.png)

Ahora la cache se divide en 2 vías o bancos. Ahora con dos vías puedo tener el mismo número de set de dos bancos de DRAM distintos. **Cuantas más vías tengo, más sets con el mismo número y distinto bancos puedo tener.** La eficiencia de esto es muy alta. **Con un cache asociativo de entre 4 y 8 vías se logran eficiencias superiores al 90%.**

Los bits LRU sirven para marcar la vía menos recientemente usada. Sirve para saber a cuál de las dos vías desalojar en caso que quiera almacenar un set de un tercer banco. De nuevo, esto sigue el principio de vecindad temporal.

## Coherencia de un cache

### ¿Qué ocurre durante las escrituras?

Cuando una variable está alojada en la cache, también está alojada en alguna dirección de la DRAM. Idealmente, ambas copias de la variable tendrían que mantener el mismo valor. Esto es lo que se entiende por coherencia. Cuando un procesador modifica la variable y escribe en un sólo lugar, se dice que se perdió la condición coherencia de esa variable. Hay que definir qué política de escritura vamos a utilizar.

### Políticas de escritura

**Write through:**

El procesador va y escribe en la DRAM, al costo de tiempo que sea. Luego, el controlador cache, una vez que esa escritura se efectuó, refresca el dato en el caché para mantenerlo actualizado. **Con esto la coherencia es perfecta, pero la desventaja ahora es que el tiempo de escritura me queda siempre penalizado por  la demora de la DRAM. O sea, para las escrituras, la cache no cumple su cometido. Es lo mismo que no tenerlo.**

**Write through buffered:**

Es write through mejorado con un buffer. Cuando el procesador quiere escribir, en realidad escribe en el cache. Luego, el controlador cache actualiza el dato en la DRAM más tarde. El buffer en el controlador de cache se utiliza para encolar las operaciones de escritura a memoria. **Este método no penaliza tanto las escrituras, salvo que el procesador se ponga a escribir demasiado frecuentemente.**

**Write back o copy back:**

El procesador escribe en la cache. El controlador de cache marca línea escrita como sucia (dirty). La cache queda completamente incoherente de la copia en DRAM. Luego, cuando la línea tiene que ser desalojada, va y copia su valor en la DRAM. **Esta política no mantiene coherencia pero es muy performante ya que el procesador siempre escribe en la cache.**

### Coherencia en sistemas SMP

En un sistema multi-procesador, la política de write back es, en principio, inviable. Uno quiere mantener la coherencia lo más posible, así que utilizaría write thorugh o write through buffered.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2012.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2012.png)

**SMP = Symmetric Multi-Processing**

Se dice simétrico porque los procesador son iguales, son simétricos.

**Escenario:**

- Tenemos dos thread de un mismo proceso ejecutando en los dos procesadores con las mismas variables y justo tienen la misma variable cada uno en su cache.
- Uno de los dos thread modifica la variable en cache, con lo cual, el dato queda incoherente para la cache del otro procesador y para la DRAM.
- **Problema: Ni la DRAM ni la otra cache se enteran que la variable se modificó.**

Independientemente de la política que utilicemos, tenemos que restaurar la coherencia lo más rápido posible. Lo más dificil es que el otro procesador se entere del cambio.

**Solución:** **Agregamos el Snoop BUS ("BUS de espiar").**

### Snoop BUS

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2013.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2013.png)

El procesador 1 escribió una variable. La variable se refrescó también en la DRAM (asumiendo que utilizamos write through o write through buffered). Esto quiere decir que por el BUS del sistema viajó la variable. Con el Snoop BUS, los controladores de cache espían el BUS de address y el BUS de control dentro del BUS del sistema para saber qué hacen los demás. Entonces, cuando un procesador detecta una dirección que se está escribiendo por otro procesador, marca la dirección como inválida en su memoria cache, así la próxima vez la va a buscar a la DRAM. **El Snoop BUS resuelve el problema de la coherencia.**

**El Snoop BUS no es BUS entre los controladores. No une a los controladores. Une a cada controlador con el BUS de address del sistema, pero en sentido inverso.**

**Siguiente motivación:**

Si bien el Snoop BUS resuelve el problema de coherencia, nos gustaría hacer optimizaciones. **Queremos ver si existe alguna forma de usar Copy Back, ya que es la mejor política de escritura. Si bien podríamos usar Write Through Buffered siempre, y utilizar siempre la cache, de todas formas estaríamos utilizando el Bus del Sistema todo el tiempo cuando a no es necesario. En el escenario que vimos hasta ahora, copy back no es factible, ya que depende de que la memoria DRAM esté siempre luego de escribir.** Deberíamos buscar una forma de utilizar copy back todo lo que se pueda, y cuando no queda más remedio, utilizar write through o write through buffered.

- Cuando un procesador escribe un dato que está en otra cache, copy back no sirve.
- Pero cuando sólo ese procesador tiene esa variable, no hace falta actualizarlo en la DRAM inmediatamente (para qué la va a estar actualizando en la DRAM del sistema si no la tiene nadie más?).
- Si el procesador pudiera saber si alguien más tiene esa variable, podría hacer copy back mientras solo él la utilice.

### Protocolo MESI

**M.E.S.I. = Modified, Exclusive, Shared, Invalid**

Son los cuatro estados que puede tomar cada línea de cache en un controlador.

**`Modified`:**

Esta es la única copia de la línea en una caché pero la modifiqué. La tengo dirty. **Esto me permite hacer copy back.** **En este estado tengo la certeza de que soy el único poseedor de la variable.**

**`Exclusive`**:

Esta es la única copia de la línea en una caché y además está limpia (sin modificar). **En este estado tengo la certeza de que soy el único poseedor de la variable.**

**`Shared`:**

No soy el único que la tiene. **Puede** estar almacenada en los caches de otros procesadores. **No puedo hacer copy back. Hago write through y que los demás utilicen el Snoop BUS.**

**`Invalid`:**

La línea de cache no es válida. Es basura.

### Coherencia en sistemas SMP con MESI

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2014.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2014.png)

**Se agregan las líneas Shared y RFO (Request For Ownership).**

### Operación del Protocolo MESI

- Todas las transacciones a líneas que un procesador quiere ejecutar (ya sea una lectura o escritura de línea) se resuelven en el cache, excepto si la línea en el cache está marcada como `Invalid`.
- Las líneas marcadas como `Invalid` se buscan en DRAM.
- El controlador cache que posee líneas en estado `Exclusive`, monitorea siempre por el Snoop BUS cada transaccion en la DRAM.
    - Si detecta un acceso a una línea que tiene almacenada en su cache, el controlador owner cambia su estado a `Shared` y activa la línea Shared para enviar un broadcast al resto. Todos se enteran que alguien tiene esa línea shared.
- Una línea que está en estado `Shared` o en estado `Exclusive` puede ser descartada y pasar a inválida en cualquier momento sin avisarle a nadie.
- Una línea `Modified` también puede ser descartada, sólo que en este caso se requiere actualizar previamente la DRAM.
- Una línea que esta `Modified` o `Exclusive` se puede escribir desde la CPU en cualquier momento. En caso de que esté `Exclusive`, pasa a `Modified`.
- En el caso en que se necesite escribir en una línea cuyo estado sea `Shared`, el protocolo indica que todas las demás caches que tienen esa línea la invaliden previamente. Para ello se emplea una operación broadcast denominada **Request For Ownership**.
- Un cache que tiene una línea en estado `Modified` y detecta por el Snoop BUS que alguien la lee, también debe insertar el dato contenido por la línea, ya que está incoherente con la DRAM. Para ello realiza lo siguiente:
    - Activa la línea RFO, indicándole a los demás que ese dato está incoherente.
    - Escribe en la DRAM el valor actual de la línea. El lector copiará ese valor correcto a su cache cuando aparece en el BUS de datos.
    - Ambos pondrán la línea en `Shared`.
- Una línea en estado `Shared` pasa a `Invalid` cuando se recibe un RFO.

### Read For Ownership

- El protocolo de coherencia combina una escritura de una línea con un broadcast de invalidación al resto de los controladores.
- Es enviada por un controlador cache si intenta escribir una línea que está en estado `Shared` o está en estado `Invalid`.
- Como resultado, el resto de los cache que tengan esa línea la tienen que invalidar.
- Desde el punto de vista del controlador cache, es una lectura de línea cacheada con toma de BUS del sistema para escribir el contenido de la línea en la memoria DRAM.

### Protocolo MESI - Diagrama de estados

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2015.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2015.png)

- PR: Processor Read (yo)
- BR: Bus Read (otro controlador lee, detecto un read en el bus)

## Arquitecturas de cache avanzadas

### Cache Multinivel

En algún momento de la evolución de los procesadores, la tecnología de integración alcanzó scalings que permitieron meter controladores cache + cache level 1 en un chip, y dejar una cache level 2 afuera del chip.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2016.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2016.png)

La cache level 1 la metieron adentro del chip del procesador para incrementarle la frecuencia. La cache level 2 estaba afuera del chip y su frecuencia tenía que ser la del estándar PCI. Adentro del chip, la frecuencia se podía duplicar.

### 2do. Nivel On chip

- Mete el cache level 2 también dentro del chip.
- **Cache level 1 era como una arquitectura Harvard (separaba datos de instrucciones).**

### 3er. Nivel On chip

- Arranca con Intel Netburst.
- Mete el cache level 3 también dentro del chip.

### Smart Cache

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2017.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2017.png)

# ________________________________________________________________________________________

# Paralelismo a Nivel de Instrucción

## Pipeline

### Máquina de estados elemental

Una instrucción en un computador se ejecuta en etapas. Según el modelo de Von Neumann, las etapas son: fetch, decode y execute. Hoy en día cada instrucción se puede desdoblar en más etapas.

Antes del 80286, la mayoría de los microprocesadores ejecutaban cada etapa en serie. Es decir, en el primer ciclo de clock, se ejecutaba una etapa de una instrucción, luego se ejecutaba la siguiente etapa de la misma instrucción, y así sucesivamente hasta haber ejecutado la última etapa de esa instrucción, para luego empezar ejecutando la primer etapa de la siguiente instrucción.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2018.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2018.png)

Ejecución de una instrucción de forma serializada

**Problema:** Para ejecutar la siguiente instrucción hay que esperar a que la primer instrucción termine de ejecutarse completamente. No podríamos ejecutar dos instrucciones a la vez?

### Pipeline

Arquitectura que permite crear el **efecto** de superponer en el tiempo la ejecución de varias instrucciones a la vez con el objetivo de mejorar la performance.

**Requiere muy poco hardware adicional.**

**Idea:** Mientras se ejecu

**Ejemplo:**

5 *stages* (etapas):

1. Opcode fetch
2. Decode
3. Operand fetch
4. Execution
5. Retire result

Pipeline **ideal** para esas 5 etapas:

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2019.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2019.png)

**Primer ciclo:** Opcode fetch instr #1.

**Segundo ciclo:** Opcode fetch instr #2 + Decode instr #1.

**Tercer ciclo:** Opcode fetch instr #3 + Decode instr #2 + Operand fetch instr #1.

**Cuarto ciclo:** Opcode fetch instr #4 + Decode instr #3 + Operand fetch instr #2 + Exec instr #1.

**Quinto ciclo:** Opcode fetch instr #5 + Decode instr #4 + Operand fetch instr #3 + Exec instr #2 + Retire result instr #1. **Recién acá se libera el primer resultado (el de la instrucción #1).**

**Conclusiones:**

- El pipeline demora tantos ciclos de clock en llegar al primer resultado como etapas tenga.
- En un pipeline de 5 etapas, en el caso de que cada etapa consuma solamente 1 ciclo de clock, obtenemos un resultado de instrucción por cada ciclo de clock a partir de la quinta etapa.
- Este escenario es teórico y no responde a la situación real.
- Agregar etapas parecía mejorar la performance del pipeline.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2020.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2020.png)

### Hazards (obstáculos)

Cuando hay un obstáculo se denomina **pipeline stall (congestión del pipeline).**

**Obstáculos estructurales:**

- Una etapa no está suficientemente atomizada, tiene muchas cosas que hacer y no se puede completar en un ciclo de clock (tarda mucho).
- Si dos instrucciones que van a utilizar esta etapa están más o menos próximas en el tiempo, o están a una distancia temporal mayor a la que la etapa consume para procesar, van a caer en un conflicto de recursos para su ejecución. La que está primera en el pipeline va a tomar la etapa y cuando llegue la que venía en segundo lugar y quiera esa etapa del pipeline no va a poder.

**Ejemplo:**

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2021.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2021.png)

En el ciclo 5, la etapa de Opcode Fetch de la instrucción #5 y la etapa de Operand Fetch de la instrucción #3 quieren acceder a memoria a la vez. La solución es elegir alguna de las dos y demorar la otra, corriendo todo el pipeline. Un criterio posible es priorizar la instrucción que este en la etapa más avanzada. En este caso, la instrucción #3, la cual ya está en la etapa de Operand Fetch.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2022.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2022.png)

Luego, en el ciclo 8, también hay un conflicto. Lo soluciono haciendo lo mismo (priorizando la instrucción #4, que la más avanzada).

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2023.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2023.png)

Luego, en el ciclo 9, también hay un conflicto. Lo soluciono haciendo lo mismo (priorizando la instrucción #5, que la más avanzada).

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2024.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2024.png)

**Posibles soluciones:**

- **Cualquier solución cuesta hardware**
- En el caso de accesos a memoria:
    - Podemos desdoblar el cache L1 en cache de datos y cache de instrucciones.
    - Emplear buffers de instrucciones implementados como pequeñas colas FIFO.
    - Ensanchamiento de los buses más allá de los anchos de palabra del procesador. Esto permite, por ejemplo, hacer que un opcode fetch se resuelva en un ciclo de clock. Si ensancho los buses, en un ciclo de clock leo mucha más información. Es una forma de fetchear muchas instrucciones de una, o traerse muchos operandos de una. Tiene sentido por el principio de vecindad.
- Aumentar la capacidad del pipeline. Hacer etapas más simples, capaces de resolver en un ciclo de clock su tarea.

**Obstáculos de datos:**

- Una instrucción pide un dato antes de que éste esté disponible por efecto de la secuencia lógica que contiene el programa.

Ejemplo:

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2025.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2025.png)

La instrucción dsub depende del resultado de la instrucción dadd.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2026.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2026.png)

En el quinto ciclo, se genera el resultado de la suma, pero dicho resultado es requerido por `dsub`, `and`, `or` y `xor`. Las instrucciones `dsub` y `and` no pueden conseguir a tiempo el resultado en R1 para poder usarlo como operando.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2027.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2027.png)

**Posibles soluciones:**

- **Forwarding:**

    Retroalimento la ALU con la salida en el mismo ciclo que termina de ejecutarse la operación aritmética, así, en el ciclo 5, la ALU ya tiene el operando correcto sin haber pasado por R1. No soluciona el problema del todo, pero se ahorra un ciclo.

    ![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2028.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2028.png)

    No siempre se puede hacer forwarding. Si la primer operación no pasa por la ALU no se puede hacer forward.

    ![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2029.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2029.png)

**Obstáculos de control:**

- Son causados por saltos.
- Un branch es lo peor que le puede pasar a un pipeline.
- El branch hace que todo lo que tenias preprocesado deba descartarse. Esto se conoce como **branch penalty**.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2030.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2030.png)

## Unidades de Predicción de saltos

### Necesidad de predicción de saltos

- Cuanto más profundo es un pipeline, más grande es la penalización de un branch. Ejemplo: para un pipeline de 5 etapas de 1 ciclo de clock cada una, la penalización es de 4 ciclos de clock.
- A medida que aumenta la complejidad del procesador, también es lógico que las etapas del pipeline aumenten (sencillamente porque el procesador es más complicado).
- **En la práctica los Branch Predictors se implementan en la etapa de fetch.**

Predecir un salto es poder predecir el valor del program counter. Predecir un salto significa empezar a fetchear de una manera anticipada, para reducir el hueco en el pipeline. Hay situaciones en las que es imposible predecir.

### Asumir non-taken

**Asume por defecto que el salto nunca se toma.** Entonces el pipeline sigue fetcheando las instrucciones siguientes a la instrucción del branch. Es útil cuando el salto es hacia adelante. Por ejemplo:

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2031.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2031.png)

### Asumir taken

**Asume por defecto que el salto siempre se toma.** Entonces el pipeline empieza a fetchear las instrucciones que están en la dirección de salto. Es útil en un loop donde se salta hacia atras. En general las iteraciones se hacen muchas veces, con lo cual los saltos son más probables en esos casos. Por ejemplo:

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2032.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2032.png)

### Delayed branch

- Se introdujo en los primeros procesadores RISC.
- Tenemos N slots llamados Delay Slots.
- Las N instrucciones que vienen después de la instrucción de branch se ejecutan siempre, sin importar del camino tomado por el branch.
- Luego aplicas el resultado según se necesite o no.
- Ejemplo con N=1:

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2031.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2031.png)

### Loop unrolling

**Es una tarea para el compilador.** Consiste en convertir los ciclos en instrucciones secuenciales, sin branches.

### Predicción de saltos dinámica

Los métodos anteriores dependían del compilador, del set de instrucciones. El hardware del procesador no hacía ningún análisis de código para analizar la instrucción.

**Idea:** Que ahora el procesador haga análisis de flujo y tome decisiones acorde a lo que va viendo adelante de la instrucción de salto.

**Debemos predecir:**

1. Si la instrucción es de salto o no.
2. Si es taken o non-taken.
3. La dirección de salto (if taken).

**Branch Prediction Buffer (Last Time Predictor)**

- Tabla en caché que sirve para saber si el salto va a ser taken o non-taken.
- Se guarda como un bit extra en la BTB.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2033.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2033.png)

- Funciona bien para patrones tipo: TTTTTTTTTTTTTTTNNNNNNNNNNN.
- **El problema:** Funciona mal para patrones tipo TNTNTNTNTNTNTNTNTNT (0% accuracy en ese caso).
- **Solución:** Armar una máquina de estados con dos bits.
- **Idea:** **No vamos a cambiar nuestra predicción al primer desacierto, la vamos a cambiar al segundo.**

**Si estamos en el estado de "Predice TAKEN (fuerte)" y la branch fue non-taken, pasamos al estado de "Predice TAKEN (debil)" en vez de pasar a un estado de "Predice Non-TAKEN".**

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2034.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2034.png)

**Branch Target Buffer**

- Tabla en caché que sirve para saber la dirección de salto (if taken).
- Cada entrada contiene la dirección de la instrucción de salto y la dirección target resuelta (en vez de los bits taken o non-taken, a diferencia de la Brancg Prediction Buffer).
- Es más rápido que el Branch Prediction Buffer (ya que ahora directamente podemos obtener la dirección de salto de esta tabla), pero el criterio sigue siendo el mismo.
- La proxima vez que nos topamos con el branch, la buscamos en la BTB. Si tenemos un hit, usamos la address guardada en la BTB para fetchear instrucciones.
- Si el valor no se encuentra en la BTB, se asume taken.
    - Si el resultado es Non-taken se acepta el delay en el pipeline y no almacena nada en la BTB.
    - Si el resultado es taken, ingresa el valor en la BTB.
- Si el valor se encuentra en la BTB, se aplica el campo de la dirección target almacenado.
    - Si el resultado es taken, no hay penalidad. No se guarda en el BTB ningún nuevo valor ya que nos sirve.
    - Si el resultado es non-taken, sigue la máquina de estados de **Branch Prediction Buffer**.

## Superscalar

Consiste en paralelizar el pipeline, agregando otro.

**Ventaja:** Poder ejecutar más de una instrucción por ciclo de clock, en paralelo.

### Superscalar de dos vías

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2035.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2035.png)

El Pentium fue el primer procesador superscalar de la familia Intel.

### Problemas

- Los [obstáculos estructurales](https://www.notion.so/asdolo/Resumen-Final-Orga2-7e347eedef584449a5560e58e2399975#9099dba0628641ff9c93e12f10a9c42e) ahora quedan más expuestos que antes. Ahora cada etapa, ademas de lidiar con las otras etapas de su propio pipeline (que pueden acceder en simultáneo a la misma instrucción o dato), también tiene que lidiar con las mismas etapas del pipeline de al lado, que también pueden ir a buscar datos o código. **Por eso los buses son muy importantes. Es importante separar buses de datos y address para minimizar los obstáculos estructurales.**
- Cuantas más vias tenga el pipeline, más concurrencia de memoria.
- Si tengo dos ALUs, puedo ejecutar una instrucción en cada uno. En el caso de que una ALU dependa del resultado de la otra, esto no es posible.
- Una falla en el branch prediction limpia **todos** los pipelines.

## Scheduling Dinámico

El Scheduling de instrucciones es la forma en que el procesador organiza la ejecución de instrucciones. 

Hasta antes de superscalar, el scheduling era estático. Ahora, con superscalar, el scheduling es dinámico.

### Obstáculos de Datos

Para los obstáculos de Datos con superscalar, no podemos usar forwarding. El estudio de dependencias de datos se debe extender a instrucciones en los diferentes pipelines.

**Idea fuerza:**

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2036.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2036.png)

- La instrucción 2 (add.d) depende de la instrucción 1 (div.d), que para completarse requiere muchos ciclos de clock (debido a otros tipos de obstáculos que afectan a la instrucción 1 pero no afectan a la instrucción 2).
- O sea, las instrucciones 2 y 3 no pueden ser ejecutadas hasta que la instrucción 1 termine.
- Esta obstrucción deja a todo el procesador sin uso hasta que la instrucción 1 termine.
- **La instrucción 3 (sub.d) no tiene ninguna dependencia con las instrucciones previas, sin embargo, la instrucción queda esperando.**

**Solución: Ejecución fuera de orden. Ejecuto la instrucción 3 igual, sin esperar.** 

# Ejecución Fuera de Orden

## Conceptos fundamentales

### Idea fuerza

- Enviar las instrucciones a ejecución independientemente del orden que tengan en el código. Con qué criterio?
- Una vez que una instrucción es decodificada, puedo saber si esa instrucción tiene atascos (estructurales, de datos, etc).

### Ejecución Fuera de Orden vs En Orden

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2037.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2037.png)

- Separamos la etapa de resultado en resultado y escritura.
- Si bien vamos a ejecutar fuera de orden, no podemos aplicar los resultados de las operaciones en un orden distinto al que está establecido en el programa porque sencillamente alteraríamos la lógica del programa y eso es inadmisible (por algo las instrucciones están en ese orden).
- Como las instrucciones están atomizadas en distintas etapas, lo que vamos a tratar de hacer es que una parte de ese pipeline trabaje fuera de orden, y otra parte trabajen en orden.
- En general, la etapa de ejecución es la etapa que se hace fuera de orden.
- La etapa de write va en orden para no alterar el comportamiento.

### Riesgos

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2038.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2038.png)

- **Write, After Read (WAR):**

    La instrucción 3 escribe F8 y después la instrucción 2 lee F8. **La operación de la instrucción 2 tiene un operando inválido.**

- **Write, After Write (WAW):**

    La instrucción 4 escribe F6 y después la instrucción 2 escribe F6. **Me quedo con un valor más viejo de F6 en la instrucción 5.**

- **Read, After Write (RAW):**

    La instrucción 2 lee F0 y después la instrucción 1 escribe F0. **Este es el clásico obstáculo de datos que vimos al principio, antes de superscalarx. Se soluciona stalleando el pipeline.**

### Excepciones imprecisas

- Las operaciones generan excepciones, que a su vez generan interrupciones para resolver las excepciones.
- Si estamos ejecutando fuera de orden una instrucción que genera una excepción, no deberíamos generar la excepción fuera de orden, ya que eso limpiaría el pipeline para saltar a la interrupción.
- Se debe preservar ese escenario.
- Tendríamos que poder "bufferear" el estado de esa excepción.

## Métodos prehistoricos

### Scoreboarding

- Es el primer método que se desarrolló para ejecutar fuera de orden.
- Es el menos sofisticado.
- Se implementó en la CDC 6600 en **1964**.
- No se usa.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2039.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2039.png)

- Una Unidad de Búsqueda arma una cola de prebúsqueda que contiene las próximas instrucciones.
- La Unidad de Envío toma lo que hay en la cola de prebúsqueda y lo pone en un Scoreboard de capacidad 4.
- La Unidad de Lectura de Operando se fija si los operandos de las instrucciones en el Scoreboard estaban disponibles y en función de eso las despacha a las Unidades Funcionales.

**Desventajas:**

- Los operandos se leen directamente en los registros, así que no se podía hacer forwarding. No tenía una lectura prolija de los operandos.

## Método actual

### Modelo de Tomasulo

- 1967: Tomasulo presentó un trabajo de Scheduling dinámico en la unidad de punto flotante del mainframe IBM 360/91.
- **Trata de minimizar los riesgos RAW.**
- **Neutraliza los riesgos WAR y WAW.**

**Tomasulo se preguntó qué necesita un procesador para poder ejecutar fuera de orden?** 

1. **Mantener un "enlace" entre quien produce un dato y quien o quieres lo consumen. La lógica del procesador tiene que tener claro, para cada operando destino, quién lo va a utilizar en las instrucciones posteriores.**
2. **Mantener en espera las instrucciones que todavía no se puedan ejecutar, es decir, que tengan al menos un operando en espera.**
3. **Las instrucciones tienen que saber cuándo están disponibles sus operandos.**
4. **Ejecutar la instrucción cuando todos sus operandos estén "Ready".**

### **Register Alias Table (RAT)**

- **Soluciona el problema de [mantener un enlace entre el productor de un dato y sus consumidores](https://www.notion.so/asdolo/Resumen-Final-Orga2-7e347eedef584449a5560e58e2399975#c0321a3e163c45348807d0dbb4648bb1).**
- A cada operando, se le asocia un alias y se indica si es válido o no.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2040.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2040.png)

- **Tag:** Alias/renombre del registro.
- **Valor:** Valor del registro.
- **Validez:** Dice si el valor es válido o no. Si es inválido significa que otra instrucción todavía no escribió el nuevo valor de este registro.

**Ejemplo:**

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2041.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2041.png)

- La instrucción 2 tiene un riesgo WAR en F8 con la instrucción 3.
- La instrucción 5 tiene un riesgo WAR en F6 con la instrucción 2.
- Reemplazamos los operandos problemáticos por sus respectivos aliases (S y T).

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2042.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2042.png)

### **Reservation Station (RS)**

- **Soluciona los otros tres problemas del algoritmo de Tomasulo.**
    - **Soluciona el problema de [mantener en espera las instrucciones que todavía no se pueden ejecutar](https://www.notion.so/asdolo/Resumen-Final-Orga2-7e347eedef584449a5560e58e2399975#ec2674e5cbde4c80a09bc7b5579de51b).**
    - **Soluciona el problema de [saber cuándo están disponibles los operandos de una instrucción](https://www.notion.so/asdolo/Resumen-Final-Orga2-7e347eedef584449a5560e58e2399975#c00f1cc2022b445c88df8598b0a030c3).**
    - **Soluciona el problema de [ejecutar la instrucción cuando todos sus operandos estén disponibles](https://www.notion.so/asdolo/Resumen-Final-Orga2-7e347eedef584449a5560e58e2399975#d5c52ffa904c4430a8947f9d5ddf09d0).**
- Cada línea de la RS es una instrucción y sus dos operandos.
- La RS tiene un tamaño limitado.
- Una vez realizado el renombre se le asigna, a la instrucción, una Reservation Station.
- Una Reservation Station es un subsistema de hardware compuesto de bancos de registros internos que se encarga de mantener las instrucciones en espera hasta que estén listas para ser ejecutadas. Éste chequea constantemente por la disponibilidad de los operandos de la instrucción. Para cada uno de ellos cuyo valor no esté disponible, la RS guarda el tag que se le asignó en el paso anterior.
- Cada vez que una unidad de ejecución pone Ready un operando, transmite su tag asociado junto con su valor a todas las RS. Cuando una instrucción tiene todos  sus operandos Ready, la RS espera a que la unidad funcional asociada a ella esté libre y luego la despacha.

    ![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled_Diagram_(1).png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled_Diagram_(1).png)

### **Common Data Bus:**

- Es un datapath que va por toda la arquitectura.
- **Se usa para brodcastear el tag y value que salen de las ALU hacia la Register Alias Table y las RS para que tengan esos valores actualizados.**

### FPU de [IBM 360/91](https://www.notion.so/asdolo/Resumen-Final-Orga2-7e347eedef584449a5560e58e2399975#571969b6eefd4ed8a76aec1777096105) con la mejora de Tomasulo

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2043.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2043.png)

### Algoritmo de Tomasulo

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2044.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2044.png)

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2045.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2045.png)

**El algoritmo se ejecuta para cada instrucción del programa.**

// Defino si meto la instrucción en la RS o si stalleo el pipeline

- Chequeamos que haya lugar en la RS para todos los operandos de la instrucción (tanto fuentes como destino).

    // Hay lugar en la RS

    1. Creo un alias para cada operando no válido de la instrucción
    2. Insertamos la instrucción y sus operandos renombrados en la RS. Estos valores los sacamos directamente de la Register Alias Table.

- Si no hay lugar, stall

// La instrucción ya está en la RS

- Cada instrucción almacenada en la RS hace:
    1. Chequear el Common Data Bus en busca de tags que correspondan a sus operandos fuente.
    2. Cuando se detecta el tag que se esta esperando, se graba el valor de la fuente en la RS.
    3. Cuando ambos operandos estan Ready, la instrucción se marca Ready para ser ejecutada.

// La instrucción ya está lista para ser ejecutada

- Me fijo si hay alguna Unidad Funcional disponible (quien ejecuta la instrucción)

    // Hay una Unidad Funcional disponible

    1. Si hay, despacho la instrucción

    **// Listo, se despachó la instrucción ✅**

- Me fijo si finalizó la ejecución de la instrucción

    // Finalizó la ejecución de la instrucción

    1. La Unidad Funcional que ejecutó la instrucción broadcastea, usando el Common Data Bus, el tag y valor resultante.

        // Esto significa que el operando destino de esta instrucción ahora está Ready. Entonces se lo comunico a los demás vía broadcast

        // A la Register Alias Table le llega, por broadcast, el tag y valor

    2. Si tiene ese tag guardado:
        1. Escribe el valor que le llega en el registro (R1, R2, etc), según corresponda con el tag.
        2. Marca ese tag como válido.
        3. Libera el tag.

### Ejemplo del Algoritmo

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2046.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2046.png)

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2047.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2047.png)

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2048.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2048.png)

## Especulación por Hardware

### Reordenando los resultados

- En el modelo de Tomasulo no hay ningún bloque que asegure que los resultados se escriben en orden.
- **Más allá de que las instrucciones puedan ejecutarse en paralelo, la aplicación de los resultados necesariamente debe ser en orden.**
- Las implementaciones posteriores introdujeron un módulo para hacer eso que se llama ReOrder Buffer (ROB).
    - Es un bloque parecido a la Reservation Station de Tomasulo. Contiene los valores de resultado de la etapa de ejecución y a qué registros deben ir.
    - El resultado permanece en el ROB desde que se obtenga hasta que se copie en el operando destino.
    - Contiene los campos `Tipo de instrucción`, `Destino`, `Valor` y `Ready`.
    - Escribe un valor en su destino si los anteriores valores están en ready o ya fueron aplicados. Se pueden escribir varios valores en el mismo ciclo si están todos en ready.

# Casos prácticos que mezclan todo lo visto

## Pentium Pro

- Fue un procesador muy importante dentro de la genealogía de Intel. Inauguró la microarquitectura P6, cuyo fundamento de ejecución fuera de orden se mantiene hasta la fecha.
- Fue el primer procesador de Intel que ejecutaba fuera de orden. Los Pentium ejecutaban en orden. Los Pentium Pro ejecutaban fuera de orden.
- Luego vinieron el Pentium II, Pentium II Xeon, Celeron, Pentium III y Pentium III Xeon.
- Todos estos se basaban en una estructura interna denominada Three Cores Engine.

### Three Cores Engine

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2049.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2049.png)

- **Tres cores:**
    1. **Unidad de decodificación y búsqueda (Fetch/Decode Unit)**
    2. **Unidad de despacho y ejecución (Dispatch/Execute Unit)**
    3. **Unidad de retiro (Retire Unit)**
- Cache de datos y cache de código separadas
- Scheduling dinámico
- Basado en una ventana de instrucciones y no en un pipeline superescalar
- **Las instrucciones se traducen en microoperaciones básicas.**
- **Las microoperaciones se almacenan en el instruction pool (que no es más que un reorder buffer).**
- Los tres cores tienen visibilidad de esa ventana de ejecución.
- La ejecución fuera de orden y especulativa es para las microoperaciones.
- Las microoperaciones tenían todas el mismo tamaño, como si fuera RISC.

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2050.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2050.png)

### Unidad de Interfaz con el Bus

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2051.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2051.png)

- Es un bloque que trabaja parcialmente en orden.
- Está encargada de conectar los tres cores con el mundo exterior.
- Divide los modelos:
    - De la Unidad de Interfaz hacia afuera (incluyendo la Cache L2 afuera), es Von Neumann.
    - De la Unidad de Interfaz hacia adentro es Harvard. La Cache L1 está separada en datos y código.
- Soporta hasta cuatro accesos concurrentes a la Cache L2.
- El acceso al Bus del sistema se regula todo por MESI y snooping para asegurar la coherencia de la memoria.

### Unidad de decodificación y búsqueda

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2052.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2052.png)

- **Instruction Cache L1:** tiene 16 bytes por línea. Entrega los 16 bytes alineados a la Unidad de Decodificación.
- **Puntero Next IP:** Apunta a la línea donde está la siguiente instrucción o a la de la instrucción target de un salto. Es decir, indica qué instrucción tiene que ir fetcheando el pipeline.
- **Tres Instruction Decoders:** Dos de instrucciones simples y uno de instrucciones complejas.
    - Los decodificadores de instrucciones simples traducen la instrucción en una microoperación
    - El decodificador de instrucciones complejas traduce la instrucción en dos o más microoperaciones.
- **Microcode Instruction Sequencer:** Convierte una instrucción todavía más compleja en una secuencia de microoperaciones.

### Unidad de despacho y ejecución

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2053.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2053.png)

- **Esta unidad es la única que trabaja fuera de orden.**
- Selecciona las microoperaciones dependiendo del estado (no del orden) desde el pool de instrucciones.
    - Si el estado de la microoperación indica que sus operandos están disponibles, la Reservation Station verifica que alguna unidad funcional esté libre para su ejecución y le envía la microoperación.
- El resultado se escribe en el pool de operaciones (ReOrder Buffer).
- **Branches:** Las microoperaciones se marcan como saltos en el ReOrder Buffer y también se escribe allí la dirección predicta por el BTB (Branch Target Buffer). Si el salto falla, limpia el ROB, las RS (limpia todo).

### Unidad de retiro

![Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2054.png](Resumen%20Final%20Orga2%20a7de9775164c482cad5121a79d2a7fdc/Untitled%2054.png)

- Mira permanentemente el estado de cada instrucción en el ROB.
- No sólo chequea su estado, sino que las reinserta en el orden en que ocupan en el programa.
- Esto incluye el procesamiento de interrupciones, excepciones, traps, breakpoints y predicciones fallidas.
- **Retirement Register File:** Se encarga de escribir los operandos resultantes en los registros de la arquitectura.
- **Unidad de interfaz de memoria:** Aplica los datos en el Cache L1 de datos.

## Intel NetBurst (Pentium 4)

- Es el siguiente en la línea que marcó una cierta innovación.
- En vez de Cache L1 de código tenía un **Trace Cache:**
    - Es una cache que guarda microoperaciones en vez de instrucciones.

# Procesadores Multithread

- Los procesadores multithread tienen dos estados arquitecturales.
- **No son dos procesadores, sino que son dos vistas de procesadores.**
- **Se duplica lo necesario y se comparte lo crítico.**
- Se duplica:
    - La cola de microoperaciones
    - El Instruction Pointer
    - Register Alias Table
    - El ROB
- Se comparte:
    - La cache L1 de datos
    - Las unidades de ejecución
    - Los registros internos de la arquitectura
    - Las Reservation Station
    - etc
- **Conclusión:** La mayoría de cosas se comparte. Con un 15% más de electrónica se logra un aumento mucho mayor a 15% en la performance.

# Multicore y Manycore

- **Es poner dos procesadores completos dentro del chip.**
- Dejaron obsoletos a los procesadores multithread.
- **Es mejor muchos cores sencillos que un sólo core superpoderoso. Con más cores tenemos igual performance y menor consumo.**
