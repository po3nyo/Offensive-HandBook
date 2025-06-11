# SC (Service Control)

`sc` 명령어는 Windows에서 **서비스(Service)를 제어 및 관리**하기 위한 명령줄 도구입니다.\
Service Control의 줄임말이며, PowerShell이나 명령 프롬프트(cmd)에서 사용됩니다.

***

## 주요 용도

* 서비스 **조회**, **시작/중지/재시작**
* 서비스 **설정 변경** (예: 실행 경로, 시작 유형)
* **신규 서비스 등록** 또는 **삭제**
* **서비스 상태** 확인
* 서비스 자동 실행 여부 확인 (`START_TYPE`)
* 실행 파일 경로 확인 (`BINARY_PATH_NAME`)



## 기본 문법

```powershell
sc [명령어] [서비스이름] [옵션]
```



## 자주 사용되는 명령어&#x20;

| 명령어         | 설명                   | 예시                                      |
| ----------- | -------------------- | --------------------------------------- |
| `sc query`  | 서비스 상태 조회            | `sc query wuauserv`                     |
| `sc qc`     | 서비스 구성 정보 조회         | `sc qc wuauserv`                        |
| `sc start`  | 서비스 시작               | `sc start wuauserv`                     |
| `sc stop`   | 서비스 중지               | `sc stop wuauserv`                      |
| `sc config` | 서비스 설정 변경            | `sc config wuauserv start= disabled`    |
| `sc create` | 서비스 등록               | `sc create MySvc binPath= "C:\svc.exe"` |
| `sc delete` | 서비스 삭제               | `sc delete MySvc`                       |
| `sc sdshow` | 서비스 보안 디스크립터 보기      | `sc sdshow wuauserv`                    |
| `sc sdset`  | 보안 디스크립터 설정 (ACL 변경) | 위험 요소 있음                                |



## 모의침투 관점에서의 활용

* `sc qc`, `sc sdshow` → 권한 정보 확인
* `sc config` → 실행 경로 탈취 (권한 상승)
* `sc create`, `sc start` → 공격용 서비스 등록 및 실행
* `sc delete` → 흔적 삭제

