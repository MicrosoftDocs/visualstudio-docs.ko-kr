---
title: '오류: Kerberos 인증 실패 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe13fd3d0dc7e29fc12d369ec0865bcbc97b1a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737662"
---
# <a name="error-kerberos-authentication-failed"></a>오류: Kerberos 인증 실패
원격 디버깅을 시작할 때 다음 오류 메시지가 나타날 수 있습니다.

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 이 오류는 로컬 시스템 또는 네트워크 서비스 계정으로 Visual Studio 원격 디버깅 모니터를 실행할 때 발생합니다. 이러한 계정 중 하나를 사용하는 경우 원격 디버거에서는 Kerberos 인증 연결을 설정하여 Visual Studio 디버거 호스트 컴퓨터와 통신해야 합니다.

 다음과 같은 경우에는 Kerberos 인증을 사용할 수 없습니다.

- 대상 컴퓨터 또는 디버거 호스트 컴퓨터가 도메인이 아닌 작업 그룹에 있는 경우

   \- 또는 -

- 도메인 컨트롤러에서 Kerberos가 해제된 경우

  Kerberos 인증을 사용할 수 없는 경우 Visual Studio 원격 디버깅 모니터를 실행하는 데 사용되는 계정을 변경해야 합니다. 해당 절차는 [오류: 대상 컴퓨터의 Visual Studio 원격 디버거 서비스가 이 컴퓨터에 다시 연결할 수 없습니다.](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)를 참조하세요.

  두 컴퓨터가 모두 같은 도메인에 연결되어 있는 경우에도 이 메시지가 나타나면 해당 컴퓨터의 DNS에서 디버거 호스트 컴퓨터의 이름을 제대로 확인하고 있는지 검사합니다. 다음 절차를 참조하십시오.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>대상 컴퓨터의 DNS에서 디버거 호스트 컴퓨터 이름을 제대로 확인하고 있는지 검사하려면

1. 대상 컴퓨터에서 **시작** 메뉴를 열고 **보조 프로그램**을 가리킨 다음, **명령 프롬프트**를 클릭합니다.

2. **명령 프롬프트** 창에 다음을 입력합니다.

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. `ping` 응답의 첫 번째 줄에는 지정된 컴퓨터의 DNS에서 반환하는 전체 컴퓨터 이름과 IP 주소가 표시됩니다.

4. 디버거 호스트 컴퓨터에서 **명령 프롬프트** 창을 열고 `ipconfig`를 실행합니다.

5. IP 주소 값을 비교합니다.

## <a name="see-also"></a>참조
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
