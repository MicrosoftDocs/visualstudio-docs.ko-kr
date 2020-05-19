---
title: 원격 디버깅을 위한 방화벽 구성 대화 상자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a2511fc2adfa63ff28f8459f48cbdf4b4623ff5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745658"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>원격 디버깅을 위한 방화벽 구성 대화 상자
이 대화 상자는 Windows 방화벽에서 디버거가 네트워크를 통해 정보를 받는 것을 차단할 때 나타납니다. 원격 디버깅을 계속하려면 디버거가 정보를 받을 수 있도록 방화벽에서 한 지점을 열어야 합니다.

> [!CAUTION]
> 방화벽에서 한 지점을 열면 방화벽을 통해 차단해야 하는 보안 위협에 컴퓨터가 노출될 수 있습니다. 원격 디버깅을 위해 빈 영역을 열면 Visual Studio 2015에서 4020 및 4021 포트가 차단 해제됩니다. 다른 버전의 Visual Studio에서는 다른 포트 번호가 사용됩니다. 자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요. 또한 디버거가 포트를 추가로 열 수 있습니다. 자세한 내용은 [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)을 참조하세요.

## <a name="uielement-list"></a>UI 요소 목록
 **원격 디버깅 취소** - 원격 디버깅 시도를 취소합니다. 컴퓨터의 보안 설정은 그대로 유지됩니다.

 **로컬 네트워크(서브넷)의 컴퓨터에서 원격 디버깅 차단 해제** - 로컬 서브넷에 있는 머신의 원격 디버깅을 사용하도록 설정합니다. 이 옵션을 설정하면 로컬 서브넷에 있는 컴퓨터의 보안이 취약해질 수 있지만 방화벽은 계속해서 서브넷 외부에서 들어오는 정보를 차단합니다.

 **모든 컴퓨터에서 원격 디버깅 차단 해제** - 네트워크에 있는 모든 머신의 원격 디버깅을 사용하도록 설정합니다. 이 설정은 보안이 가장 취약합니다.

## <a name="see-also"></a>참조

- [디버거 보안](../debugger/debugger-security.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [사용자 인터페이스 참조 디버그](../debugger/debugging-user-interface-reference.md)