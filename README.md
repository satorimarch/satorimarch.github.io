# jiangdu's blog

我的~~垃圾~~个人博客
使用了 `hexo` 博客框架，[butterfly](https://github.com/jerryc127/hexo-theme-butterfly)主题。

源文件在 `source` 分支（默认分支）
`post` 在 `/source/_posts` 文件夹里

## 做博客时遇到的问题：

1. 如果初次 `deploy` 失败，记得填写 `_config.yml` 中的  `url` 和 `root`，例如：

   ```yaml
   url: https://satorimarch.github.io
   root: /
   ```

2. `post`文件名中不要有 `#`，例如 `C#`，`#` 没经过转义，其后面的内容在HTTP请求中会被忽略

3. git 设置代理：

   ```bash
   git config --global http.proxy http://127.0.0.1:7890
   ```

   git 取消代理：

   ```bash
   git config --global --unset http.proxy
   ```

4. 运行 `hexo s` （没有其他参数）时报错：
   > hexo node:events:368 throw er; // Unhandled 'error' event
   > Error: listen EACCES: permission denied 0.0.0.0:3000

   猜测是端口被占用了，但用 `-p` 参数换了几个端口也不行，用 `netstat` 也没查到有占用这个端口的进程。
   最后在 `powershell` 里输入这个命令解决：

   ```
   net stop winnat
   net start winnat
   ```

   查到 `hyper-v` 会保留一部分端口，而我装了 `wsl2`。等我下次再遇到这个问题的时候再研究怎么修改动态端口范围吧。