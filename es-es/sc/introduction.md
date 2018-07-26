# Introducción al Contrato Inteligente de NEO

## ¿Qué es un contrato inteligente?

Un contrato inteligente es un conjunto de compromisos que se definen en formato digital, incluido el acuerdo sobre cómo los participantes en el contrato cumplirán estos compromisos. La tecnología de cadena de bloques nos proporciona un sistema descentralizado, no alterado, altamente confiable en el que los contratos inteligentes son extremadamente útiles. Los contratos inteligentes son una de las características más importantes de las tecnologías de cadena de bloques y la razón por la que puede decirse que las cadenas de bloques son una tecnología disruptiva. Aumenta la eficiencia de nuestra estructura social cada día que pasa.

## ¿Cuáles son las características de los contratos inteligentes NEO?

El Contrato Inteligente 2.0 de NEO incluye las siguientes características: certeza, alto rendimiento y capacidad de expansión. Los tipos de contrato incluyen: contratos de validación, contratos de función y contratos de aplicación.

Desde el punto de vista del rendimiento, NEO utiliza la ligera NeoVM (NEO Virtual Machine) como su entorno para la ejecución de contratos inteligentes. Arranca muy rápido y consume una pequeña cantidad de recursos y es adecuada tanto para contratos inteligentes como procedimientos cortos. La compilación estática y el almacenamiento en caché de los contratos de punto de acceso pueden mejorarse significativamente con la tecnología JIT (compilador en tiempo real). La configuración instructiva de la máquina virtual NEO proporciona una serie de instrucciones criptográficas para optimizar la eficiencia de la ejecución de algoritmos criptográficos en los contratos inteligentes. Además, las instrucciones de manipulación de datos proporcionan soporte para arreglos y estructuras de datos complejas directamente. Todo lo anterior mejorará el rendimiento en el Contrato Inteligente 2.0 de NEO.

El Contrato Inteligente 2.0 de NEO logra un enfoque escalable a través de una combinación de alta concurrencia y partición dinámica, combinada con su diseño de bajo acoplamiento. El procedimiento de contrato de bajo acoplamiento se ejecuta en una máquina virtual (máquina virtual NEO) y se comunica con el exterior a través de la capa de servicio interactiva. Por lo tanto, la gran mayoría de las mejoras a la función de contrato inteligente se puede lograr a través del API de la capa de servicio interactivo.

## Escribir contratos inteligentes en cualquier idioma

Desde el punto de vista lingüístico, la diferencia entre el Contrato Inteligente 2.0 de NEO y Ethereum es más intuitiva: a diferencia del lenguaje Solidity original de Ethereum, el contrato inteligente NEO puede ser utilizado directamente por casi cualquier lenguaje de programación de alto nivel. Los primeros idiomas soportados son C #, VB.Net, F #, Java y Kotlin. NEO proporciona compiladores y complementos para estos idiomas, que se utilizan para compilar lenguajes de alto nivel en conjuntos de instrucciones soportados por las máquinas virtuales NEO. El primer compilador será para MSIL (lenguaje intermedio de Microsoft), así que teóricamente cualquier lenguaje .Net y cualquier lenguaje que pueda traducirse en MSIL serán inmediatamente compatibles.

Los lenguajes actualmente admitidos son:

1. C #, VB.Net, F #
2. Java, Kotlin

Los lenguajes que planeamos apoyar incluyen:

1. C, C++, GO
2. Python, JavaScript

Con soporte para varios idiomas, más del 90% de los desarrolladores pueden participar directamente en el desarrollo de un contrato inteligente NEO sin necesidad de aprender un nuevo idioma. El código del sistema empresarial existente podría incluso ser directamente 
trasladado a la cadena de bloques. Creemos que esto aumentará en gran medida la popularidad general de la futura cadena de bloques.

Además, los contratos inteligentes tradicionales son difíciles de depurar y probar dada la falta de soporte de herramientas. NEO, sin embargo, proporciona soporte para la depuración a nivel de máquina virtual NEO, lo que te permite desarrollar el Contrato Inteligente 2.0 de NEO mucho más fácilmente y mucho más rápido.

## Desencadenadores de contratos inteligentes

Existen dos formas de desencadenar contratos inteligentes:

1. Contrato de autenticación de usuario: Aquí el contrato inteligente es una cuenta. Cuando el usuario usa un activo (por ejemplo una transferencia) de la cuenta contrato se desencadena el contrato inteligente.
2. Enviar manualmente una solicitud de transacción de contrato inteligente: Aquí el usuario genera una transacción (Invocación de Transacción) para desencadenar la implementación de un contrato inteligente.

## Máquina Virtual de Neo

Neo-VM es la máquina virtual que ejecuta el código de los contratos inteligentes de Neo. Hablamos de máquina virtual en el sentido estricto del término, no en referencia a sistemas operativos o programas que puedan simularlas como son VMware o Hyper-V.

Por ejemplo, en la JVM de java o en el CLR de .NET el código fuente es compilado en su correspondiente bytecode y ejecutado por su correspondiente máquina virtual. Tanto la JVM o el CLR ejecutarán el bytecode de la misma forma que si se ejecutara en una máquina física real. Aún así, las correspondientes instrucciones binarias se siguen ejecutando en una máquina física. La máquina física obtiene las instrucciones de la memoria, las transfiere a la CPU a través del bus, se decodifican, se ejecutan y almacena el resultado.

### Arquitectura de la máquina virtual

<img style="vertical-align: middle" src="C:/neo-project/docfx/docs/es-es/sc/assets/neo-vm.jpg">

El diagrama de arriba muestra la arquitectura del sistema para la máquina virtual de Neo (Neo-VM), donde la parte contenida dentro de la línea de puntos es el núcleo de la máquina virtual.

#### Motor de ejecución

La parte verde de la derecha es el motor de ejecución de la máquina virtual (equivalente a la CPU) donde puede ejecutar instrucciones comunes como control de flujo, operaciones de pila, operaciones de bits, operaciones aritméticas, métodos criptograficos e interactuar con la capa del servicio de interoperabilidad. (descrito abajo)

#### Calcular pila

La parte media del gris es la pila de computación de la máquina virtual (equivalente a la memoria). La máquina virtual tiene dos formas para computar la pila, ya sea basado en la pila o basado en el registro. La dos formas de lograr esto tiene sus ventajas y desventajas. En la actualidad existen máquinas virtuales basadas en la pila como JVM, CPython y .Net CLR y máquinas virtuales basadas en registros existen en reales. Las máquinas virtuales basadas en la pila tienen un concepto de pila que permite a las máquinas virtuales interactuar directamente con la pila al realizar operaciones reales.

Como por defecto es recuperar datos de la pila de operandos no hay necesidad de especificar operandos. Por ejemplo, en ensamblador x86 la operación "ADD EAX, EBX" tienes que especificar donde se realizará la operación y en que lugar se guardaran los resultados. Las instrucciones de la máquina virtual basadas en pila no necesita especificar estos parámetros. Por ejemplo, para una operación de suma los operandos se guardan en la pila de operandos y podemos extraerlos directamente de la pila para hacer la suma.

#### Capa del servicio de interoperabilidad

La parte azul del lado derecho es la capa de servicio interoperable de la máquina virtual (equivalente a los periféricos). En la actualidad, la capa de servicio interoperabilidad proporciona algunas API para acceder a los datos de cadena del contrato inteligente, que pueden acceder a información de bloque, información de transacción, información de contrato, información de activos, etc.

Además, la capa de servicio interoperable también proporciona un área de almacenamiento persistente para cada contrato. Cada uno de los contratos inteligentes se crea opcionalmente con almacenamiento privado, que es un objeto del tipo valor-clave determinado por el destinatario del contrato, en lugar del contexto del almacén persistente.

### Carga de tarifas

Un contrato inteligente se puede programar para cargar cierta tarifa, dividida entre costes de desarrollo y costos de implementación.

Los costes de desarrollo hacen referencia a la necesidad del desarrollador a desplegar un contrato inteligente en la blockchain y pagar una tarifa por el despliegue (actualmente de 500 NeoGas). Los costes de ejecución el usuario paga por ejecutar un contrato inteligente. (Es gratis)

## Contrato inteligente sencillo

Ejemplo de un contrato inteligente sencillo que hereda de VerificationCode

```c#
public static bool Verify ()
{
    return true;
}
```

Aquí el valor de retorno siempre es true, indicando que cualquiera puede consumir la dirección del contrato de los activos (puede entenderse como dinero).

Existe una función para eliminar un activo del monedero del cliente. Cuando se elimina un activo, este es enviado a una dirección especificada que es la dirección del contrato generada por el contrato inteligente anterior.

```c#
public static bool Verify ()
{
    return false;
}
```

El valor de retorno del contrato es siempre falso, lo que indica que los activos de este contrato no puede ser utilizado (se puede entender como destruir un activo).

Para más ejemplos, ver:

[Call](tutorial/call.md)

[Deploy-Invoke](tutorial/deploy-invoke.md)

[Domain](tutorial/Domain.md)

[HelloWorld](tutorial/HelloWorld.md)

[Lock](tutorial/Lock.md)