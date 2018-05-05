## 소개
### EC2 Container Service에 배포된 자바 마이크로서비스


컨테이너는 OS 가상화의 방법으로 당신이 독립적인(resource-isolated) 환경에서 애플리케이션과 그 의존관계에 있는 것들을 실행할 수 있게 해줍니다. 컨테이너는 애플리케이션의 코드, 설정, 의존성들을 쉽게 패키징 할수 있게 해주며 그를 통해 환경적인 일관성, 운영에서의 효율성, 개발자의 생산성 그리고 버전관리를 제공하는 구성 요소들을 쉽게 사용할 수 있습니다. 컨테이너는 배포 환경에 관계없이 앱이 빠르고, 신뢰할 수 있고, 일관성있게 배포되는 것을 보장합니다. 컨테이너는 또한 리소스에 대한 세분화된 제어를 제공함으로써 당신의 인프라스트럭쳐를 효율성을 개선할 수 있습니다.


하나의 서버에 하나의 컨테이너를 실행하는 것은 쉽습니다. ECS는 클러스터 관리 서비스로 당신이 GUI 또는 CLI를 통해서 클러스터 그룹을 관리하는 것을 도와줍니다. ECS를 통해 당신은 당신의 클러스터 관리 인프라를 설치하고 운영하고 규모를 조정할 수 있습니다. 간단한 API 요청를 통해 당신은 도커로 되어있는 애플리케이션을 실행하고 멈출수 있고, 당신의 클러스터의 완료 상태를 조회할 수 있고, `보안 그룹(security group)`, `ELB`, `EBS volumes` 그리고 `IAM roles`과 같은 익숙한 기능들에 접근할 수 있습니다. 아마존 ECS를 사용하여 당신은 자원 요구사항과 가용성 요구사항에 기초해 당신의 클러스터에 컨테이너의 배치를 예약할 수 있습니다. 또한 비즈니스와 애플리케이션의 특별한 요구사항을 만족하기 위해서 자체 스케줄러 또는 타사 스크케줄러를 통합할 수 있습니다.


이 예제는 컨테이너도 아니고 오케스트레이션도 없이 인스턴스에 직접 배포된 단일 자바 애플리케이션이 ECS를 사용하여 오케스트레이션된 컨테이너 마이크로 서비스 아키텍처로 발전하는 모습을 보여줍니다.


이 예제에서는 [Spring Pet Clinic](https://github.com/spring-projects/spring-petclinic)을 기본으로 시작하여 고수준의 아키텍처로 확장합니다.
이 앱의 고수준 아키텍처는 다음과 같습니다.
![alt text](https://github.com/awslabs/amazon-ecs-java-microservices/blob/master/images/PetClinicApp.png)

그럼 시작해봅시다.

1. [파트 1: 기존의 자바 스프링 앱을 ECS로 배포된 컨테이너로 변경하기](https://github.com/awslabs/aws-java-microservice-refarch/blob/master/1_ECS_Java_Spring_PetClinic)
2. [파트 2: ECS에서 단일 애플리케이션을 마이크로서비스로 쪼개기](https://github.com/awslabs/aws-java-microservice-refarch/tree/master/2_ECS_Java_Spring_PetClinic_Microservices)
3. [파트 3: 지속적 통합과 지속적 배포 구축](https://github.com/awslabs/aws-java-microservice-refarch/tree/master/3_ECS_Java_Spring_PetClinic_CICD)

## 사전에 필요한 것들

배포 스크립트를 작성하기 전에 최신 버전의 AWS CLI와 maven이 필요합니다. 이 컴포넌트들을 설치할때 도움이 필요하다면 아래 링크를 참고하세요.

1. [AWS CLI 설치](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)
2. [Maven 설치](https://maven.apache.org/install.html)
3. [Docker 설치](https://docs.docker.com/engine/installation/)
4. [Python 설치](https://www.python.org/downloads/)
5. [JQ 설치](https://stedolan.github.io/jq/download/)
