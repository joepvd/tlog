# tslog

Prepends lines received on STDIN with a time stamp.

## Installation


From source:

```sh
$ go get jehiah/go-strftime"
$ go get ogier/pflag"
$ go build tslog.go
$ cp tslog /path/
```


## Usage

Basic usage:

``` sh
long_running_command | tlog
```

`tlog` accepts the following options;

<dl>
  <dt>`-i`, `--incremental`</dt>
  <dd>Measure incremental time since last line logged.</dd>

  <dt>`-r`, `--relative`</dt>
  <dd>Measure relative time since program start.</dd>
</dl>


Default is to log time in the current time zone in microseconds in the following
format: `%Y-%m-%dT%H:%M:%S%L`

`tlog` is intended to be used in shell scripts and on CI serfvers where timing
information is usually omitted. Including this will prepend stdout and stderr from
your script with a time stamp:

```sh
exec > >(tlog) 2>&1
```

## Credits

Developed by Joep van Delft. Discovered that `ts` is also part of `moreutils`.
On my machine, this go implementation performs 3 times better than the perl
script.

## License

MIT
