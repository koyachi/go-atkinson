# go-atkinson

Atkinson Dithering with Go.

![lena.result.jpg](https://raw.githubusercontent.com/koyachi/go-atkinson/master/example/lena.result.jpg)


## Example

```go
package main

import (
	"github.com/koyachi/go-atkinson"
	"fmt"
	"image/jpeg"
	"log"
	"os"
	"path/filepath"
)

func main() {
	fmt.Printf("processing...\n")
	imagePath := "./lena.jpg"
	img, err := atkinson.DitherFile(imagePath)
	if err != nil {
		log.Fatal(err)
	}

	path, err := filepath.Abs("result.jpg")
	if err != nil {
		log.Fatal(err)
	}
	file, err := os.Create(path)
	if err != nil {
		log.Fatal(err)
	}
	err = jpeg.Encode(file, img, nil)
	if err != nil {
		log.Fatal(err)
	}
}
```


## Links

- http://www.tannerhelland.com/4660/dithering-eleven-algorithms-source-code/
- http://en.wikipedia.org/wiki/Bill_Atkinson
