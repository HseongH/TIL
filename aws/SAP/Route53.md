# Route 53

## 1. alias record

Amazon Route 53 별칭 레코드는 DNS 기능에 Route 53 고유의 확장을 제공합니다. 별칭 레코드를 사용하면 CloudFront 배포와 Amazon S3 버킷 등 선택한 AWS 리소스로 트래픽을 라우팅할 수 있습니다. 호스팅 영역의 한 레코드에서 다른 레코드로 트래픽을 라우팅할 수도 있습니다.

별칭 레코드를 사용하여 AWS 리소스로 트래픽을 라우팅하면 Route 53이 리소스의 변경 내용을 자동으로 인식합니다. 예를 들어, example.com의 별칭 레코드가 lb1-1234.us-east-2.elb-amazonaws.com의 ELB 로드 밸런서를 가리킨다고 가정합니다. 로드 밸런서의 IP 주소가 변경된다면, Route 53은 자동적으로 새로운 IP 주소를 사용하여 DNS 쿼리에 응답하기 시작합니다.
