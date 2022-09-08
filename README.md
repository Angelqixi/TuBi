# T00ls 签到脚本
t00ls 每日签到脚本 整合了钉钉和邮件通知，本脚本运行环境是 Python3.6 +

请随时关注 https://www.t00ls.com 的域名变化，域名更替会签到失败。 这里已经更新到2022.9.7的域名。上一个域名 https://www.t00ls.cc

**依赖安装**：

```bash
pip install requests
pip install beautifulsoup4
```

# 脚本详情

基于国光大佬的代码进行小更改。详细情况可以去国光大佬的博客仔细阅读学习。
[Python 实现 T00ls 自动签到脚本（邮件+钉钉通知）](https://www.sqlsec.com/2020/07/t00ls.html)

# 定时任务

这里采用了在 Linux 下使用原生的 crontab 命令实现定时任务了：

```bash
# 查看定时任务
crontab -l

# 编辑定时任务
crontab -e
```

编辑定时任务，一行一个任务，本次填写的内容如下：

```bash
30 9 * * * cd /usr/local/python3/bin/; python3 /root/Desktop/TuBi.py>&1
```

表示每天 9:30 自动运行下面的命令： 先cd跳转到/usr/local/python3/bin/目录下，通过python3 运行 /root/Desktop/下的TuBi.py脚本。
（在这的话因为crontab的函数比较呆，可能你在shell环境下能运行的路径，到crontab下的话可能会报错，所以我跳了个点，分开运行。）

````bash
cd /usr/local/python3/bin/; python3 /root/Desktop/TuBi.py>&1
````

这样看起来是不是很简单呢，如果语法没有问题的话，wq退出保存之后会自动弹窗如下提示：

```
crontab: installing new crontab
```

这表示新建定时任务成功，后面就可以躺着赚去每天的 2 个 TuBi 了。

