# Git Tutorials
   
## 정의 
> 깃(Git)은 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율 하기 위한   
> 분산 버전 관리 시스템이다. 소프트웨어 개발에서 소스 코드 관리에 주로 사용되지만 어떠한 집합의 파일의 변경   
> 사항을 지속적으로 추적하기 위해 사용될 수 있다. [위키백과](https://ko.wikipedia.org/wiki/%EA%B9%83_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4))

## Git 사용 이유
> Git의 사용 이유는 정의부분에서도 언급 했듯이 여러 명의 작업결과를 효율적으로 관리하는데에 있다.   
> ![image](https://backlog.com/git-tutorial/kr/img/post/intro/capture_intro1_1_2.png)    
> 그림에서 볼 수 있듯이 2명이상의 파일접근자가 수정을 했을 때 Git은 파일의 버전관리를 통해 최신상태의 유지를 돕는다.   

## Branch??
> Git이 기본적으로 파일의 최신상태의 유지를 지원하는 것을 확인했다. 그렇다면 하나의 파일을 기반으로   
> 2개 이상의 작업물로 별개로 관리하고자 할 때는 어떻게 해야 되나.   
> 이를 위한 Git에서는 Branch기능을 제공한다.   
> Branch(브랜치)란 독립적으로 어떤 작업을 진행하기 위한 개념이다.  
> 필요에 의해 만들어지는 각각의 브랜치는 다른   
> 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행할 수 있다.   
> ![image](https://hackernoon.com/hn-images/1*aChmZqHLVJM5UXGkZmL8aA.png)   
> 다양한 Branch를 생성해 개별 작업을 진행하다가 다시 Master Branch에 합병을 통해   
> 통합 관리를 할 수도 있다. 그렇다면 통상적으로 Branch를 어떻게 구성하는지 알아보자.   

## Branch 종류
> [참조](http://nvie.com/posts/a-successful-git-branching-model/)
- <strong>master</strong> 
> 'master' 기본적으로 생성되는 브랜치로 배포 가능한 상태만을 관리한다.  
   
- <strong>develop</strong>
> 개발버전의 소스가 있는 branch이다. 모든 기능이 정상적으로 동작할 수 있는   
> 안정적인 상태를 유지해야 하며 모든 기능이 추가되고 안정화가 마무리되어 배포가능   
> 상태라면 'master'에 merge한다.   
> 다음 Release될 버전의 소스라고 생각하면 된다.  
> <img src="http://nvie.com/img/main-branches@2x.png" width="300" height="400">  

- <strong>Feature</strong>
> 'develop'에서 분기하며 새로운 기능 개발 및 버그 수정이 필요할 때마다 분기되어 생성된다.   
> 목적(개발 및 버그 수정)이 마무리되면 다시 'develop'으로 merge하여 작업물을 공유한다.   
> <img src="http://nvie.com/img/fb@2x.png" width="150" height="300" >   
> 사용 목적이 끝난 'feture'는 'develop'으로의 merge시 삭제한다.   
> <img src="http://nvie.com/img/merge-without-ff@2x.png" width="400" height="400">   
> merge시 사용되는 --no-ff 명령어는 따로 존재했던 커밋이력을 하나로 통합하는 명령어이다.   
> 자세한 내용은 추후 다시 알아보자.   
   
- <strong>Release</strong>
> 'develop'에서 분기되며 'develop' 과 'master'로 merge된다.   
> 'release'의 이름은 관례적으로 'RB_'의 접두어를 붙인다.   
> Release를 위한 최종 버그 수정등의 작업을 관리하며 작업이 종료되면 'master'로 병합한다.   
   
- <strong>Hotfix branch</strong>
> 'master'에서 분기되며 'develop' 과 'master'로 merge된다.   
> 배포한 버전에 긴급하게 수정이 필요할때 'master'에서 분기한다.   
> 예시 상황으로 'develop'에서 개발 진행중 배포한 소스코드에서 큰 버그가 발견될 경우 빠르게   
> 수정후 재배포를 해야하는데 'develop'에서 문제부분을 수정하여 배포가능 버전을 만들기에는   
> 시간이 많이 소요되고 안정성 보장도 어려우므로 바로 배포 가능한 'master'에서 직접 분기하여   
> 필요부분만 수정후 merge를 한다.   
> <img src="http://nvie.com/img/hotfix-branches@2x.png" width="400" hegiht="450">

- <strong>전체 branch</strong>
> <img src="http://nvie.com/img/git-model@2x.png" width="550" height="600">
   
## branch 생성, 삭제, 확인
> ```
> git branch new_branch orig_branch         # git branch로 생성 
> # new_branch에는 생성할 branch명
> # orig_branch에는 분기할 branch명
>   
> git branch -D del_branch                  # git branch에서 '-D' 옵션 추가
> # del_branch에는 삭제할 branch명
>    
> git branch -m oriName_branch chnName_branch   # git branch에서 '-m' 옵션 추가
> # oriName_branch -> chnName_branch로 이름 변경 
>   
> git checkout target_branch                # checkout 명령어 사용
> # 현재 branch에서 target_branch로 이동
>   
> git checkout -b new_branch                # checkout명령어에서 '-b' 옵션 추가
> # new_branch의 생성과 이동을 한번에
>   
> git branch                                # 현재 등록된 브랜치 확인
> git branch -v                             # 자세한 정보 확인
>   
> git branch --merged | --no-merged         # '--merged' | '--no-merged' 옵션 사용
> # 현재 checkout한 브랜치를 기준으로 merge된 브랜치인지 확인       (안된 브랜치 *로 표시)
> # 현재 checkout한 브랜치를 기준으로 no-merge된 브랜치인지 확인
>   
> # Merge하지 않은 커밋을 담고있는 브랜치는 git branch -d 명령어로 삭제되지 않는다.
> # 강제로 삭제하려면
> git branch -D 옵션을 사용
> ```

## Merge (병합)
> Merge를 진행할때 크게 2가지의 경우가 있다. fast-forward / merge commit   
> 먼저 fast-forward를 알아보자.   
> <img src="https://git-scm.com/book/en/v2/images/basic-branching-1.png" width="60%" height="50%">   
> 정상적인 master branch      
> <img src="https://git-scm.com/book/en/v2/images/basic-branching-2.png" width="60%" height="50%">   
> iss가 발생해 이를 해결하고자 'iss53'branch를 생성한다.   
> <img src="https://git-scm.com/book/en/v2/images/basic-branching-3.png" width="60%" height="50%">   
> commit 3 인 'C3'을 통해 문제를 해결   
> <img src="https://git-scm.com/book/en/v2/images/basic-branching-4.png" width="60%" height="50%">   
> 그 때 갑작스런 hotfix가 발생해 master에서 새롭게 분기되어 새로운 commit 4인 'C4'가 생성    
> <img src="https://git-scm.com/book/en/v2/images/basic-branching-5.png" width="60%" height="50%">   
> 문제를 해결한 'hotfix'는 'master'로 다시 병합하는데 병합시점에서 **마스터가 새로운 커밋을 생성하지 않았을 때**,  
> 마스터가 가르키고 있는 'C2'에서 'C4'로 'fast-forward'(빨리감기)한다. (C4는 C2에서 기반하였기에 이동만 한다.)   
> 따라서 별도의 Commit을 생성하여 병합하는 것이 아니라, master가 가르키는 브랜치 포인터만 변경하여 merge를 한다.   
> <img src="https://git-scm.com/book/en/v2/images/basic-branching-6.png" width="60%" height="50%">   
> C5를 추가로 문제가 해결된 'iss'은 다시 'master'로 merge해야 한다.   
> <img src="https://git-scm.com/book/en/v2/images/basic-merging-1.png" width="60%" height="50%">   
> 그러나 앞선 'hotfix'때와는 달리 'iss'가 생성된 시점에서 추가적인 Commit이 생겨 merge대상과의 브랜치 포인터가   
> 다르기 때문에 문제가 발생한다.   
> <img src="https://git-scm.com/book/en/v2/images/basic-merging-2.png" width="60%" height="50%">    
> 이를 해결하기 위해 merge전 공통의 조상(C2)을 찾는다. 이후 '3-way-merge'(공통C2, merge대상(C4), 작업브랜치(C5)가 상호작용하는)의   
> 방식으로 작업물을 합치고, 합쳐진 결과를 새로운 커밋으로 생성후 브랜치 포인터가 가리키도록 한다.   
> 참고링크  **[3-way-merge](https://opentutorials.org/module/2676/15307)**   

## README.md 작성방법
> github repository에는 해당 프로젝트를 소개하는 README.md 파일이 있다.   
> 여기서 확장자는 .md 파일로 markdown을 의미하는데 HTML과 유사한 속성을 가지고 있으며   
> 문법과 관리가 쉬운 장점을 가지고 있어 문서 작성에서 사용되고 있다.   
> 다양한 문법과 사용법이 있는 md파일에 대한 자주사용되는 작성법을 알아보자.   
>   
>   
## 제목 (Header)   
> ```<h1>``` ~ ```<h6>``` 까지 제목을 표현할 수 있다.   
> # 제목 1
> ## 제목 2
> ### 제목 3
> #### 제목 4
> ##### 제목 5
> ###### 제목 6
>    
> ```
> # 제목 1
> ## 제목 2
> ### 제목 3
> #### 제목 4
> ##### 제목 5
> ###### 제목 6
> ```
   
## 강조 (Emphasis)
> 원하는 부분을 강조하고 싶을때 사용.   
> <태그>대상<태그>형식으로 사용된다.   
>   
> *이텔릭체* : ```*별표 한개(asterisks)* 또는 _언더바(underscore)_```   
> **두껍게** : ```**별표 두개(asterisks)** 혹은 __언더바(underscore)__```   
> ~~취소선~~ : ```~~물결표시(tilde)~~```   
> <u>밑줄</u> : ```<u>밑줄</u>```   
   
## 목록 (List)
> 1. 번호 있는 목록 1 (`1.`로 작성하지만 위에서 순서대로 값이 지정된다.)   
> 1. 번호 있는 목록 2   
>   - 번호 없는 목록(서브)    
>   - 번호 없는 목록(서브)    
> 1. 번호 있는 목록 3
>   1. 번호 있는 목록 (서브) 1  (들여쓰기 이후 번호는 다시 카운트가 된다.)   
>   1. 번호 있는 목록 (서브) 2   
> 1. 번호 있는 목록 4
> 
> - 번호 없는 목록   (기호마다 다른 표시)   
>   - 대쉬(hyphen)   
>   * 별표(asterisks)  
>   + 더하기(plus sign)   
> ```
> 1. 번호 있는 목록 1 (`1.`로 작성하지만 위에서 순서대로 값이 지정된다.)   
> 1. 번호 있는 목록 2   
>   - 번호 없는 목록(서브)    
>   - 번호 없는 목록(서브)    
> 1. 번호 있는 목록 3
>   1. 번호 있는 목록 (서브) 1  (들여쓰기 이후 번호는 다시 카운트가 된다.)   
>   1. 번호 있는 목록 (서브) 2   
> 1. 번호 있는 목록 4
> 
> - 번호 없는 목록   (기호마다 다른 표시)   
>   - 대쉬(hyphen)   
>   * 별표(asterisks)  
>   + 더하기(plus sign)   
> ```
   
## 링크 (Links)
> 작성한 페이지로 이동할 수 있는 링크를 제공 HTML의 a태그와 같은 역할을 한다.   
> [Google](https://google.com)   
> [Google2](https://google.com "마우스 hover시 띄울 내용을 작성할 수 있다.")   
> [상대적 참조 -> ./src](./src) 현재 페이지 기준으로 경로를 지정 이동할 수 있다.   
>   
> 문서내에서 위와 같은 문법없이 링크 그대로 사용할 수도 있다.   
> 구글 : https://google.com   
> 네이버 : <https://naver.com>  꺽쇠로 구분하여 가독성을 높일수 있다.   
>   
> ```
> 작성한 페이지로 이동할 수 있는 링크를 제공 HTML의 a태그와 같은 역할을 한다.   
> [Google](https://google.com)   
> [Google2](https://google.com "마우스 hover시 띄울 내용을 작성할 수 있다.")   
> [상대적 참조](./src) 현재 페이지 기준으로 경로를 지정 이동할 수 있다.   
>   
> 문서내에서 위와 같은 문법없이 링크 그대로 사용할 수도 있다.   
> 구글 : https://google.com   
> 네이버 : <https://naver.com>  꺽쇠로 구분하여 가독성을 높일수 있다.   
> ```
   
## 이미지 (Images) 
> 이미지 주소를 통한 출력할 수 있다.   
> 주소를 사용하기 때문에 링크 (Links)의 표현과 비슷하다.   
> 차이점을 두기 위해 이미지 (Images) 앞에는 !를 붙인다.   
>   
> ![링크에 문제시 띄울 alt 문구 입력 가능](https://cdn.pixabay.com/photo/2015/03/12/04/43/landscape-669619_960_720.jpg "링크와 같이 마우스 hover시 띄울 내용 작성가능")
>   
> ```
> ![링크에 문제시 띄울 alt 문구 입력 가능](https://cdn.pixabay.com/photo/2015/03/12/04/43/landscape-669619_960_720.jpg "링크와 같이 마우스 hover시 띄울 내용 작성가능")
> ```
   
## 이미지 링크
> 출력한 이미지에 링크의 역할을 추가할 수 있다.   
> 이미지 클릭시 링크에 정의된 위치로 이동가능하다.   
> 이미지 코드를 링크 코드 작성법에 묶어서 사용.   
> [![Python](https://www.python.org/static/community_logos/python-logo-master-v3-TM.png)](https://www.python.org/)   
>   
> ```
> [![Python](https://www.python.org/static/community_logos/python-logo-master-v3-TM.png)](https://www.python.org/)   
> ```

## 코드 (Code)
> \` 기호 3번이상 원하는 부분을 감싸면 코드출력 형식으로 전환된다.   
> \` 입력이후 코드의 종류작성시 문법에 맞게 가시성을 높여준다.   
>   
> ```html
> <button onclick="location.href='POP UP'">Click</button>
> ```
>   
> ```css
> h1 {
>   color: red;
> }
> ```
>   
> ```javascript
> function gitHub(){
>   console.log("This page Git Tutorial");
> }
> ```
>   
> ```bash
> cd ./
> ```
>   
> ```python
> for i in 5:
>   print(i)
> ```
>   
> ```
> code language종류 작성없이 사용가능.   
> 그러나 문법에 맞는 표시 또한 없다.   
> ```
>   
> ``````
> ```html
> <button onclick="location.href='POP UP'">Click</button>
> ```
>   
> ```css
> h1 {
>   color: red;
> }
> ```
>   
> ```javascript
> function gitHub(){
>   console.log("This page Git Tutorial");
> }
> ```
>   
> ```bash
> cd ./
> ```
>   
> ```python
> for i in 5:
>   print(i)
> ```
>   
> ```
> code language종류 작성없이 사용가능.   
> 그러나 문법에 맞는 표시 또한 없다.   
> ```
> ``````
    
## 인용문 (BlockQuote)
> 해당 주제에 대한 내용을 작성할 때 사용.   
> \> 기호의 개수로 들여쓰기의 개수가 달라짐.   
>   
> # 주제
>> ## 서브주제
>>> 내용 1
>>>> 내용 1-1
>   
> ```
> > # 주제
> >> ## 서브주제
> >>> 내용 1
> >>>> 내용 1-1
> ```
   
## 수평선 (Horizontal Rule)
> 각 기호를 3번 이상 입력하여 사용.   
> ---
> (Hyphens)
> 
> ***
> (Asterisks)
> 
> ___
> (Underscores)
>   
> ```
> ---
> (Hyphens)
> 
> ***
> (Asterisks)
> 
> ___
> (Underscores)
> ```