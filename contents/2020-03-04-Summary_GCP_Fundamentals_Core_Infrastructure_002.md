# Google Cloud Platform Fundamentals: Core Infrastructure

Created By: youngkyun Kim
Last Edited: Mar 08, 2020 3:53 PM

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

## Development in the cloud

Cloud Source Repository?

git repository 기능 제공

IAM 기반 권한 제어 가능

Cloud Functions? (Beta)

event driven architecture에서의 server-less function 제공

ex) 사진 업로드 이벤트 → 썸네일 자동 생성, 파일 저장 등

이벤트 발생 횟수에 따라 과금

1. event 선택
2. Node.js 환경에서 실행 될 function 작성

MSA 구현 전체를 Cloud Functions 만으로 구현 가능

## Deployment: Infrastructure as code

인프라를 명령어로 관리하기보다, 템플릿으로 정형화 해서 선언적인 형태로 관리하는 것이 효율적이다.

템플릿은 소스로 만들 수 있기 때문에 버전 컨트롤이 가능하다.

## Monitoring: Proactive instrumentation

Stackdriver?

GCP 모니터링 도구

Stackdriver Monitoring?

web app의 endpoint 체크, uptime 체크 (instance, load balancers), alert setting

notification 도구들과 사용 가능하며, dashboard 구성도 가능함.

Stackdriver Logging?

app의 로그를 보거나 필터링 할 수 있음.

로그 기반의 metric을 정의하여 대시보드나 alert에 노출시킬 수 있음.

로그를 bigquery, pubsub 등에 export 할 수 있다.

Stackdriver Error Reporting?

에러를 그룹화 하고 추적하여 app에서 에러 발생 시 notify

Stackdriver Trace?

App Engine의 레이턴시 샘플링, URL 단위의 statistics 제공

Stackdriver Debugging?

디버깅 기능 제공

어플리케이션에 디버깅 코드를 작성하는 기존 방식과 달리, 어플리케이션의 상태를 inspect할 수 있도록 production data를 소스코드에 연결함.

Cloud Source repository에 소스코드가 있을 경우 잘 동작함.

## Google Cloud Big Data Platform

Cloud Dataproc?

hadoop 기반 빅데이터 솔루션(hdfs, spark, hive, pig)을 사용할 수 있게 해주는 managed platform

Cloud Dataflow?

batch/streaming 가능한 ETL 파이프라이닝 도구.

Source, Transform, Sink 구조. 각 파이프라인의 모든 단계는 동적 확장이 가능함.

클러스터를 시작하고 리소스 관리할 필요 없이, on demand로 리소스 할당 가능.

BigQuery?

ad-hoc SQL query on massive datasets.

fully managed, peta-byte scale, low-cost DW.

pay as you go model. 즉, 사용한 만큼 비용 지불.

cloud storage, cloud datastore의 데이터를 bigquery로 로드해서 사용.

스타트업부터 큰 규모의 기업까지, free quota와 높은 SLA 등의 장점으로 많은 기업에서 사용함.

리전 설정 가능. 데이터를 유럽, 아시아 등의 단위로 저장하도록 설정 가능함.

스토리지와 컴퓨팅이 나눠져 있음. 따라서, 실제로 쿼리가 동작할 경우에만 과금.

누가 데이터에 접근했는지 등의 컨트롤이 가능함.

데이터셋을 타 프로젝트와 공유할 경우, 퍼포먼스나 비용에 영향을 주지는 않음.

90일 이상 지난 데이터는 자동으로 cold tier로 저장되어 가격이 저렴해짐.

Cloud Pub/Sub and Cloud Datalab?

Cloud Pub/Sub은 카프카와 같은 메세지 큐라고 보면 됨.

단일 프로듀스, 다중 컨슈머 모델.

low latency를 보장하는 at least once 모델. 즉, 매우 적은 확률로 한 번 이상의 메세지가 전달될 수 있다.

초당 백만 단위의 on demand scale 지원함.

Cloud Dataflow와 합이 매우 잘 맞음. 특히 IoT와 같은 real-time 데이터일 경우.

Cloud Datalab은 Jupyter와 같음.

Compute Enging VM 위에서 동작함. 생성 시 VM 타입과 리전 설정 필요.

## **Google Cloud Machine Learning Platform**

Cloud Machine Learning Platform?

managed 머신러닝 플랫폼.

Google에 의해 pre-train 된 다양한 머신러닝 모델을 사용할 수 있다.

Tensorflow 지원.

Tensor Proccessing Unit(TPU)을 Compute Engine VM으로 구성하여 Tensorflow 활용 가능.

사용에 대한 과금 정책이기 때문에, 역시 인프라에 대한 비용 투자를 효율적으로 할 수 있음.

다양한 목적에 따라 사용할 수 있는 머신러닝 API를 제공함.

정형 데이터 vs 비정형 데이터

정형 데이터 - 분류, 회기, 추천, 어노멀리 디텍션

비정형 데이터 - 이미지, 비디오, 텍스트 분석

Machine learning APIs?

Cloud Vision API - rest API 기반의 이미지 분석

Cloud Natural Language API - STT. 80개 이상 언어 지원.

Cloud Translation API - 특정 문자열을 다양한 언어로 번역. 소스 언어를 몰라도 자동으로 찾아냄.

Cloud Video Intelligence API(Beta) - 비디오 컨텐트의 annotation을 통해 검색 가능.
