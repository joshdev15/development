Ejemplo de código de un **Hola Mundo!** en **Go**.

```go
package main
import "fmt"

func main() {
	fmt.Println("Hola mundo!")
}
```

En el ejemplo vemos con pocas líneas de código como podemos hacer un programa básico para imprimir en terminal el texto "Hola Mundo!"

Literalmente se pueden ver **5** líneas de código en las que podemos identificar lo siguiente.

---
**Línea #1 - Declaración de paquete**:
```go
package main
```

Nos dice a que paquete pertenecen las funciones y variables actuales. _(detallamos más adelante)_

---
**Línea #2 - Importación de paquete**:
```go
import "fmt"
```

Nos dice que el paquete **"fmt"** está siendo usado en este archivo (o paquete) de go. _(detallamos más adelante)_ 

---
**Línea #4 y #6 - Declaración, apertura y cierre de una función de go**:
```go
func main() {
}
```

Nos dice que en la primera línea se está declarando el inicio de una
función _(con la palabra "func")_, el nombre de la función _(la palabra "main")_, la apertura de un bloque de código perteneciente a
dicha función con **"{"** y en la última el cierre de dicho bloque con **"}"**.

A continuación profundizaremos en cada detalle pero a grandes rasgos esta es la forma de escribir un programa sencillo con Go.