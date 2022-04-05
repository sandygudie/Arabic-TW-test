(rr-make-debugging)=
# Debugging Makefiles

写入Makefile时， 有时可以看到在 Makefile 中找到错误或 bug 的 个变量值是有用的。 要便利 这就需要包含两个命令： `info` 和 `错误`，并且有一个调试 模式需要Make。

使用 `信息` 命令，您可以打印一个变量的当前值到 stdout, 而Make 正在处理该文件。 例如，在 上面的 Makefile 中，您可以添加：

```makefile
$(info $$DATA = $(DATA))
```

This will print `DATA = data/action.csv ... data/western.csv`.

使用 `错误` 命令你可以停止在 Makefile 中的一个 点执行 Make 文件。 当您想打印一个 变量的值而不再运行时，这将是有用的：

```makefile
$(error $$DATA = $(DATA))
```

Finally, you can also debug the Makefile by running Make with the debug flag: `make -d`. This will print all the rules (including built-in ones) that Make tries for each of the targets, and whether or not a rule needs to be run.

如果您只想打印将运行的规则，而不实际运行 您可以使用 `制作-n` 后两种备选办法也可以结合在一起， 所以 您可以看到调试输出并且不运行任何东西： `make -dn`。 These last two options can also be combined, so that you see the debug output and Make doesn't run anything: `make -dn`.
