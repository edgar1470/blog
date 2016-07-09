GIT Tips
<!-- toc -->


### 在bash提示符显示当前的git分支
[Show the current Git branch on your Bash pro](https://makandracards.com/makandra/524-show-the-current-git-branch-on-your-bash-prompt)
Append this to your ~/.bashrc:
```bash
export PS1='\[\033[01;32m\]\h\[\033[01;34m\] \w\[\033[31m\]$(__git_ps1 "(%s)") \[\033[01;34m\]$\[\033[00m\] '
```
Reload the changes by saying
```bash
source ~/.bashrc
```


### 本地SVN仓库转换成git仓库
```bash
git svn clone file:///media/sf_D_DRIVE/test_svn_repos test.git
```
