# HAS_Hide And Seek
![HAS_social](https://user-images.githubusercontent.com/50609368/80462249-65c5e800-8971-11ea-96d3-a71d8806b00d.png)

## 주제
자동 측위 및 식별 시스템 기반의 실내 위치추적 기술 개발

## 개요
* ns-3 시뮬레이터와 라즈베리파이를 통해 실내 위치 추적 기술을 개발한다. 최종 목표는 한림대학교 공학관의 실내 위치 추적을 하는 것으로, 최종 구현 결과물의 정확도와 안정성을 높이기 위해 RSS(Received Signal Strength)기반의 fingerprint 기법을 이용한다.

## 팀 구성
* 지도교수 : 김태운 교수님
* 홍연경 : 팀장/Raspberry Pi 실내 통신환경 구축 / GUI 프로그램 구현 
* 김윤하 : 예산관리/Raspberry Pi 실내 통신환경 구축 및 데이터 수집, 분석
* 김진아 : NS-3 시뮬레이션 무선네트워크 환경 구축 및 데이터 수집, 분석 / fingerfrint 구현
* 김보라 : 깃헙관리/NS-3 시뮬레이션 무선네트워크 환경 데이터 분석 / 삼변측량 구현

## 개발 목표
* 자동 측위 및 식별 시스템 기반의 실내 위치추적 기술 개발한다.
* 복잡한 내부 구조 및 시설물로 인해 GPS 정확도가 현저히 떨어지는 실내 환경에서 높은 정확도의 측위 기술 및 객체(예: 사람, 사물 등) 인식 기술을 개발한다. 
* 오픈소스 소프트웨어인 ns-3를 사용하여 시뮬레이션 환경에서 측위 알고리즘을 구현하고 알고리즘 성능을 개선한다. 
* 라즈베리 파이를 이용해 실내 환경에서 높은 정확도의 측위 시스템을 구현한다. 
* 객체의 위치를 실시간으로 나타내는 GUI프로그램을 개발한다.

## 활용방안
* 구현한 공학관 위치추적 프로그램은 강의실 찾기 서비스 /전자출결 출석 후 수업 미참여(일명 출튀) 학생 구분 서비스 등에 활용 가능
* gps를 이용한 건물 내의 길 찾기 서비스
* 건물 내의 비상구를 쉽게 알 수 있는 긴급구조용 위치 서비스
* 실내 공간 정보 검색, 실내 로봇 응용, 실내 공간 관리, 실내 공간 기반 게임 등 실내 환경에 다양한 서비스를 제공

## 프로그램 구성도
![구성도](https://user-images.githubusercontent.com/50609368/85051035-f41c5480-b1d1-11ea-8872-4e49ee882dfe.PNG)

## NS-3
1. [NS-3 설치 설명서](https://drive.google.com/file/d/115PVnxi2bxedmq_MLoXg6lGM1okgEvpK/view?usp=sharing)
2. 거리에 따른 RSS 수집
 * RPi 단말기가 동일한 tx power로 데이터/신호를 전송하도록 설정
 * 수신 단말기에서 received signal strength (RSS, 수신 신호 세기)를 측정
 * 두 대의 RPi 장비는 일정간격으로(예: 1초) 상대방 단말기로 부터 전송한 신호의 RSS 신호를 저장
 * 두개의 RPi 장비간 거리가 멀어짐에 따라 RSS 값이 작아지는 것을 확인
 * 거리를 x축으로, 거리에 따른 RSS값을 y축으로 그래프 표현
![rssDistance(dbm)](https://user-images.githubusercontent.com/50609368/80571044-e00c7000-8a36-11ea-9c33-d71d04f412e4.PNG)
![rssDistance(watt)](https://user-images.githubusercontent.com/50609368/80572171-c53afb00-8a38-11ea-914e-cb5d2567f4fc.PNG)
3. Scenario-1
 * 사각형 영역. 각각의 모서리에 1개의 노드 배치. 화면 중앙에 노드 1개 배치
 * 5개의 노드가 모두 주기적으로 broadcasting
 * 하나의 노드가 broadcasting 하면, 다른 4개 노드는 해당 노드의 ID값 (id, ip, mac 등, 해당 노드를 유일하게 구분할 수 있는 어떤 데이터든 관계 없음) 및 RSS값을 log/trace에 기록
4. Scenario-2
 * 화면 중앙에 있는 노드를 이동, 이 외의 조건은 Scenario-1과 동일
5. 결과
 * NS-3를 통해 fingerprint를 통한 위치 추적이 가능함을 확인

## RPi
* [wavemon, iwconfig 등의 tool을 사용해서 RSS값 측정](https://drive.google.com/file/d/18h2EYKPiQfDfjL27Fy-pDv_DGVKYsRgQ/view?usp=sharing)
* [실내 환경에서 sender/receiver간 거리에 따른 RSS값 변화 측정](https://drive.google.com/file/d/1dB44r0sZaxvjT3-pFy_2ttB63CJEOstQ/view?usp=sharing)
 ![거리에 따른 RSS값 변화 그래프](https://user-images.githubusercontent.com/50609368/85047878-676f9780-b1cd-11ea-8686-10469f88c880.PNG)
* [위치측정을 위해 RPi를 AP 모드로 변경](https://drive.google.com/file/d/1HiYkCAV3NG9jZy35zZtxu7XRE7Z6VtLh/view?usp=sharing)

## 실내 위치 측정 기법
* 삼변측량
> 삼각측량과 이름이 비슷하지만, 삼각측량은 거리와 각도를 가지고 위치를 추적하고, 삼변측량은 거리만 가지고 위치 추적. 3개 이상의 신호발생기에서 발생하는 신호강도(rss)를 이용하여 각각의 신호발생기 교차범위의 위치가 사용자의 위치라는 이론. fingerprint에 비해 정확한 위치 측정 가능하지만, ap위치가 변하거나 지형지물에 따라 신호강도가 달라져 예외사항이 발생한다.

* fingerprint
> 사전에 격자형태로 신호세기를 저장한 뒤, 사용자가 자신주변의 신호를 모아 위치를 요청하면 서버는 기록된 신호세기와 요청 신호세기를 비교하여 위치를 측정하는 형태. fingerprint를 수행하기위해서는  사전수집단계, 측위단계 2단계 필요. 사전수집단계에서 데이터 미리 측정해야 한다는 점과 실내환경이 변경되면 전파맵의 보정이 필요하다는 점이 특징이다.

 ## GUI 사용 공학관 map
![map](https://user-images.githubusercontent.com/50609368/85044706-f9c16c80-b1c8-11ea-8718-a4dd6d3eb750.png)

## 사용환경
![개발도구](https://user-images.githubusercontent.com/50609368/85049672-fe3d5380-b1cf-11ea-8e1e-16ac164875c6.PNG)
 
 ## 회의록
 * [2020-1학기 캡스톤디자인 200317 회의록](https://drive.google.com/file/d/18ute8Sk0x_bHUOz7mdzSNhEgZ52nLWls/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200324 회의록](https://drive.google.com/file/d/1zDEydlisIfj0WCvA-W77H4ijMMDAw5e7/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200331 회의록](https://drive.google.com/file/d/15oF0xEkqqlKzznCChwq66feqiK9S26tS/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200407 회의록](https://drive.google.com/file/d/19yURt9eabhi2oRWYOXDplFDTgC1e-nip/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200414 회의록](https://drive.google.com/file/d/1tJ-4pPjRItMvVlCovkR7KeBeXz2obJSu/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200421 회의록](https://drive.google.com/file/d/1ahfUIlp6Wn95fFzrZXbw-HZ7V-MkfEwQ/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200428 회의록](https://drive.google.com/file/d/1PnQCxsvJLDd7R9Vzn6pvhagP0IxTOf-d/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200512 회의록](https://drive.google.com/file/d/1tFszON3l0FZqbq4PcgkeHNDcu8kwllhQ/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200519 회의록](https://drive.google.com/file/d/1prEXLQ_5slSAFTah8wYXbpZJWsySlt4y/view?usp=sharing)
 * [2020-1학기 캡스톤디자인 200602 회의록](https://drive.google.com/file/d/1J-jgfdsKsWC9NX6BENrY0Ix8coHTf_yZ/view?usp=sharing)
