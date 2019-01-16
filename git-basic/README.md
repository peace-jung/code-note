# Git 기초 정리

## Git ?

Git은 특정 시점에서의 파일들의 상태를 저장하고 관리할 수 있는 소프트웨어이다.

버전관리란?

- 파일의 변화를 시간에 따라 기록한다.
- 나중에 특정 시점의 버전을 다시 꺼내올 수 있다.
- 누가 문제를 일으켰는지 확인가능하고
- 언제 발생한 이슈인지 확인한다.
- 파일을 잃어버리거나 잘못된 부분을 쉽게 복구할 수 있다.

## 로컬 저장소

Git 은 저장소를 가진다.

로컬 저장소는 크게 세 부분으로 구분할 수 있다.

작업 디렉토리 -> 인덱스 -> HEAD

1. 작업 디렉토리에서 실제 파일들이 존재한다.
2. 작업 내용을 저장소에 등록하기 위해 준비 영역에 등록한다. (staging)
3. 최종 확정본(commit)을 HEAD 에 등록한다.

위와 같은 단계를 거쳐 작업을 진행한다.

1번에서 2번으로 가기위해 add 라는 명령어를 사용하며,
2번에서 3번으로 가기위해 commit 이라는 명령어를 사용한다.

여기까지는 모두 '로컬' 저장소에서 발생하는 일을 기록하는 것이며,
서버와 같은 '원격' 저장소에 등록하는 작업은 추가로 진행해야 한다.

## Git 환경설정

설치 확인

```
git --version
```

계정 설정

```
git config --global user.name '깃 이름'
git config --global user.email '깃 이메일 주소'
```

설정 확인

```
git config --list
```

## Git 저장소 만들기

기존 저장소 Clone

```
git clone <remote-url>
```

기존 디렉토리를 git 저장소로 만들기

```
mkdir <directory-name> // 새로운 디렉토리 생성ac
cd <directory-name> // 디렉토리 이동
git init // git 저장소 생성
git remote add origin <remote-url> // 연결할 원격 저장소 url
```

## 기본 명령어

```
// git 버전 확인
git --version

// 현재 디렉토리에 git 저장소 생성
git init

// 파일 상태 확인 - 커밋되지 않은 변경사항을 조회한다.
git status

//커밋에 추가하기 위해 상태를 staged 로 만들어준다.
git add -A // 전체 상태 변경
git add --all // 전체 상태 변경
git add <filename> // 특정 파일(폴더)만 상태 변경

git add -i // 파일을 추가할 때 대화식으로 추가한다.
git add -u // 이전에 커밋한 적이 있는 파일만 인덱스에 등록한다.

// 기존에 존재하는 파일을 새 파일로 이동 - 변경이력 유지
git mv [파일명] [새파일명]
```

## Commit

커밋은 파일이나 폴더의 변경사항을 저장소에 기록하는 것이다.
커밋은 작업의 분기점이 되므로 필히 거쳐야하는 단계이다.
add 를 통하여 staged 상태의 파일을 대상으로 변경사항을 저장소에 저장한다.

```
git commit -m "commit-message"
```

commit 이 만들어 질 때에는 40자리의 SHA-1 해시 값이 만들어 커밋에 저장된다.
이 커밋 해시는 고유한 값이기 때문에 하나의 커밋만을 가리키고 있다.

```
git log
```

commit history 를 확인하여 흐름을 파악할 수 있다.

```
git log --all --online --decorate --graph [-number] // 일부분만 출력하는 기능을 제공한다.
```

commit 간의 차이점 확인

```
git diff // 수정하고 인덱스 하지 않은 변경사항과 인덱스를 비교
git diff --cached // 커밋 대기 상태인 변경 사항과 저장소를 비교
git diff <commit>...<commit> // 커밋 간의 변경사항 비교
```

기존 커밋 수정

```
git commit -C HEAD -a --amend
```

## Branch

브랜치는 커밋 그래프 상의 경로이다.
안정되고 격리된 상태에서 무언가를 만들 때 사용하며, 격리된 저장소의 개념이다.
여러 개의 브랜치를 만들 수 있으며, 그만큼 다양한 경로(상태, 용도)를 만들 수 있다.

프로젝트 진행 시 안정되고 팀원 간 별도의 작업을 할 때 유용하게 사용한다.
기준이 되는 브랜치에서 팀원 별로 여러 브랜치를 만들어 각자 작업을 하다가
추후 변경사항을 반영할 때 merge 하여 브랜치들을 병합하여 하나의 완성본을 만든다.

기본 브랜치(default-branch)는 master이며 변경할 수 있다.

```
git branch <branch-name> // 브랜치 생성, 이동 안함

git branch -d || -D // -d 는 삭제, -D 는 강제 삭제

git checkout <branch-name> // 브랜치 이동
git checkout -b <branch-name> // 브랜치 생성 후 이동
git checkout -b <branchA> <branchB> // 브랜치A에서 브랜치B를 생성 후 이동

git checkout --<file> // 변경한 인덱스에 등록되지 않은 파일을 되돌린다.

git tag 태그명 브랜치명 // 브랜치의 현재 시점에 태그명으로 된 태그를 붙힌다.

git rebase <branchA> //브랜치A의 변경사항을 현재 브랜치에 적용

git merge <branceA> // 브랜치A를 현재 브랜치로 합침
```

커밋하지 않은 상태에서는 브랜치 이동이 불가하다.
브랜치가 병합되어 있지 않으면 -d 를 사용한 삭제가 제한된다.

## Stash

작업 중인 내용을 커밋하기 애매할 때 stash 를 사용하여 저장해두고, 다른 브랜치에서 작업 후 다시 복구하여 사용할 수 잇다.

```
git stash // 추적 중인 파일만 저장
git stash -u || -a // 추적 중이지 않은 파일까지 저장

git stash list // 저장 중인 목록 확인. 최근이 0번
git stash save <stash-name> // 이름을 지정하여 저장할 수도 있다.

git show stash@{number} // stash 번호(id) 또는 지정한 이름을 통하여 해당하는 자세한 내용을 확인할 수 있다.

git stash pop // 가장 최근의 stash 를 적용 후 삭제한다.
git stash apply [stash@{id}] // stash 를 반영 후 삭제하지 않는다. 번호 생략 시 가장 최근걸로...

git stash drop stash@{id} // 해당 stash 삭제
git stash clear // 모든 stash 삭제
```

## Merge

브랜치는 개발의 흐름을 나타낸다.
master(default) 를 제외한 모든 브랜치는 부모가 잇다.
다른(자식) 브랜치와 합쳐질 수 있는데 이를 병합(merge)라고 한다.

브랜치는 master로 부터 부모로부터 가지치기 하듯 나온 것이며, 추후 부모로 돌아갈 수 있다.

병합이 반영될 브랜치에서 아래 명령어를 사용하여 병합을 실행한다.

```
git merge <branch-name>
```

병합 시 두 브랜치에서 같은 파일을 수정하고 커밋 했을 시 충돌이 발생하는데,
개발자가 해당 부분을 수동으로 해결하여야 한다.

## commit 수정

커밋 순서변경, 메시지 및 파일 변경, 커밋 합치기 또는 분리, 커밋 삭제 등을 수행할 수 있다.

```
git commit --amend
```

편집기와 같은 형태로 작업을 할 수 있다.

## Reset

HEAD 는 현재 브랜치를 가리키며, 가장 마지막 커밋을 가리킨다.
reset 명령을 통하여 HEAD 이전 상태로 되돌린다.
reset mode 옵션이 있다.
reset 은 커밋이 이력에 남지 않는다.
커밋을 하기 전에 실행하는 명령어로 커밋 직전 인덱싱을 취소한다.

```
git reset HEAD --<file> // 인덱스에 등록한 파일을 취소한다.

git reset [--mixed] <commit-id> // 작업 디렉토리 유지 && 인덱스를 HEAD와 함께 되돌림

git reset --soft <commit-id> // 작업 디렉토리, 인덱스 유지 && 커밋만 취소

git reset --hard <commit-id> // 작업 내용을 버리고 되돌리기
```

파일 수정 후 인덱스에 추가하지 않은 생태에서 특정 파일의 작업 내역을 모두 삭제하고자 할 때는

```
git checkout <path/filename>
```

## Revert

reset 과 달리 취소에 대한 이력을 커밋으로 남길 수 있다.
또한 HEAD 부터가 아닌 중간에 있는 커밋이거나, 이미 원격 저장소에 반영된 커밋일 경우 사용한다.

```
git revert <commit-id> // 한 개의 커밋 적용

git revert <commit-id>^..<commit-id> // 적용 커밋 범위 지정

git revert -m 1 <merge commit-id> // merge 커밋을 되돌릴 경우. -m 1 옵션은 부모가 보호되어야 한다는 의미
```

## Cherry-pick

브랜치를 통째로 merge 하지 않고, 특정 커밋을 반영할 떄 사용한다.
cherry-pick 뒤에 입력하는 commit 의 변경사항을 현재 브랜치에 적용한다.

```
git cherry-pick <commit-id>
```

## Rebase

merge 를 통하여 브랜치를 병합할 수 있다.
merge 를 하면 브랜치 분기가 합쳐졌다는 이력을 남기지만, 병합할 브랜치의 이력을 모두 가져오지는 않는다.
이전 브랜치의 변경내용까지 가져오기 위해 rebase 를 사용한다.
rebase를 사용하면 기준이 되는 브랜치의 변경이력에 병합할 브랜치의 변경이력을 남길 수 있다.

커밋을 나누고 합치고 지우고 순서를 바꾸고...
대화형 스크립트를 사용하며 사용한다.

```
git rebase -i HEAD~<n> // HEAD 부터 n번째까지의 커밋을 의미
```

수차례 연습을 통해 이해하고 숙달시키도록 하자.

## Clean

관리대상이 아닌 파일을 정리할 수도 있다.

```
git clean [-n || -f || -x] // 관리 대상이 아닌 파일을 삭제한다.
// -n 옵션은 삭제되는 파일을 확인할 수 있다.
// -f 옵션은 실제로 파일을 삭제한다.
// 일반적으로 .gitignore 에 지정된 파일은 삭제하지 않지만
// -x 옵션을 붙이면 삭제할 수 있다.
```

## 원격 저장소

로컬 저장소의 브랜치를 원격 저장소로 업로드 한다.

```
git remote -v // 현재 연결된 저장소를 가리킨다.
git remote // 원격 저장소 목록 확인
git remote show <name> // 해당 원격 저장소 정보 확인
git remote show origin // 원격 저장소 상세 정보와 브랜드 정보들도 확인한다.
git remote rm <name> // 원격 저장소 제거

git clone <저장소주소> [폴더명] // 원격저장소를 복제하여 저장소를 생성한다.

git fetch // 원격 저장소의 변경사항을 가져와 갱신한다.

git pull // fetch 에서 가져온 변경 사항을 지역 브랜치에 합치는 작업을 한꺼번에 한다.

git push origin <bransh-name> // 특정 브랜치를 원격 저장소에 반영한다.
git push origin :<bransh-name> // 특정 브랜치를 원격 저장소에서 삭제한다.

git pull // 원격 저장소 브랜치로부터 데이터를 가져오고, 자동으로 로컬과 merge 해준다. fetch->merge
```

협업 시 원격 저장소의 브랜치에 뒤쳐져 push 시에 에러가 발생할 수 있다.
이 때 pull 을 실행 시 merge 커밋이 생성된다.

```
git pull --rebase // 원격 저장소의 최종 커밋을 바탕으로 rebase 한다.
```

이렇게 하고 push 를 실행하면 불필요한 merge 커밋을 생성하지 않고 히스토리를 관리할 수 있다.
