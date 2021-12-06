# 代理服务器联网的神奇过程

软件：clash for windows
软件只是一个帮你设置代理的工具，要想翻墙还要有订阅的地址。

- [OvO](https://ovocloud.cc/#/dashboard)
- [NordVPN](https://nordvpn.com/zh/)
- [Surfshark](https://surf-chiny.com/zh/)
- [后两款的教程](https://chuanyueweiqiang.com/fq/)
- [Clash for windows官方文档](https://docs.cfw.lbyczf.com/)

过程：

1. 安装服务模式（Tun模式）

2. 配置文件（用YAML语言）：在设置里找到“Mixin混合配置”，编辑其中的YAML语言的文件。代码：

   ```yaml
   mixin:
     dns:
       enable: true
       enhanced-mode: fake-ip
       nameserver:
         - 223.5.5.5
         - 223.6.6.6
         - 119.29.29.29
         - 8.8.8.8
         - 114.114.114.114
       fake-ip-filter:
         - "dns.msftncsi.com"
         - "www.msftncsi.com"
         - "www.msftconnecttest.com"
     tun:
       enable: true
       stack: system
       dns-hijack:
         - 198.18.0.2:53
       auto-route: true
       auto-detect-interface: true
   ```

   

3. 在主菜单中开启混合配置选项



# latex语法汇总

- `\xxx`为xxx控制序列，`\xxx{}`中{}里面的为必要参数`\begin`与`\end`两个控制序列之间的内容被成为环境

- 数学公式及相关符号：

  1. 插入数学公式：行内公式：`$...$`（最简便，要在typora的“文件”中的“偏好设置”里面的“Markdown”中打开才能正常显示），行间公式：`$$...$$`、`\[...\]`(无编号)、（有编号用equation环境），貌似在markdown中插入行间公式就一定要用`$$...$$`

     ```
     \begin{equation}
     ...
     \end{equation}
     ```

  2. 数学公式：`\lmoustache`为积分符号、`\frac{}{}`为分数、`\cdot`为·号、`\lim`是极限的符号、`limits_{n \to \infty}`为极限的下标，其中`\to`是->号，`\infty`为∞
  3. 格式符号及环境：`&`为对齐（可以加多个）、`\\`为换行、`{aligned}`为对齐环境

# 12月任务数学题
1. $$
   \lmoustache \frac{e^{-\sin x} \cdot \sin 2x}{(1-\sin x)^2} dx
   $$
   
   解：
   $$
   \begin{equation}
   \begin{aligned}
   	\lmoustache \frac{e^{-\sin x} \cdot \sin 2x}{(1-\sin x)^2} dx &=         	 2\lmoustache {e^{-\sin x} \cdot \sin x} d(\frac {1}{1- \sin x}) \\&=
   	2(\frac{t}{e^t \cdot(1-t)} - \lmoustache \frac{1}{1-t}d(\frac{t}{e^t})) \\&=2(\frac{t}{e^t \cdot(1-t)} - \lmoustache \frac{e^t - te^t}{(1-t)e^{2t}}dt)
   	\\&=2(\frac{t}{e^t \cdot(1-t)} - \lmoustache \frac{1}{e^t}dt)
   	\\&=2(\frac{t}{(1-t)e^t} + \frac{1}{e^t}) + c
   	\\&=\frac{2 \sin x + 2}{(1- \sin x)e^{\sin x}} + c
   \end{aligned}
   \end{equation}
   $$
   

- 思路：看到$\sin 2x$和$(1- \sin 2x)^{-2}$就能想到用直接法把它们换掉，然后得到$2\lmoustache {e^{-\sin x} \cdot \sin x} d(\frac {1}{1- \sin x})$，看到式子都有$\sin x$，就想到换元，然后用分部积分法解即可。

  

2. $\lim \limits _{n \to \infty} sin^2(\pi \sqrt{n^2+n})$

   解：
   $$
   \begin{aligned}
   \lim \limits _{n \to \infty} sin^2(\pi \sqrt{n^2+n}) &= \frac{1}{2}\lim \limits_{n \to \infty}1- \cos(2 \pi \sqrt{n^2+n})
   \\&=\frac{1}{2}\lim \limits_{n \to \infty}1- \cos(2 \pi \sqrt{n^2+n}-2 \pi{n})
   \\&=\frac{1}{2}\lim \limits_{n \to \infty}1- \cos{(2 \pi(\sqrt{n^2+n}-n))}
   \\&=\frac{1}{2}\lim \limits_{n \to \infty}1- \cos{(2 \pi(\frac{n}{\sqrt{n^2+n}+n}))} &用了平方差公式
   \\&=\frac{1}{2}\lim \limits_{n \to \infty}1- \cos{(2 \pi(\frac{1}{\sqrt{1+\frac{1}{n}}+1}))}
   \\&=\frac{1}{2} \cdot(1-(\cos\pi))
   \\&=1
   \end{aligned}
   $$
   


- 思路：先把平方变为一次方，因为$2 \pi \sqrt{n^2+n}$没有极限，所以要想求得极限则需要利用三角函数的性质（周期性），使得其可以变成$2 \pi \sqrt{n^2+n}-2 \pi{n}$，由于有了减号，式子就有极限，就可以用平方差公式把它变为分式，从而把极限求出。



# Git

- 安装：搭梯子去官网下，按默认设置一路点过去~

- 初始设置：`$ git config --global user.name "Mario"`设置本机器用户名、`$ git config --global user.email "927035481@qq.com"`设置本机器邮箱（注意：`""`前的空格不能丢，否则后面就报错“识别不了”了）

- 建立版本库：

  1. 在指定地方建立版本库（这里建立的是名为ima的版本库）：

     `$ mkdir /d/repository/ima`

  2. 切换到指定目录：`$ cd /d/repository/ima`

  3. 显示当前所在目录：`$ pwd`

  4. 将该目录变为git可管理的仓库：`$ git init`

- 把文件添加到版本库中：

  1. 编写一个文件，放在ima目录下
  2. 把文件添加到仓库：`git add latex语法汇总及12月任务.md`，还是最好用英文
  3. 把文件提交到仓库：`git commit -m "first"`，`""`里面的为对这次提交的说明，且记得前面的空格不要丢！！！不然就报错让你输名字和邮箱。

- 关联远程库：

  1. `$ git remote add origin https://github.com/Mari00oo00/IMA-Mario.git`，后面的`.git`不要丢
  2. `$ git remote add origin git@github.com:Mari00oo00/IMA-Mario.git`，据说这个会快一点

- 把内容推送到远程库：

  1. 第一次推送：`$ git push -u origin master`，之后就可以`$ git push origin master`

## 今日报错：

2021/12/5:

输入`$ git push -u origin master`
报错：`fatal: unable to access 'https://github.com/Mari00oo00/IMA-Mario.git/': Failed to connect to github.com port 443 after 21076 ms: Timed out`

尝试：为git设置全局代理`$ git config --global https.proxy http://127.0.0.1:7890`，还是不行。有设置了一次，这次用`$ git config --global http.proxy http://127.0.0.1:7890`就成功了。（7890是代理服务器给的，可在“设置”的“代理中查看”）

