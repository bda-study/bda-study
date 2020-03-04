# Google Cloud Platform Fundamentals: Core Infrastructure 002 Q/A


---
# Containers, Kubernetes, and Kubernetes Engine

### 강의: Containers, Kubernetes, and Kubernetes Engine
    Q. 각 클라우드 컴퓨팅 부분에 대해 대표적인 GCP 서비스는?
       IaaS, CaaS, Paas, FaaS
    A. IaaS : Compute Engine
       CaaS : Kuberentes Engine
       PaaS : App Engine
       FaaS : Cloud Funtions


### 강의: Introduction to Kubernetes and GKE
    Q. 사용자가 원하면 Kubernetes Master를 직접 제어할 수 있는가?
    A. 불가. 워커만 제공. 마스터는 GCP에서 관리됨


### 강의: Introduction to Hybrid and Multi-Cloud Computing (Anthos)
    Q. K8s 엔진을 기반으로 멀티 클라우드를 지원하는 GCP 서비스는?
    A. Anthos


### 강의: Lab Introduction Getting Started with Kubernetes Engine
    Q. 생략


### 강의: Demo: Getting Started with Kubernetes Engine
    Q. 배포된 어플리케이션을 외부에서 접근 가능하도록 IP 발급을 받아야 한다. 이 때 사용하는 K8s 리소스는?
    A. Service


---
# Module introduction; introduction to App Engine


### 강의: Module introduction; introduction to App Engine
    Q. App Engine 에서 제공하는 기본 제공 서비스가 아닌 것은?
       NoSQL 데이터베이스, 메모리 내 캐싱, 로드 밸런싱, 상태 확인, 로깅, 사용자 인증, SSH 접근, 제어 가능한 컨테이너 환경
    A. "제어 가능한" 컨테이너 환경


### 강의: Google App Engine Standard Environment
    Q. App Engine 두가지 환경 중 ASP.NET 서비스를 위한 환경은?
    A. Flexible. Standard는 Java, Python, PHP, Go 지원


### 강의: Google App Engine Flexible Environment
    Q. 어떻게 Flexible 환경은 다양한 런타임을 지원하는가?
    A. Docker Container 활용


### 강의: Google Cloud Endpoints and Apigee Edge
    Q. API 지원 도구 중 어떤 것을 설명하나?
       API를 쉽게 노출하고 싶다. 신뢰하는 다른 개발자만 사용하고 있는지 확인하고 싶다.
    A. endpoints


    Q. API 지원 도구 중 어떤 것을 설명하나?
       속도 제한, 할당량 및 분석과 같은 비즈니스 문제에 중점을 둔다.
    A. apigee edge


### 강의: Demonstration: Getting Started with App Engine
    Q. App Engine 에 코드 배포시 yaml 파일로 정의할 수 있다?
    A. true



---
# Developing, Deploying and Monitoring in the Cloud


### 강의: Development in the cloud
    Q. 간헐적 또는 아주 짧은 시간만 작업 수행시 적합한 GCP 서비스는?
    A. Cloud Functions


### 강의: Deployment: Infrastructure as code
    Q. 템플릿을 통해 Infra as code를 가능하게 하는 Deployment Manager은
       Yaml, Python, Ruby, XML 중 어떤 양식을 지원하는가?
    A. Yaml, Python


### 강의: Monitoring: Proactive instrumentation
    Q. Stackdriver 핵심 구성 요소가 아닌 것은?
       모니터링, 로깅, 추적, 오류보고, 디버깅, 코드 수정
    A. 코드 수정


### 강의: Demonstration: Getting Started with Deployment Manager and Stackdriver
    Q. Stackdriver에서 AWS 계정을 모니터링하는 것이 가능한가?
    A. 가능하다



---
# Big Data and Machine Learning in the Cloud


### 강의: Introduction to Big Data and Machine Learning
    Q. 생략


### 강의: Google Cloud Big Data Platform
    Q. GCP 에서 제공하는 하둡 및 스파크, 하이브, 피그를 제공하는 서비스는?
    A. Dataproc. 사이즈를 알고, 직접 관리할 때 좋음.


    Q. Dataproc 과 직접 설치 중 저렴한 것은?
    A. Dataproc. 1 초단위 청구 가능하여 사용후 종료 시키면 됨.


### 강의: Cloud Dataflow
    Q. 스트리밍, 예측 불가 크기 및 속도의 데이터를 다룰 때 좋은 GCP 서비스는?
    A. Dataflow. 클러스터를 올릴 필요 없음.


### 강의: BigQuery
    Q. BigQuery는 과금시 스토리지 비용을 포함하는가?
    A. BigQuery는 스토리지와 계산을 분리. 쿼리와 별도로 데이터 스토리지 비용을 지불


### 강의: Cloud Pub/Sub and Cloud Datalab
    Q. 주피터 노트북을 제공하기 위한 서비스는?
    A. DataLab


### 강의: Google Cloud Machine Learning Platform
    Q. Tensorflow 를 GCP에서 강력하게 사용할 수 있도록 특화되어 제작된 하드웨어는?
    A. Tensor Processing Units


### 강의: Machine learning APIs
    Q. Machine Learning API 가 정식으로 지원하지 않는 분야는?
       Vision, Speech, Natural Language, Traslation, Video Intelligence
    A. Video Intelligence는 beta


### 강의: Demonstration: Getting Started with BigQuery
    Q. BigQuery는 기존 스토리지의 데이터를 쿼리할 수 있게 해준다? 로컬에 있는 CSV 파일이 있을 경우에는 어떤 작업이 필요한가?
    A. Cloud Storage 에 올려서. 데이터셋을 정의하면 쿼리 수행 가능
