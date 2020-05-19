---
title: '오류: 대상 컴퓨터에서 DNS가 올바르게 구성되었는지 확인 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
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
ms.openlocfilehash: c8a9a5346016964882bb524187d01ca83c203be1
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911553"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>오류: 대상 컴퓨터에서 DNS가 올바르게 구성되었는지 확인
원격으로 디버깅할 때 다음 오류 메시지가 나타날 수 있습니다.

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 이 오류는 대상 컴퓨터가 Visual Studio 디버거 호스트 컴퓨터의 이름을 확인할 수 없는 경우에 발생합니다. 대상 컴퓨터의 DNS 설정을 확인하십시오.

- Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 또는 Windows Server 2008 R2에서 DNS 설정을 확인하는 방법을 보려면 **시작** 메뉴에서 **도움말 및 지원**을 선택하고 **TCP/IP 설정 변경**을 검색하세요.

- 자세한 내용은 [Microsoft Windows 웹 사이트](https://www.microsoft.com/windows/)를 방문하거나 **TCP/IP 설정 변경**을 검색하세요.

  DNS 문제를 해결할 수 없는 경우 다른 계정으로 원격 디버거를 실행해 볼 수 있습니다. 이 오류는 로컬 시스템 또는 네트워크 서비스 계정으로 원격 디버거를 실행하는 경우에만 발생합니다. 다른 계정으로 원격 디버거를 실행하는 경우 DNS를 요구하지 않는 NTLM 인증을 사용할 수 있습니다. 을 선택합니다. 해당 절차는 [오류: 대상 컴퓨터의 Visual Studio 원격 디버거 서비스가 이 컴퓨터에 다시 연결할 수 없습니다.](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)를 참조하세요.
