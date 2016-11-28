## Unit Testing
> 开发的一部分

### 什么是单元测试

> In computer programming, unit testing is a software testing method by which individual units of source code, sets of one or more computer program modules together with associated control data, usage procedures, and operating procedures, are tested to determine whether they are fit for use

> 在计算机编程中，单元测试是一种软件测试方法，通过该方法测试源代码的单个单元，一个或多个计算机程序模块的集合，结合相关联的控制数据，使用过程和操作过程，以确定它们是否适合使用


#### 需要测试的代码
 - 代码单个单元
 - 单个模块或多个模块集合

#### 测试方法
 - 控制数据
 - 使用过程
 - 操作过程


### 为什么要单元测试

- 加大开发的时间？
- 作用不大？

[对单测的误解 - 百度百科][单测百科]

- 保证开发质量
- 更好的团队协作
- 集成测试发现迭代的 bug
- 交接、维护
- 测试上的低成本、高效率


### 怎么做单测

对所有可测试模块进行测试，结果只有两种：

- 通过
- 不通过

将测试结果存储起来，对于不通过的代码，需要保存不通过的测试用例和不通过的原因，方便修改源码实现或者测试逻辑

目前有两种测试风格

- TDD (Test Driven Development)
- BDD (Behaviour Driven Development)

TDD: 围绕着程序的设计目标和需求得出测试用力去测试，可以认为是一种开发技术，要求代码覆盖率在 80% 以上。node.js 本身提供 TDD 的测试库。
代表库 assert

BDD: 站在用户的角度去测试功能和可用性。
代表库 should/expect


### 单测框架介绍对比

目前前端常用的测试框架包括

- mocha ( tj )
- jasmine ( from JUnit )
- karma ( 自动化测试工具，支持多浏览器环境测试 )
- selenium webdriver ( 更强大的工具集 )

mocha vs jasmine (类比 react vs angular )


### 单测实践工具集 ( 推荐 )

- mocha ( 框架 )
- chai ( 断言库 )
- sinon ( 针对函数的辅助库，spy/mock 能力 )
- enzyme ( React 组件 )
- jsdom ( 虚拟 dom 环境 )
- supertest ( 测试 node.js server )
- karma ( 自动化测试 )

#### mocha

一种测试框架，可以在 Node.js 和浏览器环境运行。<br>
支持丰富的功能特性，包括：

- 支持异步/Promise测试
- 测试覆盖率报告
- 支持 api 运行
- 支持文件 watch 自动测试
- 支持重试
- 支持异步 timeout
- 支持高亮运行缓慢的测试
- 全局变量泄漏检测
- 支持 mocha.opts 文件
- 支持 node debugger
- 自动检测多次调用 done
- 支持任意断言库
- 可扩展 reporter
- 4 种 hooks
- ...

详见 [mocha 官网](http://mochajs.org/)


基础语法特性：

- describe
- it
- before
- beforeEach
- after
- afterEach
- this.timeout ( not support arrow functions )
- ...


#### chai

支持 TDD/BDD 的断言库 [chai 官网](http://chaijs.com/api/bdd/)

TDD: assert
BDD: expect/should


#### sinon

辅助测试库，对函数进行包装，实现不同功能能力。

[sinon 官网](http://sinonjs.org/)

- spy： 可以函数调用参数、返回值等信息
- stub：可以预设函数的行为，包括 spy 的功能
- mock: spy + stub + 执行结果的预期
- fake time: replace setTimeout/clearTimeout/setInterval/clearInterval/Date
- fake xhr
- fake server


#### supertest

用来测试 nodejs http server，包括 express/connect

- 与 superagent 一致的 api

[supertest github 首页][supertest]


#### jsdom && phantomjs

- jsdom：模拟浏览器环境，基本能解决大多数基于浏览器的组件测试。但是
jsdom 无法处理太复杂的页面或者基于事件/dom 变化的交互。
- phantomjs:功能更全面的真实浏览器环境


### 怎么保证单测质量

代码覆盖率

- 语句覆盖率
- 分支覆盖率
- 函数覆盖率
- 行覆盖率

核心单元与模块应该达到或接近 100%，页面级别组件覆盖率可达到 90%

覆盖率工具：istanbul


#### istanbul

- check-coverage: 根据预设的阀值判断覆盖率是否达标
- cover: 运行单测，生成覆盖率报告

istanbul support es6: v1.0.0-alpha.2

istanbul support windows: npm script 与 linux 不同

支持下面四种覆盖率：

 - statements：语句覆盖率
 - branches：分支覆盖率
 - functions：函数覆盖率
 - lines：行覆盖率

配置上，支持命令行参数和配置文件

.istanbul.yml（ 默认配置文件名，可设置 ）

获取配置文件格式:

```javascript
./node_modules/.bin/istanbul help config
```
配置文件 example:

```text
verbose: false
instrumentation:
    root: .
    extensions:
        - .js
    default-excludes: true
    excludes: []
    variable: __coverage__
    compact: true
    preserve-comments: false
    complete-copy: false
    save-baseline: false
    baseline-file: ./coverage/coverage-baseline.raw.json
    include-all-sources: false
    include-pid: false
    es-modules: false
    auto-wrap: false
reporting:
    print: summary
    reports:
        - lcov
    dir: ./coverage
    summarizer: pkg
    report-config: {}
    watermarks:
        statements: [50, 80]
        functions: [50, 80]
        branches: [50, 80]
        lines: [50, 80]
hooks:
    hook-run-in-context: false
    post-require-hook: null
    handle-sigint: false
check:
    global:
        statements: 0
        lines: 0
        branches: 0
        functions: 0
        excludes: []
    each:
        statements: 0
        lines: 0
        branches: 0
        functions: 0
        excludes: []
```

其中，常用设置选项是 reporting 和 check：

- reporting 对应 check 命令的设置
- check 对应 check-coverage 命令的设置


#### 支持多进程

可以使用 node.js 脚本开启多进程并行测试，对大型项目比较有用


#### istanbul + mocha

istanbul 可以和 mocha 无缝衔接，根据 mocha 的测试结果，生成覆盖率报告，命令如下：

```npmscript
istanbul cover node_modules/mocha/bin/_mocha --print detail -- test/**/*.test.js --require test/setup.js --reporter progress --compilers js:babel-register
```


### 实践 ([webfront-ad/zhixuan][zhixuan])

1. 纯函数的单测
    - test/actions/Message.test.js
1. ajax 的单测
    - test/actions/Notification.test.js
1. UI component 单测
    - test/components/RangedDatePicker.test.js
    - test/components/App.test.js
1. server api 单测
    - [supertest example](https://github.com/visionmedia/supertest#example)
1. 页面单测
1. 整个应用的单测
1. [高级测试 example](http://mochajs.org/#examples)
    - Express
    - Connect
    - SuperAgent
    - WebSocket.io
    - Mocha


### 总结

单元测试是前端工程化中很重要的一环。它能给我们带来的好处是无处不在的、是润物细无声的。今天你没有感受到，只是因为你还不了解它。长期以来，我们都因为各种主观客观的原因有意无意的在开发中忽视单元测试：“单测有啥用，前端需要单测吗？”，“从来没写过单测啊”，“开发时间太短，没时间搞啊”，“写单测会拖慢开发速度”，... 这些理由虽然有些是合理的，但也正是它们阻止我们向一个合格的程序员迈出下一步。在前端工程化越来越完善的今天，单元测试是很有必要的。希望大家能在更多的项目中加入单元测试，使其成为我们开发的一部分。翻过这座山，我们会看到不一样的风景~


参考资料:

单元测试：

- https://segmentfault.com/a/1190000000317146
- http://www.tuicool.com/articles/yuMvQz

前端自动化测试：

- https://www.zhihu.com/question/29922082

karma：

- http://www.open-open.com/lib/view/open1452221325651.html

selenium-webdriver：

- https://yq.aliyun.com/articles/44435

杭研/Dagger：

- https://github.com/NetEase/Dagger


[单测百科]: http://baike.baidu.com/link?url=hAIURuMweVWKRG6AC7D4dXci92XVGpfgurrZMUW9qtH6t4jLCnKYmUZIAvtbab8Fypk--p-WSb2v5ntyufluFaW-Gy22Fl1Q4rzhHbkSTGOi7OPYgSkLNJk-Xw3vizKU
[zhixuan]: https://gitlab.corp.youdao.com/webfront-ad/zhixuan/tree/indexpage_test_unit
[supertest]: https://github.com/visionmedia/supertest
