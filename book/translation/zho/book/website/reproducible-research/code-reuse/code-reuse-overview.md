(rr-code-reuse-reuse-recommendation)=
# 代码重复使用概览

This section contains a checklist of recommendations for making your software more reusable. The {ref}`rr-code-reuse-details` section contains a more in-depth explanation of each of these recommendations. 您可以遵循更适合您的软件类型的建议，并跳过与您的情况无关的建议。 You can follow the recommendations that are more suitable for your type of software and skip the ones which are not relevant in your case.

## 可重复的建议

1. 请确保您可以找到它(在空间中。 意味着：能够定位仓库/项目)
1. 请确保您可以找到它(时间；含义：能够找到某个特定版本)
1. Make sure you can execute the same sequence of operations
1. Make sure your environment and sequence of operations is robust and no human is needed to replicate what was done
1. License your code
    - with a license that allows for reuse;
    - with a license compatible with the dependencies’ licenses
1. Make sure it is citable
1. Include necessary data
1. Write useful documentation*

## 可重新运行的建议

1. 移除硬代码位(例如只存在于运行管道的硬盘上的路径)，并使代码模块
1. Test that the modules you made can take different types of input data or parameters
1. Turn the modules into a package/toolbox
1. Write useful documentation*

## 便携式建议
1. Make sure you can recreate the environment where it lived
1. Write useful documentation*

## 可扩展的建议
1. Write useful documentation*

## 可修改的建议
1. Make sure your code is readable by humans
1. Make sure comments are present
1. Write useful documentation*

The observant reader might will notice that `Write useful documentation` is mentioned for every level of reuse. This is because different levels of documentation are required for different levels of reuse.

## Documentation

*Different documentation requirements for different levels of reuse*

Writing useful documentation is an important requirement for all levels of reuse. However, for the different levels of reuse, there are different documentation requirements:

The documentation:
- explains usage, specifying:
  - what the software does; (required for repeatable)
  - how it can be used; (required for repeatable)
  - what options/parameters are available. (required for repeatable)
- contains examples of how to run it. (required for repeatable)
- has installation instructions, including good descriptions of:
  - the hardware it depends on (for example GPUs); (required for portable)
  - the operating system the software has been tested on; (required for portable)
  - software requirements (such as libraries and shell settings). (required for portable)
