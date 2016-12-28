Preparation
===========

Components
----------

Turtlebot is divided into Basic model and Premium model according to the components as shown in the table below. The biggest difference is the type of motor used and the configuration of SBC and Sensor.

+------------+--------------------------+--------+---------+
|            |                          | Basic  | Premium |
+============+==========================+========+=========+
|            | item                     | number | number  |
+------------+--------------------------+--------+---------+
|            | Waffle-plate             | 8      | 24      |
+            +--------------------------+--------+---------+
|            | Plate-support            | 10     | 20      |
+            +--------------------------+--------+---------+
|            | Board-support            | 10     | 10      |
+            +--------------------------+--------+---------+
|            | Wheel                    | 2      | 2       |
+            +--------------------------+--------+---------+
| Frame      | Rubber tire              | 2      | 2       |
+            +--------------------------+--------+---------+
| Wheel      | Ball caster              | 1      | 2       |
+            +--------------------------+--------+---------+
|            | Bolt and nut set         | 1      | 1       |
+            +--------------------------+--------+---------+
|            | Dream plate 5x5 K        | 1      | 1       |
+            +--------------------------+--------+---------+
|            | Dream L-bracket 2P K     | 1      | 1       |
+            +--------------------------+--------+---------+
|            | Rivet set                | 10     | 10      |
+------------+--------------------------+--------+---------+
|            | XL430-W350-T             | 2      | x       |
+            +--------------------------+--------+---------+
|            | Horn for XL430           | 2      | x       |
+ Motor      +--------------------------+--------+---------+
|            | XM430-W350-T             | x      | 2       |
+            +--------------------------+--------+---------+
|            | Horn for XM430           | x      | 2       |
+------------+--------------------------+--------+---------+
| Controller | OpenCR                   | 1      | 1       |
+------------+--------------------------+--------+---------+
|            | SMPS 12V 5A              | 1      | 1       |
+            +--------------------------+--------+---------+
|            | LIPO 11.1V 1800mAh       | 1      | 1       |
+            +--------------------------+--------+---------+
| Power      | Battery conversion cable | 1      | 1       |
+            +--------------------------+--------+---------+
| Battery    | Velcro                   | 2      | 2       |
+            +--------------------------+--------+---------+
| Cable      | Robot Cable-X3P 180mm    | 2      | 2       |
+            +--------------------------+--------+---------+
|            | Robot Cable-X3P 240mm    | x      | 2       |
+            +--------------------------+--------+---------+
|            | LIPO Battery Charger     | 1      | 1       |
+            +--------------------------+--------+---------+
|            | MicroUSB cable           | 1      | 1       |
+            +--------------------------+--------+---------+
|            | SBC power cable          | 1      | 1       |
+------------+--------------------------+--------+---------+
|            | RaspberryPi 3            | 1      | x       |
+ SBC        +--------------------------+--------+---------+
|            | Intel Joule              | x      | 1       |
+------------+--------------------------+--------+---------+
|            | Laser Distance Sensor    | 1      | 1       |
+ Sensor     +--------------------------+--------+---------+
|            | Intel Realsense R200/400 | x      | 1       |
+------------+--------------------------+--------+---------+

Assembly
--------

Turtlebots are delivered in a single package, not each assembly. In order for the user to use TurtleBot, it is necessary to assemble according to the following procedure.

Basic model
~~~~~~~~~~~

(comming soon)

Premium model
~~~~~~~~~~~~~

(comming soon)

Configuring your environment
----------------------------

OpenCR
~~~~~~

OpenCR 아두이노 개발 환경을 구축해 보자.

1. USB 관련 설정
''''''''''''''

root 권한없이 OpenCR USB 포트를 Arduino IDE에서 사용할 수 있게한다.

.. code:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules

2. Arduino IDE 설치
''''''''''''''''''

아래와 같이 arduino 공식 사이트에서 최신 버전의 아두이노 IDE를 다운로드하여 설치하자. 현재 1.16.0 이상의 버전에서 OpenCR 은 구동되는 것이 확인 되었다.

https://www.arduino.cc/en/Main/Software

설치시에는 원하는 폴더에 다운로드 받은 압축 파일을 풀고, 터미널 창에서 다음과 같이 설치 파일을 실행하면 된다. 참고로 아래의 예제는 Arduino IDE 가 유저 최 상위 폴더(~/)의 tools 라는 폴더에 있을 경우이다.

$ cd ~/tools/arduino-1.6.12
$ ./install.sh

끝으로 아래와 같이 bashrc 파일에 위에서 설치한 Arduino IDE 위치를 PATH 라는 절대 경로 설정에 포함시켜 주자. gedit 편집기(유저가 편한 편집기로 설정해도 된다.)로 bashrc 에 다음 경로를 추가하고 source 명령어로 변경된 사항을 반영 시켜주자.

gedit ~/.bashrc
export PATH=$PATH:$HOME/tools/arduino-1.6.12
source ~/.bashrc

3. Arduino IDE 실행
''''''''''''''''''

Arduino IDE를 리눅스에서 구동할 때는 아래와 같이 arduino 실행 명령어로 구동하도록 하자.

$ arduino

4. OpenCR 보드 설정
'''''''''''''''''

1) 환경 설정

위에서 설치한 Arduino IDE를 실행(터미널 창에서 arduino 입력)하고 IDE의 상단 메뉴에서 [File] --> [Preferences] 를 클릭한다. Preferences 화면이 뜨면 [Additional Boards Manager URLs] 항목에 다음 링크를 복사해서 붙여 넣는다.

https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json

2) Boards Manager 를 통한 OpenCR 패키지 설치

[Tools] --> [Board] --> [Boards Manager] 를 실행한다.

하단에 위치되어 있는 [OpenCR by ROBOTIS] 의 부분을 클릭하면 [Install] 버튼이 활성화 된다. 이를 클릭하여 OpenCR 패키지를 설치하도록 하자.

설치가 완료되면 다음과 같이 "INSTALLED" 라는 문구를 확인할 수 있다.

다시 [Tools] --> [Board] 의 목록을 보면 하단에 [OpenCR Board] 라는 항목이 추가 되었음을 확인할 수 있다. 이를 클릭하여 보드를 지정해주도록 하자.

3) Port 설정

Arduino IDE 에서 작업한 프로그램을 OpenCR에 라이팅하기 위한 포트 설정을 한다. 이 작업을 위해서는 OpenCR에 전원이 PC와 OpenCR이 USB로 연결되어 있어야 한다.

[Tools] --> [Port] --> [/dev/ttyACM0] 를 선택한다.
(* PC 에 접속된 환경에 따라서 /dev/ttyACM0 값은 다를 수 있다.)

6. modemmanager 삭제
'''''''''''''''''''

Arduino IDE에서 프로그래밍한 후 OpenCR에 프로그램을 다운로드 하면 OpenCR이 재시작되는데 이때에 OpenCR과 USB이 다시 접속된다. 이때에 리눅스의 modem 관련 패키지가 이를 관장하는데 AT 명령어를 보내게 된다. 이는 OpenCR의 접속 오류를 나타내기 때문에 관련 패키지를 삭제해줘야 한다. 다음과 같이 modemmanager를 삭제하도록 하자.

sudo apt-get purge modemmanager


7. 부트로더 라이팅
'''''''''''''''

OpenCR 보드에 메인 MCU로 사용되는 STM32F7xx 는 DFU를 지원하고 있다. 이는 MCU 자체에 내장된 부트로더가 실행되어 USB를 이용하여 DFU 프로토콜로 플래쉬에 테이터를 라이팅할 수 있게 되는데 주로 부트로더 초기 라이팅, 복구 모드 및 부트로더 업데이트에 사용된다. 기타 JTAG 장비 없이 USB로 부트로더를 올릴 수 있다는 것이 가장 큰 장점이다. STLink와 같은 라이팅 / 디버깅 장비 없이 MCU에 내장된 DFU 모드를 사용해서 펌웨어 라이팅해보자.

1) 프로그래머 설정

[Tools] -> [DFU-UTIL] 을 선택한다.

2) DFU 모드 실행

[Boot] 버튼을 누르고 있는 상태에서 [Reset] 버튼을 누르면 DFU 모드가 실행된다.

3) DFU 모드 실행

[Tools] -> [Burn Bootloader] 을 클릭하여 부트로더를 다운로드한다.

5. OpenCR에 TurtleBot3 펌웨어 넣기
'''''''''''''''''''''''''''''''
