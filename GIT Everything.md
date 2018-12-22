## GIT



![git data transport commands](https://ws3.sinaimg.cn/large/006tNbRwgy1fvl2vagw7fj30l90hn0x6.jpg)



git pull (fetch + merge)

git --rebase (재조정) -> 커밋 순서대로?



ㅇ - ㅇ - ㅇ

​        | — ———ㅇ ㅇ- ㅇ- ㅇ- ㅇ-ㅇ 

리베이스는 중간 conflict를 하나 하나 하나 다 확인함



## GIT COMMIT 메세지 잘 작성하기

[훌륭한 링크](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/)

1. [제목과 본문을 빈 행으로 분리한다](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/#separate)
2. [제목 행을 50자로 제한한다](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/#limit-50)
3. [제목 행 첫 글자는 대문자로 쓴다](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/#capitalize)
4. [제목 행 끝에 마침표를 넣지 않는다](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/#end)
5. [제목 행에 명령문을 사용한다](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/#imperative)
6. [본문을 72자 단위로 개행한다](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/#wrap-72)
7. [어떻게 보다는 무엇과 왜를 설명한다](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/#why-not-how)



## GIT 명령어

Git 수정한 것 되돌리기 

http://hochulshin.com/git-revert-changes/



git stash pop?

## 포크해온 원본이 업데이트 됐을 경우에?

```
포크해오는 순간 내가 마스터, origin이 되어서 local에서는 진짜 원본을 확인할 수 없게 된다

자신이 포크해 온 데이터가 원본보다 오래되었을 경우에
git remote -v //현재 remote 확인
git remote add upstream codestates-url // remote 주소 추가
git pull upstream master // 업데이트 된 파일 갱신
(주의 백업 할 것, 기존 작업하던 파일 덮어씌워질 수 있음)



```



## GIT 블로깅 배우기

ekyll,Git-을-몰라도-무료-Github-Pages-즐기기

https://ilmol.com/2015/01/Jekyll,Git-%EC%9D%84-%EB%AA%B0%EB%9D%BC%EB%8F%84-%EB%AC%B4%EB%A3%8C-Github-Pages-%EC%A6%90%EA%B8%B0%EA%B8%B0.html



지킬 한글 버전

https://jekyllrb-ko.github.io/docs/posts/



지킬로 홈페이지/블로그 만들기 상세한 버전

http://lawfully.kr/smart/jekyll.html (훌륭)



기타 등등

http://tech.kakao.com/page/3/ 카카오 깃 블로그



## 에러와 해결

### [[GIT.Error\] ! [rejected] master -> master (fetch first)](http://dwenn.tistory.com/38)

git push origin +master

강제로 진행은 할 수 있지만, 기존 데이터는 보장 못 한다



- 

```javascript
** 에러 상황
git pull upstream master을 하지만 받아오지 못한다.

wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git pull upstream master
From https://github.com/codestates/im08-2018-09-data-structure
 * branch            master     -> FETCH_HEAD
error: Your local changes to the following files would be overwritten by merge:
	sprint-one/spec/specs-cli.js
	sprint-two/spec/setSpec.js
	sprint-two/src/hashTableHelpers.js
Please commit your changes or stash them before you merge.
Aborting

해결책 : git stash // 매우 위험. 주의해서 사용할 것.

// error full log


wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git pull upstream master
From https://github.com/codestates/im08-2018-09-data-structure
 * branch            master     -> FETCH_HEAD
error: Your local changes to the following files would be overwritten by merge:
	sprint-one/spec/specs-cli.js
	sprint-two/spec/setSpec.js
	sprint-two/src/hashTableHelpers.js
Please commit your changes or stash them before you merge.
Aborting
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git remote -v
origin	https://github.com/lastrites2018/im08-2018-09-data-structure.git (fetch)
origin	https://github.com/lastrites2018/im08-2018-09-data-structure.git (push)
upstream	https://github.com/codestates/im08-2018-09-data-structure (fetch)
upstream	https://github.com/codestates/im08-2018-09-data-structure (push)
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ code .
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git pull upstream master
From https://github.com/codestates/im08-2018-09-data-structure
 * branch            master     -> FETCH_HEAD
error: Your local changes to the following files would be overwritten by merge:
	sprint-one/spec/specs-cli.js
	sprint-two/spec/setSpec.js
	sprint-two/src/hashTableHelpers.js
Please commit your changes or stash them before you merge.
Aborting

wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git stash
Saved working directory and index state WIP on master: 7cdd462 fix eslint error

wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git pull upstream master
From https://github.com/codestates/im08-2018-09-data-structure
 * branch            master     -> FETCH_HEAD
Auto-merging sprint-two/src/set.js
CONFLICT (content): Merge conflict in sprint-two/src/set.js
Auto-merging package.json
CONFLICT (content): Merge conflict in package.json
Automatic merge failed; fix conflicts and then commit the result.
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ oepn .
-bash: oepn: command not found
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ open .
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ ls
lib			node_modules		package-lock.json	package.json		sprint-one		sprint-two
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git status
On branch master
Your branch is up to date with 'origin/master'.

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:

	modified:   lib/underscore/underscore.js
	modified:   sprint-one/spec/specs-cli.js
	modified:   sprint-two/spec/setSpec.js
	modified:   sprint-two/src/hashTableHelpers.js

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   package.json
	both modified:   sprint-two/src/set.js

wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git pull upstream master
error: Pulling is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git add .
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git status
On branch master
Your branch is up to date with 'origin/master'.

All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:

	modified:   lib/underscore/underscore.js
	modified:   package.json
	modified:   sprint-one/spec/specs-cli.js
	modified:   sprint-two/spec/setSpec.js
	modified:   sprint-two/src/hashTableHelpers.js
	modified:   sprint-two/src/set.js

wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git commit -m 'fix merge error'
husky > npm run -s precommit (node v10.10.0)

 ✔ Running tasks for *.js
[master 8b82932] fix merge error
wanprobookui-MacBook-Pro:im08-2018-09-data-structure wanprobook$ git push origin master
Counting objects: 30, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (29/29), done.
Writing objects: 100% (30/30), 3.24 KiB | 1.62 MiB/s, done.
Total 30 (delta 22), reused 0 (delta 0)
remote: Resolving deltas: 100% (22/22), completed with 13 local objects.
To https://github.com/lastrites2018/im08-2018-09-data-structure.git
```



## deskotop까지 git master 설정했을때?

`rm -rf .git`



# git 단축키 만들기

https://gist.github.com/EQuimper/d875df92ef0ddaabf00636c90dbc9d25

```shell
# git po = git push origin master
git config --global alias.po 'push origin'
git config --global alias.pom 'push origin master'
git config --global alias.pum 'pull upstream master'

git config --global alias.up 'pull origin master'

git config --global alias.co checkout
git config --global alias.cob 'checkout -b'
git config --global alias.com 'checkout master'

git config --global alias.cm 'commit -m'
git config --global alias.ci commit

git config --global alias.a add
git config --global alias.b branch
git config --global alias.d diff
git config --global alias.s status 

git status는 추가하실 필요 없어요. git s라고 치시면 사용할 수 있습니다.
라고 생각했는데 써야 하는 경우도 있음...

git config --global alias.rbm 'git rebase master'


git config --global alias.abracadabra 'push origin master'
git config --global alias.vision 'status -s'
git config --global alias.qwertyuiop 'branch'

# 만든 전역 alias 보기
git config --global --get-regexp alias

# 전역 alias 삭제
$ git config --global --unset alias.d // 방금 위에서 만들었던 alias.d를 삭제할 수 있습니다.




# 지역 Alias 삭제
$ git config --unset alias.ci

//전역 및 지역 Alias 목록 보기
$ git config --get-regexp alias	

```



## [Git]Alias 추가 / 삭제 / 목록 보기

http://minsone.github.io/git/recommend-git-alias



## git ignore 재설정

```
1) 전체 cache를 다 지우고 다시 cache 하는 방법은 무식하지만, 간단하다. 만약, 파일이 많지 않다면 try.

– git rm -r –cached . => 현재 repository의 cache를 삭제

– git add . => 다시 tracking하도록 설정

– git commit -m “Updated .gitignore”
```



 <https://github.com/github/gitignore> gitignore example

https://josephkim75.wordpress.com/2012/06/13/git%EC%97%90%EC%84%9C-gitignore-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0/



## git에서 특정 브랜치만 clone하는 방법

git을 사용하다 브랜치 전체를 clone하지 않고 특정 브랜치 하나만 clone하는 것이 가능하다. 
특히 브랜치가 많은 경우 이 방법을 사용할 수 있다.

```
git clone -b {branch_name} --single-branch {저장소 URL}
ex) git clone -b javajigi --single-branch https://github.com/javajigi/java-racingcar
```

위와 같이 실행하면 java-racingcar의 javajigi branch만 clone할 수 있다.