
[Application Load Balancer](#application-load-balancer)

[Network Load Balancer](#network-load-balancer)

### Application Load Balancer

- ALL

    - [ ] 로드 밸런서 타입, 스키마 확인

    - [ ] 로드 밸런서 VPC, Subnet 확인

    - [ ] 로드 밸런서 및 API Security Group 확인

- 리스너

    - [ ] 리스너 포트 번호 확인

    - [ ] 리스너 규칙 확인 -> (curl) 규칙 별 연결 확인.

- Target Group

    - [ ] 대상 그룹 프로토콜, 프로토콜 버전, 대상 유형 확인

    - [ ] 대상 그룹 속성 확인

    - [ ] 대상 그룹 Healthcheck 프로토콜, 경로, 포트 번호 확인

- Access Log

    - [ ] ELB 요청 -> 저장된 로그 확인

    - [ ] S3 버킷 권한 확인

    - [ ] S3 Default Encryption 확인 (SSE-S3만 허용.)


### Network Load Balancer

- ALL

    - [ ] 로드 밸런서 타입, 스키마 확인

    - [ ] 로드 밸런서 VPC, Subnet 확인

    - [ ] API Security Group 확인 (NLB 및 클라이언트 CIDR 허용)

- 리스너

    - [ ] 리스너 포트 번호 확인

    - [ ] 리스너에 연결된 Target Group 확인

    - [ ] (curl) 리스너 연결 확인

- Target Group

    - [ ] 대상 그룹 프로토콜, 대상 유형 확인

    - [ ] 대상 그룹 속성 확인

    - [ ] 대상 그룹 Healthcheck 프로토콜, 경로, 포트번호 확인
    
- Access Log

    - [ ] ELB 요청 -> 저장된 로그 확인

    - [ ] S3 버킷 권한 확인

    - [ ] S3 Default Encryption 확인 (SSE-S3만 허용.)