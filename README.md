# PDF Reader


A simple Go library which enables reading PDF files. Forked from github.com/ledongthuc/pdf

Features
  - Get plain text content (without format)
  - Get Content (including all font and formatting information)

## Install:

`go get -u github.com/wait-skate/go-pdf`

## Examples:

 - Check in examples/ folder


## Read plain text

```golang
package main

import (
	"bytes"
	"fmt"

	pdf "github.com/wait-skate/go-pdf"
)

func main() {
	pdf.DebugOn = true

	f, r, err := pdf.Open("./pdf_test.pdf")
	if err != nil {
		panic(err)
	}
	defer f.Close()

	var buf bytes.Buffer
	b, err := r.GetPlainText()
	if err != nil {
		panic(err)
	}
	buf.ReadFrom(b)
	content := buf.String()
	fmt.Println(content)
}
```
