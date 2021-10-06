# Docker란 무엇인가?
![DockerLogo](./img/211002_WhatIsDocker.png ':size=200')
- 컨테이너 기반의 오픈소스 가상화 플랫폼

- 도커가 등장하고 서버관리/개발 방식이 완전히 바뀌게 됨

#### 전통적인 서버 관리 방식
![DockerLogo](./img/211002_WhatIsDocker_2.png ':size=800')
- 위 그림과 같이 복잡한 과정이 일반적, 한땀 한땀 직접 했어야함

#### 자원 격리
- 프로세스/파일/디렉토리 → 가상으로 분리

- CPU, Memory I/O → 그룹별로 제한

- Linux 기능을 이용한 빠르고 효율적인 서버 관리

- 하지만, 기술이 너무 어려움 (Google 같은 곳에서는 이미 사용중)

#### Docker 등장 후
![DockerLogo](./img/211002_WhatIsDocker_3.png ':size=800')
- 모든게 컨테이너로 추상화가 됨<br>
(어떠한 프로그램도 컨테이너로 만들 수 있음)

- 컨테이너를 만들어두면 어디서든 돌아감

#### 가상머신(VM) vs Docker
- 반은 맞고 반은 틀림

- 가상머신처럼 독립적으로 실행되지만 가상머신보다 **쉽고 빠르고 효율적**

- VM은 아래 그림과 같이 O/S가 추가되어 overhead 발생 → 성능 Loss가 심함

![DockerLogo](./img/211002_WhatIsDocker_4.png ':size=800')

#### Docker의 특징
1. **확장성/이식성**<br>
  . Docker가 설치되어 있다면 어디서든 컨테이너를 실행할 수 있음<br>
  . 특정 회사나 서비스에 종속적이지 않음<br>
  . 쉽게 개발서버를 만들 수 있고 테스트 서버 생성도 간편

1. **표준성**<br>
  . ruby, node.js, go, php등으로 만든 서비스들의 배포 방식을 서로 상이<br>
  . Docker는 컨테이너라는 표준으로 서버 배포하므로 모든 서비스들의 배포과정이 동일해짐

1. **이미지**<br>
  . 컨테이너를 실행하기 위한 압축 파일<br>
  . 이미지에서 컨테이너를 생성하기 때문에 반드시 이미지를 만드는 과정이 필요<br>
  . Dockerfile을 이용하여 이미지를 만들고 처음부터 재현 가능<br>
  . 빌드 서버에서 이미지를 만들면 해당 이미지를 이미지 저장소에 저장하고 운영서버에서 이미지를 불러옴

1. **설정관리**<br>
  . 설정은 보통 환경변수로 제어<br>
  . MYSQL_PASS=password와 같이 컨테이너를 띄울때 환경변수를 같이 지정<br>
  . 하나의 이미지가 환경변수에 따라 동적으로 설정파일을 생성하도록 만들어져야함

1. **자원관리**<br>
  . 컨테이너는 삭제 후 새로 만들면 모든 데이터가 초기화됨<br>
  . 업로드 파일을 외부 스토리지와 링크하여 사용하거나 S3같은 별도의 저장소가 필요<br>
  . 세션이나 캐시를 memcached나 redis와 같은 외부로 분리

#### Docker가 가져온 변화
- 클라우드 이미지보다 관리하기 쉬움

- 다른 프로세스와 격리되어 가상머신처럼 사용하지만 성능저하 (거의) 없음

- 복잡한 기술을 몰라도 사용할 수 있음

- 이미지 빌드 기록이 남음

- 코드와 섲렁으로 관리 → 재현 및 수정 가능

- 오픈 소스 → 특정 회사 기술에 종속적이지 않음

#### 컨테이너의 미래
- kubernetes → 서버 관리의 대세가 되어가는 중<br>
  . 여러대의 서버와 여러개의 서비스를 관리하기 쉽게 해줌

1. **스케줄링**<br>
  . 컨테이너를 적당한 서버에 배포해 주는 작업<br>
  . 여러 대의 서버 중 가장 할일 없는 서버에 배포하거나 그냥 차례대로 배포 또는 아예 랜덤하게 배포<br>
  . 컨테이너 개수를 여러 개로 늘리면 적당히 나눠서 배포하고 서버가 죽으면 실행 중이던 컨테이너를 다른 서버에 띄워줌

1. **클러스터링**<br>
  . 여러 개의 서버를 하나의 서버처럼 사용<br>
  . 작게는 몇 개 안되는 서버부터 많게는 수천 대의 서버를 하나의 클러스터로<br>
  . 여기저기 흩어져 있는 컨테이너도 가상 네트워크를 이용하여 마치 같은 서버에 있는 것처럼 쉽게 통신

1. **서비스 디스커버리**<br>
  . 서비스를 찾아주는 기능<br>
  . 클러스터 환경에서 컨테이너는 어느 서버에 생성될지 알 수 없고 다른 서버로 이동 할 수도 있음<br>
  . 따라서 컨테이너와 통신을 하기 위해서 어느 서버에서 실행중인지 알아야하고 컨테이너가 생성되고 중지될 때 어딘가에 IP와 Port같은 정보를 업데이트해줘야함<br>
  . Key-Value 스토리제에 정보를 저장할 수도 있고 내부 DNS 서버를 이용