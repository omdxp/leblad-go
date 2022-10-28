# leblad

[![Build Status](https://github.com/omdxp/leblad/workflows/Test%20CI/badge.svg)](https://github.com/omdxp/leblad/actions?query=branch%3Amain)

A go module providing a list of Algerian administrative areas with many useful APIs, based on [dzcode-io/leblad](https://github.com/dzcode-io/leblad)

## Installation

```bash
go get -u github.com/omdxp/leblad
```

## Quick Start

```go
package main

import (
    "fmt"

    "github.com/omdxp/leblad"
)

func main() {
    l := leblad.New()

    // Get all wilayas
    wilayas, err := l.GetWilayaList()
    if err != nil {
        panic(err)
    }

    fmt.Println(wilayas)

    // Get only wilayas names
    wilayas, err = l.GetWilayaList("name")
    if err != nil {
        panic(err)
    }
}
```

## API

init a new leblad instance

```go
l := leblad.New()
```

### GetWilayaList

Get all wilayas

```go
wilayas, err := l.GetWilayaList()
if err != nil {
    panic(err)
}
```

Filter wilayas by a specific field

```go
wilayas, err := l.GetWilayaList("name")
if err != nil {
    panic(err)
}
```

it accept a variadic number of fields

```go
wilayas, err := l.GetWilayaList("name", "dairats", "matricule")
if err != nil {
    panic(err)
}
```

fields can be one of the following:
| wilaya field | description |
| --- | --- |
| matricule | wilaya matricule |
| name_ar | wilaya name in arabic |
| name_ber | wilaya name in berber |
| name_en | wilaya name in english |
| name | wilaya name in french |
| phoneCodes | wilaya phone codes |
| postalCodes | wilaya postal codes |
| dairats | wilaya dairats |
| adjacentWilayas | wilaya adjacent wilayas |

### GetWilayaByZipCode

Get wilaya by zip code

```go
wilaya, err := l.GetWilayaByZipCode(1000)
if err != nil {
    panic(err)
}
```

Filter wilaya by a specific field

```go
wilaya, err := l.GetWilayaByZipCode(1000, "name")
if err != nil {
    panic(err)
}
```

it accept a variadic number of fields

```go
wilaya, err := l.GetWilayaByZipCode(1000, "name", "dairats", "matricule")
if err != nil {
    panic(err)
}
```

### GetWilayaByCode

Get wilaya by code

```go
wilaya, err := l.GetWilayaByCode(1)
if err != nil {
    panic(err)
}
```

Filter wilaya by a specific field

```go
wilaya, err := l.GetWilayaByCode(1, "name")
if err != nil {
    panic(err)
}
```

it accept a variadic number of fields

```go
wilaya, err := l.GetWilayaByCode(1, "name", "dairats", "matricule")
if err != nil {
    panic(err)
}
```

### GetAdjacentWilayas

Get adjacent wilayas as a slice of wilaya codes

```go
wilayas, err := l.GetAdjacentWilayas(1)
if err != nil {
    panic(err)
}
```

### GetZipCodesForWilaya

Get zip codes for a wilaya

```go
zipCodes, err := l.GetZipCodesForWilaya(1)
if err != nil {
    panic(err)
}
```
