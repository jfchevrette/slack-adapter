<h1 align="center">Joe Bot - Slack Adapter</h1>
<p align="center">Connecting joe with the Slack chat application. https://github.com/go-joe/joe</p>
<p align="center">
	<a href="https://github.com/go-joe/slack-adapter/releases"><img src="https://img.shields.io/github/tag/go-joe/slack-adapter.svg?label=version&color=brightgreen"></a>
	<a href="https://circleci.com/gh/go-joe/slack-adapter/tree/master"><img src="https://circleci.com/gh/go-joe/slack-adapter/tree/master.svg?style=shield"></a>
	<a href="https://goreportcard.com/report/github.com/go-joe/slack-adapter"><img src="https://goreportcard.com/badge/github.com/go-joe/slack-adapter"></a>
	<a href="https://codecov.io/gh/go-joe/slack-adapter"><img src="https://codecov.io/gh/go-joe/slack-adapter/branch/master/graph/badge.svg"/></a>
	<a href="https://godoc.org/github.com/go-joe/slack-adapter"><img src="https://img.shields.io/badge/godoc-reference-blue.svg?color=blue"></a>
	<a href="https://github.com/go-joe/slack-adapter/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-BSD--3--Clause-blue.svg"></a>
</p>

---

This repository contains a module for the [Joe Bot library][joe].

**THIS SOFTWARE IS STILL IN ALPHA AND THERE ARE NO GUARANTEES REGARDING API STABILITY YET.**

## Getting Started

This library is packaged using the new [Go modules][go-modules]. You can get it via:

```
go get github.com/go-joe/slack-adapter
```

### Example usage

In order to connect your bot to slack you can simply pass it as module when
creating a new bot:

```go
package main

import (
	"github.com/go-joe/joe"
	"github.com/go-joe/slack-adapter"
)

func main() {
	b := joe.New("example-bot",
		slack.Adapter(os.Getenv("SLACK_TOKEN")),
		…
    )
	
	b.Respond("ping", Pong)

	err := b.Run()
	if err != nil {
		b.Logger.Fatal(err.Error())
	}
}
```

So far the adapter will emit the following events to the robot brain:

- `joe.ReceiveMessageEvent`
- `joe.UserTypingEvent`

## Built With

* [nlopes/slack](https://github.com/nlopes/slack) - Slack API in Go
* [zap](https://github.com/uber-go/zap) - Blazing fast, structured, leveled logging in Go
* [pkg/errors](https://github.com/pkg/errors) - Simple error handling primitives

## Contributing

The current implementation is rather minimal and there are many more features
that could be implemented on the slack adapter so you are highly encouraged to
contribute. If you want to hack on this repository, please read the short
[CONTRIBUTING.md](CONTRIBUTING.md) guide first.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available,
see the [tags on this repository][tags. 

## Authors

- **Friedrich Große** - *Initial work* - [fgrosse](https://github.com/fgrosse)

See also the list of [contributors][contributors] who participated in this project.

## License

This project is licensed under the BSD-3-Clause License - see the [LICENSE](LICENSE) file for details.

[joe]: https://github.com/go-joe/joe
[go-modules]: https://github.com/golang/go/wiki/Modules
[tags]: https://github.com/go-joe/slack-adapter/tags
[contributors]: https://github.com/github.com/go-joe/slack-adapter/contributors
