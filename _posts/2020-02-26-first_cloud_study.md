---
title: "GCP 스터디. Core Infrastructre 첫번째"
date: 2020-02-26 22:25:00 +0900
categories: meeting
---

## 2020-02-26 GCP 스터디. Core Infrastructre 첫번째

### - 차주 스터디 계획
  - 일시 : 2020-03-04
  - 범위 : Core Infrastructure 강의 containers 부터 끝까지
  - 준비 : 클립당 1개 이상 문제 내기
  - 진행 : 문제 풀기, Q&A/자유공유

### - 스터디 진행 내용

- 개요
  - 범위 : Core Infrastructre, Introducing ~ Storage
  - 일시 : 2020-02-26 21:00~22:30
  - 참석 : 동렬, 영균, 덕헌, 광선

- 지난주 Q&A 확인
  - n/a (다음주부터)

- 문제 내보기 (클립당 1개 이상)
  - n/a (다음주부터)

- Q&A 및 공유
  - zone 과 region의 차이점
    - region은 리소스를 호스팅할 수 있는 특정한 지리적 위치
    - 각 리전에는 zone이 한 개 이상 있으며 대부분의 리전에는 zone이 3개 이상
    - region 마다 가격이 상이하고, 제공하는 서비스가 다르다.
    - region 안에 zone. zone 안에서는 빠르게 통신 가능
    - 하나의 VPC는 하나의 region 에만 만들 수 있다.
    - 하나의 zone이 하나의 데이터센터에 대응되는 것은 아니다.
    - zone을 통해 zone간 리소스를 격리하는 역할을 한다.
    - zone resource : VM인스턴스, zone 영구 디스크. zone resource는 같은 zone 안에서만 사용 가능.
    - https://cloud.google.com/compute/docs/regions-zones
 
  - 리소스의 종류
    - Zone, Region, Global 세가지 리소스 존재
    - https://cloud.google.com/compute/docs/regions-zones/global-regional-zonal-resources
 
  - Multi region과 region의 차이점
    - Cloud Storage 에서 제공하는 스토리지 클래스 유형. multi-rigion, region, nearline, coldline
    - 현재 GCP 상에는 standard(frequently), nearline(once a month), coldline(once a quarter), archive(once a year) 존재
    - 각 클래스에는 multi-region, dual-region, region이 존재
    - https://cloud.google.com/storage/docs/storage-classes
    - https://cloud.google.com/storage/docs/locations
 
  - Preemptive VM 과 일반 VM 차이점
    - Preemptive VM은 배치성 작업에 활용
    - 중단 후 다시 진행 가능함
    - 저렴한 비용으로 사용 가능
    - 인스턴스가 갑자기 빼앗길 수 있음
    - GCP는 24시간에 한번씩 무조건 종료됨
    - AWS Spot VM과 유사, AWS Spot은 경매 개념이 적용.
    - https://cloud.google.com/compute/docs/instances/preemptible?hl=ko#what_is_a_preemptible_instance
  
  - Encryption at rest 의미
    - 미사용 상태로 보관 중인 고객 데이터를 기본으로 암호화.
    - Encryption in flight(transit) : SSL과 같이 통신 구간에서 암호화되는 것.
      Encryption at rest : 저장시에 저장됨.
    - https://cloud.google.com/security/encryption-at-rest
    - https://www.quora.com/What-is-the-difference-between-at-rest-encryption-and-in-transit-encryption
