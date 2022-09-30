# 인스턴스 생성 과정

aws educate cloud 101 실습 내용

## 1. EC2 인스턴스 시작

### 1. EC2 인스턴스 이름 지정

- 하나의 EC2 인스턴스는 컴퓨터 한 대를 의미한다.
- 태그를 사용하면 용도, 소유자 또는 환경을 기준으로 하는 등 AWS 리소스를 다양한 방식으로 분류할 수 있음 -> 리소스가 많을 때 범주화가 유용

### 2. Amazon Machine Image(AMI) 선택

- AMI는 클라우드의 가상 서버인 인스턴스를 시작하는 데 필요한 정보를 제공

* 인스턴스 루트 볼륨에 대한 템플릿(예: 애플리케이션을 포함한 운영 체제 또는 애플리케이션 서버)
* 어떤 AWS 계정이 해당 AMI를 사용하여 인스턴스를 시작할 수 있는지 제어하는 시작 권한
* 인스턴스 시작 시 인스턴스에 연결할 볼륨을 지정하는 블록 디바이스 매핑

### 3. 인스턴스 유형 선택

<img width="515" alt="image" src="https://user-images.githubusercontent.com/58503875/193017058-bf4c4322-ad08-4375-be35-07a5c7bdf71b.png">

- 인스턴스 유형은 CPU, 메모리, 스토리지 및 네트워킹 용량의 다양한 조합으로 구성됨
- 각 인스턴스 유형은 하나 이상의 인스턴스 크기를 포함하고 있어 대상 워크로드의 요구 사항에 따라 리소스의 크기를 조정할 수 있음

### 4. 키 페어 구성

- Amazon EC2는 퍼블릭 키 암호화 기법을 사용하여 로그인 정보를 암호화하고 복호화한- 인스턴스에 로그인하려면 키 페어를 만들고, 인스턴스를 실행할 때 키 페어의 이름을 지정하고, 인스턴스에 연결할 때 프라이빗 키를 제공해야 함

### 5. 네트워크 설정 구성

<img width="717" alt="image" src="https://user-images.githubusercontent.com/58503875/193017206-92792ce6-788f-4dbb-b4a2-0877affa35a4.png">

- **Virtual Private Cloud(VPC)** 
  - 인스턴스를 시작할 VPC를 나타냄
  - 개발, 테스트 및 프로덕션을 위한 서로 다른 VPC를 포함하여 여러 개의 VPC를 사용할 수 있음
- **보안 그룹**
  - 하나 이상의 인스턴스에 대한 트래픽을 제어하는 가상 방화벽 역할을 함
  - 인스턴스를 시작할 때 하나 이상의 보안 그룹을 인스턴스와 연결
  - 연결된 인스턴스와 트래픽을 주고받을 수 있게 하는 규칙을 각 보안 그룹에 추가하여 언제든지 보안 그룹에 대한 규칙을 수정할 수 있다

### 6. 스토리지 추가

<img width="513" alt="image" src="https://user-images.githubusercontent.com/58503875/193017284-09f8162d-810b-4435-8b03-e7b6f6040369.png">

- Amazon EC2는 Amazon Elastic Block Store(Amazon EBS)라는 네트워크 연결 가상 디스크에 데이터를 저장
- 캡쳐화면 -> 8GiB 디스크 볼륨을 사용하여 EC2 인스턴스 시작 -> 루트 볼륨

### 7. 고급 세부 정보 구성

- 인스턴스 종료 기능 활성화

<img width="577" alt="image" src="https://user-images.githubusercontent.com/58503875/193017557-cd06a2ce-e43b-437f-a142-073977a8d79b.png">

- 인스턴스를 시작할 때 사용자 데이터를 인스턴스에 전달하는 옵션 추가
  - 자동화 구성 작업을 수행하는 데 사용
  - 인스턴스가 시작된 후 스크립트 실행 



### 8. EC2 인스턴스 시작

<img width="1131" alt="image" src="https://user-images.githubusercontent.com/58503875/193019696-a77002f2-df81-4a63-b80b-1f3d07c3b534.png">




## 2. 인스턴스 모니터링

### **상태검사 탭**

<img width="1147" alt="image" src="https://user-images.githubusercontent.com/58503875/193019763-297cf1d0-7372-44b9-b25b-19552b560fc2.png">

- 애플리케이션이 실행되지 못하도록 막는 문제를 감지했는지 빠르게 확인 가능
- EC2에서는 자동 검사를 수행하여 하드웨어 및 소프트웨어 문제를 파악



### **모니터링 탭**

<img width="1159" alt="image" src="https://user-images.githubusercontent.com/58503875/193019989-7fa47d79-31a9-405c-ac8a-8fd01cc4ba6a.png">

- Aamazon ColudWatch 지표가 표시됨
  - EC2는 지표를 EC2 인스턴스에 대한 Amazon ColudWatch로 전송



### **시스템 로그 가져오기**

<img width="467" alt="image" src="https://user-images.githubusercontent.com/58503875/193166187-521cc07a-fc47-41f0-9264-5dc214f12b30.png">



- 인스턴스의 콘솔 출력이 표시됨

  <img width="773" alt="image" src="https://user-images.githubusercontent.com/58503875/193020460-d4549c77-958f-4a1a-97fe-e98b87eef95c.png">



### **인스턴스 스크린샷 가져오기**
<img width="504" alt="image" src="https://user-images.githubusercontent.com/58503875/193166271-297684de-eb7c-4b4c-b770-47287db27bac.png">

## 3. 보안 그룹 업데이트 및 웹 서버 액세스

### 포트 80에서 웹 트래픽 허용

