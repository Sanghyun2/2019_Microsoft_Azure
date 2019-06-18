# [ 도전! Dr.Azure ]
## AZ-103 Training (2019.06.13 - 2019.06.14)

서울창업허브 세미나실3, 백범로 31길 21, 서울창업허브, 마포구, 서울특별시

한국무역협회와 MS Korea 주최

> 참고 사이트 : https://www.microsoft.com/en-us/learning/exam-az-103.aspx

## Azure Cloud 개요

### Infrastructure as a Service (IaaS)
Infrastructure as a service (IaaS) is an instant computing infrastructure, **provisioned and managed over the internet**. 

It’s one of the four types of cloud services, along with software as a service (SaaS), platform as a service (PaaS), and serverless.

IaaS quickly scales up and down with demand, letting you pay only for what you use. 

It helps you avoid the expense and complexity of buying and managing your own physical servers and other datacenter infrastructure. 

Each resource is offered as a separate service component, and you only need to rent a particular one for as long as you need it. 

A cloud computing service provider, such as Azure, manages the infrastructure, while you purchase, install, configure, and manage your own software—operating systems, middleware, and applications.

> 출처 : https://azure.microsoft.com/ko-kr/overview/what-is-iaas/

### Platform as a Service (Paas)
PaaS(Platform as a Service)는 단순한 클라우드 기반 앱에서 정교한 클라우드 사용 엔터프라이즈 응용 프로그램에 이르기까지 모든 것을 제공할 수 있는 리소스가 포함되어 있으며 **클라우드에서 제공되는 완전한 개발 및 배포 환경**이다.

사용자는 클라우드 서비스 공급자로부터 종량제 방식으로 필요한 리소스를 구매하고 보안 인터넷 연결을 통해 해당 리소스에 액세스하면 된다.

IaaS처럼 PaaS에는 서버, 저장소, 네트워킹 등의 인프라뿐만 아니라 미들웨어, 개발 도구, BI(비즈니스 인텔리전스) 서비스, 데이터베이스 관리 시스템 등도 포함되어 있다. 

**PaaS는 빌드, 테스트, 배포, 관리, 업데이트의 완전한 웹 응용 프로그램 수명 주기를 지원하도록 디자인**되었다.

PaaS를 사용하면 소프트웨어 라이선스, 기본 응용 프로그램 인프라 및 미들웨어 또는 개발 도구와 기타 리소스를 구입하고 관리하는 비용과 복잡성이 없어진다. 

사용자는 개발하는 응용 프로그램과 서비스를 관리하고 클라우드 서비스 공급자는 일반적으로 그 밖의 모든 항목을 관리한다.

> 출처 : https://azure.microsoft.com/ko-kr/overview/what-is-paas/

### Software as a Service (Saas)
SaaS(Software as a Service)를 사용하면 사용자는 인터넷을 통해 클라우드 기반 앱에 연결하여 이를 사용할 수 있다. 

일반적인 예로는 메일, 일정 및 Office 도구(예: Microsoft Office 365)가 있습니다.

SaaS는 **클라우드 서비스 공급자로부터 종량제 방식으로 구매하는 완전한 소프트웨어 솔루션을 제공**한다. 

조직을 위한 앱 사용을 대여하고 귀하의 사용자는 일반적으로 웹 브라우저를 사용하여 인터넷을 통해 해당 앱에 연결한다. 

모든 기본 인프라, 미들웨어, 앱 소프트웨어 및 앱 데이터는 서비스 공급자의 데이터 센터에 있다. 

서비스 공급자는 하드웨어 및 소프트웨어를 관리하고 적절한 서비스 계약을 통해 앱과 데이터의 가용성과 보안도 보장한다. 

SaaS를 통해 조직은 최소의 사전 투자 비용으로 빠르게 앱을 실행 중 상태로 만들 수 있습니다.

> 출처 : https://azure.microsoft.com/ko-kr/overview/what-is-saas/

### Network Address Translation (NAT)
컴퓨터 네트워킹에서 쓰이는 용어로서, IP 패킷의 TCP/UDP 포트 숫자와 소스 및 목적지의 IP 주소 등을 재기록하면서 라우터를 통해 네트워크 트래픽을 주고 받는 기술을 말한다. 

패킷에 변화가 생기기 때문에 IP나 TCP/UDP의 체크섬(checksum)도 다시 계산되어 재기록해야 한다. 

NAT를 이용하는 이유는 대개 사설 네트워크에 속한 여러 개의 호스트가 하나의 공인 IP 주소를 사용하여 인터넷에 접속하기 위함이다. 

많은 네트워크 관리자들이 NAT를 편리한 기법이라고 보고 널리 사용하고 있다. 

NAT가 호스트 간의 통신에 있어서 복잡성을 증가시킬 수 있으므로 네트워크 성능에 영향을 줄 수 있는 것은 당연하다.

> 출처 : https://ko.wikipedia.org/wiki/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC_%EC%A3%BC%EC%86%8C_%EB%B3%80%ED%99%98
