
## 📌 VPC(Virtual Private Cloud)의 개념
- vpc는 사용자가 정의하는 가상의 네트워크입니다.</br>
- vpc를 통해 속하는 네트워크를 구분하여 각 알맞는 설정을 부여합니다.
</br>

## VPC 적용 전

VPC 없이 인스턴스를 생성한다면 아래 같이 인스턴스끼리의 구분없는 연결로 인해 시스템 복잡도가 증가할것입니다.

![image](https://user-images.githubusercontent.com/84947346/136943747-87d48cfb-2518-4947-9289-c65d240d2dc6.png)

## VPC 적용 후
vpc를 적용하면 인스턴스가 vpc 속함으로써 네트워크를 구분할 수 있고 vpc 별도 필요한 설정을 통해 인스턴스에 네트워크 설정을 적용 할수 있어요.

![image](https://user-images.githubusercontent.com/84947346/136944597-387aaaac-f5ac-4777-bc16-fb107f706e52.png)

## 📌 VPC 구성요소 및 구축 과정

### VPC

VPC는 독립된 하나의 네트워크를 구성하기 위한 가장 큰 단위입니다. 각 region에 종속되며 RFC1918이라는 사설 IP 대역에 맞추어 설계해야 해야하며 VPC에서 사용하는 사설 IP 대역은 아래와 같습니다.

 

1️⃣ 10.0.0.0 ~ 10.255.255.255(10/8 prefix)

2️⃣ 172.16.0.0 ~ 172.31.255.255(182.16/12 prefix)

3️⃣ 192.168.0.0 ~ 192.168.255.255(192.168/16 prefix)

</br>


### Subnet(서브넷)

서브넷은 vpc의 IP주소를 나누어 리소스가 배치되는 물리적인 주소 범위를 뜻해요.vpc를 잘게 나눈 것이 서브넷이기 때문에 VPC를 잘게 나눈 것이 서브넷이기 때문에 VPC보다 대역폭이 낮으며 하나의 AZ(Availability Zone)에 하나의 서브넷이 연결되기 때문에 region의 AZ 수를 미리 확인하고 설정해야합니다.
</br>

![image](https://user-images.githubusercontent.com/84947346/136946281-827fe14f-ff86-4df0-b3b8-064563799a39.png)

</br>

### Router(라우터)

- 라우터는 VPC 안에서 발생한 네트워크 요청을 처리하기 위해 어디로 트래픽을 전송해야 하는지 알려주는 표지판 역할을 수행합니다. 
- 각각의 서브넷은 네트워크 트래픽 전달 규칙에 해당하는 라우팅 테이블을 가지고 있으며 요청이 발생하면 가장 먼저 라우터로 트래픽을 전송합니다.
</br>

![image](https://user-images.githubusercontent.com/84947346/136946447-89ebd606-afdd-4502-8616-2c4ce3125ace.png)


### NAT Gateway(NAT 게이트웨이)

- 트래픽을 public subnet에 속한 인스턴스에 전송해서 인터넷과 통신을 해야 합니다.
- private subent에서 발생하는 네트워크 요청이 VPC 내부의 주소를 목적지로 하는 것이 아니라면 public subnet에 존재하는 NAT로 트래픽을 전송합니다.
- 트래픽을 받은 NAT는 public subnet의 라우팅 규칙에 따라 처리함으로써 private subnet이 인터넷과 통신할 수 있도록 합니다.
</br>

![image](https://user-images.githubusercontent.com/84947346/136947968-b0bb22fd-f026-4020-bb03-d6842802d567.png)

