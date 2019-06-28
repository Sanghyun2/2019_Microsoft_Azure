# AZ-203 Training (2019.06.28)

서울창업허브 세미나실3, 백범로 31길 21, 서울창업허브, 마포구, 서울특별시

한국무역협회와 MS Korea 주최

주제 : **AZ-203(Developing Solutions for Microsoft Azure) Exam Objectivees**

> 강의자료 : [AZ-203-DevelopingSolutionsforMicrosoftAzure](https://github.com/MicrosoftLearning/AZ-203-DevelopingSolutionsforMicrosoftAzure)

## 내용정리
1. Git
    - add
    - commit
    - push
    - pull(fetch)
    - lint(githook) → Code review
    - 코딩 규약에 맞지 않으면 Git에 올릴 수 없음
    - 저장물을 안전하게 저장할 필요가 있음
    - GitLab
2. Azure Devops
    - [Azure DevOps](https://dev.azure.com)
    - Public 으로 project 생성시 무료 & 사용자 제한 없음
    - Private 으로 project 생성시 최대 5명까지 무료 / 사용자가 늘면 추가비용 발생
    - Pipeline

## 오전수업

- 예제 설명
    'MarkDown 파일을 작성, Html로 퍼블리싱하는 예제'를 Azure DevOps Pipeline을 통해 자동화
- Senario 요약
    1. Git-Bash RSA 키 발급
    2. Github 에서 특정 프로젝트 Fork
    3. Azure DevOps ID + 프로젝트 생성
    4. Github 과 Azure DevOps 연동
    5. Github 의 Commit시, Azure DevOps Pipeline을 통해 프로젝트를 자동으로 빌드
    6. 빌드 이후 Github으로 자동으로 Push
    7. Github 의 Commit을 통해, Azure DevOps Board에서 Task Auto Complete 처리
- 새로운 SSH keyfile 생성 → 'private key' 를 가진 사람만 수정이 가능
    
    `$ ssh-keygen -t rsa -f devopskeyfile`

> 실습사이트 : [kr-devops/devopskr → wiki](https://dev.azure.com/kr-devops/devopskr/)

## 오후수업

- GitHub 잘 활용하는 방법 생각해보기
- [AZ-203_06_lab.md 실습](https://github.com/Sanghyun2/AZ-203-DevelopingSolutionsforMicrosoftAzure/blob/master/Instructions/Labs/AZ-203_06_lab.md)
- 실패한 이유 : `Azure Storage Explorer 계정연동 안되서 실패`
> 실습사이트 : [kr-devops/devopskr → wiki](https://dev.azure.com/kr-devops/devopskr/)

- - -
#### 더 알아보기
1. 응집도와 결합도?
2. ZEPL 이란?
3. 배포의 의미는?
4. Azure DevOps Release 기능 사용해보기
