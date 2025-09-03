> No hay entidades en el modelo relacional, son todas relaciones y dominios. Por eso el énfasis en llamar *interrelaciones* a las del [[Modelo de entidad-relación]]. 

## Definiciones
Una relación puede pensarse como una tabla con filas y columnas.
- Las tablas son y tienen el nombre de una **relación**
- Las columnas representan **atributos**, con cada atributo dentro de un conjunto de sus valores posibles llamado **dominio** del atributo
- Las filas las llamamos **tuplas** y están formadas por los conjuntos de valores
### Relación
- **Dominio**: es un conjunto de valores atómicos.
- Una relación tiene un **esquema** (o intención de la relación) y una **extensión** (estado o instancia).
- **Esquema**: se escribe `R(A1, A2, ..., An)` se compone por el nombre de la relación `R` y un conjunto de atributos `{A1, A2, ..., An}`
- **Aridad:** cantidad de atributos que tiene la relación
- Un atributo `Ai` es el **nombre del rol** que ejerce algún dominio **D** en un esquema de relación. Si D es el dominio de `Ai`, se escribe como `dom(Ai)`

### Extensión de la relación
Se denota como `r(R)` y es un conjunto de tuplas `ti` donde cada tupla se puede definir como `ti = <v1, v2, ..., vn>`, donde cada `vi` representa un valor del atributo `Ai` y donde cada `vj` es un valor de `dom(Aj)`.
Entonces, la extensión de una relación es un subconjunto del producto cartesiano de una lista de dominios
$$
r(R) \subseteq (dom(A_1) \times dom(A_2) \times \dots \times dom(A_i))
$$
### Esquema vs Estado
El **esquema** de una relación `R` representa la intención y es estable, es poco frecuente que cambie. El **estado** (o extensión) de una relación (`r(R)`) **cambia de forma muy frecuente** acompañando los cambios en el mundo real.
#TODO Completar

## Claves
Una clave es un conjunto minimal de atributos que definen unívocamente a las tuplas. Una superClave es #TODO

**Propiedad**: Sean K una clave, E una relación y ei, ej dos tuplas cualesquiera de la relación E, entonces $e_i.K = e_j.K \implies e_i = e_j$
## Base de datos Relacional
Un esquema de Base de datos relacional es un conjunto de esquemas de relación `S={R1, R2, .., Rm}` y un conjunto de integrity constraints IC.

Un estado de una Base de datos relacional DB de S es un conjunto de estados de relación `DB={r1, r2, .., rm}` tal que cada ri es un estado de Ri y además satisface las restricciones de integridad especificadas en IC.

## Restricciones (constraints)
Una restricción de integridad es una expresión booleana que debe evaluar a Verdadero, Por ejemplo: `salario > 0` para la tabla `Empleados`.
Se expresan en la definición del esquema y se especifican sobre un esquema de base de datos y se espera que se cumplan sobre todo estado válido de la base de datos.

## Pasaje del MER al MR
- Las entidades se convierten en relaciones
- Las interrelaciones se representan usando como clave principal la tupla compuesta por la clave foránea de una de las entidades y la primaria de otra (esto dependiendo bastante del caso) o agregando la foránea como secundaria. #TODO haber prestado más atención

> **Importante**: subrayamos con una linea sólida a la clave primaria y con una linea punteada a la clave foránea. Si la clave primaria se compone de múltiples claves (dentro de una tupla), las subrayamos con dos lineas sólidas.

**Siempre** se genera un esquema aparte en el caso de la ternaria. Lo que varía es la clave del esquema dependiendo de las cardinalidad.

No importa la opcionalidad en el caso de las ternarias 1:1:1.

### Jerarquías
