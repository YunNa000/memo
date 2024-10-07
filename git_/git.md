Git 명령어 정리

1. Branch 생성
    # 방법 1
    - git pull origin main
    - git branch 브랜치이름
        - [develop]
        - [feature/기능요약]
    - git checkout 브랜치이름
    - git merge main
        - main 브랜치의 최신 커밋을 기준으로 받아오기

    # 방법 2
    - git pull origin main
    - git checkout -b 새브랜치이름
        - main 브랜치의 최신 커밋을 기준으로 새브랜치 생성 + 전환

2. Branch 삭제
    # 로컬 브랜치
    - git branch -d 브랜치이름
    - git branch -D 브랜치이름
        - 만약, 해당 브랜치에 아직 병합되지 않는 변경사항이 있어 강제 삭제인 경우
    # 원격 브랜치
    - git push origin --delete 브랜치이름

3. Branch 확인
    # 로컬인지
    - git branch
    # 원격인지
    - git branch -r
    # 로컬인지 원격인지 모두 확인
    - git branch -a

4. git local과 origin 원격 연결
    먼저 local branch 를 생성하고 이를 원격에 올리고 싶으면 다음과 같은 명령어를 사용하여 연결시킬 수 있다

    - git push --set-upstream origin <로컬-브랜치-이름> 
    

git add

git commit

작업폴더 -> git add -> staging area -> git commit -> repo

git add 파일명1 파일명2 git add .

git status

git restore --staged 파일명1 파일명2 git restore --staged . add한 모든 파일이 회수됨

git commit -m "메세지"

git log --all 모든 내용을 형식폼에 맞춰서 작성 git log --oneline 한줄로 작성, 작성자, 언제 했는지 등 git log --all --oneline (순서상관없음)

git log --all --oneline --graph 그래프 그려주지만 보잘것없음

commit 은 기능을 하나씩 추가할때마다 하기 (ctrl + s 누를때마다 하는것은 비추천) commit msg를 쓰기 좋게끔

git diff 현재 파일이 최근 commit 과 어떤 부분이 달라졌는지 알려줍니다. 엔터키나 스페이스바 변동사항도 다 알려주기 때문에 잘 사용하지 않음

git diff 커밋id 최근 commit 과 비교하는 것이 아닌 과거의 특정 commit 과 현재 파일을 비교하고 싶으면 커밋 id명시 커밋 id 는 git log --oneline에 보이는 노란 글자들

git diff 커밋id1 커밋id2

*seo

-> git difftool 이용해보기 git difftool

git difftool 커밋id git difftool 커밋id1 커밋id2

VIM 에디터 hjkl 키로 이도가능 :q 여러번 입력해야지 나갈수잇음, 아니면 :qa 입력하셈
git commit 커밋 : 새로운 기능 추가를 위한 것임 -> 이를 안전학 하고싶다? branch를 만들어라 branch 프로젝트 복사본 : 가장 최근 commit 으로부터 복사

git branch 브랜치이름

git switch 브랜치이름

branch에서 짰던 코드가 맘에 들면 원본코드의 main에 합치기 merge하는 방법

main 브랜치로 다시 이동
git merge 브랜치명 입력
conflict 났을때 <<<< / >>>> / ==== 이런 쓸데없는 것들은 다 지우고 원하는 코드만 남기면 됩니다.
(VSCode 에디터의 경우 Accept Incoming Change 어쩌구 버튼들을 제공해주는데 그거 누르면 편리합니다)

어떤 코드를 남길지 결정했으면

git add 파일명

git commit -m '메세지'

입력하면 새로운 commit 을 생성해주며 merge conflict 해결 + 브랜치 합치기 완료

merge 방법

3-way merge [기본] 새로운 브랜치와 기존 브랜치에 신규 commit 이 1회 이상 있는 경우

fast-forward merge 새로운 브랜치에만 commit이 있고 기준이 되는 브랜치에는 신규commit 이 없는 경우

-> 신규브랜치보고 main 브랜치라고 하는 것

이렇게 하나로 코스따기 싫으면 git merge --no-ff 브랜치명 강제로 3-way merge

브랜치를 삭제하려면
git branch -d 브랜치이름 git branch -D 브랜치이름

commit 이 된 상태에서는 delete 소문자 대문자 상관없지만 commit 이 되지 않은 상태에서는 -D 를 해야 강제로 삭제 가능 -> 위의 경우에는 잔가지들이 다 삭제되는 것임 최근것만 삭제되는게 아니라

delete는 진로 설정을 해주는 것이지 branch 삭제 개념이 아님(이전 로그나 복구를 해야할 가능성이 있기 때문)

** rebase 브랜치의 시작점을 다른 commit으로 옮겨주는 행위입니다

왜?)

3-way merge 말고 강제로 fast-forward merge하고 싶을때 2 개인 취향의 이유
rebase를 이용해서 신규브랜치이ㅡ 시작점을 main브랜치 최근 commit 으로 옮긴다음 fast-forward merge 하는 것

그래서 실제로 rebase and merge(=강제 fast-forward merge) 하고 싶으면

새로운 브랜치 이동
git rebase main 하면됨
그럼 브랜치가 main 브랜치 끝으로 이동하는데 그걸 FFM 하기
** Squash and merge

수많은 브랜치가 3-way merge되어있으면ㄴ (사용자 편의) 나중에 참사

-> 매우 복잡하고 commit 내역이 다 같이 출력되어 더러워짐

rebase
squash and merge
가장 최근 커밋은 (이전의 수정 커밋의 내용을 포함) 따라서 최근 커밋을 똑 떼와서 기존 브랜치에 붙여넣어줌

git merge --squash 브랜치명 브랜치명 .. 이후 commit

rebase vs squash 다른 브랜치에서 커밋 생성 개수에따라 사용 할수잇을거같음

코드 짜다가 실수했따 되돌아가자 (git revert ,reset, restore)

파일 복구

git restore 파일 하나를 되돌리려면, 주체가 파일
git restore 파일명 이러면 최근 commit 된 상태로 현재 파일의 수정내역을 되돌릴수잇음

git restore --source 커밋아이디 파일명 특정 커밋아이디 시점으로 복구

git store --staged 파일명 staging 취소

git revert 커밋을 되돌리려면, (한 커밋에 여러 파일이 변경될 가능성 있음) 주체가 커밋
git revert 커밋아이디 커밋아이디에서 일어난 일만 취솔

ㅎㅎ revert 금지

** git reset 해당 커밋이 생성될때로 시간을 되돌려줌

git reset --hard 커밋아이디

reset 옵션 설정가능

git reset --soft 해당 파일 staging area에 남겨짐 커밋은 지우고 add 한 상태로 바꿔준다 따라서 커밋할수잇음

git reset --hard 해당 파일 삭제

git reset --mixed (reset 옵션 설정안하면 디폴트) 커밋도 지우고 add 도 지우고 따라서 add 하고 커밋할 수 있음 ctrl + s 만 한 상태

-> 결론은 reset 하면서 파일을 아예지워버리는게 아니라 검토하고 다시 commit 하고 싶으면 soft, mixed 사용가능

원격저장소는 git에 올라와있는 repo(저장소)

로컬저장소는 작업폴더내에 있는 git init이라는 파일

github,com은 기본 브랜치 이름을 master가 아니라 main으로 사용하라고 강요합니다. git branch -M main 으로 하면 기본 브랜치 이름 변경

로컬 저장소 -> 원격저장소 git push -u 원격저장소주소 main
로컬 저장소의 main 브랜치를 원격저장소에 올리라는 뜻 다른 브랜치도 올릴 수 있음 github 로그인해야할수도 있음

참고로 -u 옵션은 방금 입력한 주소를 기억해라 -> 다음부터는 주소를 길게 입력안하고 git push 만 해도 됨

원격저장소를 길게 입력하기 귀찮으면 git remote add 변수명 저장소주소 origin 이라는 변수명을써서 주소로 들어갈 수 잇음

origin upstream

** 원격저장소에 있던거 그대로 내려받기 git clone 원격저장소주소

** 저장소에 올리지 않는 파일들은 .gitignore

git pull : git fetch + git merge 축약어
git fetch는 원격저장소에 있는 commit 중에 로컬에 없는 신규 commit을 가져와라 git merge 는 그것을 merge하라

git push 원격저장소주소 로컬브랜치명

특정 로컬저장소브랜치에서 원격저장소로 가는것

git push 원격저장소주소 하면 모든 로컬저장소 브랜치 -> 원격저장소