## GIT



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



## 포크해온 원본이 업데이트 됐을 경우에?

```
포크해오는 순간 내가 마스터, origin이 되어서 local에서는 
진짜 원본을 확인할 수 없게 된다

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