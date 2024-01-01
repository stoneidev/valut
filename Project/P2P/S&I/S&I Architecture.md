
## Business Context
- 현재 S&I 를 둘러쌓고 있는 비즈니스 컨텍스트에 대해서 기술한다. 현재 S&I는 인력 중심의 사업을 지속하고 있었으며, 2027년 까지 Prop Tech 중심의 IT 비즈니스로 1조 이상의 매출을 기록하는 회사로 발전하고자 한다. 이예 2024년 부터 SAFe의 LPM을 도입하여 이런 변화를 가속하고자 한다. 
- 2023년 SAFe의 LPM을 통하여 식별한 가장 중요하고 시작하고자 하는 목표는 PMS를 통한 채널의 확대를 통하여 중대형 빌딩 PMS 시장에 진출하고, 이전에 S&I의 많은 경쟁력이 있는 분야인 RMS를 현대화 하여 고객들에게 IT 비즈니스를 확대하는 것이다. 
- 2024년은 이 변화의 기반을 만드는 중요한 시기이며, 문화적이고 기술적인 토대를 마련하는 해이다.

## Development Environment Context
- 이전에 인력 중심의 비즈니스를 주로 해왔기 때문에 주로 IT에 대해서는 outsourcing 위주를 전략을 가지고 있었다. 때문에 내부 인원의 개발 경험과 아키텍쳐에 대한 경험이 많지 않으며, 현재로서는 개발 파트너 없이 독립적으로 위에서 이야기한 기반을 만들 수는 없는 상태이다. 
- 이후 50개 이상의 solution을 기반으로 사용자들에게 product를 제공하기로한 목표에 있어서 초반의 IT 기반을 이후 확장 가능하고 진화 가능하게 만드는 것은 매우 중요한 부분이지만, platform 개발 경험 이나 기술이 많이 부족한 상태입니다. 
- NPD를 이후 같이 고도화 하고자 하나 전반적인 IT에 대한 process 가 정립되어 있지 않으며, infrastructure에 대해서도 지속적으로 발전하기 어려운 상황입니다. 

## Architecture
- 개발하기 쉽고
- 유지보수 하기 쉬우며
- 지속적으로 확장 가능한
- 지속적으로 진화 할 수 있어야 함.

- Spring Boot 기반
- 이후 운영 비용이 적게 소모되는 ECS 기반
- Event Driven Architecture를 통한 decoupling
- Arch unit 등으로 지속적인 아키텍쳐 변경에 대한 추적 가능성 부여
- Trunk Based / TDD  도입을 통한 품질의 확보
- DDD 도입을 통한 이후 비즈니스 복잡도 관리의 기반을 마련
- API Gateway 및 BFF를 적극적으로 도입하여 FE/BE 간의 Coupling을 줄이고 API를 이용하여 Client Service를 속도감 있게 만들도록 함.

## Design
- 인지부하를 낮추가 위해 처음에 개발하는 Core Platform은 Meta / Finanace 두 부분으로 Multi Module로 구성된 Moduler Monolith로 구성함.
- Architect의 역량에 따라 Model Driven Design을 도입하여 일관성있는 모델링을 통하여 지속적으로 기술 부채를 관리할 예정
- Module & Bounded Context : DDD의 core domain의 개념을 적용하여 이후 확장에도 중요한 부분은 식별함.
	- Meta
		- Building
		- Owner
		- Tenant
	- Finance
		- Rents
		- Costs
		- Tax
- Report / Building Life Cycle Management 들은 Supporting Domain에 배치 하여 개발을 수행할 예정임.
- Notification / Authentication 등 비즈니스와 관련이 없는 부분은 Generic Domain 으로 배치하여 설계할 예정임.
- Meta/Finance는 모두 독립적으로 동작할 수 있어야 하며, 둘 간의 Data는 Evnet를 이용하여 통신을 수행하도록 함.
- Service Blueprint 등을 통하여 VSM의 추가에 따라 시스템도 유연하게 확장할 수 있도록 개발 Process 확립 예정

## Roadmap
### Stage I
- Spring Boot / DDD 기본적인 내용에 대한 정립
- DevOps Fundamental 구축 -> CICD 중심
- Unit Test / API Test 를 도입 

### Stage II
- Event Broker 도입을 이용하여 EDA를 구현하고 이를 통하여 시스템 확장의 기반을 마련함.
- CQRS를 도입 / Data Lake를 활용하여 분산된 데이터에 대한 활용의 기반을 마련함.
- DevOps FeedBack Loop 구성
