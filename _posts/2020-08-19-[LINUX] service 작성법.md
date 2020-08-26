---
title: "[LINUX] service 작성법"
date: 2020-08-19 08:46:00
categories: jekyll update
---

```
[Unit]
Description=Code Server IDE
After=network.target

[Service]
Type=simple
User=root
EnvironmentFile=~/.profile
EnvironmentFile=/etc/systemd/system/code-server.service.d/override.conf
WorkingDirectory=~
Restart=on-failure
RestartSec=10

ExecStart=/usr/local/bin/coder/code-server $(pwd)

StandardOutput=file:/var/log/code-server-output.log
StandardError=file:/var/log/code-server-error.log

[Install]
WantedBy=multi-user.target
```

__[UNIT]__<br>
Description=
해당 유닛에 대한 상세한 설명을 포함한다.



Requires=
상위 의존성을 구성한다. 목록의 유닛이 정상적일 경우 유닛이 시작된다. (필요 조건)



RequiresOverridable=
"Requires=" 옵션과 유사하다. 하지만 이 경우 "사용자에 의해서" 서비스가 시작하는데 상위 의존성이 있는 유닛 구동에 실패 하더라도 이를 무시하고 유닛을 시작한다. (즉 상위 의존성을 무시한다.) 자동 시작의 경우 적용 되지 않는다.



Requisite=, RequisiteOverridable=
"Requires=" 와 "RequiresOverridable=" 와 유사하다. 상위 의존성 유닛이 시작되지 않은 경우 즉시 실패를 반환한다.



Wants=
"Requires=" 보다 다소 완화된 옵션이다. 상위 의존성의 유닛이 시작되지 않더라도 전체 수행과정에 영향을 끼치지 않는다. 이 옵션은 하나의 유닛을 다른 유닛과 연계할 경우 사용하게 된다. (충분 조건)



BindsTo=
"Requires=" 와 매우 유사하다. systemd 개입 없이 갑작기 서비스가 사라진 경우 (가령 NIC 가 물리적 장애가 난 경우) 해당 유닛도 같이 중지 하도록 설정하도록 한다.



PartOf=
"Requires=" 와 매우 유사하다. 상위 의존성의 유닛을 중지하거나 재시작하는 경우 해당 유닛 또한 중지나 재시작을 수행한다. 만일 오라클과 오라클 리스너의 경우에서 처럼 하나의 서비스 다른 하나의 종속성을 가지게 되는 경우 필요한 설정이다.



Conflicts=
역의 관계를 설정한다. 만일 유닛1' 의 "Conflicts=" 설정이 '유닛2' 로 되어 있다면 '유닛1'이 시작된 경우 '유닛2'가 중지되고, '유닛1'이 중지된 경우 '유닛2'가 시작한다. 이 옵션은 "After=" 와 "Before=" 옵션과는 독립적으로 작동한다. 각 서비스가 반대의 역활을 하거나 혹은 보조적인 서비스 역활을 수행한다면 서비스 실행 관리에 편리할 것 같다. 



Before=, After=
유닛 시작의 전후 관계를 설정한다. 해당 설정은 "Requires=" 설정과는 독립적이다. "Before=" 에 나열된 유닛이 시작되기 전에 실행하고 "After=" 은 해당 유닛이 시작된 이후 나열된 유닛이 실행한다.
이 설정은 시스템이 종료(shutdown) 될때는 역으로 작동하게 된다.



OnFailure=
해당 유닛이 "실패" 상태가 되면 수행할 유닛 목록 (예 "/" 파일 시스템 마운트 실패시 복구 모드 수행)



PropagatesReloadTo=, ReloadPropagatedFrom=
리로드(reload) 명령을 다른 유닛에게 전달하거나 혹은 전달받아 해당 유닛도 리로드(reload)하게 된다.



RequiresMountsFor=
절대 경로로 지정하여 유닛을 구동하는데 필요한 마운트 목록을 자동으로 구성하여 "Requires=", "After=" 을 수행한다. 즉 필요한 마운트 경로가 준비되어 있는지 점검하고 마운트를 미리 진행한다.



OnFailureIsolate=[yes|no]
"yes” 인 경우 "OnFailure=" 에 선언된 리스트와는 격리모드(isolation mode)로 작동한다. 즉 해당 유닛에 종속성이 없는 모든 유닛은 중지 되게 된다. "OnFailureIsolate=yes" 인 경우 "OnFailure=" 옵션에 오직 하나의 유닛만 설정 할 수 있다.  

__[SERVICE]__<br>
Description=
해당 유닛에 대한 상세한 설명을 포함한다.



Requires=
상위 의존성을 구성한다. 목록의 유닛이 정상적일 경우 유닛이 시작된다. (필요 조건)



RequiresOverridable=
"Requires=" 옵션과 유사하다. 하지만 이 경우 "사용자에 의해서" 서비스가 시작하는데 상위 의존성이 있는 유닛 구동에 실패 하더라도 이를 무시하고 유닛을 시작한다. (즉 상위 의존성을 무시한다.) 자동 시작의 경우 적용 되지 않는다.



Requisite=, RequisiteOverridable=
"Requires=" 와 "RequiresOverridable=" 와 유사하다. 상위 의존성 유닛이 시작되지 않은 경우 즉시 실패를 반환한다.



Wants=
"Requires=" 보다 다소 완화된 옵션이다. 상위 의존성의 유닛이 시작되지 않더라도 전체 수행과정에 영향을 끼치지 않는다. 이 옵션은 하나의 유닛을 다른 유닛과 연계할 경우 사용하게 된다. (충분 조건)



BindsTo=
"Requires=" 와 매우 유사하다. systemd 개입 없이 갑작기 서비스가 사라진 경우 (가령 NIC 가 물리적 장애가 난 경우) 해당 유닛도 같이 중지 하도록 설정하도록 한다.



PartOf=
"Requires=" 와 매우 유사하다. 상위 의존성의 유닛을 중지하거나 재시작하는 경우 해당 유닛 또한 중지나 재시작을 수행한다. 만일 오라클과 오라클 리스너의 경우에서 처럼 하나의 서비스 다른 하나의 종속성을 가지게 되는 경우 필요한 설정이다.



Conflicts=
역의 관계를 설정한다. 만일 유닛1' 의 "Conflicts=" 설정이 '유닛2' 로 되어 있다면 '유닛1'이 시작된 경우 '유닛2'가 중지되고, '유닛1'이 중지된 경우 '유닛2'가 시작한다. 이 옵션은 "After=" 와 "Before=" 옵션과는 독립적으로 작동한다. 각 서비스가 반대의 역활을 하거나 혹은 보조적인 서비스 역활을 수행한다면 서비스 실행 관리에 편리할 것 같다. 



Before=, After=
유닛 시작의 전후 관계를 설정한다. 해당 설정은 "Requires=" 설정과는 독립적이다. "Before=" 에 나열된 유닛이 시작되기 전에 실행하고 "After=" 은 해당 유닛이 시작된 이후 나열된 유닛이 실행한다.
이 설정은 시스템이 종료(shutdown) 될때는 역으로 작동하게 된다.



OnFailure=
해당 유닛이 "실패" 상태가 되면 수행할 유닛 목록 (예 "/" 파일 시스템 마운트 실패시 복구 모드 수행)



PropagatesReloadTo=, ReloadPropagatedFrom=
리로드(reload) 명령을 다른 유닛에게 전달하거나 혹은 전달받아 해당 유닛도 리로드(reload)하게 된다.



RequiresMountsFor=
절대 경로로 지정하여 유닛을 구동하는데 필요한 마운트 목록을 자동으로 구성하여 "Requires=", "After=" 을 수행한다. 즉 필요한 마운트 경로가 준비되어 있는지 점검하고 마운트를 미리 진행한다.



OnFailureIsolate=[yes|no]
"yes” 인 경우 "OnFailure=" 에 선언된 리스트와는 격리모드(isolation mode)로 작동한다. 즉 해당 유닛에 종속성이 없는 모든 유닛은 중지 되게 된다. "OnFailureIsolate=yes" 인 경우 "OnFailure=" 옵션에 오직 하나의 유닛만 설정 할 수 있다.  

__[INSTALL]__<br>
Alias=
유닛의 알리아스 이름을 지정한다. "systemctl enable" 명령어를 통해서 알리아스 이름으로 생성할 수 있다. 알리아스 이름은 유닛 파일 확장자(유닛 타입)를 가지고 있어야 한다.
(service, socket, mount, swap 등이 있다.  예: httpd.service 의 Alias=apache.service)



WantedBy=, RequiredBy=
"systemctl enable" 명령어로 유닛을 등록할때 등록에 필요한 유닛을 지정한다. 해당 유닛을 등록하기위한 종속성 검사 단계로 보면 된다. 따라서 해당 설정은 [Unit] 섹션의 "Wants=" 와 :Requires=" 옵션과 관계 있다.



Also=
"systemctl enable" 와 "systemctl disable" 로 유닛을 등록하거나 해제할때 다른 유닛 또한 같이 등록, 해제를 하도록 구성할 수 있다.