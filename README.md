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
> Branch(브랜치)란 독립적으로 어떤 작업을 진행하기 위한 개념이다. 필요에 의해 만들어지는 각각의 브랜치는 다른   
> 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행할 수 있다. 
> ![image](https://www.google.com/url?sa=i&url=https%3A%2F%2Fhackernoon.com%2Fgit-does-not-have-branches-add468b5b4a0&psig=AOvVaw26aoTV9B5ELP8eDdCBujUL&ust=1593069886850000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCIi3qPn1meoCFQAAAAAdAAAAABAe)

## Branch 종류