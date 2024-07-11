# 问题
时不时会在Obsidian出现下面的报错信息：
```c
Uncaught (in promise) Error: fatal: unable to access 'https://github.com/Ori-Alnilam/CS50.git/': Failed to connect to github.com port 443 after 21102 ms: Couldn't connect to server
```

或者像这样的：
```c
plugin:obsidian-git:29441 Uncaught (in promise) Error: error: RPC failed; curl 28 Recv failure: Connection was reset fatal: expected flush after ref listing
```
这些偶（经）尔（常）出现的网络问题，它的报错通知在Git插件设置里是无法关闭的：
![[Pasted image 20240710165400.png]]记笔记时动不动从右上角冒出一条报错通知非常烦人。。
尝试增加Git的网络超时设置和重试次数后——没有用（。＾▽＾）最后**使用 SSH 代替 HTTPS**进行推送才成功解决了这个问题。
# 生成SSH密钥：
- 打开Git Bash，键入：
```c
ssh-keygen -t ed25519 -C "your_email@example.com"
```
- 按Enter键接受默认路径和跳过设置密码：
```c
Enter file in which to save the key (C:\Users\alnilam/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```
# 将密钥添加到`ssh-agent`：
启动`ssh-agent`服务：（这一步我在powershell中运行命令尝试启动`ssh-agent`时一直失败，最后用支持OpenSSH的终端Git Bash就好了）
```c
eval "$(ssh-agent -s)"
```
将生成好的SSH密钥添加到`ssh-agent`
```c
ssh-add ~/.ssh/id_ed25519
```
# 将公钥添加到GitHub：
复制`id_ed25519.pub`文件内容，（默认路径是`C:\Users\alnilam\.ssh\id_ed25519.pub`）
登录GitHub->`Settings`->`SSH and GPG keys`->`New SSH key`
![[Pasted image 20240710185203.png]]
在Key这里粘贴公钥内容，添加。
# 验证Git SSH配置
打开Git Bash，键入：
```c
ssh -T git@github.com
```
第一次连接到GitHub的SSH服务器，需要确认，键入`yes`，回车
应该看到：
```c
Hi xxx! You've successfully authenticated, but GitHub does not provide shell access.
```
![[Pasted image 20240710190018.png]]
# 编辑本地仓库的Git配置文件
在Obsidian vault目录下找到`.git`文件夹，打开其中的`config`文件，在`[remote "origin"]`部分，修改URL为SSH格式：
![[Pasted image 20240710191008.png]]
比如这里将原先的`url = https://github.com/Ori-Alnilam/CS50.git`修改为`url = git@github.com:Ori-Alnilam/CS50.git`，完成后保存并关闭。
# 在Obsidian中验证同步是否顺利
![[Pasted image 20240710191928.png]]
再也没有连接问题的报错信息了

成功撒花✿✿ヽ(´▽｀)ノ✿