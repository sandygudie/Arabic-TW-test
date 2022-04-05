(rr-testing-overview)=
# Overview of Testing Types

There are a number of different kinds of tests, which will be discussed here.

Firstly there are positive tests and negative tests. Positive tests check that something works, for example testing that a function that multiplies some numbers together outputs the correct answer. Negative tests check that something generates an error when it should. For example nothing can go quicker than the speed of light, so a plasma physics simulation code may contain a test that an error is outputted if there are any particles faster than this, as it indicates there is a deeper problem in the code.

In addition to these two kinds of tests, there are also different levels of tests which test different aspects of a project. These levels are outlined below and both positive and negative tests can be present at any of these levels. A thorough test suite will contain tests at all of these levels (though some levels will need very few).

(rr-testing-type of testing)=
## Types of Testing

[烟雾测试](#Smoke_testing): 非常简短的初步检查，确保运行项目挂卡所需的基本要求。 If these fail there is no point proceeding to additional levels of testing until they are fixed.

[单元测试](#Unit_tests): 在软件测试过程中测试软件的单个单元. 其目的是验证软件的每个单位是否按设计行事。 The purpose is to validate that each unit of the software performs as designed.

[集成测试](#Integration_testing): 一定水平的软件测试，将单个单元合并并作为一个组进行测试。 The purpose of this level of testing is to expose faults in the interaction between integrated units.

[系统测试](#System_tests): 一个完整、综合的系统测试过程中的一个等级。 The purpose of this test is to evaluate whether the system as a whole gives the correct outputs for given inputs.

[接受测试](#Acceptance_testing): 软件测试过程的一个级别，测试一个系统是否可以接受。 The purpose of this test is to evaluate the system's compliance with the project requirements and assess whether it is acceptable for the purpose.

下面是一个类比：在生产球点钢的过程中，钢帽，身体。 尾料、墨盒和球点是分开生产和单独测试的。 一旦两个或两个以上的单位准备就绪，就组装起来，并进行整合测试。 例如，用于检查物体顶部是否适合的测试。 当完整的笔集成时，将进行系统测试以检查它是否可以像任何笔一样写入。 接受测试可以是一张支票，以确保笔是客户订购的颜色。

还有另一种称为回归试验的试验。 回归测试是一种可在四个主要层次中的任何一个层次进行的测试，并对修改守则之前和之后的测试结果进行比较。 如果它们不同则给出一个错误。

下一节将更详细地讨论这些不同类型的检验。
