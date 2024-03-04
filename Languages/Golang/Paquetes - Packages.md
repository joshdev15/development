En Go el código se organiza en paquetes. Cada archivo de código fuente
pertenece a un solo paquete. En cada archivo el paquete debe estar en
la primera línea escrito de la siguiente forma:

```go
package main
```

Un paquete podría ser lo que llamamos, un módulo en algún otro
lenguaje o espacio de nombre, pero con las propias reglas de **Go**.

### Paquetes Estándar - Standard Library

Los paquetes estándar son aquellos que el lenguaje tiene disponible
desde la instalación y no requieren una acción adicional del
desarrollador.

Son mayormente conocidos como la librería estándar y puedes encontrar gran cantidad de funcionalidades increíbles de go, como:

* __"math"__: Para operaciones matemáticas 
* __"http"__: Para el manejo de conexiones con el protocolo TCP _protocolo (TCP/IP) / HTTP)_
* __"fmt"__: Para implementa E/S _(I/O)_ formateadas con semejanza a como se hace en **C** con **prinf** y **scanf**.
* __"json"__: Codificar y descodificar **JSON** en **Go**.
* **"errors"**: Para manejar errores.

Estos son algunos de los paquetes disponibles en la librería estándar del lenguaje.

### Paquetes Personalizados - Custom Packages

Como desarrolladores podemos declarar paquetes que se ajusten a
nuestras necesidades y podemos llamarlas como deseemos, siempre y
cuando nunca usemos las [[Palabras Reservadas - Keywords]], así como otras reglas que detallaremos a continuación.

**1.- Espacio de trabajo de Go**

Para que un paquete funcione correctamente debe estar declarado en el espacio de trabajo de nuestro programa o aplicación.

Este espacio de trabajo es el **GOPATH**.  El **GOPATH** es una ruta en nuestro
sistema operativo que debe establecerse luego de la instalación de Go
en el cual se almacenan los paquetes compilados y otras dependencias de
Go. Anteriormente era necesario hacer nuestros programas y aplicaciones,
con Go en una ruta especifica para poder acceder a los paquetes
estándar y los paquetes personalizados, sin embargo, desde la versión
1.13 es posible trabajar con **GOPATH** sin estar en esta ruta por
medio del comando `go mod`, aunque siempre es necesario establecerla.

**2.- Siempre Main

Esto es más un recordatorio, porque como es algo obligatorio, no es
solo una regla si no un requerimiento.

El paquete principal siempre debe ser main. Puede estar ubicado en
diferentes lugares, pero, siempre main.

Por ejemplo, podemos hacer esto:

```bash
Estructura de nuestro proyecto

. (app - Root folder)
├── go.mod
├── go.sum
└── main.go
```

o esto

```bash
Estructura de nuestro proyecto

. (app - Root folder)
├── go.mod
├── go.sum
└── cmd
    └── main.go
```

pero el código fuente de este archivo "main" siempre debe comenzar
con el nombre de paquete "main" como lo vemos en el ejemplo de
[[Hola Mundo!]]

**3.- Paquete = Carpeta | Package = Folder**

Definir un paquete dentro de tu espacio de trabajo, es muy sencillo,
sin embargo la organización de Go afecta a ello.

Un paquete debe ser definido en una carpeta dentro del repositorio de
tu aplicación como a continuación: 

Llamaremos a nuestro software "app" y a nuestro paquete "action".

```bash
Estructura de nuestro proyecto

. (app - Root folder)
├── go.mod
├── go.sum
├── action
│   └── action.go
└── main.go
```

```go
// Paquete personalizado "action"
// Archivo "app/action/action.go"
package action
import "fmt"

func Run() {
	fmt.Println("Action Run")
}

func Walk() {
	fmt.Println("Action Walk")
}
```

```go
// Paquete principal "main"
// Archivo "app/main.go"
package main
import (
	"fmt"
	"app/action"
)

func main() {
	fmt.Println("Running app")
	action.Run() // Ejecutamos una función de nuestro paquete "action"
}
```

Como se puede observar en el ejemplo, en la estructura de nuestro
proyecto podemos observar que nuestro archivo "action.go" se encuentra
dentro de un directorio llamado "action", de no hacerlo de esta forma
el compilador nos informa de un error en dos casos

El primer caso es si colocamos el archivo "action.go" al mismo nivel de
"main.go", esto genera un error el cual nos dice que espera
que el nombre de paquete sea main.

El segundo caso es cuando colocamos un nombre de paquete que no sea el
de nuestro directorio, el error es similar pero nos dice que espera que
el nombre de paquete sea <nombre_de_paquete>, en este caso "action"

```go
// Caso: 1
package main // package action; expected main
```

```go
// Caso: 2
package another // package another; expected action
```

Con esto podemos pasar al siguiente tema.