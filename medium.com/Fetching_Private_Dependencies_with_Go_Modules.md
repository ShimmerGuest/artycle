# Fetching Private Dependencies with Go Modules
[原文地址(https://medium.com/@tim_raymond/fetching-private-dependencies-with-go-modules-1d65afe47c62)](https://medium.com/@tim_raymond/fetching-private-dependencies-with-go-modules-1d65afe47c62)
Modules是Go中用于包依赖管理的特性。该功能现在正处于预览状态，但是在1.13中，这个特性就会默认设置为on。对于一些只用公共依赖的项目来说，这个功能非常好用。但是如果你想很好的使用私有依赖，你需要额外添加一些配置。以下是我设置本地环境以获取私有Go模块和Docker构建环境的经验.