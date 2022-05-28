# cli_test

This Project aims to test flutter cli mode (implemented on `Linux`).

## Run in CLI mode
```shell
./build/linux/x64/debug/bundle/cli_test -d
```
or

```shell
./build/linux/x64/debug/bundle/cli_test --daemon
```
## Run in GUI mode

simply call `./build/linux/x64/debug/bundle/cli_test` without parameters.

# How this repo implement cli mode

inspired by `gtk-3.0+`, we can do these steps to hide window and do not load any flutter page.

- Native
  - call `gtk_window_hide` after `show` method. (`show` is to trigger dart vm execution, and `hide` can be done in the same function. According to features of event loop, the window will not show and suddenly hide, it will only be invisible.)
- Flutter
  - skip calling `runApp` to prevent unnecessary `Application View` loading.