---
layout: post
title: git简单学习笔记
date: 2015-3-23
categories: blog
tags: [学习笔记,知识管理]
description: 寒假使用git时做的学习笔记
---

  
 
<body class="madoko">

<div class="body madoko" style="line-adjust:0"><h6 id="sec-1git" class="h5" data-heading-depth="5" style="display:block">1、安装git</h6>
<pre class="para-block pre-indented" style="display:block"><code>sudo apt-get install git</code></pre><h6 id="sec-2" class="h5" data-heading-depth="5" style="display:block">2、设置用户名与邮箱</h6>
<pre class="para-block pre-indented" style="display:block"><code>git config --global user.email &quot;you@example.com&quot;
git config --global user.name &quot;Your Name&quot;
#global表示当前电脑中所有账户都有权限</code></pre><h6 id="sec-3" class="h5" data-heading-depth="5" style="display:block">3、创建仓库目录</h6>
<pre class="para-block pre-indented" style="display:block"><code>$mkdir fileName        #在本地创建仓库目录
$cd fileName        #进入之
$git init            #将git仓库初始化至当前目录</code></pre><h6 id="sec-4" class="h5" data-heading-depth="5" style="display:block">4、提交文档</h6>
<pre class="para-block pre-indented" style="display:block"><code>git add xxx.xxx                            #将文档添加入暂存区
git commit -m &quot;Some useful message&quot;     #确认托付入分支</code></pre><h6 id="sec-5" class="h5" data-heading-depth="5" style="display:block">5、查看仓库状态</h6>
<pre class="para-block pre-indented" style="display:block"><code>git status</code></pre><h6 id="sec-6" class="h5" data-heading-depth="5" style="display:block">6、查看仓库具体改变情况</h6>
<pre class="para-block pre-indented" style="display:block"><code>git diff        #看到文档的修改细节，但是只能看到文本，位图等无法识别。</code></pre><h6 id="sec-7" class="h5" data-heading-depth="5" style="display:block">7、查看提交历史日志</h6>
<pre class="para-block pre-indented" style="display:block"><code>git log     #    git log --pretty=oneline   用于一行内输出，美观一些
#查看提交历史可以看到之前提交的commit_id，以便回滚</code></pre><h6 id="sec-8" class="h5" data-heading-depth="5" style="display:block">8、时光机</h6>
<pre class="para-block pre-indented" style="display:block"><code>git reset --hard commit_id
指针HEAD指向当前版本，HEAD^指向上一个版本,HEAD^^同理。向上100个版本写为HEAD~100
穿梭前，用git log可以查看提交历史,以便确定要回退到哪个版本。
要重返未来，用git reflog查看命令历史，以便确定回到未来的哪个版本。</code></pre><h6 id="sec-9" class="h5" data-heading-depth="5" style="display:block">9、工作区和暂存区</h6>
<pre class="para-block pre-indented" style="display:block"><code>工作区（working directory）：电脑里能看到的目录
版本库（Repository）:工作区中有一个隐藏目录.git，它就是git的版本库    
    版本库中存了很多东西，其中最重要的东西就是称为stage(或者index)的暂存区、git为我们自动创建的第一个分支master，以及指向master的一个指针HEAD

在使用git add命令时，其实是将文件添加入暂存区。
在使用git commit命令时，就是往master分支上提交。</code></pre><h6 id="sec-10" class="h5" data-heading-depth="5" style="display:block">10、撤销修改</h6>
<pre class="para-block pre-indented" style="display:block"><code>场景一：直接丢弃工作区中的修改：git checkout --fileName        
场景二：不但在工作区中做了修改，还提交到了暂存区。分两步，第一步git reset HEAD fileName，将暂存区的修改回退到工作区中，第二步同场景一使用git checkout --fileName，丢弃工作区中的修改。
场景三：已经commit了不合适的版本到版本库中，先撤销本次提交，既使用git reset --hard commit_id命令。前提是没有推送到远程库中。</code></pre><h6 id="sec-11" class="h5" data-heading-depth="5" style="display:block">11、删除文件</h6>
<pre class="para-block pre-indented" style="display:block"><code>在终端中用rm命令删除了工作区中的文件，此时工作区和版本库不一致，用git status会告诉你哪些文件被删除了。
此时有两个选择，第一：确实要从版本库中删除，使用git rm fileName，然后git commmit确认删除。
第二：在工作区中误删，使用git checkout --fileName命令。    #git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。</code></pre><h6 id="sec-12github" class="h5" data-heading-depth="5" style="display:block">12、远程仓库（以github为例）</h6>
<pre class="para-block pre-indented" style="display:block"><code>第一步：创建ssh key    $ ssh-keygen -t rsa -C &quot;youremail@example.com&quot; 一路enter，在主目录下找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
第二步：登陆GitHub，打开“Account settings”，“SSH Keys”页面。然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容。</code></pre><h6 id="sec-13" class="h5" data-heading-depth="5" style="display:block">13、关联远程库</h6>
<pre class="para-block pre-indented" style="display:block"><code>在终端中进入本地工作区 $ cd fileName
关联远程库$ git remote add origin git@server-name:path/repo-name.git 
关联后，使用命令git push -u origin master第一次推送master分支的所有内容
此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改</code></pre><h6 id="sec-14" class="h5" data-heading-depth="5" style="display:block">14、从远程克隆库</h6>
<pre class="para-block pre-indented" style="display:block"><code>要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。</code></pre><h6 id="sec-15" class="h5" data-heading-depth="5" style="display:block">15、创建与合并分支</h6>
<pre class="para-block pre-indented" style="display:block"><code>查看分支：git branch
创建分支：git branch &lt;name&gt;
切换分支：git checkout &lt;name&gt;
创建+切换分支：git checkout -b &lt;name&gt;
合并某分支到当前分支：git merge &lt;name&gt;
删除分支：git branch -d &lt;name&gt;</code></pre><h6 id="sec-16" class="h5" data-heading-depth="5" style="display:block">16、解决冲突</h6>
<pre class="para-block pre-indented" style="display:block"><code>当在两个分支都对文档内容进行了修改时，执行$ git merge branchName 时会提示错误，Git用&lt;&lt;&lt;&lt;&lt;&lt;&lt;，=======，&gt;&gt;&gt;&gt;&gt;&gt;&gt;标记出不同分支的内容,必须手动解决冲突后再保存。
# $ git log --graph命令可以看到分支合并图。</code></pre><h6 id="sec-17" class="h5" data-heading-depth="5" style="display:block">17、分支管理策略</h6>
<pre class="para-block pre-indented" style="display:block"><code>通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
$ git merge --no-ff -m &quot;some useful message&quot; branchName
因为本次合并会执行一次commit，所以合并后，$ git log可以查看到分支历史。</code></pre><h6 id="sec-18bug" class="h5" data-heading-depth="5" style="display:block">18、bug分支</h6>
<pre class="para-block pre-indented" style="display:block"><code>修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除。
当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。</code></pre><h6 id="sec-19feature" class="h5" data-heading-depth="5" style="display:block">19、feature分支</h6>
<pre class="para-block pre-indented" style="display:block"><code>开发一个新feature，最好新建一个分支；
如果要丢弃一个没有被合并过的分支，可以通过git branch -D &lt;name&gt;强行删除。</code></pre><h6 id="sec-20" class="h5" data-heading-depth="5" style="display:block">20、多人协作</h6>
<pre class="para-block pre-indented" style="display:block"><code>(1)首先，可以试图用git push origin branch-name推送自己的修改；
(2)如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
(3)如果合并有冲突，则解决冲突，并在本地提交；
(4)没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！
# 如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name。</code></pre><h6 id="sec-21" class="h5" data-heading-depth="5" style="display:block">21、创建标签</h6>
<pre class="para-block pre-indented" style="display:block"><code>命令git tag &lt;name&gt;用于新建一个标签，默认为HEAD，也可以指定一个commit id；
git tag -a &lt;tagname&gt; -m &quot;blablabla...&quot;可以指定标签信息；
git tag -s &lt;tagname&gt; -m &quot;blablabla...&quot;可以用PGP签名标签；
命令git tag可以查看所有标签。</code></pre><h6 id="sec-22github" class="h5" data-heading-depth="5" style="display:block">22、使用github</h6>
<pre class="para-block pre-indented" style="display:block"><code>可以推送pull request给官方仓库来贡献代码</code></pre><h6 id="sec-23gitignore" class="h5" data-heading-depth="5" style="display:block">23、.gitignore忽略特殊文件</h6>
<pre class="para-block pre-indented" style="display:block"><code>在使用$ git status查询状态时，有一些系统自动生成的文件会显示在未跟踪的文件中。git为强迫症着想，用户可以创建.gitignore文件，在其内写入要忽略的文件名或正则，如*.txt~
然后将该文件commit入库即可。</code></pre><span data-line=""></span></div>
</body>










