(rr-make-appendix)=
# Appendix

(rr-make-appendix-dag)=
## Directed Acyclic Graph

A Directed Acyclic Graph (DAG) is a *graph* of nodes and edges that is:

1. *directed*: 边缘有一个方向，您只能在那个 方向上走图
2. *acyclic*: does not contain cycles: A can't depend on B when B depends on A.

The latter property is of course quite handy for a build system. 更多关于 DAGs 的 信息可在 [维基百科](https://en.wikipedia.org/wiki/Directed_acyclic_graph) 上找到。

(rr-make-appendix-installing)=
## Installing Make

首先，检查您是否已安装 GNU 在终端类型中： In a terminal type:

```bash
$ make
```

If you get `make: command not found` (or similar), you don't have Make. 如果 你得到 `make：*** 没有指定目标和找不到makefile。  Stop.` 你的 确实有Make。

We'll be using **GNU Make** in this tutorial. 通过输入您 所拥有的东西来验证：

```bash
$ make --version
```

如果您没有 GNU Make 但有 BSD 版本，一些东西可能无法正常工作 ，我们建议安装 GNU Make 。

To install GNU Make, please follow these instructions:

- **Linux**: 使用您的软件包管理器安装 Make 例如在Arch Linux上： For instance on Arch Linux:

  ```bash
  $ sudo pacman -S make
  ```

  Ubuntu:
  ```bash
  $ sudo apt-get install build-essential
  ```

- **MacOS**: If you have [Homebrew](https://brew.sh/) installed, it's simply:

  ```bash
  $ brew install make
  ```

  If you have a builtin Make implementation, please ensure that it's GNU Make by checking `make --version`.

(rr-make-appendix-advancedgr)=
## Advanced: Generating Rules using Call

*本节将继续上面的教程，并展示Make 的功能，用于自动生成规则。*

In a data science pipeline, it may be quite common to apply multiple scripts to the same data (for instance when you're comparing methods or testing different parameters). In that case, it can become tedious to write a separate rule for each script when only the script name changes. To simplify this process, we can let Make expand a so-called [*canned* recipe](https://www.gnu.org/software/make/manual/make.html#Canned-Recipes).

To follow along, switch to the `canned` branch:

```bash
$ make clean
$ git stash --all        # note the '--all' flag so we also stash the Makefile
$ git checkout canned
```

在这个分支上，你会注意到 **脚本** 目录中有一个新脚本，名为 `Generate_qqplot.py`。 此脚本的工作类似于 `Generate_histogram。 y` 脚本 (它有相同的命令行语法)，但它 生成一个 [QQ-绘图](https://en.wikipedia.org/wiki/Q%E2%80%93Q_plot)。 **report.tex** 文件也已更新，以纳入这些绘图。

After switching to the `canned` branch there will be a Makefile in the repository that contains a separate rule for generating the QQ-plots. 此 Makefile 看起来像这样： This Makefile looks like this:

```makefile
# Makefile for analysis report
#

ALL_CSV = $(wildcard data/*.csv)
DATA = $(filter-out $(wildcard data/input_file_*.csv),$(ALL_CSV))
HISTOGRAMS = $(patsubst data/%.csv,output/figure_%.png,$(DATA))
QQPLOTS = $(patsubst data/%.csv,output/qqplot_%.png,$(DATA))

.PHONY: all clean

all: output/report.pdf

$(HISTOGRAMS): output/histogram_%.png: data/%.csv scripts/generate_histogram.py
    python scripts/generate_histogram.py -i $< -o $@

$(QQPLOTS): output/qqplot_%.png: data/%.csv scripts/generate_qqplot.py
    python scripts/generate_qqplot.py -i $< -o $@

output/report.pdf: report/report.tex $(FIGURES)
    cd report/ && pdflatex report.tex && mv report.pdf ../$@

clean:
    rm -f output/report.pdf
    rm -f $(HISTOGRAMS) $(QQPLOTS)
```

You'll notice that the rules for histograms and QQ-plots are very similar.

In a data science pipeline, it may be quite common to apply multiple scripts to the same data (for instance when you're comparing methods or testing different parameters). 在这种情况下，在只有脚本名称更改时为每个脚本单独写一个 规则可能变得很费解。 为了简化这个 进程，我们可以让创建一个所谓的 [*预设* 配方](https://www.gnu.org/software/make/manual/make.html#Canned-Recipes)

```makefile
define run-script-on-data
output/$(1)_$(2).png: data/$(2).csv scripts/generate_$(1).py
    python scripts/generate_$(1).py -i $$< -o $$@
endef
```

请注意，在这个配方中，我们要么使用 `$(1)` 直方图 `直方图` 要么 `qplot` 和 `$(2)` 用于基因。 这些与预期的 函数参数对应于 `run-script-on-data` 罐头配方。 另外，注意 我们在实际配方中使用 `$<` 和 `$@` 两个 `美元` 符号 用于越狱。 要真正创建所有目标，我们需要一个调用 这种预设配方的线。  在我们的情况下，我们使用双倍来循环流派和 脚本：

```makefile
$(foreach genre,$(GENRES),\
    $(foreach script,$(SCRIPTS),\
        $(eval $(call run-script-on-data,$(script),$(genre))) \
    ) \
)
```

在这些行中， `` 字符用于继续长线。

The full Makefile then becomes:

```makefile
# Makefile for analysis report
#

ALL_CSV = $(wildcard data/*.csv)
DATA = $(filter-out $(wildcard data/input_file_*.csv),$(ALL_CSV))
HISTOGRAMS = $(patsubst %,output/histogram_%.png,$(GENRES))
QQPLOTS = $(patsubst %,output/qqplot_%.png,$(GENRES))

GENRES = $(patsubst data/%.csv,%,$(DATA))
SCRIPTS = histogram qqplot

.PHONY: all clean

all: output/report.pdf

define run-script-on-data
output/$(1)_$(2).png: data/$(2).csv scripts/generate_$(1).py
    python scripts/generate_$(1).py -i $$< -o $$@
endef

$(foreach genre,$(GENRES),\
    $(foreach script,$(SCRIPTS),\
        $(eval $(call run-script-on-data,$(script),$(genre)))\
    )\
)

output/report.pdf: report/report.tex $(HISTOGRAMS) $(QQPLOTS)
    cd report/ && pdflatex report.tex && mv report.pdf ../$@

clean:
    rm -f output/report.pdf
    rm -f $(HISTOGRAMS) $(QQPLOTS)
```

请注意，我们已经添加了一个 `SCRIPTS` 变量，带有 `直方图` 和 `qplot` 名称。 如果我们要添加另一个脚本，跟这两个脚本相同的 模式。 我们只需要将其添加到 `SCRIPTS` 变量。

To build all of this, run

```bash
$ make -j 4
```
