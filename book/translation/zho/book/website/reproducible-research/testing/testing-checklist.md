# Checklist for Code Testing

This checklist contains a lot of items. 正如上面提到的 {ref}`<rr-testing-write-tests>`所述，做一些项目要比没有项目要好得多。 Do not be discouraged if this list of tasks seems insurmountable.

<a name="Writing_tests"></a>

## Writing tests

- Write a few smoke tests.
- Write unit tests for all your code units.
- Write integration tests to check the integration between units.
- Write a few system tests. Prioritise common and important paths through the program.
- Write regression tests. Regression tests can exist at any level of testing.
- If appropriate for your project write acceptance tests.
- Add runtime tests into your project.

<a name="Good_practice_checks"></a>

## Good practice checks

- [ ] 记录测试以及如何运行这些测试。
  - [ ] 写下脚本来设置和配置运行测试所需的任何资源。
- [ ] 选择并使用测试框架。
- [ ] 定期运行测试。
  - [ ] 自动运行测试过程。 考虑利用连续一体化（见连续一体化一章）来实现这一目标。
- [ ] 检查测试的代码覆盖面并尝试改进它。
- [ ] 与伙伴一起参与代码审查。
