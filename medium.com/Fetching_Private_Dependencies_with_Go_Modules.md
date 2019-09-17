# Fetching Private Dependencies with Go Modules
[原文地址(https://medium.com/@tim_raymond/fetching-private-dependencies-with-go-modules-1d65afe47c62)](https://medium.com/@tim_raymond/fetching-private-dependencies-with-go-modules-1d65afe47c62)
Modules是Go中用于包依赖管理的特性。该功能现在正处于预览状态，但是在1.13中，这个特性就会默认设置为on。对于一些只用公共依赖的项目来说，这个功能非常好用。但是如果你想很好的使用私有依赖，你需要额外添加一些配置。以下是我设置本地环境以获取私有Go模块和Docker构建环境的经验。

当我们从私用仓库获取代码更本问题就是我们需要验证，当Modules中写的是`https://`URLs，git会尝试去获取，例如`https://github.com/<yourorg>/<yourproj>`。一般来说，git立马请求你输入用户名和密码（如果git没有这么做，设置环境变量`GIT_TERMINAL_PROMPT=1`）。如果这样有效，非常棒！(这句话不知道咋翻译) I keep all my passwords in a password manager, so I don’t want to look them up all the time if I can help it.

Git有一个特性叫“credential helpers”([see gitcredentials(7)](https://git-scm.com/docs/gitcredentials))，它可以记住密码避免你每次都需要输入账号密码。如果你使用的是macOS，在安装Git时通常会包含`osxkeychain` helper。当你使用它时，macOS会让你输入账号和密码并且把输入结果加入到Keychain中。之后你就不需要输入账号密码了，只需要macOS的Keychain就可以解锁。关于`osxkeychain` helper帮助文档可以在[GitHub中找到](https://help.github.com/en/articles/caching-your-github-password-in-git)。

