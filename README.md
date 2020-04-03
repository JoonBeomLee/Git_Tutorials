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