Algunas notaciones:
- MER: Modelo entidad relación
- DER: Diagrama entidad relación
- MR: modelo relacional
## Introducción
Los componentes de este modelo son:
- **Entidad**: es una cosa del mundo real o conceptual con una existencia independiente (de otra entidad). **No lo representamos explícitamente en el DER**
- **Conjunto de entidades**: se forma por una clase o tipo de entidad. *Producto* sería un conjunto de entidades, mientras que cada juguete es representado por una entidad. 
- **Atributo**: características únicas  o propiedades descriptivas de las entidades. *Todas las entidades de una clase o tipo entidad tienen las mismas características pero pueden ser de distintos valores*. Por ejemplo: la entidad `Estudiante` tiene asociados el `Nombre` y `Número de libreta`.
- **Clave**: tipo especial de atributo que puede usarse para identificar unívocamente a cada individuo. Toda entidad tiene al menos un atributo clave.

> Toda entidad en un DER **debe** tener atributos y **debe** tener una clave.

- **Interrelaciones**: son asociaciones entre conjuntos de entidades. En cada relación pueden participar una entidad (unaria) o muchas entidades (binarias, ternarias, n-arias).
- **Reglas de dominio adicionales**: el lenguaje que usamos puede no alcanzar para expresar todas las reglas de nuestro dominio. En la materia podemos usar *lenguaje natural* para expresar toda restricción no modelada con DER.

## Interrelaciones
Para caracterizar cada interrelación usamos distintas características como:
- **Cardinalidad**: la cantidad de elementos de una entidad que pueden estar interactuando, a través de la interrelación, con elementos de otra entidad. Por ejemplo, *uno a uno*, *uno a muchos*, *muchos a muchos*.
- **Participación**: dice si todos los elementos de una entidad tienen que participar o no en la interrelación con otra. Puede ser *parcial* o *total*.

### Grado
Es la cantidad de conjuntos de entidades participantes. Por ejemplo: unarias, binarias, ternarias, n-arias...

### Rol
Cada entidad que participa en una interrelación lo hace cumpliendo un rol en particular. Este ayuda a explicar el significado de la interrelación. 

> **Importante:** en una relación unaria **siempre** deben aclararse los roles para evitar ambigüedades ya que entidades del mismo conjunto estarían actuando con roles diferentes. Además, en relaciones unarias generalmente debe haber al menos una participación parcial.

### Atributos
Las interrelaciones pueden tener atributos pero solo en situaciones específicas.

> **Importante**: las *únicas* interrelaciones que admiten atributos (descriptivos o identificatorios) son las de tipo **M:N**.

Los atributos identificatorios en las interrelaciones permiten que se repitan pares ordenados pero, dado un valor del atributo, los pares deben ser diferentes.

### Interrelaciones ternarias
En este tipo de interrelaciones participan tres entidades. La terna posee un elemento de cada entidad participante.

> **Importante**: en elemento de la ternaria **siempre** tendrá un elemento de cada entidad participante. Es decir, nunca podemos tener `<x1, null, z2>`

La **cardinalidad** de la interrelación se define viendo como se relacionan de a dos entidades y la **participación** se define individualmente.

Cuando nos toca definir relaciones entre tres entidades tener cuidado de no estar agregando relaciones **redundantes**. En caso de que se puedan deducir unas a partir de otras, hay que repensarlo.

## Entidades fuertes y débiles
Las **fuertes** se identifican por sus propios atributos mientras que las **débiles** derivan su existencia a partir de otra entidad y la necesitan para formar su identificador. 
Un ejemplo es la relación entre la entidad `Libro` y `Ejemplar` (cada libro puede tener múltiples ejemplares) donde se ve que un ejemplar no existe si no es específicamente el ejemplar de un libro en particular.
La unicidad se va a dar por la clave completa de la entidad débil, que está compuesta por la clave de su entidad fuerte junto a su atributo identificatorio propio.
## Jerarquías
Muy parecido al concepto de jerarquía que se usa en objetos. Cuando un conjunto de entidades contiene entidades con características específicas que no están asociadas al resto de las entidades se definen **subentidades**.
La relación **es_un** se usa para determinar que una entidad es *subentidad* de la otra.
- Las subentidades heredan la clave de su superentidad.
- Puede tener **cobertura** total o parcial. Esto depende de si las subentidades de una superentidad cubren todos los casos posibles o no. Un ejemplo donde no ocurre es para la superentidad estudiante. Si tenemos las subentidades estudiante trabajador y estudiante sin trabajo entonces sería total. Si no, sería parcial.
- Pueden tener solapamiento. Es decir, son disjuntas o con solapamiento. Por ejemplo, para la superentidad materia podemos tener subentidades por cada turno. Aún así, una materia podría ofrecer distintos turnos, por lo que una entidad del conjunto `Materia` podría pertenecer a más de un conjunto de entidades. 

## Agregación
Es una abstracción en la cual una interrelación (junto con sus entidades vinculadas) es tratada como una entidad de alto nivel y por lo tanto, puede participar de interrelaciones.
Si estamos tratando de modelar algo en una relación ternaria necesitamos que siempre estén los 3 elementos de la terna presentes, no podemos definir una terna donde uno falte. En ese caso, podemos hacer una agregación separando al elemento que puede ser nulo y juntando a los otros dos en una agregación.
Ahora sí podemos definir una relación binaria entre la agregación y la entidad que puede no estar (marcándola como opcional/parcial).