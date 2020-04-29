# HAS_Hide And Seek
![HAS_social](https://user-images.githubusercontent.com/50609368/80462249-65c5e800-8971-11ea-96d3-a71d8806b00d.png)

## 주제
자동 측위 및 식별 시스템 기반의 실내 위치추적 기술 개발

## 개요
* 자동 측위 및 식별 시스템 기반의 실내 위치추적 기술 개발
* 복잡한 내부 구조 및 시설물로 인해 GPS 정확도가 현저히 떨어지는 실내 환경에서 높은 정확도의 측위 기술 및 객체(예: 사람, 사물 등) 인식 기술을 개발한다. 
* 오픈소스 소프트웨어인 ns-3를 사용하여 시뮬레이션 환경에서 측위 알고리즘을 구현하고 알고리즘 성능을 개선한다. 라즈베리 파이를 이용해 실내 환경에서 높은 정확도의 측위 시스템을 구현한다. 또한, 카메라로 획득한 영상으로 객체를 인식하는 기술을 개발한다. 측위 및 객체 인식 결과를 결합하여, 객체의 동선을 실시간으로 추적하는 기술을 개발한다.
## 팀 구성
* 지도교수 : 김태운 교수님
* 홍연경 : 팀장/Raspberry Pi 실내 통신환경 구축 및 데이터 수집, 분석 
* 김윤하 : 예산관리/Raspberry Pi 실내 통신환경 구축 및 데이터 수집, 분석 
* 김진아 : NS-3 시뮬레이션 무선네트워크 환경 구축 및 데이터 수집, 분석
* 김보라 : 깃헙관리/NS-3 시뮬레이션 무선네트워크 환경 구축 및 데이터 수집, 분석
## 개발 목표
* 복잡한 내부 구조 및 시설물로 인해 GPS 정확도가 현저히 떨어지는 실내 환경에서 높은 정확도의 측위 기술 및 객체(예: 사람, 사물 등) 인식 기술을 개발. 
* 오픈소스 소프트웨어인 ns-3를 사용하여 시뮬레이션 환경에서 측위 알고리즘을 구현하고 알고리즘 성능을 개선.
* 라즈베리 파이를 이용해 실내 환경에서 높은 정확도의 측위 시스템을 구현.
 또한, 카메라로 획득한 영상으로 객체를 인식하는 기술을 개발.
 측위 및 객체 인식 결과를 결합하여, 객체의 동선을 실시간으로 추적하는 기술을 개발.
## 활용방안
* 분야 가리지 않고 실내라면 어디든지 설치가 가능.
* gps를 이용한 건물 내의 길 찾기 서비스
* 추적기를 이용한 현재 사용자의 위치추적
* 건물 내의 비상구를 쉽게 알 수 있는 긴급구조용 위치 서비스
* 실내 공간 정보 검색, 실내 로봇 응용, 실내 공간 관리, 실내 공간 기반 게임 등 실내 환경에 다양한 서비스를 제공

## RS-3
* RPi 단말기가 동일한 tx power로 데이터/신호를 전송하도록 설정
* 수신 단말기에서 received signal strength (RSS, 수신 신호 세기)를 측정
* 두 대의 RPi 장비는 일정간격으로(예: 1초) 상대방 단말기로 부터 전송한 신호의 RSS 신호를 저장하기 (파일로 저장) 
* 두개의 RPi 장비간 거리가 멀어짐에 따라 RSS 값이 작아지는 것을 확인
** 거리를 x축으로, 거리에 따른 RSS값을 y축으로 그래프 표현
> dbm 단위 ![rssDistance(dbm)](https://user-images.githubusercontent.com/50609368/80571044-e00c7000-8a36-11ea-9c33-d71d04f412e4.PNG)
> watt 단위 ![rssDistance(watt)](https://user-images.githubusercontent.com/50609368/80572171-c53afb00-8a38-11ea-914e-cb5d2567f4fc.PNG)




## RPi
* wavemon, iwconfig 등의 tool을 사용해서 RSS값 측정
> https://drive.google.com/file/d/18h2EYKPiQfDfjL27Fy-pDv_DGVKYsRgQ/view?usp=sharing
* 실내 환경에서 sender/receiver간 거리에 따른 RSS값 변화 측정
> https://drive.google.com/file/d/1dB44r0sZaxvjT3-pFy_2ttB63CJEOstQ/view?usp=sharing
* 위치측정을 위해 RPi를 AP 모드로 변경
> https://drive.google.com/file/d/1HiYkCAV3NG9jZy35zZtxu7XRE7Z6VtLh/view?usp=sharing



