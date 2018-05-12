# logCutting
logrus cutiing hooks.

#### Install

> first : go get -u github.com/Sirupsen/logrus

> second : go get -u github.com/BlueSimle/logcutting

#### Example

```go
package main

import (
	log "github.com/sirupsen/logrus"
	"logcutting/cut_log"
	"os"
)

func init() {
	log.SetFormatter(&log.TextFormatter{
		TimestampFormat:  "2006-01-02 15:04:05",
		ForceColors:      true,
		QuoteEmptyFields: true,
		FullTimestamp:    true,
	})
	log.AddHook(cut_log.ContextHook{LogPath:"/var/cut_log/log_cutting/"})
	log.SetOutput(os.Stdout)
	log.SetLevel(log.Level(5))
}

func main() {
	log.Debug("A group of walrus emerges from the ocean")
	log.Info("A group of walrus emerges from the ocean")
	log.Warn("A group of walrus emerges from the ocean")
	log.Error("A group of walrus emerges from the ocean")
	log.Fatal("A group of walrus emerges from the ocean")
}
```

#### Output
```go
DEBU[2018-05-12 15:15:15] A group of walrus emerges from the ocean      callerFile=" E:/gopath/src/logcutting/example.go:22 "
INFO[2018-05-12 15:15:16] A group of walrus emerges from the ocean      callerFile=" E:/gopath/src/logcutting/example.go:23 "
WARN[2018-05-12 15:15:16] A group of walrus emerges from the ocean      callerFile=" E:/gopath/src/logcutting/example.go:24 "
ERRO[2018-05-12 15:15:16] A group of walrus emerges from the ocean      callerFile=" E:/gopath/src/logcutting/example.go:25 "
FATA[2018-05-12 15:15:16] A group of walrus emerges from the ocean      callerFile=" E:/gopath/src/logcutting/example.go:26 "
```