# Manual de Go

## Instalación

Podemos instalar Go de varias maneras:

- Mediante el gestor de paquetes de la distribución.
- Mediante el instalador de la página web de [golang](https://golang.org/dl/).
- Instalando mediante el código fuente.

## Configuración

Todos nuestros proyectos y librerías se guardaran en la ruta especificada por `$GOPATH` con la siguiente estructura:

```bash
Go
├── bin  // Archivos ejecutables
├── pkg  // Archivos compilados como .a
└── src  // Archivos fuente
```

> Por defecto `$GOPATH` tendrá el valor de `$HOME/go`

#### Comandos básicos

El propio paquete de Go contiene una herramienta para gestionar nuestros proyectos en este lenguaje. Dicha herramienta es, casualmente, `go`:

- `go get` para instalar dependencias y librerías.
- `go build` para compilar nuestros proyectos.
- `go run` para ejecutar nuestro proyecto sin tener que compilarlo.

> Para obtener la lista completa de comandos basta con introducir solamente `go`

## Hola mundo

Como con cualquier otro lenguaje comenzaremos con el típico *hola mundo*.

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界")
}
```

Como podemos observar, los programas en go se componen de **paquetes**. En este caso, este archivo pertenece al paquete *main*.

## Tipos de datos

## Tipos de datos derivados

### Estructuras

### Slices

### Mapas

## Secuencias de control

## Bucles