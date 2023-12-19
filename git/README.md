# Git

## git docs

#### Git Flow

Git flow 는 버전 관리 시스템 ( Version Control System, VCS) 의 한 종류인 git 을 통해 효율적으로 프로젝트를 관리하기 위함이다.

깃 설정

```bash
git config --global user.name "nickname"
git config --global user.email "email@example.com"
```

위처럼 계정 설정을 해준다.

#### Git Commit

git commit 에 대한 개념은 생략합니다.

* message git commit 메세지를 적을때 최대한 자세히 적어주면 좋습니다.

```bash
git commit -m "최대한 자세히 적으면 좋음"
```

> ( **TIP**!!!!) 만약에 간단하게 적어도 되겠다 싶을때 `git commit -am "message"` 를 사용하면, git add를 생략할 수 있습니다.

git commit 메세지 내용이 길 경우 vim 모드로 들어가서 적어주도록 합니다.

```bash
git commit

-> vi 모드로 들어간다.

최대한 자세히 적어주면 다음에 보는사람이 좋습니다.
커밋메세지가 본인이 생각할때 길 경우 vim 모드로 들어가서 적어주면
좀 더 상세히 적을 수 있습니다.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.

:wq -> vim 모드에서 저장하고 나간다
```

#### Git squash

커밋을 여러번 했을때 커밋을 하나로 합치면 커밋 히스토리를 깔끔하게 할 수 있습니다.

```bash
git rebase -i HEAD~3 # 만약 작업한 내용이 3개 일경우
pick 3a2c14 login modal html css
pick 14csaf login post axios
pick 5dfafc get token after login

# 밑에 처럼 변경해준다.

pick 3a2c14 login modal html css
s 14csaf login post axios
s 5dfafc get token after login

# :wq 로 저장하고 나간다. -> commit message 수정
```

#### Git rebase

rebase 를 해도 되고 안해도 되지만 rebase 를 하면 커밋메세지를 깔끔하게 정리 할 수 있습니다.

rebase 는 병합(merge) 와는 다릅니다.

rebase 는 브랜치의 base 를 옮겨 재정렬 하는겁니다.

만약 merge 했을경우

```bash
  dev          * ----- *                         * -----
                        \\                      /
  feature/login           ----- * ----- * -----
                               (x)     (y)
```

그리고 rebase 를 했을경우

```bash
(a)    (b)     (x)     (y)
 * ----- * ----- * ----- *
        (dev)           (feature/login)
```

깔끔해 지는 느낌이다.

feature 브랜치에서 작업을 하고 main 브랜치에 rebase 를 수행하면 feature 브랜치의 변경사항이 main 브랜치의 최신 커밋 이후에 적용됩니다.

```bash
git checkout feature/test
git rebase main # main 브랜치의 최신 커밋 위에 재배치 됩니다.
```

rebase 는 히스토리를 깔끔하게 해주지만 사용할때 주의를 해야한다.

커밋 히스토리가 변경이 되는데 다른 개발자들에게 혼란을 줄 수 있다.

#### Git fetch

git fetch는 원격 조장소의 최신 번경 사항을 로컬 저장소로 가져오는데 사용한다.

위는 git pull 와는 다르다. [https://stack-queue.tistory.com/5](https://stack-queue.tistory.com/5)

fetch 는 원격 저장소의 변경사항을 로컬로 가져오기만 하며, 현재 작업중인 브랜치에 자동으로 병합하지 않습니다.

git pull 은 git fetch 다음에 git merge 하는것과 같습니다.

그래서 git pull 를 사용하는것 보다 git fetch 를 하는것을 추천합니다.

git pull 하게 되면 충돌이 발생할수도 있습니다.

```bash
git fetch
# 원격 저장소의 최신 변경사항을 로컬 저장소로 가져온다.
# 변경사항을 현재 작업 중인 브랜치에는 적용하지 않습니다.

git status 
# 원격 브런치와 로컬 과이 차이를 확인
# git status 와 git diff 는 확인하는 습관 가지는게 좋습니다.
```

만약 git pull 를 했다면 ??

git fetch 처럼 a,b,c 커밋들이 로컬 저장소에 가져와집니다.

그후 현재 로컬 브랜치에 a,b,c 커밋들이 자동으로 병합됩니다.

로컬 현재 브랜치에 업데이트가 됐을때 충돌이 발생하지 않는다면 아주 나이스 하겠지만,

충돌이 발생한다면, 다시 일을 치뤄야합니다.
