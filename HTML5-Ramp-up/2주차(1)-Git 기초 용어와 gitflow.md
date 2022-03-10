## 2주차(1) - Git 기초 용어와 gitflow
### Git 기초 용어
Sourcetree는 git을 편리하게 사용하기 위한 GUI 도구입니다.
회색 칸 안의 예시는 git bash 기준 명령어입니다.
- <b>init(create)</b>: 새로운 깃 저장소를 만듭니다.
  - <pre>$ git init</pre>
- <b>clone</b>: 원격에 있는 깃 저장소를 다운로드하여 가져옵니다.
  - <pre>$ git clone [repo's url]</pre>
- <b>commit</b>: 현재 작업 상태를 저장하고 기록합니다.
  - <pre>$ git commit -m [commit message]</pre>
- <b>add</b>: 커밋할 특정 파일이나 폴더를 지정합니다.
  - <pre>$ git add [file name || folder name]</pre>
- <b>fetch</b>: 원격 저장소의 변경 내용을 다운로드합니다.
  - <pre>$ git fetch</pre>
- <b>pull</b>: 원격 저장소의 변경 내용을 다운로드하고 merge합니다.
  - <pre>$ git pull</pre>
- <b>push</b>: 현재까지의 커밋 목록을 원격 저장소에 보냅니다.
  - <pre>$ git push [branch name]</pre>
- <b>branch</b>: 같은 저장소 내에서 코드 작업 공간을 용도별로 분리한 것입니다.
  - <pre>$ git branch [branch name]</pre>
- <b>checkout</b>: 특정 브랜치로 작업 상태를 옮기고 싶을때 사용합니다.
  - <pre>$ git checkout [branch name]</pre>
- <b>stash</b>: 브랜치의 작업 내용을 커밋하지 않고, 임시로 저장해 둘 때 사용하는 기법입니다.
  - 커밋할 수 없는 작업 도중에, 다른 브랜치로 체크아웃 해야 할 때 사용합니다.
  - 또는 A브랜치에서 현재 작업 중인 내용을 A브랜치가 아닌, B브랜치에만 적용하고 싶을 때 사용합니다.
  - <pre>$ git stash</pre>
  - <pre>$ git stash list</pre>
  - <pre>$ git stash apply [stach name]</pre>
- <b>merge</b>: 서로 다른 두 개의 브랜치를 현재 브랜치로 합칩니다.
  - <pre>$ git merge [branch name]</pre>
