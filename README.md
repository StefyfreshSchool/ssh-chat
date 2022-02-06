# ssh-chat

Custom SSH server written in Go. Instead of a shell, you get a chat prompt.

This is a modified version by [Stefyfresh](https://github.com/StefyfreshSchool/) with a few tweaks.


## Compiling / Developing

You can compile ssh-chat by using `make build`. The resulting binary is portable and
can be run on any system with a similar OS and CPU arch. Go 1.8 or higher is required to compile.

If you're developing on this repo, there is a handy Makefile that should set
things up with `make run`.

Additionally, `make debug` runs the server with an http `pprof` server. This allows you to open
[http://localhost:6060/debug/pprof/]() and view profiling data. See
[net/http/pprof](http://golang.org/pkg/net/http/pprof/) for more information about `pprof`.


## Quick Start

```
Usage:
  ssh-chat [OPTIONS]

Application Options:
  -v, --verbose    Show verbose logging.
      --version    Print version and exit.
  -i, --identity=  Private key to identify server with. (default: ~/.ssh/id_rsa)
      --bind=      Host and port to listen on. (default: 0.0.0.0:2022)
      --admin=     File of public keys who are admins.
      --whitelist= Optional file of public keys who are allowed to connect.
      --motd=      Optional Message of the Day file.
      --log=       Write chat log to this file.
      --pprof=     Enable pprof http server for profiling.

Help Options:
  -h, --help       Show this help message
```

After doing `go get github.com/shazow/ssh-chat/...` on this repo, you should be able
to run a command like:

```
$ ssh-chat --verbose --bind ":22" --identity ~/.ssh/id_dsa
```

To bind on port 22, you'll need to make sure it's free (move any other ssh
daemons to another port) and run ssh-chat as root (or with sudo).

## Frequently Asked Questions

The FAQs can be found on the project's [Wiki page](https://github.com/shazow/ssh-chat/wiki/FAQ).
Feel free to submit more questions to be answered and added to the page.

## License

MIT
