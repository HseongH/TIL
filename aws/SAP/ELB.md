# ELB

## 1. 애플리케이션에 적절한 로드 밸런서 선택하기

ELB는 Application Load Balancer(ALB), Network Load Balancer(NLB), Classic Load Balancer(CLB), Gateway Load Balancer(GLB) 총 4가지 유형의 로드 밸런서를 지원합니다.

HTTP 요청을 로드 밸런싱해야 하는 경우 ALB를 사용하는 것이 좋고 네트워크/전송 프로토콜(4계층 - TCP, UDP) 로드 밸런싱의 경우와 고도의 성능이 요구되거나 대기 시간이 낮아야 하는 애플리케이션의 경우 NLB를 선택하는 것이 좋습니다. 애플리케이션이 Amazon Elastic Compute Cloud(Amazon EC2) Classic 네트워크 안에 구축된 경우 CLB를 사용해야 합니다. 서드 파티 가상 어플라이언스를 배포하고 실행해야 하는 경우 GLB를 사용할 수 있습니다.
