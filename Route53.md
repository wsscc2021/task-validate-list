
[Hosted Zone](#hosted-zone)

[Record](#record)

[Resolver](#resolver)

[DNS Firewall](#dns-firewall)

### ALL

- DNS Query 를 테스트할 때에는 항상 DNS Cache를 염두합니다. (TTL 값에 유의)

### Hosted Zone

- Private Hosted Zone

    - [ ] Associated VPCs 확인

### Record

- ALL

    - [ ] Record 설정 확인

    - [ ] Hosted Zone 확인

- Simple Routing policy

    - [ ] (nslookup, dig) DNS Query

- Failover Routing Policy

    - [ ] (nslookup, dig) Primary DNS Query 

    - [ ] (nslookup, dig) Primary Down → Standby DNS Query

- Geolocation Routing policy
    
    - [ ] (nslookup, dig) Location(region) DNS Query

    - [ ] (nslookup, dig) Another location(region) DNS Query

- Latency Routing Policy

    - [ ] (nslookup, dig) Nearby DNS Query

    - [ ] (nslookup, dig) Not nearby DNS Query

- Weighted Routing Policy

    - [ ] (nslookup, dig) DNS Query 반복 → 가중치 확인

- Multivalue Answer Routing Policy

    - [ ] (nslookup, dig) DNS Query → Multi-value 확인

### Resolver

- Inbound Endpoint

    - [ ] Host VPC, Subnet 확인

    - [ ] SecuriyGroup 확인 (인바운드 규칙에 external resolver의 TCP/UDP 53 허용)

    - [ ] external resolver를 서버로 지정하고, 내부 레코드 Query

- Outbound Endpoint

    - [ ] Host VPC, Subnet 확인

    - [ ] SecurityGroup 확인 (인바운드 규칙에 VPC 두 번째 주소의 TCP/UDP 53 허용)

    - [ ] (Rule) Domainn 확인

    - [ ] (Rule) Associate VPC 확인

    - [ ] 외부 레코드 Query

### DNS Firewall

- ALL

    - [ ] Rule Group 의 VPCs associated 확인

    - [ ] Rule Group 의 Rule 확인

    - [ ] Rule Group 의 Rule 에 연결된 Domain list 확인

    - [ ] (nslookup, dig) DNS Query -> Action 확인 (ALLOW, BLOCK, ALERT)

### Query Logging

- !! Query Logging은 요청에 대한 정보만 기록함. (응답에 대한 정보는 기록하지 않음.)

- ALL

    - [ ] Destination ARN 확인

    - [ ] logged for VPC 확인

    - [ ] (nslookup, dig) DNS Query -> 실제 Log 확인