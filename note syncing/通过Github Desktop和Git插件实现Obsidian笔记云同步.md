# 新建Obsidian笔记库
打开Obsidian -- 创建![[Snipaste_2024-07-08_12-25-09.png]]
名称`testing`，位置`E:\`![[Snipaste_2024-07-08_12-28-45.png]]
点击创建后，在E盘会出现一个`testing`的文件夹![[Snipaste_2024-07-08_12-32-06.png]]
里面有Obsidian的配置文件夹`.Obsidian`，![[Snipaste_2024-07-08_12-35-20.png]]
之后所有添加的笔记都在这个vault目录中，此时只有`欢迎.md`
# 打开Github Desktop新建仓库
打开Github Desktop -- File -- New repository
Name->`testing`，Local path->`E:\`（需要**和Obsidian笔记库路径一致**，在这个示例中是`E:\`）
点击创建
点击publish repository，可以选择是否公开
# 安装Git插件
回到Obsidian，设置 -- 第三方插件 -- 关闭安全模式
浏览插件市场 -- 搜索Git -- 安装Git插件
启用Git插件，如果报错请看这篇文章，我操作时没有出现报错。
点击选项，可以设置自动同步间隔时间，这里是1分钟
# 检查是否成功
Obsidian中打开笔记库，修改`欢迎.md`笔记内容
在自己的GitHub中查看是否同步了修改内容
完成