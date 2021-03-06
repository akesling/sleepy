## Sleepy

#### A RESTful framework for Go

Sleepy is a micro-framework for building RESTful APIs.

```go
package main

import (
    "net/http"
    "github.com/akesling/sleepy"
)

type Item struct { }

func (item Item) Get(request http.Request) (int, interface{}) {
    items := []string{"item1", "item2"}
    data := map[string][]string{"items": items}
    return 200, data
}

func main() {
    api := sleepy.NewAPI()
    api.AddResource(new(Item), "/items")
    api.Start(3000)
}
```

Now if we curl that endpoint:

```bash
$ curl localhost:3000/items
{"items": ["item1", "item2"]}
```

`sleepy` has not been officially released yet, as it is still in active
development.

## Docs

Documentation lives [here](http://godoc.org/github.com/dougblack/sleepy).

## License

`sleepy` is released under the [MIT License](http://opensource.org/licenses/MIT).
