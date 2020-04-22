# Essential Cloud Infrastructure: Foundation 003

## Module 3 part1 Q&A , Summary

---

## by 광선

### Questions
- q1. 스토리지 유형을 적절하게 선택하세요.
  - Cloud SQL (Object / Relational / Non-Relational / Warehouse)
  - Cloud Bigtable (Object / Relational / Non-Relational / Warehouse)
  - BigQuery (Object / Relational / Non-Relational / Warehouse)
  - Cloud Spanner (Object / Relational / Non-Relational / Warehouse)
  - Cloud Firestore (Object / Relational / Non-Relational / Warehouse)
  - Cloud Storage (Object / Relational / Non-Relational / Warehouse)

- q2. Cloud Storage 는 원할 때 regional bucket을 Multi-regional bucket으로 변경할 수 있다. (O/X)

- q3. Signed URL 을 사용하는 경우, 원하는 시간 후에 사용불가하는 것이 가능하다. (O/X)

- q4. Cloud Stroage 는 삭제 후에 원복하는 게 가능하다. (O/X)

- q5. IAM 리소스 계층을 상위부터 순서대로 나열하라
  - (folder, project, org., res.)

- q6. 회사의 조직구조와 IAM 리소스를 적절하게 연결하라.
  - (회사, 사업부, 팀, 상품)

### Answers
  - a1. Relational, Non-Relational, Warehouse, Relational, Non-Relational, Object
  - a2. X
  - a3. O
  - a4. O
  - a5. Organization, Folders, Projects, Resources
  - a6. 회사: org., 사업부:folder., 팀:folder, 상품:folder

---

## by 동렬
문제
* (3-1) 클라우드 리소스 계층구조를 루트부터 리프노드까지 나열하시오.
* (3-2) 다음 중 조직 관리자(Organization Admin) 역할이 **아닌** 것은?
	1. IAM 정책을 정의
	2. 리소스 계층구조를 결정
	3. 조직 관리 역할을 다른 사용자에게 배정
	4. 네트워킹, 청구, IAM 역할을 통한 리소스 계층 구조처럼 치명적인 컴포넌트의 책임을 위임
* (3-3) role의 3가지 종류?
* (3-3) Owner 역할에는 ? 역할이 포함되고 Editor 역할에는 ? 역할의 권한이 포함됩니다.
* (3-5) member의 5가지 종류?
* (3-6) 서비스 계정의 3가지 종류?

해답
* (3-1) 조직(최상위 루트노드) -> 폴더 -> 프로젝트 -> 리소스(리프노드)
* (3-2) 3
* (3-3) primitive, predefined, custom
* (3-3) Editor, Viewer
* (3-5) Google Account, Service Account, Google Group, G Suite, Cloud Identity Domains
* (3-6) 사용자 정의(사용자가 생성), 빌트인, 구글 API 서비스 계정
