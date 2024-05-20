
# info
## Links
* git 간편 안내서 : https://rogerdudler.github.io/git-guide/index.ko.html
* 누구나 쉽게 이해할 수 있는 Git 입문 : https://backlog.com/git-tutorial/kr/stepup/stepup1_1.html
* 지옥에서온 Git : https://opentutorials.org/module/2676
* git 튜토리얼 메뉴얼 페이지 : http://www.funit.net/git
* [GIT 사용법] Git Tutorial : http://www.dreamy.pe.kr/zbxe/CodeClip/95408
* git 사용법(Manual) : http://bunhere.tistory.com/37
* git server repository 환경 구성하기 : http://khmirage.tistory.com/309
* Subversion 사용자를 위한 git, Part 1: 시작 : http://www.ibm.com/developerworks/kr/library/l-git-subversion-1/
* git setting : http://live.gnome.org/git/Developers
* issue to Code review : https://www.popit.kr/github로-프로젝트-관리하기-part1-이슈-발급-부터-코드리뷰까/
* Git 되돌리기 : https://www.devpools.kr/2017/02/05/초보용-git-되돌리기-reset-revert/
* heejeong Kwon : https://gmlwjd9405.github.io/2018/05/18/git-stash.html

## Services
* Git Hub     : https://github.com
* Bitbucket   : https://bitbucket.org
* SourceForge : https://sourceforge.net

# Setup
## Install Git
### CentOS
    $ sudo yum install git
### Ubuntu
    $ sudo apt-get install git-core

## git config
### Password 저장
```
git config credential.helper get
git config credential.helper erase
git config credential.helper store
git config credential.helper cache
git config credential.helper 'cache --timeout=36000'
git config credential.helper store --global
```
### General Settings
```
git config --global user.name "Steve J. South(NamJungGu) "
git config --global user.email "nowage@gmail.com"
git config --global color.status auto
git config --global color.branch auto
git config --list
```

### 다른 유저로 Push 하기
```
git config  user.name "jgnam2020"
git config  user.email "jgnam@gkn.co.kr"
git config --local credential.helper ""
git push origin master
```
## Windows에서 필수 셋팅
* GitBash에서는 autocrlf로 되어 있어서 enter키가 외곡됨으로 필수 셋팅
```
git config --global core.autocrlf false
git config --global core.eol lf
```
## ~/.gitconfig 파일
```
[user]
        name = nowage
        email = nowage@gmail.com
[core]
        autocrlf = true
        eol = lf
[difftool "sourcetree"]
        cmd = '' \"$LOCAL\" \"$REMOTE\"
[mergetool "sourcetree"]
        cmd = "'' "
        trustExitCode = true
[alias]
	lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
	lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all
	lg = !"git lg1"
```

* Usage
```
git lg
# == git log --graph --decorate --oneline
```
## Prompt for git branch name
```
# Only this session
PS1="\[\033[32m\]\h \[\033[34;1m\]\w \[\033[32m\]\[\033[m\]\[\e[91m\]\$(parse_git_branch)\[\e[00m\]$ "
# Make alias
alias ps1g='PS1="\[\033[32m\]\h \[\033[34;1m\]\w \[\033[32m\]\[\033[m\]\[\e[91m\]\$(parse_git_branch)\[\e[00m\]$ "'
#  → jMac2 ~/test (master)$
```
# Basic Usage
## Set Up Git
```
git config --global user.name "NamJungGu"
git config --global user.email "nowage@gmail.com"
```
## init & commit
```
mkdir src
cp xx src/
cd src
git init
git add .
git commit -m "Initial commit"
git log
```
### Commit Only Change
```
echo "This is a change" > test01
git diff
# 변경사항 커밋하기, -a는 수정된 파일들에 대해서만 커밋함
# 하지만 새로운 파일은 자동으로 추가하지 않음
git commit -a -m "xx"
git commit -m "xx"
```
## Branch
```
git init
echo z>z.txt
git add z.txt
git commit -m "z.txt"
git branch b1

git remote add origin https://github.com/nowage/test
git fetch --all
git reset --hard origin/master
git pull origin master

git checkout b1
git rebase master
# 충돌 있으면 master로 checkout 후 → git add [해당파일];git rebase --continue;vi [해당파일];git add -A

git checkout master
git merge b1
git branch -d "b1"
ls
git push
```

## Clone
```
  ## 저장소로 이동
    cd ~/src
	## bare clone
		git clone --bare . ../remote-repository.git
	## 	General clone
		git clone gitPath
		git clone shiny@R-graph.com:/git/ttest.git
```
## 충돌 해결
```
vi README.md
git commit -a -m "README.md change"
git pull ##  같은 파일이라도 다른 부분을 수정하면 자동 merge됨
# git status # 자동 merge 안되면
# git diff # 자동 merge 안되면
# vi README.md # 자동 merge 안되면
git add README.md
git commit -m "complicted clear"
git push
```

## 다른 저장소로 변경내용 Push 하기
## Add Remote
```
    # ../remote-repository.git 저장소를 origin으로 추가한다.
    git remote add origin https://xxxxxxxx/remote-repository.git
    # 자 현 저장소(working copy)에 수정을 가한다.
    echo "I added a remote repo" > test02
    # Staging index 로 commit 한다.
    git commit -a -m "This is a test for the new remote origin"
    # origin으로 push 한다. 만일 git push 만 입력할 경우 자동으로 origin으로 보내게 된다.
    git push origin
```

## pull remote
```
    git remote add nj shiny@nj:/git/meta.git
    git pull nj master
```
## local에서 만든 repository와 remote repository 동기화
```
git init
echo z>z.txt
git add z.txt
git commit -m "z.txt"
git branch b1

git remote add origin https://github.com/nowage/test
git fetch --all
git reset --hard origin/master
git pull origin master

git checkout b1
git rebase master
# 충돌 있으면 master로 checkout 후 → git add [해당파일];git rebase --continue;vi [해당파일];git add -A

git checkout master
git merge b1
git branch -d "b1"
ls
git push
```
## Update fork directly on Github
* https://rick.cogley.info/post/update-your-forked-repository-directly-on-github/
```
git remote add upstream https://github.com/in4it/prometheus-course
git remote -v
git fetch upstream
git checkout master
git merge upstream/master
```
# git 관련 명령어
## git
* cli명령
## gitk
* 내장 gui

# git 명령어
## add
```
git add -A [.]
git add -i     # 대화식으로 추가
git add a.txt
git status
git reset HEAD xx  # unstaging
git status
```

## branch
```
git branch        # branch list
git branch -d b1  # b1 branch를 삭제
```
## cherry-pick
* 다른 브랜치의 커밋을 현재 브랜치로 가져옴

```
git branch b1
git branch
touch a;git add -A;git commit -a -m 'a'
touch b;git add -A;git commit -a -m 'b'
touch c;git add -A;git commit -a -m 'c'
git log --graph --decorate --oneline
git checkout b1
git cherry-pick <<2c06166>>
ls
git checkout master
git merge b1
git branch -d b1
git log --graph --decorate --oneline
```
## clone
```
git clone https://github.com/nowage/test
cd test
```
## commit
* stage → repository로 이전
```
git commit -m "message"
git commit       # list를 확인하며 vi편집기를 통해 메세지 입력
git commit --amend "현재 추가된 내용을 기존 commit과 합친다."
```
## diff
* Unstaging 영역에서 작동(add하면 안보임)
```
git diff [파일명]
```
## checkout
```
```

## init
```
mkdir test
cd test
git init
ls -als
```
## fetch
* 원격 저장소의 데이터를 로컬에 가져오기만 함.
* pull=fetch+merge
```
## remote/master가 수정되었을때
git fetch --all
git checkout origin/master
cat README.md          # 내용 확인
git checkout master
git merge origin/master
cat README.md
# git push 필요 없음.
```


## log
```
git log
git log -p -2
git log --graph --decorate --oneline
git log --pretty=format:"%h %s" --graph
git lg # .gitconfig에 lg라는 alias가 있을때
```

## merge
```
git checkout master
git merge b1           # b1 branch를 merge함
git merge --squash b1  # b1 commit history를 제거하고 commit
```

## push
```
git commit -a -m "--"
git push
```
## rebase
* 현재 branch를 기준으로 merge(일반적인 merge는 master branch를 기준으로 merge함)함
* 충돌을 해결하는 또 다른 방법
* 원격 레포지터리 merge할때도 쓰임
* 장점 : 여러 개발자들이 같은 브랜치를 공유할 때 커밋을 합치는 가장 직관적이고 깔끔한 방법.
* 단점 :
  - 충돌상황에서 다소 복잡. 커밋 순서대로 Rebase 를 하는데, 각 커밋마다 충돌해소를 순서대로 해주어야
  - 해당 커밋들을 다른 곳에 푸시한 적이 있다면 해결하기 힘듦

```
git checkout b1
git rebase master
```


* cf) git rebase (--continue | --abort | --skip)
* cf) git rebase -i HEAD~2


## reset
* 해당  commit 시점 으로 되돌림
### soft reset : commit 정보 사라짐, 적용 내용 남아 있음.
```
git reset --soft <<commit번호>>
```
### hard rest : commit 정보 사람짐,  적용 내용 모두 사라짐
```
git reset --hard <<commit번호>>
git reset HEAD  [file_or_folder] # unstage
```
### mixed reset : commit 정보 사라짐, 적용 내용 남아 있음
```
git reset --mixed <<commit번호>>
git reset <<commit번호>>
```

### commit 합치기
```
touch a;git add -A;git commit -a -m 'a'
touch b;git add -A;git commit -a -m 'b'
touch c;git add -A;git commit -a -m 'c'
git reset --soft HEAD~3
git status
git commit -m 'abc'
```


## revert
* 해당 Commit만 되돌림. 변경 내용은 git log에 history 보존됨.
```
git log --pretty=format:"%h %s" --graph
git revert <<commit id>>
git log --pretty=format:"%h %s" --graph
```

## stash
* 아직 마무리하지 않은 작업을 스택에 잠시 저장할 수 있도록 하는 명령
* 아직 완료하지 않은 일을 commit하지 않고 나중에 다시 꺼내와 마무리 가능
```
touch x
git add x
git stash
touch y
git add -A
git status # y파일만 staging됨
git commit
git stash list
git stash apply stash@{0} # git stash list에서 stash@{0}을 찾음
```

## status
```
touch a.txt
git status
```


## submodule
* 하위 레포지터리를 추가할 수 있다.
* [Git submodule 사용하기](https://pinedance.github.io/blog/2019/05/28/Git-Submodule)
* Example
```
# 추가하기
git submodule add https://github.com/big-data-europe/docker-hive docker-hive

# 파일 가져오기
git submodule update

# 삭제하기
git rm --cached docker-hive

# Update
git submodule update --init --recursive --remote

```



## tag
* 커밋을 참조하기 쉽도록 알기 쉬운 이름을 붙이는 것
```
git tag                                    # 태그 목록 보기
git tag 태그명 [커밋 아이디]             # 태그 생성 (light weight tag)
git tag -a 태그명 -m 태그설명 [커밋아이디]# 태그 생성 (annotated tag)
git tag -d 삭제할태그명                 # 태그 삭제
git push --tags                            # 태그 원격 저장소로 업로드
git show 태그명
git tag 태그명
```






# SourceTree
## shortcut
### Navigation & Menus
|Action                          |Shortcut       |
|--------------------------------|---------------|
|File Status Screen              |cmd + 1        |
|Log Screen                      |cmd + 2        |
|Search Screen                   |cmd + 3        |
|Repo select window              |cmd + b        |
|New repo                        |cmd + n        |
|Command history                 |cmd + shift + w|
|Hide/show sidebar               |cmd + shift + k|
|Spelling and grammar            |cmd + shift + ;|
|Settings                        |cmd + ,        |
|Help                            |cmd + shift + /|

### Staging & Commit Operations
|Action                          |Shortcut       |
|--------------------------------|---------------|
|Commit All... Screen            |cmd + shift + c|
|Commit options                  |cmd + shift + o|
|Reset Selected File             |cmd + shift + r|
|Diff                            |cmd + d        |
|Remove Selected File            |cmd + delete   |
|Search                          |cmd + shift + h|
|Refresh                         |cmd + r        |
|Find                            |cmd + f        |
### Branch Operations
|Action                          |Shortcut       |
|--------------------------------|---------------|
|Stash                           |cmd + shift + s|
|Add Tag                         |cmd + shift + t|
|Branch                          |cmd + shift + b|
|Merge                           |cmd + shift + m|

### Repository Operations
|Action                          |Shortcut       |
|--------------------------------|---------------|
|Fetch                           |cmd + shift + f|
|Pull from repository            |cmd + shift + l|
|Remotes                         |cmd + shift + ,|
|Open Working Copy               |cmd + o        |

## Window (Normal Mac Shortcuts)
|Action                          |Shortcut|
|--------------------------------|--------|
|Quit                            |cmd + q |
|Close window                    |cmd + w |
|Hide                            |cmd + h |
|Minimise                        |cmd + m |

# Tip
* gitk : git의 내장 GUI
* git config color.ui true : 콘솔에서 git output을 컬러로 출력하기
* git config format.pretty oneline : 이력(log)에서 확정본 1개를 딱 한 줄로만 표시하기
* git add -i : 파일을 추가할 때 대화식으로 추가하기


## OSX .gitignore
```
# General
*/.*

# for macOS
.DS_Store
.AppleDouble
.LSOverride
## Icon must end with  \r
Icon?

# Thumbnails
._*

# Files that might appear in the root of a volume
.DocumentRevisions-V100
.fseventsd
.Spotlight-V100
.TemporaryItems
.Trashes
.VolumeIcon.icns

# Directories potentially created on remote AFP share
.AppleDB
.AppleDesktop
Network Trash Folder
Temporary Items
.apdisk

# for Python and Jupyter
__pycache__
*/*.pyc
## Jupyter
.Trash-0
**/.ipynb_checkpoints
**/.ipynb_checkpoints/*.ipynb

```
