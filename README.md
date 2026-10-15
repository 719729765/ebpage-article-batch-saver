# 网页文章批量保存器

从网页富文本、HTML 源码、Markdown 和纯网址中提取文章链接，筛选目标页面，并批量保存网页 HTML 快照。

<div align="center">

**项目介绍：** [码铃薯 · 网页文章批量保存器](https://www.tudoucode.cn/plugins/addons/147/)  
**码铃薯首页：** [www.tudoucode.cn](https://www.tudoucode.cn/)  
**GitHub 仓库：** [719729765/ebpage-article-batch-saver](https://github.com/719729765/ebpage-article-batch-saver)

</div>

> 当前扩展版本：**1.1.1**。项目处于早期测试阶段，建议先使用少量链接验证结果。源码包包含 Chrome/Edge 和 Firefox 两套扩展目录；这不代表扩展已经通过 Chrome Web Store 或 Mozilla AMO 的官方审核。

## 功能特点

- **富文本链接提取：** 将网页文章列表粘贴到富文本编辑区，读取标题背后的真实 `<a href>` 链接；前提是复制内容保留了超链接信息。
- **HTML 源码解析：** 支持普通 HTML 源码，以及常见的实体转义源码，例如 `&lt;a href="..."&gt;`。
- **多格式识别：** 支持 Markdown 链接、纯网址、相对文章地址，以及常见的 `href`、`data-href`、`data-url` 属性。
- **筛选与去重：** 可设置相对链接基准网址、域名筛选、优先保留 `.html` 文章链接、排除常见媒体/静态资源，并去除重复 URL。
- **手动检查结果：** 提取后可以逐项勾选或取消，支持复制选中的链接和导出 TXT。
- **批量保存 HTML：** 对已选择的链接分批打开页面并保存 HTML 快照；可设置每批数量和处理间隔，并停止队列。
- **处理日志：** 页面会显示链接处理结果，方便检查成功或失败项目。

## 项目介绍与获取方式

想先了解工具用途和使用说明，可以访问码铃薯的项目介绍页面：

**[点击查看：码铃薯 · 网页文章批量保存器](https://www.tudoucode.cn/plugins/addons/147/)**

需要获取项目源码时，可以打开本仓库，点击绿色 **Code** 按钮，再选择 **Download ZIP**。下载到的是仓库源码压缩包，不是经过官方商店签名的安装包。

## 支持的浏览器

- Google Chrome
- Microsoft Edge（Chromium 版）
- Mozilla Firefox（当前包可用于临时加载测试；正式发布请以 AMO 审核和签名状态为准）

## 安装方法

### Chrome / Edge

1. 下载本仓库 ZIP 并解压到固定目录。
2. 在 Chrome 地址栏打开 `chrome://extensions/`；Edge 用户打开 `edge://extensions/`。
3. 开启“开发者模式”。
4. 点击“加载已解压的扩展程序”。
5. 选择解压目录内的 `chrome-edge` 文件夹，确认该目录中直接包含 `manifest.json`。
6. 加载完成后，点击扩展图标打开工具。

### Firefox

1. 下载本仓库 ZIP 并解压。
2. 打开 `about:debugging#/runtime/this-firefox`。
3. 点击“临时载入附加组件”。
4. 选择 `firefox` 文件夹中的 `manifest.json`。

Firefox 临时加载的附加组件通常会在浏览器关闭后失效，需要再次载入。面向普通用户长期分发时，应使用符合 Mozilla 要求并完成签名流程的版本。

## 使用方法

1. 打开扩展，复制网页前台的文章列表。
2. 将内容直接粘贴到**富文本编辑区**。不要先经过纯文本编辑器，否则可能丢失标题背后的真实链接。
3. 点击“提取链接”。若未提取到链接，切换到 HTML 源码输入区，粘贴包含 `href` 的源码后再次提取。
4. 根据目标网站调整基准网址、域名和链接类型。默认筛选偏向 `.html` 文章页面；如果目标网址采用其他格式，请修改筛选规则。
5. 检查提取结果，取消不需要处理的链接。
6. 开始批量保存，并按浏览器提示授权访问对应网站。
7. 文件默认保存到浏览器下载目录下的“批量保存网页”子目录。若希望保存到桌面，可将浏览器默认下载位置设为桌面，并关闭“下载前询问每个文件的保存位置”。

## 权限用途

| 权限 | 用途 |
| --- | --- |
| `tabs` | 打开用于处理所选网页的标签页。 |
| `scripting` | 在用户授权访问的页面中读取当前 DOM/HTML。 |
| `downloads` | 将 HTML 快照写入浏览器下载目录。 |
| 可选网站访问权限 | 在处理目标链接时，请求访问相关网站。 |

扩展需要读取用户明确选择的网页内容才能生成 HTML 快照。请只授权你信任的网站，并仅处理自己有权访问和保存的内容。

##**截图**
<img width="1401" height="1986" alt="图片" src="https://github.com/user-attachments/assets/09645017-d2f4-46ad-b44d-37fc98271aeb" />


## 隐私说明

链接提取与筛选在扩展页面本地执行。当前项目源码不包含向项目作者服务器上传提取列表或 HTML 快照的功能，也未集成作者控制的分析或遥测服务。开始批量保存后，浏览器仍会正常访问目标网站；目标网站可能根据自身规则记录访问日志。详细说明请参阅项目中的 [PRIVACY.md](PRIVACY.md)。

## 已知限制

- 保存的是**当前页面的 HTML/DOM 快照**，不是完整离线网页包。图片、CSS、字体及其他外部资源不会自动打包，保存后的页面外观可能与原网页不同。
- 需要登录、验证码、反爬验证、特殊权限或复杂动态渲染的网站，可能只能保存验证页或无法成功读取。
- 如果剪贴板只保留纯文本、没有真实链接，工具无法仅凭标题恢复隐藏的 `href`；请改用 HTML 源码或实际网址。
- 浏览器弹窗策略、权限设置、网站跳转和访问限制都可能影响批量任务。建议先用少量链接测试，并合理设置处理间隔。
- 项目仍处于早期版本，尚不代表已完成所有浏览器的全面回归测试或通过官方扩展商店审核。

## 项目结构

```text
webpage-article-batch-saver/
├── README.md
├── PRIVACY.md
├── .gitignore
├── chrome-edge/
│   ├── manifest.json
│   ├── background.js
│   ├── manager.html
│   └── manager.js
└── firefox/
    ├── manifest.json
    ├── background.js
    ├── manager.html
    └── manager.js
```

## 反馈与支持

- **工具介绍：** [码铃薯 · 网页文章批量保存器](https://www.tudoucode.cn/plugins/addons/147/)
- **码铃薯首页：** [https://www.tudoucode.cn/](https://www.tudoucode.cn/)
- **GitHub 项目：** [https://github.com/719729765/ebpage-article-batch-saver](https://github.com/719729765/ebpage-article-batch-saver)

提交问题时，请提供浏览器名称与版本、复现步骤和错误提示。请先移除 Cookie、登录令牌、私人网址和其他敏感信息，不要将其公开到 Issue 或讨论区。
