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
