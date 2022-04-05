(rr-renv-yaml)=
# YAML

YAML is an indentation-based markup language which aims to be both easy to read and easy to write. Many projects use it for configuration files because of its readability, simplicity, and good support for many programming languages. It can be used for many things, including defining computational environments, and is well integrated with [GitHub actions](https://travis-ci.org/), which is discussed in the {ref}`rr-ci-github-actions` chapter.

(rr-renv-yaml-files)=
## YAML Files

A YAML file defining a computational environment might look something like this:

```
# 将操作系统定义为 Linux
os: linux

# 使用 Linux
的xenial 分布: xenial

# 使用编程语言 Python
语言: python

# 使用版本的 Python 3。 python: 3.2

# 使用 Python 软件包编号并使用版本 1。 6.1
软件包：
  编号：
    版本：1.16.1
```

Note that comments can be added by preceding them with a `#`.

(rr-renv-yaml-syntax)=
## YAML Syntax

A YAML document can consist of the following elements.

(rr-renv-yaml-syntax-scalars)=
### Scalars

Scalars are ordinary values: numbers, strings, booleans.

```
number-value: 42
floating-point-value: 3.141592
boolean-value: true

# strings can be both 'single-quoted` and "double-quoted"
string-value: 'Bonjour'
```

YAML syntax also allows unquoted string values for convenience reasons:

```
unquoted-string: Hello World
```
(rr-renv-yaml-syntax-lists)=
### Lists and Dictionaries

Lists are collections of elements:

```
jedis:
  - Yoda
  - Qui-Gon Jinn
  - Obi-Wan Kenobi
  - Luke Skywalker
```

Every element of the list is indented and starts with a dash and a space.

Dictionaries are collections of `key: value` mappings. All keys are case-sensitive.

```
jedi:
  name: Obi-Wan Kenobi
  home-planet: Stewjon
  species: human
  master: Qui-Gon Jinn
  height: 1.82m
```

Note that a space after the colon is mandatory.

(rr-renv-yaml-syntax-gotchas)=
### YAML Gotchas

Due to the format aiming to be easy to write and read, there are some ambiguities in YAML.

- **Special characters in unquoted strings:** YAML has several special characters you cannot use in unquoted strings. For example, parsing the following sample will fail:
  ```
  unquoted-string: let me put a colon here: oops
  ```
  Quote the string value makes this value unambiguous:
  ```
  unquoted-string: "let me put a colon here: oops"
  ```
  Generally, you should quote all strings that contain any of the following characters: `[] {} : > |`.
- **Tabs versus spaces for indentation:** do _not_ use tabs for indentation. While the resulting YAML can still be valid, this can be a source of many subtle parsing errors. Just use spaces.

(rr-renv-yaml-environments)=
## How To Use Yaml To Define Computational Environments

Because of their simplicity, YAML files can be handwritten. Alternatively, they can be automatically generated as discussed in the {ref}`rr-renv-package` subchapter. 从YAML文件中可以通过几种方式复制计算环境。 From a YAML file, a computational environment can be replicated in a few ways.

- **手动。 ** 可以通过仔细安装指定的软件包来手动完成。 Because YAML files can also specify operating systems and versions that may or may not match that of the person trying to replicate the environment, this may require the use of {ref}`rr-renv-vm`.

- **通过Conda等包管理系统。 ** 正如 {ref}`所讨论的 <rr-renv-package>`以及能够从计算环境生成YAML 文件。 Conda 也可以从 YAML 文件生成计算环境。

(rr-renv-yaml-security)=
## Security Issues

There is an inherent risk in downloading/using files you have not written to your computer, and it is possible to include malicious code in YAML files. Do not load YAML files or generate computational environments from them unless you trust their source.
