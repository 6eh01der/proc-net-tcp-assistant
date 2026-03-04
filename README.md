# proc-net-tcp-assistant - original version https://github.com/RemyRM/proc-net-tcp-assistant

`ProcNetTcpConverter.exe` will take the output of any script that runs `cat /proc/net/tcp` and convert the standard hex notation of ipv4 addresses:ports to decimal for easier readability at a glance. It will also convert the status code to its string value.

Add ipv4 addresses to `ipFilters` to filter out matching entries. These addresses can either be hard coded or provided upon launch.

`ProcNetTcp.bat` and `adb.exe` are just examples. Instead of `ProcNetTcp.bat` and `adb.exe` there may be any Powershell or bash script, wsl.exe or ssh inside them - anything that will execute `cat /proc/net/tcp`.

It's able to run `ProcNetTcpConverter.exe` in Linux by [Mono](https://www.mono-project.com/) for example.

# About usage

Besides the "classic mode" originally implemented by @RemyRM where `ProcNetTcpConverter.exe` asks user for a script path and an ipFilters, there was added `interval` and `count` parameters and ability to put them as positional arguments. For example:

```cmd
ProcNetTcpConverter.exe ProcNetTcp.bat "" 500 0
```

`""` - no IP Filter (remote ip addresses separated by space that should be excluded from output)
`500` - `interval`, milliseconds between ProcNetTcp.bat executions
`0` - zero value for `count` so `ProcNetTcpConverter.exe` will run endlessly
