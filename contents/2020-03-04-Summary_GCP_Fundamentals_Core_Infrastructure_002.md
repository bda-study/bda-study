# Google Cloud Platform Fundamentals: Core Infrastructure

Created By: youngkyun Kim
Last Edited: Mar 04, 2020 9:28 PM

[https://www.coursera.org/learn/gcp-fundamentals?specialization=gcp-architecture#syllabus](https://www.coursera.org/learn/gcp-fundamentals?specialization=gcp-architecture#syllabus)

- Introducing Google Cloud Platform
- Getting Started with Google Cloud Platform
- Virtual Machines in the Cloud
- Storage in the Cloud

# week 1

## Introducing Google Cloud Platform

[https://www.coursera.org/learn/gcp-fundamentals/lecture/qWhgM/gcp-computing-architectures](https://www.coursera.org/learn/gcp-fundamentals/lecture/qWhgM/gcp-computing-architectures)

IaaS vs PaaS vs SaaS

## VPC Network

[https://www.coursera.org/learn/gcp-fundamentals/lecture/wyDK3/important-vpc-capabilities](https://www.coursera.org/learn/gcp-fundamentals/lecture/wyDK3/important-vpc-capabilities)

load-balance options

Interconnect options

## Cloud Storage

[https://www.coursera.org/learn/gcp-fundamentals/lecture/HLKXf/cloud-storage](https://www.coursera.org/learn/gcp-fundamentals/lecture/HLKXf/cloud-storage)

object storage vs block storage vs file storage

object storage는 바이트를 key value pair로 저장. 키가 url 형태이므로 web 기반 기술과 궁합이 좋음.

immutable 형태. (새로운 버전으로 생성만 가능)

암호화 저장, https 전송 default

versioning을 안 할 경우, 매 번 overwrite

versioning을 할 경우, 마지막 N개만 유지하도록 설정 가능

Cloud Storage Class

- Multi-regional (Geo-redundant)
- Regional
- Nearline (long-tail)
- Coldline (archiving)

## Cloud Bigtable

Bigtable은 NoSQL이다.

stands for HBase (sparsely populated table에 유리)

단일 lookup key를 가진 매우 큰 persistant hash table이라고 생각해도 됨.

장점 (vs HBase 직접 구축)

- managed, scalability (no need admin for upgrade, restart)
- encryption (in-flight, at-rest)
- IAM
- GCP 연동

## Google Cloud SQL and Google Cloud Spanner

Cloud SQL은 RDBMS다.

트랜잭션이 가능함.

테라바이트 처리가 가능한 MySQL or PostgreSQL(beta)

장점 (vs MySQL 직접 구축)

- automatic replication/failover for multiple zone
- on-demand/scheduled backup
- scaling both vertical/horizontal
- security
- GCP 연동

Cloud Spanner? horizontally scalable RDMBS

## Google Cloud Datastore

Cloud Datastore는 NoSQL이다.

stands for MongoDB

Bigtable과 다른 점?

- 어플리케이션 백엔드 목적
- 트랜잭션 지원
- SQL 쿼리 지원
- Daily Quota 지원

---

## Containers, Kubernetes, and Kubernetes Engine

VM vs Container

VM은 OS를 포함하기 때문에 불필요한 리소스를 점유한다.

그에 반해, Container 방식은 독립적인 디펜던시를 유지하여 PaaS, IaaS와 같은 추상화 제공.

따라서, 워크로드 대응에 따른 동적 확장 용이함.

## Introduction to Kubernetes and GKE

Cluster?

masters + nodes(computing instance)

Google Cloud의 kubernetes node는 VM(Compute Engine)으로 구동된다.

pod?

kubernetes에서 컨테이너를 배포하기 위한 유닛. pod은 보통 1개의 컨테이너를 포함하지만, 여러 개도 가능 (의존성이 강할 경우)

deployment?

복제 세트를 관리 및 컨트롤하는 단위

service?

외부 접근 가능한 endpoint를 제공함. 고정 아이피를 가지며 내부적으로 pod을 라우팅함

kubectl autoscale을 통해 자동 스케일 가능.

imperative vs declarative?

kubernetes의 강점. 명령적으로 운영하는 것이 아니라, 이상적인 상태를 선언하여 유지하도록 만듬

명령으로 scale → 파일 edit 후 apply

update strategy: rolling update

## Introduction to Hybrid and Multi-Cloud Computing (Anthos)

Anthos?

구글에서 개발한 hybrid/multi cloud 시스템 관리 솔루션

GKE, GKE on prem 위에서 동작함

GCP Marketplace를 통해 단일 소스 버전 컨트롤 가능

Anthos, Istio로 kubernetes 클러스터의 서비스 핸들링

stack driver로 kubernetes 클러스터 모니터링

single source of truth 지원

 Anthos 주요 구성

- Google Kubernetes Engine
- GKE On-Prem
- Istio on GKE
- Anthos Config Management

Quiz

Kubernetes allows you to manage container clusters in multiple cloud providers.

True

## Module introduction; introduction to App Engine

App Engine은  PaaS다.

사용자가 code만 주면, 나머지 Infrastructure는 App Engine이 자동으로 해결함.

서버를 관리하지 않아도 되기 때문에, 워크로드가 동적이거나 예측 불가능할 때 좋음.

standard, flexible 두 가지 타입의 환경 제공

## Google App Engine Standard Environment

sdk를 제공하여 로컬에서 실행해보고, 운영용 App engine에 올릴 수 있음.

runtime?

App engine이 실제로 구동되는 환경

바이너리, 라이브러리와 같다고 볼 수 있음

Java, Python, Go, PHP의 특정 버전 지원

만약 이외의 언어가 필요하면, flexible을 사용해야 함.

datastore, memcached, task queue 등

sandbox?

코드가 동작할 때 물리적인 정보와 독립적으로 동작하도록 하는 제약.

standard 환경에서 autoscale을 하기 위한 중요 요소.

로컬 파일시스템에 파일을 쓸 수 없음. 대신, 데이터베이스에 저장.

모든 리퀘스트의 타임아웃은 60초.

써드파티 소프트웨어 사용 불가.

역시 이런 제약을 가질 수 없다면, flexible을 사용해야 함.

idle time 시 사용료가 없음.

## Google App Engine Flexible Environment

standard 환경 사용이 불가하지만, App Engine은 사용하고싶을 때 필요한 옵션.

container에서 동작하며, Compute Engine 즉 VM에서 실행됨.

VM의 세부적인 사항을 App Engine이 대신 관리해주게 됨.

standard 환경의 모든 런타임을 그대로 사용할 수 있음.

VM 리소스에 대한 시간당 비용 발생.

## Google Cloud Endpoints and Apigee Edge

API 서비스다.
