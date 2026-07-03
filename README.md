keyring-pass
============
[![CI](https://github.com/lox/keyring-pass/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/lox/keyring-pass/actions/workflows/test.yml)
[![Go Reference](https://pkg.go.dev/badge/github.com/lox/keyring-pass.svg)](https://pkg.go.dev/github.com/lox/keyring-pass)

[`pass`](https://www.passwordstore.org/) provider for [`github.com/lox/keyring/v2`](https://github.com/lox/keyring).

## Usage

```bash
go get github.com/lox/keyring-pass
```

```go
import (
	"context"

	"github.com/lox/keyring/v2"
	pass "github.com/lox/keyring-pass"
)

ctx := context.Background()

ring, err := keyring.Open(ctx,
	keyring.WithServiceName("example"),
	keyring.WithProvider(pass.Provider()),
)
```

`pass.Provider` accepts `Dir`, `Cmd`, and `Prefix` options. It requires the
`pass` command and returns `keyring.ErrUnavailable` during open on unsupported
platforms.
