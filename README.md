# jiangdu's blog

我的~~垃圾~~个人博客
使用了 `hexo` 博客框架，[butterfly](https://github.com/jerryc127/hexo-theme-butterfly)主题。

源文件在 `source` 分支（默认分支）
`post` 在 `/source/_posts` 文件夹里，欢迎PR（

## 做博客时遇到的坑：

1. 如果初次 `deploy` 失败，记得填写 `_config.yml` 中的  `url` 和 `root` , 例如：

   ```yaml
   url: https://satorimarch.github.io
   root: /
   ```

2. `post`文件名中不要有 `#` ，例如 `C#`，`#` 后面的在HTTP请求中会被忽略

3. git 设置代理:

   ```bash
   git config --global http.proxy http://127.0.0.1:7890
   ```

   git 取消代理:

   ```bash
   git config --global --unset http.proxy
   ```

   