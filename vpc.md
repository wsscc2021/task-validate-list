
[VPC](#VPC)

[Subnet](#Subnet)

[NAT Gateway](#NAT-Gateway)

[Route Table](#Route-Table)

[PrivateLink](#PrivateLink)

[VPC Peering](#VPC-Peering)

### VPC

- ALL

  - [ ] CIDR 확인 ❗ CIDR은 이후에 변경할 수 없으므로 꼼꼼히 확인합니다.

  - [ ] Tag 확인 

### Subnet

- ALL

  - [ ] CIDR 확인 ❗ CIDR은 이후에 변경할 수 없습니다.

  - [ ] Availability Zone 확인 ❗ Availability Zone은 이후에 변경할 수 없습니다.

  - [ ] Tag 확인

- Public

  - [ ] IPv4 Auto-Assign option 활성화 확인

### NAT Gateway

- ALL

  - [ ] 연결된 Subnet의 AZ 확인.

  - [ ] Tag 확인

### Route Table

- Public

  - [ ] Subnet association 확인 (모든 public subnet)

  - [ ] Route 확인 (`0.0.0.0/0` -> Internet Gateway)

- Private

  - [ ] Subnet association 확인 (Private Subnet - same AZ)

  - [ ] Route 확인 (`0.0.0.0/0` -> Nat Gateway - same AZ)

### PrivateLink

- ALL

  - [ ] Endpoint에 연결된 Policy 확인

- Gateway type

  - [ ] Endpoint에 연결된 Route Table 확인

  - [ ] VPC 내부에서 연결 확인
      
    - 명령어
      ```
      $ traceroute dynamodb.us-east-1.amazonaws.com
      ```
      
    - 정상
      ```
      traceroute to dynamodb.us-east-1.amazonaws.com (52.94.2.78), 30 hops max, 60 byte packets
      1  * * *
      2  * * *
      3  * * *
      ...
      ```

    - 비정상
      ```
      traceroute to dynamodb.us-east-1.amazonaws.com (52.119.233.202), 30 hops max, 60 byte packets
      1  ec2-3-236-62-41.compute-1.amazonaws.com (3.236.62.41)  6.800 ms ec2-3-236-62-85.compute-1.amazonaws.com (3.236.62.85)  70.109 ms ec2-3-236-62-53.compute-1.amazonaws.com (3.236.62.53)  3.763 ms
      2  240.0.56.65 (240.0.56.65)  0.377 ms  0.359 ms 243.254.27.198 (243.254.27.198)  0.219 ms
      3  243.254.17.141 (243.254.17.141)  0.202 ms 243.254.16.13 (243.254.16.13)  0.189 ms 243.254.27.141 (243.254.27.141)  0.176 ms
      ...
      ```

- Interface type

  - [ ] Endpoint에 연결된 Security Group 확인

  - [ ] Endpoint에 연결된 Subnet 확인

  - [ ] Private DNS names enabled 활성화 확인 (비활성화되어 있으면, DNS로 접근이 불가능함.)

  - [ ] VPC 내부에서 연결 확인

    - 명령어 
      ```
      $ nslookup api.ecr.us-east-1.amazonaws.com
      ```
    
    - 정상적으로 설정한 경우 : Private IP address가 쿼리됨.
    
    - 비정상적으로 설정한 경우 : Public IP address가 쿼리됨.

- Endpoint Service

  - [ ] Endpoint 생성 후 승인 확인
  
  - [ ] 최종 API의 Security Group 확인 (CIDR추가되어 있어야 함)
  
  - [ ] Endpoint DNS 주소로 연결 확인
  

### VPC Peering

- ALL

  - [ ] Status 확인 (Active)

  - [ ] Requester VPC , Accepter VPC 확인

  - [ ] DNS settings 활성화 확인

  - [ ] 연결된 Route-Table, Route 확인 (삭제를 시도하면 한눈에 확인 가능함.)

  - [ ] 연결 확인 (과제 요구사항에 맞는... ex. HTTP 연결)