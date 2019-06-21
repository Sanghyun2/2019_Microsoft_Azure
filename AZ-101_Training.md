# AZ-101 Training (2019.06.20)

서울창업허브 세미나실3, 백범로 31길 21, 서울창업허브, 마포구, 서울특별시

한국무역협회와 MS Korea 주최

### 주제 : Azure App Service Platform

## az-101-02__instructions.md

Exercise 1: Implement Azure web apps

> **참고자료** : [https://github.com/MicrosoftLearning/AZ-101-MicrosoftAzureIntegrationandSecurity/blob/master/Instructions/az-101-02__instructions.md](https://github.com/MicrosoftLearning/AZ-101-MicrosoftAzureIntegrationandSecurity/blob/master/Instructions/az-101-02__instructions.md)

Git Clone Url : https://sangsang2-webapp1-staging.scm.azurewebsites.net:443/sangsang2-webapp1.git

## az-101-03__instructions.md

### Exercise 0: Deploy Azure VMs by using Azure Resource Manager templates

App Service Environments(ASE) 

Azure App Service
- 여러 언어 및 프레임 워크
- DevOps 최적화
- 고 가용성을 갖춘 글로벌 규모
- SaaS 플랫폼 및 사내 구축 형 데이터에 대한 연결
- 보안 및 준수
- 응용프로그램 템플릿
- Visual Studio 통합
- API 및 모바일 기능
- 서버리스 코드

App Service 에서 스테이징 환경

스테이징 환경의 기능

FTP로 배포하는 경우는 재부팅 해주어야 한다.

WebApp 관리하기
- Azure PowerShell
- Azure Command Line Interface
- REST API
- Azure Portal

App Service 보안 레벨
- Infrastructure and platform security + Application security

> **참고자료** : [https://github.com/MicrosoftLearning/AZ-101-MicrosoftAzureIntegrationandSecurity/blob/master/Instructions/az-101-03__instructions.md](https://github.com/MicrosoftLearning/AZ-101-MicrosoftAzureIntegrationandSecurity/blob/master/Instructions/az-101-03__instructions.md)

## Word Press 생성 실습

> **참고자료** : [https://github.com/krazure/workshop-itpro-101](https://github.com/krazure/workshop-itpro-101)

- - -

# AZ-101 Training (2019.06.21)

### ARM Template 를 이용한 배포
Azure CloudShell & ARM Template 이용해서 WordPress 배포

### Docker
도커(Docker)는 리눅스의 응용 프로그램들을 소프트웨어 컨테이너 안에 배치시키는 일을 자동화하는 오픈 소스 프로젝트

Docker 각광받는 이유
- Microservice 개발방법론의 한가지 방안
- Infra 에 종속되지 않고 어디서는 동일한 환경
- 운영체제 Kernel 을 공유
- OS 영역을 공유하기 때문에 배포 용량이 적음

Docker 는 Image 를 기반으로 리소스 공유
- Container : Image 를 실행시켰다고 볼 수 있음
- Image : 이미지는 컨테이너 실행에 필요한 파일과 설정값등을 포함하고 있는 것, 상태값을 가지지 않고 변하지 않음

Azure Kubernetes Service 구성하고 ACR에 있는 wordpress image를 이용하여 AKS에 wordpress를 배포하는 실습
***2.3_deploy_wordpress_on_AKS.md***
> **실패장소** : `$ kubectl create -f wordpress.yaml`
> - 나중에 해보기

Serverless Computing
- 서버리스 컴퓨팅은 서버, 인프라 및 운영 체제의 추상화
- 코드에 집중할 수 있도록 완벽하게 관리되는 서비스
- 응용 프로그램 코드가 실행되는 동안만 지불
- **누군가 대기하고 있지 않다는 것을 의미**

Serverless Application
- Compute : Azure Functions - 이벤트 중심의 컴퓨팅 경험
- Cloud Messaging : Event Grid, Service Bus

Azure Functions vs Logic Apps
- 코드 우선 (필수) vs 디자이너 우선 (선언적)

#### AZ 101 Module 3 - Implement Advanced Virtual Networking
- Exercise 1 : 완료
- Exercise 2 : 미완료
- 참고사이트 : [https://github.com/MicrosoftLearning/AZ-101-MicrosoftAzureIntegrationandSecurity/blob/master/Instructions/az-101-03__instructions.md](https://github.com/MicrosoftLearning/AZ-101-MicrosoftAzureIntegrationandSecurity/blob/master/Instructions/az-101-03__instructions.md)

- - -
> **출처** : [도커 - 위키백과](https://ko.wikipedia.org/wiki/%EB%8F%84%EC%BB%A4_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4))

