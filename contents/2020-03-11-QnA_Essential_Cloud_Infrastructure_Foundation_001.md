# Essential Cloud Infrastructure: Foundation 001

## Module 1. Q&A , Summary

---

## by 영균

### Using GCP

    Q. GCP를 사용하는 4가지 방법
       1. GCP console - Web GUI
       2. Cloud Shell and SDK - Terminal (Temporary VM, 5GB /home)
       3. REST API
       4. Cloud Mobile APP

### Lab: console and Cloud Sheel

    The GCP interface consists of two parts: the GCP Console and Cloud Shell.

    Q. [GCP Console/Cloud Shell]:
       - Provides a fast way to get things done
       - Presents options to you, instead of requiring you to know them
       - Performs behind-the-scenes validation before submitting the commands

    Q. [GCP Console/Cloud Shell]:
       - Detailed control
       - Complete range of options and features
       - A path to automation through scripting

### Lab: Infrastructure Preview

    Q. GCP Marketplace에서 소프트웨어 패키지를 바로 배포할 수 있도록 미리 정의된 템플릿을 제공해주는 GCP 서비스는?
       1. Deployment Manager
       2. Template Manager
       3. Firestore
       4. Terraform

    Q. Cloud Shell에서, 재시작 시에도 환경변수가 사라지지 않고 적용되도록 추가해주는 파일 이름은?
       [        ]


### Projects

    Q. Cloud console에서 현재 활성화된 프로젝트를 변경하기 위한 명령어는?
       [                    ]

---

## by 동렬

    Q. (3-1) GCP와 상호작용하는 4가지 방법은?

    Q. (3-5) GCP 클라우드 shell에서 환경변수를 영구적으로 저장하는 방법?

    Q. (3-5) GCP 클라우드 shell에서 버킷 만드는 명령은?

---

## by 덕헌

### 1주차
- GCP와 iteract 할 수 있는 방법 4가지
  1. Google Cloud Platform Console
  2. Cloud Shell and Cloud SDK
  3. REST-based API
  4. Cloud Mobile App
- Maketplace
  - 개발 속도를 높이기 위해 바로 사용할 수 있는 개발 스택, 솔루션, 서비스를 제공
  - Jenkins 설치 및 운영 hand-on lab
- Deployment Manager
  - 애플리케이션에 필요한 모든 리소스를 yaml을 사용한 선언 형식으로 지정
  - Python 또는 Jinja2 템플릿을 사용해 구성을 매개변수화
  - 부하 분산 및 자동 확장되는 인스턴스 그룹 같은 일반적인 배포 패러다임을 재사용
- Demo : Proejct
  - ...
- Virtual Private Cloud(VPC) Object
  - Proejcts
    - 오브젝트와 비용이 청구되는 서비스로 구성되어 있다.
    - 최대 5개의 network를 구성할 수 있다.(shared/peered)
  - Networks
    - default, auto mode, custom mode로 구성할 수 있다.
      - default
        - 모든 프로젝트에 생성되어 있다.
        - 각 region마다 1개의 서브넷이 있다.
        - 기본 방화벽 정책이 적용되어 있다.
      - auto mode
        - default 네트워크
        - 각 region마다 1개의 서브넷이 있다.
        - regional IP가 할당할 수 있다.
        - 리전마다 /20 서브넷 네트워크가 고정되어 있다.
        - /16까지 확장할 수 있다.
      - custom mode
        - default로 생성되어 있지 않다.
        - IP 대역을 전체적으로 컨트롤 해야 한다.
        - regional IP를 할당할 수 있다.
        - RFC 1918 size까지 확장할 수 있다.(RFC 1918 : 네트워크 규격? 표쥰?)
    - IP 대역에 대한 정보가 없다.
    - 모든 Region에 대하여 글로벌하 확장할 수 있다.
    - subnetwork들을 포함한다.
    - 같은 네트워크에 있는 다른 리전 인스턴스는 내부 IP로 통신할 수 있다.
    - 다른 네트워크에 있는 같은 리전 인스턴스는 내부 IP로 통신할 수 없고, 외부 IP로 통신할 수 있다.
    - 인스턴스 재생성 없이 서브넷을 확장할 수 있다.
      - 다른 subnet과 겹칠 수 없다.
      - RFC 1918 주소 규격? 표준?을 준수해야만 한다.
      - 서브넷은 확장할 수 있지만 축소할 수는 없다.
      - auto 모드는 /20 부터 /16까지 확장할 수 있다.
      - 큰 서브넷은 지양해야 한다.
    - custom subnet with a /29 mask. A /29 mask provides you with 8 addresses, but of those, 4 are reserved by GCP, which leaves another 4 for your VM instances.
      - 4 GCP : subnet, gateway... what 2?
  - Subneworks
  - Regions
  - Zones
  - IP address
    - internal, external, range
    - DHCP(Dynamic Host Configuration Protocol) : 호스트의 IP주소와 각종 TCP/IP 프로토콜의 기본 설정을 클라이언트에게 자동적으로 제공해주는 프로토콜
    - vm name + 내부 IP + project id로 dns가 등록된다. [hostname].[zone].c.[project-id].internal
    - 외부 IP는 실행중인 VM에 연결되지 않은 경우 청구된다.
    - VM은 외부 IP를 찾을 수 없다. 내부 IP와 mapping 되어 있다.
  - Virtual Machines(VMs)
  - Routes and Firewall rules
    - 라우터
      - 모든 네트워크는 인스턴스가 트래픽을 서로 직접 송신할 수 있는 라우터를 가지고 있다.
      - 외부 네트워크로 직접 패킷을 보낼 수 있는 default 라우터를 가지고 있다.
    - 방화벽 정책
      - vpc 네트워크는 분산 방화벽 기능을 한다.
      - 방화벽 정책은 전체 네트워크에 적용되어 있다.
      - 연결은 인스턴스 레벨에서 허용 및 제한한다.
      - 방화벽 정책은 stateful 하다. 추적 가능하다.
      - ingress는 모두 제한, egress는 모두 허용을 기본으로 한다.
  - 가격정책
    - Ingress : No charge
    - Egress to the same zone (internal IP address) : No charge
    - Egress to Google products (YouTube, Maps, Drive) : No charge
    - Egress to a different GCP service (within same region; exceptions) : No charge
    - Egress between zones in the same region : (per GB) $0.01
    - Egress to the same zone : (external IP address, per GB) $0.01
    - Egress between regions within the US and Canada : (per GB) $0.01
    - Egress between regions, not including traffic between US regions : Varies by region
  - bastion host
    - 내부 네트워크와 외부 네트워크를 연결하는 일종의 게이트웨이 역할을 수행하는 호스트. 내부 네트워크 전면에서 내부 네트워크의 보안을 책임진다.
### Quiz
1. GCP를 intracive 하게 control 할 수 있는 방법은?
2. 개발속도를 높이기 위해 바로 사용할 수 있는 개발 스택, 솔루션 및 서비스를 제공하는 GCP 서비스는?
3. 데이터 센터 네트워크와 같은 실제 네트워크의 가상 버전으로, GCP 오브젝트 및 리소스를 연결하는 오브젝트는?
4. VPC, 라우터, 방화벽 규칙은 전역 리소스다.(True/False)
5. VPC 에는 IP 주소 범위가 포함되어 있다.(True/False)
6. 서브넷은 리전 리소스다.(True/False)
7. (Lab review) CIDR 10.0.0.0/29 일 때, 이에 대응되는 IP 범위는?
8. (Lab review) CIDR 10.0.0.0/29 일 때, vm instance를 최대 4개까지 생성 가능했다. 이유는?
9. 1개의 프로젝트는 최대 몇 개의 네트워크 구성이 가능한가?(shared/peered 포함)
10. 내부 IP 확인 command(ubuntu)
11. 외부 IP 확인 command(ubuntu)
12. 기본적으로 방화벽 정책은 (1)은 모두 허용, (2)는 모두 거부를 포함하고 있다.
13. 다음 가격 정책 중에서 비용이 부과되는 정책을 모두 고르시오
14. 내부 네트워크와 외부 네트워크를 연결하는 일종의 게이트웨이 역할을 수행하는 호스트 일컫는 오브젝트를 무엇이라고 하는가?
15. 인스턴스간 네트워크 연결 및 단절 또는 네트워크 요청을 받아들일수 있는지 여에 대한 테스트는 ping 프로그램을 사용한다. ping 테스트를 가능하게 하는 프로토콜 및 방화벽 정책은?
