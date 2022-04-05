(rr-checklist-for-code-review)=
# Checklist for code review process

This section presents some checklists for both the coder and the reviewer, as part of a formal review process. The reviewer checklists are split into two categories: one for the whole program, and one for individual files or proposed changes.

The lists are created with a focus on good software engineering practice and are intended to be a source of inspiration. When assessing the checklists, it is recommended to consider to what extent the item mentioned is implemented. Some items on the lists may not apply to your project or programming language, in which case they should be disregarded.

In all cases, the goal is to use your programming experience to figure out how to make the code better.

## For the coder

- Does the new code meets the required standards of the project? The standards are typically written under `contributing guidelines` by the project you are contributing to.
- Is there [documentation](#documentation) that meets the required standards of the project?
- Are you following any declared {ref}`style guide<rr-code-quality>` for the project?
- Are there new [tests](#tests) for the new material, based on the required standards of the project?
  - Do these tests pass locally?
  - Are the tests in the rest of the code base still passing locally?
- Create the pull request.
- Many {ref}`continuous integration (CI)<rr-ci>` systems will check if the tests in the main project pass automatically once you create a pull request. If the repository is using a CI, make sure all builds and tests complete. Consult the CI reports to see if your code is causing the tests in the main project to fail.
- If necessary, now formally request a review.

## For the reviewer

- Check the required standards of the project. 标准通常由您要贡献的项目在 `贡献指南` 下写入。
- Check the code meets basic project {ref}`style guide<rr-code-quality>`, if this is not automatically checked by {ref}`continuous integration (CI)<rr-ci>`.
- Do the [tests](#tests) and [documentation](#documentation) conform to the standards?
- Is all the code easily understood? Depending on the language, files may contain interfaces, classes or other type definitions, and functions (see [Architecture](#architecture)). The essential architectural concepts can be reviewed as follows:
  - Check the [interfaces](#interfaces) lists.
  - Check the [classes and types](#classes-and-types) lists.
  - Check the [function/method declarations](#function-method-declarations) lists.
  - Check the [function/method definitions](#function-method-definitions) lists.
- Do the [tests](#tests) actually ensure the code is robust in its intended use?
  - Are there any bugs or other defects?
- Are [security](#security) issues handled correctly?
  - Check the [security of new codes](#security-of-new-codes).
- Does the new code meet the [legal requirements](#legal)?

## Program level checklist

下面是一个在查看整个程序时要考虑的事项列表。 而不是在查看单个文件或更改时。

### Documentation

Documentation is a prerequisite for using, developing, and reviewing the program. 没有参与您的项目的人应该了解您的代码做了什么， 以及您采取了什么方法。 Here are some things to check for.

- Is there a description of the purpose of the program or library?
- Are detailed requirements listed?
- Are requirements ranked according to [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method)?
- Is the use and function of third-party libraries documented?
- Is the structure/architecture of the program documented? (see below)
- Is there an installation manual?
- Is there a user manual?
- Is there documentation on how to contribute?
  - Including how to submit changes
  - Including how to document your changes

### Architecture

这些项目主要对较大的程序很重要，但也许还是很好的 来考虑小的项目。

- Is the program split up into clearly separated modules?
- Are these modules as small as they can be?
- 这些模块之间是否有清晰、等级或分层的依赖结构？
  - 如果没有，则应重新安排功能，或者，或许需要将严重的 相互依存的模块合并起来。
- Can the design be simplified?

### Security

如果你制作的软件可供外部世界访问(例如一个 web 应用程序)，安全就变得重要。 安全问题是缺陷， 但并非所有缺陷都是安全问题。 有安全意识的设计可以帮助 减轻缺陷对安全的影响。

- Which modules deal with user input?
- Which modules generate output?
- Are input and output compartmentalized?
  - 如果不是，请考虑将管理所有输入 和输出的模块分开，所以验证可以在一个地方发生。
- In which modules is untrusted data present?
  - The fewer the better.
- Is untrusted data compartmentalized?
  - 理想的情况是，在输入模块中验证并只将 验证数据传递给其他部分。

### Legal

作为开发者，你应该关注你使用的代码的 创作者的合法权利。 Here are some things to check. 在 怀疑时，向有许可证经验的人询问咨询意见。

- Are the licenses of all modules/libraries that are used documented?
- Are the requirements set by those licenses fulfilled?
  - Are the licenses included where needed?
  - Are copyright statements included in the code where needed?
  - Are copyright statements included in the documentation where needed?
- Are the licenses of all the parts compatible with each other?
- Is the project license compatible with all libraries?

## File/Change level checklist

当您检查一个拉取请求中的个别更改或文件时， 代码本身就成为受检查的对象。 根据语言，文件 可能包含接口、类或其他类型的定义和函数。 所有 都应该被检查。

### Interfaces

- Is the interface documented?
- Does the concept it models make sense?
- Can it be split up further? (Interfaces should be as small as possible)

请注意，以下大多数项目都假定了一个面向对象的编程 风格，这可能与你正在查看的代码无关。

### Classes and types

- Is the class documented?
  - Are external programs needed by the class documented?
- Does it have a single responsibility? Can it be split?
- If it's designed to be extended, can it be?
- If it's not designed to be extended, is it protected against that?
- If it's derived from another class, can you substitute an object of this class for one of its parent class(es)?
- Is the class testable?
  - Are the dependencies clear and explicit?
  - Does it have a small number of dependencies?
  - Does it depend on interfaces, rather than on classes?

### Function/Method declarations

- Are there comments that describe the intent of the function or method?
- Are input and output documented? Including units?
- Are pre- and postconditions documented?
- Are edge cases and unusual things commented?

### Function/Method definitions

- Are edge cases and unusual things commented?
- Is there any incomplete code?
- Could this function be split up (is it not too long)?
- Does it work? Perform intended function, logic correct, ...
- Is it easy to understand?
- Is there redundant or duplicate code? (DRY)
- Do loops have a set length and do they terminate correctly?
- Can debugging or logging code be removed?
- Can any of the code be replaced by library functions?

### Security of new codes

- If you're using a library, do you check errors it returns?
- Are all data inputs checked?
- Are output values checked and encoded properly?
- Are invalid parameters handled correctly?

### Tests

- Do unit tests actually test what they are supposed to?
- Is bounds checking being done?
- Is a test framework and/or library used?
