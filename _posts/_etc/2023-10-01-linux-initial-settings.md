

**Linux Server 를 설치한후 반드시 하는 설정!!**

## 터미널에서 비프음(Beef) 소리가 안나게 설정하기

1. `inputrc` 파일을 열어서 무음 설정값을 추가 한다.
   ```shell
   # vi /etc/inputrc
    set bell-style none
   ```
2. 파일을 저장 후, 터미널을 다시 로그인 해서 무음이 된걸 확인한다

## 노트북 커버를 닫아도 슬립 모드로 전환 안되도록 설정하기

1. `login.conf` 파일을 열어 `HandleLidSwitch` 를 설정하고 파일을 저장한다.
  ```shell
   # vi /etc/systemd/login.conf
    HandleLidSwitch=ignore
  ```
2. `systemd-logind.service` 서비스를 재시작한다
  ```shell
  # systemctl restart systemd-logind.service
  ```

## SELinux 무효 처리하기

>Secutry Enhanced Linux의 약자로 소스코드가 공개되어 있기 때문에 보안성이 취약한 리눅스의 시스템 액세스 권한을 제어하기 위해 미국 국가보안국(NAS)에서 개발한 보안 아키텍처.

Android OS 와 ios OS 를 비교하면 알기 쉬운데, 보통 제품에서 보안이 강화되면 사용자의 사용 편리성이 낮아지고, 사용자의 사용 편리성이 높아지면 반대로 보안이 낮아지게 된다.<br>


### SELinux 동작모드

#### enforcing

SELinux의 기본값으로 보안정책이 실행되어 로그 기록과 보호를 모두 실행하는 상태

#### permissive

SELinux가 보안정책에 대하여 로그는 기록 하지만 실제 차단되지 않는 상태

#### disable

SELinux가 비활성화되어 동작하지 않는 상태

### SELinux 상태확인

`sestatus` 와 `getenforce` 의 커맨드로 SELinux 의 상태및 현재 동작모드를 확인할 수 있다

### 재부팅 없이 일시적으로 모드변경

- 현재 `enforcing` 혹은 `permissive` 모드를 사용중이라면 `setenforce`커맨드를 사용해서 재부팅없이 일시적으로 모드를 변경할수 있다 (※재부팅 하면 원상태로 돌아옴)
   ```shell
    # setenforce 0   //permissive 모드로 변경
    # setenforce 1   //enforcing 모드로 변경
    # getenforce     //모드상태 확인
   ``` 
- `disabled`모드를 사용중이라면 `setenforce`커맨드로 변경을 할수가 없다

### Config 수정을 통한 모드변경

- 에디터로 `/etc/selinux/config` 파일을 열어 `SELINUX=` 뒷부분에 원하는 모드를 기술하고, 재기동 하면 변경된다 
```shell
$ sudo vi /etc/selinux/config
SELINUX=disabled
```


## Firewall 무효화 하기
```shell
$ sudo systemctl stop firewalld
$ sudo systemctl disable firewalld
```