# Jin Xie 个人主页

目标网址：https://michaelxie-leo.github.io/

这是 Minima 风格的纯 HTML/CSS 学术主页，参考 https://ljz0.github.io/ 的简洁布局。
无需安装 Ruby、Jekyll、Node.js 或任何第三方依赖；GitHub Pages 直接发布这些静态文件。
Minima 模板的许可保留在 `LICENSES/minima.txt`，许可说明适用于模板部分。
个人资料、论文以及 CV 的权利仍归各自权利人所有。

## 修改主页

- `index.html`：个人介绍、论文、教学和联系方式。
- `assets/main.css`：字体、颜色、间距和手机布局。
- `assets/CV_JinXie_20260425.pdf`：现有公开主页所链接的 CV。替换文件名时，同时修改 `index.html` 中的两个 CV 链接。

直接双击 `index.html` 即可本地查看。页面无需 JavaScript，也不依赖外部字体或样式服务。

在此仓库文件夹打开 PowerShell，修改完成后运行：

```powershell
$homepageDirectory = (Get-Location).Path.Replace('\', '/')
$homepageTrust = "safe.directory=$homepageDirectory"
git -c $homepageTrust status
git -c $homepageTrust add index.html assets
git -c $homepageTrust diff --cached --stat
git -c $homepageTrust commit -m "Update research and CV"
git -c $homepageTrust push
```

提交前用 `git -c $homepageTrust diff --cached` 查看将上传的内容。上传成功后，GitHub Pages 会自动更新，通常需要几分钟。
上面的目录信任参数仅在本次命令生效，用于处理主页文件由 Codex 创建、上传由你的 Windows 账户执行时的目录所有者差异，不修改全局 Git 信任设置。

## GitHub Pages 设置

仓库为 `MichaelXie-LEO/MichaelXie-LEO.github.io`，发布分支为 `main`。
在 GitHub 仓库的 Settings → Pages 中，选择 Deploy from a branch → `main` → `/ (root)`。
`.nojekyll` 使 GitHub Pages 直接使用静态页面，无需主题构建。
2026-09-07 已上传主页并确认上述发布设置生效，HTTPS 已开启。

## 在其他本地代码文件夹使用 GitHub

先用 `git status` 确认该文件夹是否已有 Git 仓库；已有仓库应保留现有历史和远程设置。
在一个尚未初始化的新代码文件夹中，先创建适合该项目的 `.gitignore`，然后执行：

```powershell
git init -b main
git add <要上传的代码文件>
git diff --cached
git commit -m "Initial commit"
gh repo create <仓库名> --private --source . --remote origin --push
```

把尖括号占位符替换为实际文件和仓库名。研究代码可先使用私有仓库；个人主页使用公开仓库。
GitHub 登录检查：`gh auth status`。需要重新登录时：`gh auth login --hostname github.com --git-protocol https --web`。

## 资料来源

资料核对日期：2026-09-07。

- 现有个人主页：https://sites.google.com/view/jin-xie-phbs/home
- 现有研究页面：https://sites.google.com/view/jin-xie-phbs/home/research
- 个人提供的中英文网站介绍及 2026 年 3 月 CV。
- 公开主页上的 2026-04-25 CV。
- 参考模板配置：https://github.com/ljz0/ljz0.github.io/blob/main/_config.yml
- Minima：https://github.com/jekyll/minima/tree/v2.5.1

研究页面中的最新题名、作者、发表信息、论文分类和公开链接优先于较早的本地 CV。
保留了 7 篇发表论文、6 篇工作论文、2 项进行中研究和 3 篇永久工作论文。
工作论文审稿状态沿用核对当日的现有公开主页。未提供公开下载链接的论文只展示题名和作者。
本仓库仅包含主页文件，不包含求职材料、推荐信、评审表或原始研究数据。
