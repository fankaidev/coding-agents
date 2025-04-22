# Coding Agents

这个项目聚合了多个开源的coding agent项目，用于学习和评估。
每个子项目都作为 submodule 添加到当前项目中。

## Coding Agents 分析框架

* 项目结构和框架：分析项目的编程语言和框架、代码目录结构、核心模块等信息
* 交互方式：评估agent与用户的基本交互界面和方法，包括命令行、IDE集成、独立GUI等
* 基本流程：分析agent的核心工作流程，从接收指令到完成任务的处理步骤
* 上下文管理：考察agent如何维护和处理代码上下文，包括文件系统、代码理解和记忆，以及如何从交互中学习并优化自身行为
* 工具使用：评估agent集成和使用外部工具的能力，如版本控制、Lint工具、编译器等
* 模型选择：分析agent的模型使用策略，包括单模型架构、多模型协作及模型切换机制
* 安全策略：评估agent的安全机制，包括代码执行权限、文件访问限制和敏感信息处理
* 执行效果：分析agent完成任务的质量、速度和可靠性
* 成本控制：考察agent如何优化计算资源和API调用成本的策略
* 可扩展性：考察agent如何支持新的语言、框架或工具的能力
* 调试能力：分析agent自我诊断问题和修复错误的能力
* 其他特性：评估agent的其他独特功能或设计理念


## 项目分析

* [aider](aider.md)
* [cline](https://github.com/fankaidev/cline)
* [Roo-Code](https://github.com/RooVetGit/Roo-Code)
* [codex](https://github.com/openai/codex)
* [anon-kode](https://github.com/fankaidev/anon-kode)
* [OpenHands](https://github.com/fankaidev/OpenHands)
* [auto-coder](https://github.com/fankaidev/auto-coder)

## 项目比较

<table>
  <thead>
    <tr>
      <th>维度</th>
      <th>aider</th>
      <th>cline</th>
      <th>OpenHands</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>实现方式</strong></td>
      <td>基于Python的命令行工具，专注于结对编程体验</td>
      <td>作为VSCode扩展实现，深度集成IDE环境</td>
      <td>独立平台，同时支持Web界面和多种运行模式</td>
    </tr>
    <tr>
      <td><strong>交互体验</strong></td>
      <td>通过命令行进行交互，使用"/命令"系统控制工作流，支持语音输入和外部编辑器监视</td>
      <td>在VSCode中提供图形化界面，支持图像上传、差异视图和文件编辑，实现无缝IDE体验</td>
      <td>提供多种交互模式，包括Web界面、CLI和无头模式，支持GitHub Action自动化和API集成</td>
    </tr>
    <tr>
      <td><strong>上下文管理</strong></td>
      <td>
        <strong>代码知识图谱</strong>：构建Repository Map，使用networkx分析代码依赖关系<br>
        <strong>智能重要性排序</strong>：应用PageRank算法识别核心组件，优先处理关键代码<br>
        <strong>多级缓存系统</strong>：维护标签缓存、树缓存和映射缓存，基于文件修改时间更新<br>
        <strong>Git记忆机制</strong>：每次修改自动提交，提交信息包含修改意图，形成可检索的知识库
      </td>
      <td>
        <strong>语法结构分析</strong>：使用tree-sitter解析AST，深入理解代码结构和语义<br>
        <strong>检查点系统</strong>：在关键步骤创建工作区快照，支持比较和回溯<br>
        <strong>文件系统索引</strong>：建立工作区文件索引，识别关联文件和依赖<br>
        <strong>上下文压缩</strong>：智能截断和组织上下文，优化token使用效率
      </td>
      <td>
        <strong>文件系统映射</strong>：构建结构化项目表示，识别关键配置和依赖<br>
        <strong>微代理知识体系</strong>：根据关键词触发特定领域知识，动态加载相关指南<br>
        <strong>任务记忆持久化</strong>：通过memory模块维护短期和长期记忆，在相关任务间传递知识<br>
        <strong>项目特定化</strong>：通过.openhands目录加载仓库特定指南，应用团队约定
      </td>
    </tr>
    <tr>
      <td><strong>工具集成</strong></td>
      <td>
        <strong>版本控制</strong>：自动Git提交、差异查看和撤销<br>
        <strong>代码质量</strong>：运行linter和测试，提供修复<br>
        <strong>系统工具</strong>：执行shell命令，捕获输出<br>
        <strong>多媒体</strong>：处理图像和PDF文件作为设计参考
      </td>
      <td>
        <strong>编辑器工具</strong>：精确文件编辑、代码补全<br>
        <strong>终端集成</strong>：执行命令并监视输出流<br>
        <strong>浏览器自动化</strong>：点击、输入、截图、读取控制台<br>
        <strong>诊断整合</strong>：自动检测并修复编译/lint错误
      </td>
      <td>
        <strong>沙箱执行</strong>：在Docker环境中安全运行代码和命令<br>
        <strong>网络工具</strong>：通过browsergym进行浏览器自动化<br>
        <strong>版本控制</strong>：管理Git仓库、分支、PR和issue<br>
        <strong>开发工具</strong>：代码linting、测试运行、依赖管理
      </td>
    </tr>
    <tr>
      <td><strong>安全机制</strong></td>
      <td>实现文件访问控制和代码路径验证，支持只读模式查看敏感文件，使用Git安全检查防止意外覆盖</td>
      <td>采用"人在循环"设计，所有操作需用户确认，提供代码审核机制和检查点回滚功能</td>
      <td>使用Docker沙箱隔离执行环境，实现细粒度访问控制，安全管理API密钥，严格验证用户输入</td>
    </tr>
    <tr>
      <td><strong>扩展能力</strong></td>
      <td>通过插件式设计和可扩展编辑器框架支持功能扩展，可添加新的编辑策略</td>
      <td>利用Model Context Protocol (MCP)创建自定义工具，支持多语言开发，提供本地化界面</td>
      <td>基于微代理架构实现领域专用知识和工作流扩展，支持多种部署方式，可集成到CI/CD流程</td>
    </tr>
    <tr>
      <td><strong>特色功能</strong></td>
      <td>架构师模式支持两个模型协作（设计与实现分离），丰富的命令系统（40+命令），智能历史摘要</td>
      <td>浏览器自动化支持端到端测试，检查点系统允许比较和恢复工作区，@提及语法快速添加上下文</td>
      <td>微代理系统分为知识型、任务型和仓库型，完整的评估框架，支持多种交互模式满足不同场景需求</td>
    </tr>
  </tbody>
</table>

