---
id: installation
title: Installation
---

# Installation

Please refer to the installation method more applicable to you.

Our recommendation is to use the pre-built releases and verify the provided checksums.

***

### Building from source <a href="#building-from-source" id="building-from-source"></a>

Prior to using `go install` make sure that you have Go `>=1.17` installed and properly configured.

The stable branch is `develop`.

Copy

```
git clone https://github.com/0xEVMBuilder/z-edge.git
cd z-edge/
go build main.go -o z-edge
sudo mv z-edge /usr/local/bin
```

***

### Using `go install` <a href="#using-go-install" id="using-go-install"></a>

Prior to using `go install` make sure that you have Go `>=1.17` installed and properly configured.

`go install github.com/0xEVMBuilder/z-edge@develop`

The binary will be available in your `GOBIN` environment variable, and will include the latest changes from the mainline `develop` branch.
