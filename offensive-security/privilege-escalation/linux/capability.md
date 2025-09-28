# Capability

> 리눅스의 **Capabilities**는 프로세스에 필요한 최소권한만 세부적으로 나누어 관리하는 메커니즘입니다.



## 1. Capabilities의 등장 배경

리눅스는 기본적으로 다음과 같은 사용자 기반 권한 모델을 사용합니다.

* **UID=0 (root):** 시스템의 모든 작업 수행 가능
* **UID≠0 (일반 사용자):** 제한된 권한

일반 사용자가 시스템 수준의 일부 특정한 작업(예: 포트 바인딩, 파일 소유자 변경, 마운트 등)을 수행하기 위해서는 `setuid`, `setgid`, `sticky bit`와 같은 특수 권한을 부여하여 해당 작업을 가능하게 만들어야 했습니다.

하지만 이러한 방식은 **전체 root 권한을 부여하거나, 권한의 범위를 세밀하게 제어할 수 없다는 한계**를 가지고 있습니다. 특히 `setuid`는 하나의 작업만을 수행하기 위해 프로그램 전체에 루트 권한을 부여하는 방식이기 때문에, **보안 취약점이 존재할 경우 시스템 전체가 공격에 노출되는 심각한 문제가 발생할 수 있습니다**.

이를 해결하고자 리눅스 커널은 **root 권한을 세분화하여 기능 단위로 분리할 수 있는 Linux Capabilities를 도입**하였습니다. Capabilities는 각 작업(예: 네트워크 포트 바인딩, 파일 소유자 변경, 마운트 등)에 필요한 최소한의 권한만을 프로세스에 부여할 수 있도록 하여, 최소 권한 원칙(Principle of Least Privilege)을 시스템 수준에서 실현할 수 있게 합니다.



## 2. Capabilities의 종류

리눅스에서는 약 41개 정도의 Capabilities가 정의되어 있으며, 사용하는 커널 버전에 따라 조금씩 다를 수 있습니다. 권한 상승에 취약한 주요 Capabilities 목록은 아래 표와 같습니다.

<table><thead><tr><th width="228">Capability</th><th width="368">주요 기능 설명</th><th width="150">권한 상승 위험성</th></tr></thead><tbody><tr><td><strong>CAP_SYS_ADMIN</strong></td><td>시스템 전체 관리 권한. mount, chroot, 네임스페이스 관리 등 광범위한 작업 허용</td><td>🔴 매우 높음</td></tr><tr><td><strong>CAP_SETUID</strong></td><td>프로세스의 UID를 0(root) 등으로 변경 가능</td><td>🔴 매우 높음</td></tr><tr><td><strong>CAP_SETGID</strong></td><td>프로세스의 GID를 변경 가능</td><td>🔴 매우 높음</td></tr><tr><td><strong>CAP_DAC_OVERRIDE</strong></td><td>DAC(소유자 기반 권한 검사) 무시 가능 → 모든 파일 읽기/쓰기</td><td>🔴 매우 높음</td></tr><tr><td><strong>CAP_DAC_READ_SEARCH</strong></td><td>읽기 및 디렉토리 검색 권한 무시</td><td>🔴 매우 높음</td></tr><tr><td><strong>CAP_FOWNER</strong></td><td>자신이 소유하지 않은 파일에도 소유자 권한으로 작업 가능</td><td>🔴 높음</td></tr><tr><td><strong>CAP_CHOWN</strong></td><td>파일 소유자 변경 가능</td><td>🔴 높음</td></tr><tr><td><strong>CAP_SYS_PTRACE</strong></td><td>다른 프로세스 메모리 접근 및 디버깅 가능 (암호, 토큰 탈취 등)</td><td>🔴 매우 높음</td></tr><tr><td><strong>CAP_NET_ADMIN</strong></td><td>네트워크 설정 변경 가능 (라우팅, 인터페이스 제어, 방화벽 등)</td><td>🔴 높음</td></tr><tr><td><strong>CAP_NET_RAW</strong></td><td>Raw socket 사용 가능 (ping, sniffer 등)</td><td>🟡 중간</td></tr><tr><td><strong>CAP_SYS_MODULE</strong></td><td>커널 모듈 삽입/제거 가능 (커널 레벨 취약점 공격 가능)</td><td>🔴 매우 높음</td></tr><tr><td><strong>CAP_SYS_TIME</strong></td><td>시스템 시간 변경 (로그 위조, 시간 기반 우회 가능)</td><td>🟡 중간</td></tr><tr><td><strong>CAP_MKNOD</strong></td><td>디바이스 파일 생성 가능 (가짜 디스크, TTY 생성 등)</td><td>🟡 중간</td></tr></tbody></table>

<details>

<summary>Capability의 4가지 집합과 옵션</summary>

Capabilities를 설정할 때는 일반적으로 다음 세 가지 플래그가 사용됩니다.

| Capability 집합              | 의미                                         | 해당 옵션                            |
| -------------------------- | ------------------------------------------ | -------------------------------- |
| **Permitted (허용된 집합)**     | 프로세스가 **가질 수 있는** Capability 목록            | **`p (permitted)`**              |
| **Effective (유효 집합)**      | 프로세스가 **즉시 사용할 수 있는** Capability 목록        | **`e (effective)`**              |
| **Inheritable (상속 가능 집합)** | 프로세스가 자식 프로세스에 **상속할 수 있는** Capability 목록  | **`i (inheritable)`**            |
| **Ambient (주변 집합)**        | 명시적 설정 없이 자동으로 자식 프로세스에 전달되는 Capability 목록 | 별도 옵션 없음 (`ambient`는 별도 명령어로 관리) |

</details>

## 3. Capabilities 확인 및 설정 방법&#x20;

### 1.  Capability가 설정된 모든 파일 확인

```bash
getcap -r / 2>/dev/null
```

### 2. 파일의 Capability 확인

```bash
getcap [파일경로]
#ex 
getcap /usr/bin/ping
```

### 3. 프로세스의 Capability 확인

```bash
getpcaps [프로세스PID]
#ex
getpcaps 1324
```

### 4. 파일에 Capability 설정

```bash
sudo setcap [Capability]=[권한] [파일경로]
#ex
sudo setcap cap_setuid=+ep /usr/bin/python3
```



## 4. Capability를 이용한 권한상승 시나리오

### 1. CAP\_SETUID 를 이용한 root shell 획득

* `/home/po3nyo/.local/python3` 바이너리에 `cap_setuid+ep` 설정 확인

<figure><img src="../../../.gitbook/assets/2025-05-17 08 20 12.png" alt=""><figcaption></figcaption></figure>

* 해당 폴더로 이동 후 python 실행파일을 이용하여 아래 [ 코드](https://gtfobins.github.io/gtfobins/python/#capabilities) 실행 후 root shell 획득

<figure><img src="../../../.gitbook/assets/2025-05-17 08 29 45.png" alt=""><figcaption></figcaption></figure>

### 2. CAP\_DAC\_OVERRIDE 를 이용한 /etc/shadow 파일 접근

* `/usr/bin/cat`바이너리에 `cap_dac_override+ep` 설정 확인

<figure><img src="../../../.gitbook/assets/2025-05-17 09 11 48.png" alt=""><figcaption></figcaption></figure>

* `/etc/shadow` 조회

<figure><img src="../../../.gitbook/assets/2025-05-17 09 18 13.png" alt=""><figcaption></figcaption></figure>

* root 계정 패스워드 해시 추출

```bash
root:$y$j9T$0jySFGwRLizG1CF2zeBsd1$B9D3ly/.g4kS.6S/POc7KcD6dRS3DtmulhAECzkLouD:20225:0:99999:7:::
```



* 해시 크래킹을 통해 root 패스워드 획득

<figure><img src="../../../.gitbook/assets/2025-05-17 09 43 07 (2).png" alt=""><figcaption></figcaption></figure>

* `su` 명령으로 root 계정 로그인

<figure><img src="../../../.gitbook/assets/2025-05-17 09 47 22 (1).png" alt=""><figcaption></figcaption></figure>

## 5. Mitigation

### 1. 불필요한 Capability 제거

일반 사용자 접근 가능한 바이너리에 `cap_setuid`, `cap_sys_admin`, `cap_dac_override` 같은 **고위험 Capabilities**가 부여되어 있으면 누구든지 루트 쉘을 획득할 수 있습니다. 따라서 정기적으로 확인하여 관리해야합니다.

* Capability 설정 확인

```bash
getcap -r / 2>/dev/null
```

* 출력 결과 위험 Capability가 설정된 바이너리 확인 및 제거

```bash
sudo setcap -r /path/to/file
```



### 2. 최소 권한 원칙(Least Privilege Principle) 적용

Capabilities는 루트 권한을 대체할 수 있는 만큼, 반드시 **정확하게 필요한 작업만 수행하도록 최소화**해야 합니다.

예시:

* `ping` → `cap_net_raw`만 필요
* `mount` → 절대로 일반 사용자에게 부여하면 안 됨 (`cap_sys_admin`은 root급 권한)



### 3. 인터프리터 바이너리(cap\_sh, python, bash 등)에 Capabilities 금지

Python, Bash, Perl 등의 인터프리터에 `cap_setuid`, `cap_dac_override` 등을 부여하면, 임의 코드 실행으로 루트 쉘을 매우 쉽게 얻을 수 있으므로 이러한 범용 도구에는 절대 Capability를 부여하면 안되며 부득이한 경우 `AppArmor`나 `SELinux` 같은 **Mandatory Access Control(MAC)** 시스템을 통한 추가적인 관리가 필요합니다.



### 4. 정기적 점검 및 감시

Capabilities 설정은 파일 속성(xattr)에 저장되므로, 일반 파일 검사로는 보이지 않습니다. 정기적으로 스크립트나 보안 점검 도구로 감시해야 합니다.

스크립트 예시:

```bash
#!/bin/bash
getcap -r / 2>/dev/null | grep -E 'cap_(setuid|sys_admin|dac_override|sys_ptrace|chown)' > /var/log/capabilities_audit.log
```

