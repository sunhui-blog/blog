---
title: Git使用过程中遇到的问题
date: 2019-09-04 03:08:44
tags:
categories: 工具
---
<p>此篇用于记录Git使用过程中遇到的问题。</p>
<style type="text/css">
.pt{padding-top:10px;}
.pt5{padding-top:5px;}
.fb{font-weight:bolder;}
</style>
<!-- more -->
<ol>
  <li class="pt">多个公私密钥情况下，如何添加ssh-add？
    <div class="pt">
      <span class="fb">起因：</span>出于安全考虑，我的github和公司内部的git分别用两套ssh生成的公私密钥，在使用过程中，由于ssh-add不是永久的，切换后反复需要再次加上，费时费力。
      <p class="pt5"><span class="fb">解决方式：</span>通过如下方式，将key加入keychain中解决</p>
      ```
      ssh-add -K ~/.ssh/keyname
      ```
      <span class="fb">参考：</span>https://segmentfault.com/q/1010000000835302
    </div>
  </li>
  <li class="pt">如何撤销rebase？
    <div class="pt">
      <span class="fb">起因：</span>
      在rebase过程中，操作失误，将conflict合并至本地分支，当然可以通过处理冲突后再commit方式来解决，但无疑多增加了一次不必要的commit，因此考虑撤销rebase再来rebase一次。
      <p class="pt5"><span class="fb">解决方式：</span>git reflog + git reset --hard</p>
      ```
      git reflog 
      git reset --hard HEAD@{index} // 如 index=rebase前的索引
      ```
      <span class="fb">参考：</span>https://www.cnblogs.com/suanec/p/7511137.html
    </div>
  </li>
  <li class="pt">Add all files to a commit except a single file?
    ```
    git add -u
    git reset -- XXX.txt
    ```
  </li>
  <li class="pt">撤销push到远程的某个文件的commit同时清除历史？

  </li>
  <li class="pt">查看本地分支和远程分支
    ```
    git branch       // 本地分支
    git branch -r    // 远程分支
    ```
  </li>
  <li class="pt">删除本地分支和远程分支
    ```
    // 本地分支
    git branch -D BranchName

    // 远程分支
    git branch -r -D origin/BranchName
    git push origin -d BranchName    
    ```
  </li>
  <li>查看两个branch差异？
    <div>查看A有B没有
    ```
    git log A ^B
    ```
    </div>
    <div>查看B有A没有
    ```
    git log B ^A
    ```
    </div>
    <div>查看A比Bd多了哪些？
    ```
    git log A..B
    ```
    </div>
    <div>查看B比A多了哪些？
    ```
    git log B..A
    ```
    </div>
    <p>在上线发布前对比master分支时，需要确认一下分支情况。</p>
    <div>直接将两个分支上最新的提交做diff
    ```
    git diff topic master
    git diff topic..master
    ```
    </div>
    <span class="fb">参考：</span>https://blog.csdn.net/u011240877/article/details/52586664
  </li>
</ol>
