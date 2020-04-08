# Essential Cloud Infrastructure: Foundation 003

## Module 3 part1 Q&A , Summary

---

## by 광선

### Questions

- VM을 만드는 GCP 서비스는?

- VM에 포함되지 않는 것은?
  cpu, memory, disk, security, ip

- 가장 빠른 스토리지를 순서대로
  SSD, local SSD, standard hard drive

- 지원하는 OS 이미지는?
  Windows, Mac, Linux, BSD

- VM 시작시 특정 작업하고 싶을 때는?

- Local SSD와 SSD 차이는?

- 인스턴스 하나에 Local SSD 최대 용량은?

- 인스턴스 하나에 SSD 최대 용량은?

- staging 상태에는 IP가 할당되지 않는다[T/F]

- 머신 타입 종류는?

- 인메모리 DB에 어울리는 머신 타입은?
  high memory vs memory optimized

- 각 Zone 마다 기본으로 제공하는 프로세서가 있다 [T/F]

- 최초 30초 사용시 1분치 과금 [T/F]

- Sustained use discounts 기반에서는 VM 할인율은 많이 사용할 수록 커진다. [T/F]

- Sustained use discounts 기반에서 최대 할인율은?


### Answers
  - Compute Engine
  - security
  - local SSD > SSD > Standard hard drive
  - Windows, Linux
  - startup script를 사용한다.
  - Local SSD는 VM에 물리적으로 붙는다. 인스턴스 stop/delete시 함께 제거
  - 3T = 375G x 8partitions
  - 64T
  - F. 할당된다.
  - standard, high memory, high cpu, memory optimized, compute optimized, shared-cores, custom
  - memory optimized
  - T. US-central1 은 Sandy Bridge processor가 기본
  - T. 이후 초당 과금
  - T.
  - 30%

---

## by 동렬
### 정리

#### (2-1) 몇가지 머신 타입
* vCPU 하나당 2Gbps까지 네트워크 처리량 확장
* 8 vCPU로 16 Gbps까지 이론상 최대 처리량
하나의 vCPU는 1개의 hyper-thread와 같음

#### (2-5) 멱등성
[https://padawanr0k.github.io/2018/06/23/etc/Idempotent/](https://padawanr0k.github.io/2018/06/23/etc/Idempotent/)
[https://ko.wikipedia.org/wiki/%EB%A9%B1%EB%93%B1%EB%B2%95%EC%B9%99](https://ko.wikipedia.org/wiki/%EB%A9%B1%EB%93%B1%EB%B2%95%EC%B9%99)
* 연산을 여러 번 적용하더라도 결과가 달라지지 않는 성질을 의미

#### 3. To see details about the RAM installed on your VM, run the following command:
VM에 설치된 RAM에 대한 자세한 내용을 보려면 다음 명령을 실행하십시오.
```bash
sudo dmidecode -t 17
sudo dmidecode -t memory
```
[https://www.sharedit.co.kr/posts/1415](https://www.sharedit.co.kr/posts/1415)

#### (3-1)
표준 머신 유형은 CPU와 메모리 요구가 균형을 이루는 작업에 적합합니다.
메모리 최적화 시스템 유형은 높은 메모리 시스템 유형보다 메모리 대 vCPU 비율이 높은 메모리를 집중적으로 사용해야하는 작업에 이상적입니다. 이러한 머신 유형은 SAP HANA 및 비즈니스웨어 하우스 워크로드, 게놈 분석 및 SQL 분석 서비스와 같은 인 메모리 데이터베이스 및 인 메모리 분석에 완벽하게 적합

#### (3-2)
* 좀 더 저렴하게 사용하는 Google Cloud Platform(GCP)

[https://medium.com/@jwlee98/%EC%A2%80-%EB%8D%94-%EC%A0%80%EB%A0%B4%ED%95%98%EA%B2%8C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-google-cloud-platform-gcp-456cd71379f8](https://medium.com/@jwlee98/%EC%A2%80-%EB%8D%94-%EC%A0%80%EB%A0%B4%ED%95%98%EA%B2%8C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-google-cloud-platform-gcp-456cd71379f8)


### 문제

#### (2-1) GCP compute and processing option의 5가지 종류?
#### (2-3) VM의 5개의 life cycle
#### (2-5) 메모리양 확인 shell 명령?
#### (2-5) 프로세스 개수 확인 shell 명령?
#### (2-5) cpu 정보를 확인 shell 명령?
#### (3-1) 표준 CPU 타입은 한 CPU 당 ? 기가를 가짐.

---

## by 덕헌

### Questions

- Q1. VM의 일반적인 lifecycle은?
- Q2. 외부/내부 IP 주소를 할당받는 VM의 lifecycle 단계는?
- Q3. (T/F) VM이 Stopped 상태인 경우에는 요금이 부과되지 않는다.
- Q4. (T/F) Running VM 변경 가능 여부
  - Q4-1. machine type을 변경할 수 있다.
  - Q4-2. CPU platform을 변경할 수 있다.
  - Q4-3. zone을 변경할 수 있다.
  - Q4-4. preemptible 설정을 변경할 수 있다.
- Q5. (T/F) Stopped VM 변경 가능 여부
  - Q5-1. machine type을 변경할 수 있다.
  - Q5-2. CPU platform을 변경할 수 있다.
  - Q5-3. zone을 변경할 수 있다.
  - Q5-4. preemptible 설정을 변경할 수 있다.
- Q6. Compute options 관련하여, machine type별 vCPU당 메모리크기는?
  - Q6-1. Standard machine
  - Q6-2. High memory
  - Q6-3. High CPU
  - Q6-4. Memory optimized
  - Q6-5. Compute optimize
- Q7. Compute Pricing : Per-(1) billing, with minimum (2).
- Q8. Preemptible의 최대 할인율은?


### Answers
- A1. Provisioning -> Staging -> Running -> Stopping -> Terminated
- A2. Staging 단계
- A3. F, 디스크 사용과 할당된 IP에 대한 비용이 부과된다.
- A4. (T/F) Running VM 변경 가능 여부
  - A4-1. F
  - A4-2. F
  - A4-3. F
  - A4-4. F
- A5. (T/F) Stopped VM 변경 가능 여부
  - A5-1. T
  - A5-2. T
  - A5-3. F
  - A5-4. F
- A6. Compute options 관련하여, machine type별 vCPU당 메모리크기는?
  - A6-1. 3.75GB/vCPU
  - A6-2. 6.5GB/vCPU
  - A6-3. 0.9GB/vCPU
  - A6-4. 14GB/vCPU
  - A6-5. 4GB/vCPU(3.8 gigahertz sustained all-core turbo)
- A7. Compute Pricing : Per-second billing, with minimum 1 minute.
- A8. 80%
