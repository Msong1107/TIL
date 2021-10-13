## CloudFront

- 정적 및 동적 웹 콘텐츠를 사용자에게 더 빨리 배포하도록 지원하는 웹 서비스입니다.

#### 서비스
- AWS CloudFront
- AWS S3

## CDN (Contents Delivery Network) 이란?

콘텐츠를 효율적으로 전달하기 위해 여러 노드를 가진 네트워크에 데이터를 저장하여 제공하는 시스템을 말합니다. 인터넷 서비스 제공자에 직접 연결되어 데이터를 전송하므로, 콘텐츠 병목을 피할 수 있는 장점이 있습니다.
- AWS CloudFront도 CDN의 일종이라고 생각하시면 됩니다.
![제목 없음-1](https://user-images.githubusercontent.com/84947346/137123623-01d69df5-45e4-4132-84ba-4211dd05f7e5.png)

## CloudFront 구성

* Origin Server
  - 원본 데이터를 가지고 있는 서버입니다.
  - AWS에서는 S3, EC2 instance를 나타냅니다.

* Edge Server
  - AWS 에서 실질적으로 제공하는 전 세계에 퍼져있는 서버입니다.
  - Edge Server에는 요청 받은 데이터에 대해서 빠르게 응답해주기 위해 캐싱 기능을 제공합니다.
