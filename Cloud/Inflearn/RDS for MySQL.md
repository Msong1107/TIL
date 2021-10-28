## RDS for MySQL 생성하기

#### 1. 아키텍처로 구현할 기술
- 완전 관리형 MySQL 데이터 베이스를 구성하고 Linux 기반의 가상 서버에서 MySQL 클라이언트로 연결합니다.


####  필요 AWS 서비스
- Amazon Relational Database Service(RDS)

#### RDS 란?
- AWS 클라우드에서 관계형 데이터베이스를 더 쉽게 설치, 운영 및 확장할 수 있는 웹 서비스입니다.


## 실습 해보기

#### 검색하여 RDS 들어간다 왼쪽 데이터베이스 -> 데이터베이스 생성 누른다


![image](https://user-images.githubusercontent.com/84947346/139198280-b9b8cb7e-ecac-4a61-a893-95f97f449ff6.png)


#### 표준 생성을 선택하고 엔진 유형은 MySQL로 한다


![image](https://user-images.githubusercontent.com/84947346/139198604-7c4ffa24-5919-4d01-9b8b-59beef447f94.png)


#### 템플릿은 개발/테스트를 선택하고 마스터 암호를 생성해줍니다.


![image](https://user-images.githubusercontent.com/84947346/139198924-7b5e0b56-d412-4687-838b-2df6b7c24d79.png)


#### 인스턴스 클래스는 버스터블 로 선택해줍니다.


![image](https://user-images.githubusercontent.com/84947346/139199051-5214664d-32a7-477f-b843-3e07fadc3b96.png)


#### Virtual Private Cloud(VPC) 는 lab VPC를 선택! 그리고 보완 그룹은 default 가용영역은 2a 또는 1a로 선택


![image](https://user-images.githubusercontent.com/84947346/139206425-d64f4e97-e160-47d5-8d5e-1a79d2f7db5a.png)

#### 이름은 샘플 smaple 자동백업 체크해제  데이터 베이스 생성!!

![image](https://user-images.githubusercontent.com/84947346/139206710-6c274364-6eda-4a92-b3fd-ec27128da7b0.png)

#### 생성 완료


## 보안그룹 설정

#### EC2 를 들어가고 보안 그룹을 들어간다 보안그룹 생성!

#### lab-web-rds-mysql-sg 라고 이름을 설정해준다 그리고 vpc를 선택해줍니다

#### 타입 mysql를 선택하고 0.0.0.0/0 전체 공개로 한다
![image](https://user-images.githubusercontent.com/84947346/139207887-575d8321-9fa1-4735-8057-f7a96373ab94.png)


#### Rds 에들어가서 아까 만든 데이터베이스를  수정을 눌러서 기존 기존 VPC 보안 그룹 만들걸로 바꾸어줘요

![image](https://user-images.githubusercontent.com/84947346/139208433-161f56b6-3d68-415d-a70f-31c0a81c6d62.png)

## RDS 설정 끝!😆
