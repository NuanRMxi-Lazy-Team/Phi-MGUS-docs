# 前言

本网站为[Phi-MGUS](https://github.com/NuanRMxi-Lazy-Team/Phi-MGUS)开发文档，包含**所有代码逻辑**以及**客户端基本适配方法**  
<font color="yellow">警告：项目仍处在开发阶段，文档将跟随开发进度进行更新，您可以在Github中的Actions中获得仍处在开发中的代码的编译版本。</font>

- 服务器采用`C#`语言，使用`Fleck`包作为`WebSocket`服务器实现。  
- 服务器允许受SSL加密的端口与不受SSL加密的端口同时使用，但我们不建议这么做。  
- 服务器不存储任何数据，服务器也不依赖任何平台，仅独立运行。
- 服务器SSL证书格式需为`.pfx`。
- 服务器大量采用异步。