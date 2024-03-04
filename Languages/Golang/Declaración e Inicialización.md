Una declaración es el hecho de comunicarnos con el lenguaje y decirle
que queremos establecer una variable.

Así como en otros lenguajes Go tiene la declaración y la inicialización,
en go podemos hacer una o ambas a la vez, usando diferentes métodos dependiendo del tipo de dato que almacenará la variable.

**Declaración de una variable**

Una variable en Go se puede definir de tres formas

**Ejemplo 1**: Solo declaración.

Se compone de la palabra reservada `var`, seguido del nombre de la
variable y por último su tipo de dato.

```go
var saludo string
```

Una curiosidad de esto es que si imprimimos la variable, podemos
comprobar que la misma tiene un valor inicial, en el caso del tipo 
`string` es igual a **""** _(una cadena vacía)_
`int` es igual a **0** _(un numero 0)_
`error` es igual a **nil** _(un valor nulo)_

**Ejemplo 2**: Declaración e inicialización.

Es lo mismo que la anterior, sin embargo se asigna un valor de forma
inmediata a la declaración por medio del operador de asignación **=**.

```go
var saludo string = "Hola"
```

**Ejemplo 3**: Declaración e inicialización inferida.

Podemos definir una variable sin especificar el tipo explícitamente, pero esto no quiere decir que no posea un tipo, sino que Go reconocerá
el tipo y lo asignará inmediatamente en su declaración.

```go
saludo := "Hola"
```

Esta es una práctica muy útil cuando no sabemos el tipo especifico que
debemos almacenar y también hace mas flexible la escritura de un
programa en este lenguaje.

## Declaración de tipos de datos especiales, compuestos y estructuras de datos

### Tipo de datos especiales

**Estructuras - Structs:**

- `struct`: Una estructura en sí, es una forma de definir un tipo de datos, por tanto, no se puede asignar a una variable como tal, pero si una instancia de ella.

```go
type Human struct {
	name string
}

var human1 Human
human2 := Human{name: "Joshua"}
```

**Interfaces**

* `interface` Una interfaz es una forma de determinar un conjunto de métodos que un tipo de datos debe implementar.

Una interfaz se puede usar de dos formas en Go

```go
type Running interface {
	Run()
}
```

En este ejemplo se define una interfaz que podemos usar en diversos
lugares, como por ejemplo, en el parámetro de una función para decirle
al programa que la variable que reciba, independientemente de su tipo de
dato, debe cumplir con el método `Run` en este caso.

Ejemplo 1:

```go
type Running interface {
	Run()
}

type Human struct {
	name string
}

func (h Human) Run() {
	fmt.Println("Human is running")
}

type Cat struct {
	name string
}

func (c Cat) Run() {
	fmt.Println("Cat is running")
}

func startRunning(specie Running) {
	fmt.Println("Start Running")
	specie.Run()
}

func main() {
	human := Human{name: "Joshua"}
	cat := Cat{name: "Kimmy"}

	startRunning(human)
	startRunning(cat)
}
```

En el ejemplo 1 se puede observar que, definimos una interfaz llamada
`Running` que define, que el tipo de dato recibido en la función `startRunning` debe cumplir con el conjunto de métodos definido en la
interfaz, en este caso, `Running` posee solo un método, con el cual las
estructuras `Human` y `Cat` cumplen satisfactoriamente.

La otra forma de usar el tipo de dato `interface` es en la asignación de
una variable o estructura de datos que deba implementar cualquier tipo
como veremos a continuación.

Ejemplo 2:

```go
value := map[string]interface{}
```

En el ejemplo 2, vemos que podemos establecer una variable de tipo `map`
en la cual las llaves serán de tipo `string` pero el valor de cada
elemento será de tipo `interface`.

Como una interface no define un tipo, sino un conjunto de métodos, es
posible establecer este tipo de estructuras de datos que permiten
almacenar valores de diversos tipos, sin embargo, esta practica tiene sus pros y sus contras, pero permite tomar decisiones más flexibles.

### Tipo de datos compuesto

**Composición**

La composición es una práctica en la que se agrupan tipos de datos para
formar tipos de datos más adecuados a las necesidades del software.

```go
type Pet struct {
  name   string
  specie string
}

type Person struct {
  name        string
  isTall      bool
  anotherData map[string]string
  pets        [3]Pet
}

func main() {
  person := Person{
    name:        "Joshua",
    isTall:      true,
    anotherData: map[string]string{"phone": "+58419-555-55-55"},
    pets: [3]Pet{
      {
	    name:   "Kimmy",
	    specie: "Cat",
      },	
    },  	
  }
  
  fmt.Println(person)
}
```

En el ejemplo creamos un nuevo tipo de dato que contiene internamente
diversos tipos de datos primitivos.
### Estructuras de datos

**Arrays:**

- `[50]any`: Un array es un vector, matris o lista que puede almacenar una cantidad determinada de datos de un mismo tipo.

```go
// Declaración de Array
var array1 [50]string = []
array2 := [25]byte{}
```

En este caso el "array1" puede almacenar 50 elementos de tipo `string` y
el "array2" solo 25 pero de tipo `byte` o `uint8`.

**Slices:**

- `[]any`: Un slice es un vector, matris o lista que puede almacenar una cantidad indeterminada de datos de un mismo tipo.

```go
// Declaración de Array
var slice1 []string = []
slice2 := []byte{}
```

En este caso el "slice1" puede almacenar elementos de tipo `string` y
el "slice2" de tipo `byte` o `uint8`.

**Maps:**

- `map`: Un map es una representación de un diccionario de hashes en go, o sea, una estructura de datos que nos permite acceder a un valor por medio de un hash (palabra clave).

```go
var supermap map[string]string = map[string]string{}
hipermap := map[string]string{}
```
