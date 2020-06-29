---
title: 원격 Linux 컴퓨터에서 Python 코드 디버그
description: 필요한 구성 단계, 보안 및 문제 해결을 포함해서 Visual Studio를 사용하여 원격 Linux 컴퓨터에서 실행 중인 Python 코드를 디버그합니다.
ms.date: 05/12/2020
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ccc0f23663eb4f892c4eb5e4ab66d7cb526f100f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285687"
---
Visual Studio는 Windows 컴퓨터에서 Python 애플리케이션을 로컬 및 원격으로 시작하고 디버그할 수 있습니다([Remote Debugging](../../../debugger/remote-debugging.md)(원격 디버깅) 참조). 또한 [debugpy 라이브러리](https://pypi.org/project/debugpy/)를 사용하여 CPython 이외의 다른 운영 체제, 디바이스 또는 Python 구현에서 원격으로 디버그할 수도 있습니다.

debugpy를 사용하는 경우 디버그되는 Python 코드는 Visual Studio에서 연결할 수 있는 디버그 서버를 호스팅합니다. 이 호스팅을 사용하려면 서버를 가져오고 사용할 수 있도록 코드를 약간 수정해야 하며, TCP 연결을 허용하기 위해 원격 컴퓨터에 네트워크 또는 방화벽 구성이 필요할 수 있습니다.

> [!NOTE]
> Visual Studio 2019 버전 16.4 및 이전에는 [ptvsd 라이브러리](https://pypi.python.org/pypi/ptvsd)가 사용되었습니다. debugpy 라이브러리는 Visual Studio 2019 버전 16.5에서 ptvsd 4를 대체했습니다.

## <a name="set-up-a-linux-computer"></a>Linux 컴퓨터 설정

이 연습을 수행하려면 다음 항목이 필요합니다.

- Mac OSX 또는 Linux와 같은 운영 체제에서 Python을 실행하는 원격 컴퓨터.
- 원격 디버깅의 기본값으로 해당 컴퓨터의 방화벽에서 열려 있는 포트 5678(인바운드).

> [!NOTE]
> 이 연습은 Visual Studio 2019 버전 16.6을 기반으로 합니다.

쉽게 [Azure에서 Linux 가상 머신](/azure/virtual-machines/linux/creation-choices)을 만들고 Windows에서 [원격 데스크톱을 사용하여 Linux 가상 머신에 액세스](/azure/virtual-machines/linux/use-remote-desktop)할 수 있습니다. Python이 기본적으로 설치되어 있으므로 VM에 Ubuntu를 사용하면 편리합니다. 그렇지 않은 경우 추가 Python 다운로드 위치는 [원하는 Python 인터프리터 설치](../../installing-python-interpreters.md)를 참조하세요.

Azure VM에 대한 방화벽 규칙을 만드는 방법에 대한 자세한 내용은 [Azure Portal을 사용하여 Azure에서 VM으로 포트 열기](/azure/virtual-machines/windows/nsg-quickstart-portal)를 참조하세요.

## <a name="prepare-the-script-for-debugging"></a>디버그할 스크립트 준비

1. 원격 컴퓨터에서 다음 코드를 사용하여 *guessing-game.py*라는 Python 파일을 만듭니다.

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. `pip3 install debugpy`를 사용하여 사용자 환경에 `debugpy` 패키지를 설치합니다.
   >[!NOTE]
   >문제 해결에 필요한 경우를 대비하여 debugpy 버전을 기록해 두는 것이 좋습니다. [debugpy 목록](https://pypi.org/project/debugpy/)은 사용 가능한 버전도 보여줍니다.

1. *guessing-game.py*에서 가능한 가장 빠른 지점에 다른 코드보다 먼저 해당 코드를 추가하여 원격 디버깅을 사용하도록 설정합니다. (엄격한 요구 사항은 아니지만, `listen` 함수를 호출하기 전에 생성된 모든 백그라운드 스레드를 디버그할 수는 없습니다.)

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. 파일을 저장하고 `python3 guessing-game.py`를 실행합니다. `listen`에 대한 호출이 백그라운드에서 실행되고, 달리 프로그램과 상호 작용하지 않으면 들어오는 연결을 기다립니다. 원하는 경우 디버거가 연결될 때까지 `listen` 뒤에 `wait_for_client` 함수를 호출하여 프로그램을 차단할 수 있습니다.

> [!Tip]
> `listen` 및 `wait_for_client` 외에도 debugpy는 디버거가 연결되어 있으면 중단점을 프로그래밍 방식으로 작동하는 `breakpoint` 도우미 함수를 제공합니다. 또한 디버거가 연결되어 있으면 `True`를 반환하는 `is_client_connected` 함수도 있지만, 다른 `debugpy` 함수를 호출하기 전에 이 결과를 확인할 필요가 없습니다.

## <a name="attach-remotely-from-python-tools"></a>Python 도구에서 원격으로 연결

이 단계에서는 간단한 중단점을 설정하여 원격 프로세스를 중지합니다.

1. 로컬 컴퓨터에 원격 파일의 복사본을 만들고 Visual Studio에서 엽니다. 파일의 위치는 중요하지 않지만, 이름은 원격 컴퓨터의 스크립트 이름과 일치해야 합니다.

1. (선택 사항) 로컬 컴퓨터에서 debugpy에 IntelliSense를 사용하려면 Python 환경에 debugpy 패키지를 설치합니다.

1. **디버그** > **프로세스에 연결**을 선택합니다.

1. 나타나는 **프로세스에 연결** 대화 상자에서 **연결 형식**을 **Python 원격(debugpy)** 으로 설정합니다.

1. **연결 대상** 필드에 `tcp://<ip_address>:5678`을 입력합니다. 여기서 `<ip_address>`는 원격 컴퓨터의 IP 주소이고(명시적 주소 또는 myvm.cloudapp.net과 같은 이름일 수 있음), `:5678`은 원격 디버깅 포트 번호입니다.

1. **Enter** 키를 눌러 해당 컴퓨터에서 사용할 수 있는 debugpy 프로세스의 목록을 채웁니다.

    ![연결 대상 입력 및 프로세스 나열](../../media/remote-debugging-attach.png)

    이 목록을 채운 후 원격 컴퓨터에서 다른 프로그램을 시작하게 되는 경우 **새로 고침** 단추를 선택합니다.

1. 디버그할 프로세스를 선택한 다음 **연결**을 선택하거나 프로세스를 두 번 클릭합니다.

1. 그러면 스크립트가 원격 컴퓨터에서 계속 실행되는 동안 Visual Studio에서 디버깅 모드로 전환하여 모든 일반적인 [디버깅](../../debugging-python-in-visual-studio.md) 기능을 제공합니다. 예를 들어 `if guess < number:` 줄에 중단점을 설정한 다음 원격 컴퓨터로 전환하고 다른 guess를 입력합니다. 이렇게 하고 나면 로컬 컴퓨터의 Visual Studio가 해당 중단점에서 중지하고 로컬 변수 등을 보여 줍니다.

    ![Visual Studio에서 중단점이 적중될 때 디버깅 일시 중지](../../media/remote-debugging-breakpoint-hit.png)

1. 디버깅을 중지하면 Visual Studio는 원격 컴퓨터에서 계속 실행되는 프로그램에서 분리됩니다. 또한 debugpy는 계속 디버거 연결을 수신 대기하므로 언제든지 프로세스에 다시 연결할 수 있습니다.

### <a name="connection-troubleshooting"></a>연결 문제 해결

1. **연결 형식**에 **Python 원격(debugpy)** 을 선택했는지 확인합니다.
1. **연결 대상**의 비밀이 원격 코드의 비밀과 정확히 일치하는지 확인합니다.
1. **연결 대상**의 IP 주소가 원격 컴퓨터의 IP 주소와 일치하는지 확인합니다.
1. 원격 컴퓨터에서 원격 디버깅 포트를 열었는지와 연결 대상에 `:5678`과 같은 포트 접미사를 포함했는지 확인합니다.
    - 다른 포트를 사용해야 하는 경우에는 `debugpy.listen((host, port))`와 같이 `listen`에 포트를 지정할 수 있습니다. 이 경우 방화벽에서 해당 특정 포트를 엽니다.
1. `pip3 list`로 반환된 원격 컴퓨터에 설치된 debugpy 버전이 Visual Studio에서 사용 중인 Python 도구 버전에서 사용되는 debugpy 버전과 일치하는지 아래 표에서 확인합니다. 필요한 경우 원격 컴퓨터에서 debugpy를 업데이트합니다.

    | Visual Studio 버전 | Python 도구/debugpy 버전 |
    | --- | --- |
    | 2019 16.6 | 1.0.0b5 |
    | 2019 16.5 | 1.0.0b1 |

> [!NOTE]
> Visual Studio 2019 버전 16.0~16.4는 debugpy가 아닌 ptvsd를 사용했습니다. 이 연습에서 이러한 버전에 대한 프로세스는 유사하지만 함수 이름은 다릅니다. Visual Studio 2019 버전 16.5는 debugpy를 사용하지만 함수 이름은 ptvsd에서와 동일합니다. `listen` 대신 `enable_attach`를 사용합니다. `wait_for_client` 대신 `wait_for_attach`를 사용합니다. `breakpoint` 대신 `break_into_debugger`를 사용합니다.

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>레거시 디버깅에 ptvsd 3.x 사용
Visual Studio 2017 버전 15.8 이상에서는 ptvsd 버전 4.1 이상에 기반한 디버거를 사용합니다. Visual Studio 2019 버전 16.5 이상에서는 debugpy에 기반한 디버거를 사용합니다. 이러한 버전의 디버거는 Python 2.7 및 Python 3.5 이상과 호환됩니다. Python 2.6, 3.1~3.4 또는 IronPython을 사용하는 경우 Visual Studio에서는 **디버거는 이 Python 환경을 지원하지 않습니다.** 라는 오류를 표시합니다. 다음 정보는 ptvsd 3.x를 사용하는 원격 디버깅에만 적용됩니다.

1. ptvsd 3.x에서 `enable_attach` 함수를 사용하려면 실행 중인 스크립트에 대한 액세스를 제한하는 첫 번째 인수로 “secret”을 전달해야 했습니다. 원격 디버거를 연결할 때 이 비밀을 입력합니다. (권장되지는 않지만, `enable_attach(secret=None)`를 사용하여 모든 사용자의 연결을 허용할 수 있습니다.)

1. 연결 대상 URL은 `tcp://<secret>@<ip_address>:5678`입니다. 여기서 `<secret>`은 Python 코드의 `enable_attach`에 전달된 문자열입니다.

기본적으로 ptvsd 3.x 원격 디버그 서버에 대한 연결은 비밀로만 보호되고 모든 데이터는 일반 텍스트로 전달됩니다. 보다 안전한 연결을 위해 ptvsd 3.x에서는 다음과 같이 설정하는 `tcsp` 프로토콜을 사용하여 SSL을 지원합니다.

1. 원격 컴퓨터에서 다음과 같이 openssl을 사용하여 별도의 자체 서명된 인증서 및 키 파일을 생성합니다.

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    openssl에서 메시지를 표시하면 **일반 이름**에 대해 호스트 이름 또는 IP 주소(어느 쪽이든 연결에 사용하는 항목)를 사용합니다.

    (자세한 내용은 Python `ssl` 모듈 문서의 [Self-signed certificates](https://docs.python.org/3/library/ssl.html#self-signed-certificates)(자체 서명된 인증서)를 참조하세요. 해당 문서의 명령은 결합된 단일 파일만 생성합니다.)

1. 코드에서 파일 이름을 값으로 사용하는 `certfile` 및 `keyfile` 인수를 포함하도록 `enable_attach`에 대한 호출을 수정합니다(이러한 인수는 표준 `ssl.wrap_socket` Python 함수에 대해 같은 의미를 지님).

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    로컬 컴퓨터의 코드 파일에서도 같은 변경을 수행할 수 있지만, 이 코드는 실제로 실행되지 않으므로 필요 없습니다.

1. 원격 컴퓨터에서 Python 프로그램을 다시 시작하여 디버깅을 준비합니다.

1. Visual Studio가 설치된 Windows 컴퓨터에서 신뢰할 수 있는 루트 CA에 인증서를 추가하여 채널을 보호합니다.

    1. 로원격 컴퓨터의 인증서 파일을 로컬 컴퓨터에 복사합니다.
    1. **제어판**을 열고 **관리 도구** > **컴퓨터 인증서 관리**로 이동합니다.
    1. 나타나는 창의 왼쪽에서 **신뢰할 수 있는 루트 인증 기관**을 확장하고, **인증서**를 마우스 오른쪽 단추로 클릭하고, **모든 작업** > **가져오기**를 선택합니다.
    1. 원격 컴퓨터에서 복사한 *.cer* 파일로 이동하여 이 파일을 선택한 다음, 대화 상자를 클릭하여 가져오기를 완료합니다.

1. 앞에서 설명한 대로 Visual Studio에서 연결 프로세스를 반복하고 이제 **연결 대상**(또는 **한정자**)에 대한 프로토콜로 `tcps://`를 사용합니다.

    ![SSL로 원격 디버깅 전송 선택](../../media/remote-debugging-qualifier-ssl.png)

1. SSL을 통해 연결하면 Visual Studio에서 잠재적인 인증서 문제에 대한 메시지를 표시합니다. 경고를 무시하고 계속할 수 있지만, 채널이 여전히 도청으로부터 암호화되더라도 메시지 가로채기(man-in-the-middle) 공격에 개방될 수 있습니다.

    1. 아래의 **원격 인증서를 신뢰할 수 없습니다.** 경고가 표시되는 경우 신뢰할 수 있는 루트 CA에 인증서를 제대로 추가하지 않았음을 의미합니다. 해당 단계를 확인하고 다시 시도합니다.

        ![SSL 인증서를 신뢰할 수 있습니다. 경고](../../media/remote-debugging-ssl-warning.png)

    1. 아래의 **원격 인증서 이름이 호스트 이름과 일치하지 않습니다.** 경고가 표시되는 경우 인증서를 만들 때 **일반 이름**으로 올바른 호스트 이름 또는 IP 주소를 사용하지 않았음을 의미합니다.

        ![SSL 인증서 호스트 이름 경고](../../media/remote-debugging-ssl-warning2.png)
