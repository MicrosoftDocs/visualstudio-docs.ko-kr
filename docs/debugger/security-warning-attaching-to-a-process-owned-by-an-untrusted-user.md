---
title: '보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 확실하지 않은 경우 이 프로세스에 연결하면 안 됨 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729772"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 잘 모르겠으면 이 프로세스에 연결하지 마세요.
이 경고 대화 상자는 부분적으로 신뢰할 수 있는 코드가 포함되어 있거나 신뢰할 수 없는 사용자가 소유한 프로세스에 연결할 때 연결이 실행되기 바로 전에 표시됩니다. 악의적인 코드가 포함된 신뢰할 수 없는 프로세스는 디버깅을 수행하는 컴퓨터에 손상을 줄 수 있습니다. 프로세스를 신뢰할 수 없는 이유가 있는 경우에는 **취소**를 클릭하여 디버깅을 중지해야 합니다.

 정상적인 시나리오를 디버그할 때 이 경고를 표시하지 않으려면 Visual Studio를 닫고 이 레지스트리 키의 값을 1로 설정한 다음(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`), Visual Studio를 다시 시작합니다. 시나리오의 디버깅을 마친 후 이 값을 0으로 다시 설정하고 Visual Studio를 다시 시작합니다.

 "신뢰할 수 있는 사용자"에는 사용자 자신을 비롯하여 `aspnet`, `localsystem`, `networkservice` 및 `localservice`와 같은 .NET Framework가 설치된 컴퓨터에 일반적으로 정의되어 있는 표준 사용자 집합도 포함됩니다.

## <a name="uielement-list"></a>UI 요소 목록
 이름 - 디버그하도록 요청된 어셈블리의 이름입니다.

 사용자 - 현재 사용자입니다.

 연결 - 연결하여 계속 디버그합니다.

 연결 안 함 - 프로세스에 연결하지 않습니다.

## <a name="see-also"></a>참조
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [디버거 보안](../debugger/debugger-security.md)