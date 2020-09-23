---
title: 방화벽 인증 안 함 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
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
ms.openlocfilehash: a8548880df8c69fa59d58bf4c13f7f547ad359bd
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852721"
---
# <a name="error-firewall-no-authentication"></a>오류: 방화벽 인증 안 함
원격 컴퓨터의 인터넷 연결 방화벽이 원격 디버깅을 허용하도록 설정되어 있지 않습니다. `No Authentication`을 사용하여 원격으로 디버깅하는 경우 msvsmon.exe가 예외 목록에 추가되어 있어야 합니다. 일부 IPSEC 포트를 열어야 할 수도 있습니다.

> [!NOTE]
> 원격 디버거는 Windows 방화벽을 자동으로 구성할 수 있습니다. 타사 소프트웨어 방화벽이나 하드웨어 방화벽과 같은 Windows 방화벽 이외의 방화벽을 사용하는 경우 원격 디버깅을 허용하도록 방화벽을 수동으로 구성해야 합니다. 이렇게 하려면 msvsmon.exe가 수신 대기하는 TCP/IP 포트에서 트래픽을 허용합니다. 기본적으로 이러한 포트는 포트 4018 및 4019입니다. 4018은 모든 운영 체제에서 사용되고, 4019는 x86 프로세스의 디버깅을 허용하기 위해 Windows x64에서만 사용됩니다.

 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.