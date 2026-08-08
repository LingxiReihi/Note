# Github远程同步配置

----

### 使用前提

- 计算机已经安装`git`
- 注册有`Github`账号

----

### 配置SSH

#### 生成SSH密钥对

```powershell
ssh-keygen -t ed25519 -C "你的邮箱"
```

中途遇见提示可以直接使用回车默认值：

![生成SSH密钥](https://cdn.jsdelivr.net/gh/LingxiReihi/PicGo@master/img/20260809061851135.png)

生成后会出现两个文件：

- `~/.ssh/id_ed25519`，私钥。

- `~/.ssh/id_ed25519.pub`，公钥，可以提交到平台。

#### 复制密钥准备上传

前往对应目录打开公钥文件，或使用以下命令打开，复制整行内容：

```powershell
cat ~/.ssh/id_ed25519.pub
```

### 连接到Github

#### 将密钥添加到Github中

`点击个人头像 -> Settings -> SSH and GPG keys -> New SSH key`，可以在上方备注该密钥来源等信息。

![添加SSH key到Github中](https://cdn.jsdelivr.net/gh/LingxiReihi/PicGo@master/img/20260809070827617.png)

#### 测试连通性

在控制台中输入以下指令进行测试：

```powershell
ssh -T git@github.com
```

当出现` You've successfully authenticated`时则可正常连接（若出现`ssh: connect to host github.com port 22: Connection refused`则需要进行科学上网）。

![验证连通性](https://cdn.jsdelivr.net/gh/LingxiReihi/PicGo@master/img/20260809071401356.png)

### 上传或拉取远程仓库内容

#### 关联本地与远程仓库

进入到本地仓库中，使用如下指令添加远程库：

```powershell
git remote add origin git@github.com:你的用户名/你的仓库名.git
```

同时可以使用以下指令验证是否成功关联：

```powershell
git remote -v
```

![关联远程仓库](https://cdn.jsdelivr.net/gh/LingxiReihi/PicGo@master/img/20260809071741331.png)

#### 拉取或推送到远程仓库

在本地进行提交后，可以使用`push`指令将仓库推送到远程库中，或使用`pull`指令拉取远程库中的内容到本地仓库。

```powershell
git push origin main
git pull origin main
```

