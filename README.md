## SiteProxy 2.0
 - [English ver](README_english.md)

SiteProxy 是一个**功能强大的在线代理工具**，采用了最新的技术，提升了代理的稳定性和兼容性。我们致力于提供 **简单、高效、安全** 的代理服务，为用户提供最佳的互联网访问体验。

- **超高速性能**：采用 Hono 替代传统的Express 服务器，性能提升 4 倍，带来更流畅的使用体验。
- **云端部署**：完美支持 Cloudflare Worker 部署，快速且高效。
- **AI 智能聊天**：集成 DuckDuckGo AI Chat，免费提供 GPT-3.5 和 Claude 3，让你的代理服务更加智能。
- **高级安全保护**：支持密码控制代理，只有授权用户才能访问，大幅提升安全性。
- **零配置使用**：用户无需进行任何客户端配置，只需访问代理网址即可畅游全球互联网。
- **便捷登录**：全面支持 GitHub 和 Telegram Web 登录，操作简单快捷。
- **强力加密**：采用 `RSA + AES` 双重加密技术，保护用户登录密码，防止中间人攻击。
- **隐私保护**：通过代理网址访问全球互联网，同时隐藏用户真实 IP，保护隐私。
- **无缝体验**：无需任何软件安装和浏览器配置，即可立即使用，提供极致便利的用户体验。

<details>
  <summary>查看原理</summary>

```
                                                 +----> google/youtube
                             +----------------+  |
                             |                |  |
user browser +-------------->+ siteproxy      +-------> wikipedia
                             |                |  |
                             +----------------+  |
                                                 +----> chinese forums
```

</details>

> [!CAUTION]
> 严禁将本项目用于任何非法用途，否则后果自负

> [!WARNING]
> 由于支持多个网站的 Login，为了减少钓鱼风险，Siteproxy 在 2.0 版本对代码进行了混淆，同时禁止了默认主页网址的修改。



   - 现在可以通过 `https://your-worker-domain.com/your-password/` 访问代理服务（确保最后的斜杠存在，并替换为你自己的域名和密码）。


  其他安装方式详见官方，下面是Docker版安装方法

## Docker 部署
1. **配置 SSL 证书和 Nginx**：
   - 配置域名对应的 SSL 证书和 Nginx，将其指向本地的 5006 端口。
2. **克隆仓库**：
   - 执行命令：`git clone https://github.com/liyehuicn/siteproxy.git`
3. **编辑配置文件**：
   - 打开并修改 `config.json` 文件，内容如下：
     ```json
     {
        "proxy_url": "https://your-proxy-domain.com", // 替换为你申请到的代理服务器域名
        "token_prefix": "/user-SetYourPasswordHere/",  // 设置网站密码，用于防止非法访问，保留首尾的斜杠
        "description": "注意：token_prefix 相当于网站密码，请谨慎设置。 proxy_url 和 token_prefix 合起来就是访问网址。"
     }
     ```
   - 保存文件。
  
   - 修改/docker-node/docker-compose.yml里面的image: node:21为image: siteproxy2:latest
   - 下载https://github.com/liyehuicn/siteproxy/releases/  并导入镜像（以1panel为例）
5. **启动 Docker 容器**：
   - 进入 `docker-node` 子目录。
   - cd siteproxy/docker-node/
   - 执行命令：`sudo docker compose up`
6. **访问代理服务**：
   - 现在可以通过 `https://your-proxy-domain.com/user-your-password/` 访问代理服务。请将域名和密码替换为你自己的域名和密码。


