go 项目结构规范具体内容如下：

## Go目录

- /cmd，本项目的主干。每个应用程序的目录名应该与想要的可执行文件的名称相匹配 (例如，/cmd/myapp）
- /internal，私有应用程序和库代码。可以阻止其他人在其应用程序或库中导入代码，这个布局模式是由 Go 编译器本身执行的。
- /pkg，外部应用程序可以使用的库代码 (例如 / pkg/mypubliclib)。其他项目会导入这些库，希望它们能正常工作，所以在这里放东西之前要三思。
- /vendor，应用程序依赖项 (手动管理或使用你喜欢的依赖项管理工具，如新的内置 Go Modules 功能)。go mod vendor 命令将创建 / vendor 目录。如果未使用默认情况下处于启用状态的 Go
  1.14，则可能需要在 go build 命令中添加 - mod=vendor 标志。

## 服务应用程序目录

- /api，OpenAPI/Swagger 规范，JSON 模式文件，协议定义文件。

## Web 应用程序目录

- /web，特定于 Web 应用程序的组件: 静态 Web 资产、服务器端模板和 SPAs。

## 通用应用目录

- /configs，配置文件模板或默认配置。可以将 confd 或 consul-template 模板文件放在这里。
- /init，System init（systemd，upstart，sysv）和 process manager/supervisor（runit，supervisor）配置。
- /scripts，执行各种构建、安装、分析等操作的脚本。
- /build，打包和持续集成。
- /deployments，IaaS、PaaS、系统和容器编排部署配置和模板 (docker-compose、kubernetes/helm、mesos、terraform、bosh)。
- /test，额外的外部测试应用程序和测试数据。

## 其他目录

- /docs，设计和用户文档 (除了 godoc 生成的文档之外)。
- /tools，这个项目的支持工具。注意，这些工具可以从 /pkg 和 /internal 目录导入代码。
- /examples，应用程序和 / 或公共库的示例。
- /third_party，外部辅助工具，分叉代码和其他第三方工具 (例如 Swagger UI)。
- /githooks
- /assets，与存储库一起使用的其他资产 (图像、徽标等)。
- /website，如果不使用 Github 页面，则在这里放置项目的网站数据。

## 不应该拥有的目录

- /src，有些 Go 项目确实有一个 src 文件夹，但这通常是开发人员有 Java 背景，在那里它是一种常见的模式。如果可以的话，尽量不要采用这种 Java 模式。

示例:

```sh
├─api
├─bin
├─cmd
│  └─learn
├─config
├─doc
├─internal
├─log
├─pkg
│  └─mod
│      └─cache
├─test
└─tools
```