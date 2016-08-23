## Useful terminal commands

### `tail`
Display the last part of a file

- `-f`
The -f option causes tail to not stop when end of file is reached, but rather to wait for additional data to be appended to the input.  The -f option is ignored if the standard input is a pipe, but not if it is a FIFO.

Example:

```
tail -f server.log
```

- `-n`
The location is number lines

Example:

```
tail -n 100 server.log
```

- pipe to grep

```
tail -f access.log | grep 24.10.160.10
```