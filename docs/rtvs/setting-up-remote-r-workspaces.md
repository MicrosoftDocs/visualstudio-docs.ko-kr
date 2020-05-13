---
title: R에 대한 원격 작업 영역
description: 원격 R 작업 영역을 설정하고 Visual Studio에서 이 작업 영역에 연결하는 방법입니다.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 686f98aaaade035f1632139d255ccff8b37eddf3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75850060"
---
# <a name="set-up-remote-workspaces"></a>원격 작업 영역 설정

이 문서에서는 SSL 및 적절한 R 서비스를 사용하여 원격 서버를 구성하는 방법을 설명합니다. 이렇게 하면 RTVS(Visual Studio용 R 도구)가 해당 서버의 원격 작업 영역에 연결할 수 있습니다.

## <a name="remote-computer-requirements"></a>원격 컴퓨터 요구 사항

- Windows 10, Windows Server 2016 또는 Windows Server 2012 R2. RTVS에는 다음이 필요합니다.
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 이상

## <a name="install-an-ssl-certificate"></a>SSL 인증서 설치

RTVS를 사용하려면 원격 서버와의 모든 통신이 HTTP를 통해 수행되어야 하며 이를 위해 서버에 SSL 인증서가 있어야 합니다. 신뢰할 수 있는 인증 기관에서 서명한 인증서(권장) 또는 자체 서명된 인증서를 사용할 수 있습니다. (자체 서명된 인증서를 사용할 경우 RTVS에서 연결 시 경고를 실행합니다.) 한 인증서를 준비하면 인증서를 컴퓨터에 설치하고 프라이빗 키에 대한 액세스를 허용해야 합니다.

### <a name="obtain-a-trusted-certificate"></a>신뢰할 수 있는 인증서 가져오기

신뢰할 수 있는 인증서는 인증 기관에서 발급합니다. 배경에 대해서는 [certificate authorities on Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority)(Wikipedia의 인증 기관)를 참조하세요. 정부 신분증을 얻는 것과 같이 신뢰할 수 있는 인증서 발급에는 추가 프로세스와 수수료가 필요할 수 있지만 이 작업을 통해 요청 및 요청자에 대한 신뢰성이 확인됩니다.

인증서에 있어야 하는 주요 필드는 R 서버 컴퓨터의 정규화된 도메인 이름입니다. 인증 기관에서는 서버가 속한 도메인에 대해 새 서버를 만들 수 있는 권한을 부여받았다는 증명을 요구합니다.

추가 배경에 대해서는 Wikipedia에서 [public key certificates](https://en.wikipedia.org/wiki/Public_key_certificate)(공개 키 인증서)를 참조하세요.

## <a name="install-an-ssl-certificate-on-windows"></a>Windows에 SSL 인증 설치

SSL 인증서를 Windows에서 수동으로 설치해야 합니다. 다음 지침에 따라 SSL 인증서를 설치합니다.

### <a name="obtain-a-self-signed-certificate-windows"></a>자체 서명된 인증서 가져오기(Windows)

신뢰할 수 있는 인증서가 있는 경우 이 섹션을 건너뜁니다. 신뢰할 수 있는 기관에 비해 자체 서명된 인증서는 신분증을 직접 만드는 것과 비슷합니다. 물론, 이 프로세스는 신뢰할 수 있는 기관을 이용하는 것보다 훨씬 더 간단하지만 철저한 인증이 부족하여 공격자가 이러한 인증서를 서명되지 않은 인증서로 대체하고 클라이언트와 서버 간의 모든 트래픽을 캡처할 수 있습니다. 따라서 *자체 서명된 인증서는 테스트 시나리오용으로 신뢰할 수 있는 네트워크에서만 사용해야 하고 프로덕션에서는 사용하면 안 됩니다.*

이 이유로 RTVS는 자체 서명된 인증서로 서버에 연결할 때 항상 다음 경고를 표시합니다.

![자체 서명된 인증서 경고 대화 상자](media/workspaces-remote-self-signed-certificate-warning.png)

자체 서명된 인증서를 발급하려면:

1. 관리자 계정으로 R 서버 컴퓨터에 로그온합니다.
1. 새 관리자 PowerShell 명령 프롬프트를 열고 다음 명령을 실행하여 `"remote-machine-name"`을 서버 컴퓨터의 정규화된 도메인 이름으로 바꿉니다.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. 이전에 R 서버 컴퓨터에서 PowerShell을 실행한 적이 없으면 다음 명령을 실행하여 명시적으로 명령을 실행할 수 있도록 설정합니다.

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

배경에 대해서는 Wikipedia에서 [self-signed certificates](https://en.wikipedia.org/wiki/Self-signed_certificate)(자체 서명된 인증서)를 참조하세요.

### <a name="install-the-certificate"></a>인증서 설치

원격 컴퓨터에서 인증서를 설치하려면 명령 프롬프트에서 *certlm.msc*(인증서 관리자)를 실행합니다. **개인** 폴더를 마우스 오른쪽 단추로 클릭하고 **모든 작업** > **가져오기** 명령을 선택합니다.

![인증서 가져오기 명령](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>SSL 인증서의 프라이빗 키를 읽을 권한 부여

인증서를 가져온 후 다음 지침에 설명된 대로 `NETWORK SERVICE` 계정에 프라이빗 키를 읽을 수 있는 권한을 부여합니다. `NETWORK_SERVICE`는 서버 컴퓨터에 들어오는 SSL 연결을 종료하는 서비스인 R Services Broker를 실행하는 데 사용되는 계정입니다.

1. 관리자 명령 프롬프트에서 *certlm.msc*(인증서 관리자)를 실행합니다.
1. **개인** > **인증서**를 확장하고, 인증서를 마우스 오른쪽 단추로 클릭하고, **모든 작업** > **프라이빗 키 관리**를 선택합니다.
1. 인증서를 마우스 오른쪽 단추로 클릭하고 **모든 작업**에서 **프라이빗 키 관리** 명령을 선택합니다.
1. 대화 상자가 나타나면 **추가**를 선택하고 계정 이름으로 `NETWORK SERVICE`를 입력합니다.

    ![프라이빗 키 관리 대화 상자에서 NETWORK_SERVICE 추가](media/workspaces-remote-manage-private-key-dialog.png)

1. **확인**을 두 번 선택하여 대화 상자를 닫고 변경 내용을 커밋합니다.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Ubuntu에 SSL 인증 설치

`rtvs-daemon` 패키지는 기본적으로 설치의 일부로 자체 서명된 인증서를 설치합니다.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>자체 서명된 인증서 가져오기(Ubuntu)

자체 서명된 인증서를 사용하는 장점 및 위험에 대해서는 Windows 설명을 참조하세요. `rtvs-daemon` 패키지는 설치하는 동안 자체 서명된 인증서를 생성 및 구성합니다. 자동 생성된 자체 서명된 인증서를 바꾸려는 경우 이 작업만 수행하면 됩니다.

자체 서명된 인증서를 자체적으로 발급하려면 다음을 수행합니다.

1. Linux 머신에 SSH 또는 로그인합니다.
2. `ssl-cert` 패키지를 설치합니다.

    ```sh
    sudo apt-get install ssl-cert
    ```

3. `make-ssl-cert`를 실행하여 기본 자체 서명된 SSL 인증서를 생성합니다.

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. 생성된 키와 PEM 파일을 PFX로 변환합니다. 생성된 PFX는 홈 폴더에 있어야 합니다.

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>RTVS 디먼 구성

SSL 인증서 파일 경로(PFX 경로)는 */etc/rtvs/rtvsd.config.json*에 설정되어야 합니다. `X509CertificateFile` 및 `X509CertificatePassword`를 각각 파일 경로 및 암호로 업데이트합니다.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

파일을 저장하고, `sudo systemctl restart rtvsd`로 디먼을 다시 시작합니다.

## <a name="install-r-services-on-windows"></a>Windows에 R Services 설치

R 코드를 실행하려면 다음과 같이 원격 컴퓨터에 R 인터프리터가 설치되어 있어야 합니다.

1. 다음 중 하나를 다운로드하여 설치합니다.

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R for Windows](https://cran.r-project.org/bin/windows/base/)

     두 항목의 기능은 똑같지만 Microsoft R Open은 [Intel Math Kernel Library](https://software.intel.com/intel-mkl)의 허가로 추가적인 하드웨어 가속화된 선형 대수 라이브러리를 활용합니다.

2. [R Services 설치 관리자](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md)를 실행하고 메시지가 표시되면 다시 부팅합니다. 설치 관리자에서 다음을 수행합니다.

    - *%PROGRAMFILES%\R Tools for Visual Studio\1.0\\* 에 폴더를 만들고, 필요한 모든 이진 파일을 복사합니다.
    - `RHostBrokerService` 및 `RUserProfileService`를 설치하고 자동으로 시작되도록 구성합니다.
    - `seclogon` 서비스가 자동으로 시작되도록 구성합니다.
    - *Microsoft.R.Host.exe* 및 *Microsoft.R.Host.Broker.exe*를 기본 포트 5444의 방화벽 인바운드 규칙에 추가합니다.

컴퓨터가 다시 부팅되면 R Services가 자동으로 시작됩니다.

- **R Host Broker Service**에서는 Visual Studio와 R 코드가 실행되는 컴퓨터의 프로세스 간의 모든 HTTPS 트래픽을 처리합니다.
- **R 사용자 프로필 서비스**에서는 Windows 사용자 프로필 생성을 처리하는 권한 있는 구성 요소입니다. 새 사용자가 R 서버 컴퓨터에 처음 로그온할 때 서비스가 호출됩니다.

이러한 서비스는 서비스 관리 콘솔(*compmgmt.msc*)에서 확인할 수 있습니다.

## <a name="install-r-services-on-linux"></a>Linux에 R Services 설치

R 코드를 실행하려면 다음과 같이 원격 컴퓨터에 R 인터프리터가 설치되어 있어야 합니다.

1. 다음 중 하나를 다운로드하여 설치합니다.

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R for Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     두 항목의 기능은 똑같지만 Microsoft R Open은 [Intel Math Kernel Library](https://software.intel.com/intel-mkl)의 허가로 추가적인 하드웨어 가속화된 선형 대수 라이브러리를 활용합니다.

2. 물리적 Ubuntu 컴퓨터, Azure Ubuntu VM, WSL(Linux용 Windows 하위 시스템) 및 Azure 컨테이너 리포지토리에서 실행되는 컨테이너를 비롯한 Docker 컨테이너가 설명되어 있는 [Linux용 원격 R Service](setting-up-remote-r-service-on-linux.md)의 지침을 따릅니다.

## <a name="configure-r-services"></a>R Services 구성

원격 컴퓨터에서 실행되는 R Services에서는 사용자 계정을 만들고, 방화벽 규칙을 설정하고, Azure 네트워킹을 구성하고, SSL 인증서를 구성해야 합니다.

1. 사용자 계정: 원격 컴퓨터에 액세스하는 각 사용자에 대한 계정을 만듭니다. 표준(권한 없음) 로컬 사용자 계정을 만들거나 R 서버 컴퓨터를 도메인에 조인하고 적절한 보안 그룹을 `Users` 보안 그룹에 추가할 수 있습니다.

1. 방화벽 규칙: 기본적으로 `R Host Broker`는 TCP 포트 5444에서 수신 대기합니다. 따라서 인바운드 및 아웃바운드 트래픽에 둘 다 사용할 수 있는 Windows 방화벽 규칙이 있는지 확인합니다(패키지 및 비슷한 시나리오를 설치하려면 아웃바운드가 필요함).  R Services 설치 관리자에서는 기본 제공 Windows 방화벽에 대해 이러한 규칙을 자동으로 설정합니다. 그러나 타사 방화벽을 사용하는 경우 `R Host Broker`에 대해 포트 5444를 수동으로 엽니다.

1. Azure 구성: 원격 컴퓨터가 Azure의 가상 머신인 경우 Windows 방화벽과 관계가 없는 Azure 네트워킹 내에서도 포트 5444를 엽니다. 자세한 내용은 Azure 설명서에서 [네트워크 보안 그룹을 사용하여 네트워크 트래픽 필터링](/azure/virtual-network/virtual-networks-nsg)을 참조하세요.

1. R Host Broker에 로드할 SSL 인증서 알림: 인트라넷 서버에서 인증서를 설치할 경우 서버의 정규화된 도메인 이름이 NETBIOS 이름과 같을 수 있습니다. 이 경우 기본 인증서가 로드되므로 아무 작업도 수행하지 않아도 됩니다.

    하지만 인터넷 연결 서버(Azure VM)에서 인증서를 설치할 경우 인터넷 연결 서버의 FQDN이 NETBIOS 이름과 같지 않으므로 서버의 FQDN(정규화된 도메인 이름)을 사용합니다.

    FQDN을 사용하려면 R Services가 설치된 위치(기본적으로 *%PROGRAM FILES%\R Remote Service for Visual Studio\1.0*)로 이동하고 텍스트 편집기에서 *Microsoft.R.Host.Broker.Config.json* 파일을 연 후 해당 콘텐츠를 다음으로 바꿔서 서버의 FQDN에 CN을 할당합니다(예: `foo.westus.cloudapp.azure.com`).

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    파일을 저장하고 컴퓨터를 다시 시작하여 변경 내용을 적용합니다.

## <a name="troubleshooting"></a>문제 해결

**질문: R 서버 컴퓨터가 응답하지 않습니다. 어떻게 해야 하나요?**

명령줄에서 원격 컴퓨터에 ping을 실행해보세요. `ping remote-machine-name` Ping이 실패하면 컴퓨터가 실행 중인지 확인합니다.

**질문: R 대화형 창에 원격 컴퓨터가 켜져 있다고 표시되는데 서비스가 실행되지 않는 이유는 무엇인가요?**

가능한 이유는 세 가지입니다.

- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 이상이 컴퓨터에 설치되어 있지 않습니다.
- `Microsoft.R.Host.Broker` 및 `Microsoft.R.Host`에 대한 방화벽 규칙이 포트 5444의 들어오는 연결과 나가는 연결에 둘 다 사용되지 않습니다.
- `CN=<remote-machine-name>`을 가진 SSL 인증서가 설치되지 않았습니다.

위와 같이 모두 변경한 후 컴퓨터를 다시 시작합니다. 그런 다음, 작업 관리자(서비스 탭) 또는 *services.msc*를 통해 `RHostBrokerService` 및 `RUserProfileService`가 실행 중인지 확인합니다.

**질문: R 서버에 연결하는 동안 R 대화형 창에 “401 액세스 거부”가 표시되는 이유는 무엇인가요?**

가능한 두 가지 이유는 다음과 같습니다.

- `NETWORK SERVICE` 계정에는 SSL 인증서의 프라이빗 키에 대한 액세스 권한이 없을 수 있습니다. 이전 지침에 따라 `NETWORK SERVICE`에 프라이빗 키에 대한 액세스 권한을 부여합니다.
- `seclogon` 서비스가 실행 중인지 확인합니다. *services.msc*를 사용하여 `seclogon`이 자동으로 시작되도록 구성합니다.

**질문: R 서버에 연결하는 동안 R 대화형 창에 “404 찾을 수 없음”이 표시되는 이유는 무엇인가요?**

이 오류의 원인은 Visual C++ 재배포 가능 라이브러리가 없기 때문일 수 있습니다. R 대화형 창에 누락된 라이브러리(DLL)에 관한 메시지가 있는지 확인합니다. 그 다음에 VS 2015 재배포 가능이 설치되어 있고 R도 설치되어 있는지 확인합니다.

**질문: R 대화형 창에서 인터넷/리소스에 액세스할 수 없습니다. 어떻게 해야 하나요?**

`Microsoft.R.Host.Broker` 및 `Microsoft.R.Host`에 대한 방화벽 규칙에서 포트 5444의 아웃바운드 액세스를 허용하는지 확인합니다. 변경 내용을 적용한 후 컴퓨터를 다시 시작합니다.

**질문: 이러한 솔루션을 모두 시도했는데 여전히 작동하지 않습니다. 이제 무엇을 해야 할까요?**

*C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*에서 로그 파일을 찾습니다. 이 폴더에는 실행된 R Broker Service의 각 인스턴스에 대한 개별 로그 파일이 들어 있습니다. 서비스를 다시 시작할 때마다 새 로그 파일이 생성됩니다. 가장 최근 로그 파일에서 발생할 수 있는 문제에 대한 단서를 확인합니다.
