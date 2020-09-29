## Basics

<p align="right"> <a href="../">🏠</a> </p>

**Table of contents**
- [Hello world program](#hello-world-program)
- [Variables](#variables)
- [Constants](#constants)
- [Packages](#packages)

#### Hello world program
simplest go program (see [fmt](../PACKAGES/fmt.md) package)
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello world!")
}
```


#### Variables
variable declaration
```go
var str string = "String variable"
// available only in function body
anyVar := 123
```

type inference
```go
var (
    name     = "Bakshi" // string
    age      = 28 // int
    location = "Azerbaijan" // string
)
```

declare multiple variables at once
```go
var x, y, z = 1, 2, 3
// or
x, y, z := 1, 2, 3
```
declare list of variables
```go
var (
    name     string = "Bakshi"
    age      int    = 28
    location string = "Azerbaijan"
)
// grouping types
var (
    age, height   int
    name, surname string
)
// grouping and assigning
var (
    age, birthYear int    = 27, 1992
    name, surname  string = "Bakshi", "Iskandarov"
)
```

- go compiler fails if variable was declared and not used

`main.go`
```go
package main

func main() {
    var name = "Bakshi"
    // var name string = "Bakshi"
    // name := "Bakshi"
}
```
running `go run main.go` will output `./main.go:4:6: name declared but not used`

`_` is a blank identifier that tells the compiler to ignore binding 
```go
package main

func main() {
    var _ = "Bakshi"
}
// code will run without error
```

It's okay if you have unused global variables and function arguments
```go
package main

//global scope
var canDefineGlobalVariable = true

func unusedArguments(a int, b int) {
    // local scope
}

func main() {
    // local scope

    unusedArguments(1, 2)
}
```

#### Constants

Constants are like variables, but with the `const` keyword.
Constants can only be character, string, boolean or numeric and cannot be declared using the `:=` syntax.


#### Packages

Every go program is made up of packages. Programs start running in package `main`
```go
package main

func main() {

}
```
if you are writing an executable code, then you need to define a `main` package and a `main()` function which will be the entry point to your software

By convention, the package name is the same as the last element of the import path. For instance, the `"math/rand"` package comprises files that begin with the statement `package rand`

```go
import "fmt"
import "math/rand"

// grouped
import (
    "fmt"
    "math/rand"
)
```
you must use imported package or use `_` to initialize package with it's side effects
```go
import (
    _ "fmt"
    "math"
)

```