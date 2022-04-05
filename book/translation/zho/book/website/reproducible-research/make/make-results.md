(rr-make-results)=
# Including numerical results and tables

此时你可能会想到“太酷了，我现在可以将数字 添加到我的手稿中！ But how exactly does this work for numerical results?"

上面链接的可重现纸显示了这样做的一种方法： 在计算结果后， 它们是以 LaTeX 表格的形式写出来的。 Here is how one of these tables looks like right after it was computed:

```latex
\start{tabular}{lrrr|rrrr}
属性 & HypoParsr & 狙击枪 & 适合性 & 模式 & 类型 & 无Tie & 完全\\
\hline
分隔符 & 87. 8 & 86.82 & 65.41 & 92.61 & 88.33 & 91。 8 & \textbf{94.92}\\
Quotechar & 82. 0 & 92.36 & 44.60 & 95。 3 & 90.10 & 93.80 & \textbf{97.36}\\
Escapechar & 87. 6 & 94.37 & 74.85 & 97.95 & 96.26 & 95。
```

要将此表包含在您的手稿中，您可以使用 LaTeX 的 `\input{}` 函数。 如果表格的文件名为 `mytable.tex`, 此命令 可以插入到您的手稿中:

```latex
\begin{table}
\input{mytable}
\end{table}
```

An alternative is to make use of variables. 不要在单独的文件中创建一个表，而是可以写一个表骨架 并使用变量。 您计算的结果与变量相关，一旦您的 手稿被编译，变量将被交换为实际数字结果。 Here is how such a table looks like in your manuscript:

```latex
\begin{table}
    \begin{tabular*}{ccc}
        \textbf{Variable} & \textbf{Mean}   & \textbf{Std. \step{table}
    \begin{tabular*}{ccc}
        \textbf{Variable} & \textbf{Mean}   & \textbf{std 绕道} \
        \hline
        变量1        & \var1mean       & \var1std \
        变量2        & \var2mean       & \var2std
    \end{tabular*}
\end{table}
```

你可以注意到 `\var1means` 不是标准的 LaTeX 命令：这是一个变量 你可以自己定义！ How is this done? 让脚本在 `\newcommand{}{}` 定义中的结果打印到一个文件， 例如这样(简化的 Python 示例)：

```python
# this loops to data vectors of two variables (data1, data2), compute the
# mean and standard deviation, and print the results together with the
# variable name ('var1', 'var2')
for name, data in (['var1', data1], ['var2', data2]):
    mean = np.mean(data)
    std = np.mean(data)
    print('\\newcommand{\\%s }{ %f }' % (name + 'mean', mean))
    print('\\newcommand{\\%s }{ %f }' % (name + 'std', std))
```

让我们说第一个数据集的平均值为9.2, 定义看起来就像 这样: `\newcommand{\var1me}{9.2}`。 请注意这个示例使用 Python ，但您可以使用您 熟悉的任何语言或方法来打印类似的定义。 使用此定义，LaTeX将表格单元格与 `\var1means` 和计算结果 数字结果交换。 您可以使用 `>` 抓取定义并将其写入一个文件。 In this example, we write it to a file called `results_def.tex`

```makefile
results_def.tex: code/make_summary_stats.py
    python code/make_summary_stats.py > results_def.tex
```

作为 `>`的备选案文， 您也可以使用 Unix [管道](https://en.wikipedia.org/wiki/Pipeline_(Unix)) 和 [tee](https://en.wikipedia.org/wiki/Tee_(command)) 命令 (`python code/make_summary_stats重定向结果。 y | tee results_def.tex`)。 这不仅将脚本的输出重定向到文件，而且还将 打印到您的终端。 This helpful trick can help you observe whether everything works as expected during the execution of your script.

最后，使用 `input{}` 命令将新的变量包括在您的 手稿和表中的变量：

```latex
\begin{document}
\input{results_def.tex}
```

此处所列举的例子过于简单，但有点想法， 你可以 确保将结果包含在你的手稿中，只要它们是计算出来的。 这有助于您(没有错误复制结果到表格，yay!)，并使您的 研究更容易访问和可复制。
