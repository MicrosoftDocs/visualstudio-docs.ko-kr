---
title: '보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 확실하지 않은 경우 이 프로세스에 연결하면 안 됨 | Microsoft Docs'
ms.date: 1/15/2021
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ec174a03e62cb8cb033be0b92db679fb19f0180
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881258"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 잘 모르겠으면 이 프로세스에 연결하지 마세요.

이 경고 대화 상자는 부분적으로 신뢰할 수 있는 코드가 포함되어 있거나 신뢰할 수 없는 사용자가 소유한 프로세스에 연결할 때 연결이 실행되기 바로 전에 표시됩니다. 악의적인 코드가 포함된 신뢰할 수 없는 프로세스는 디버깅을 수행하는 컴퓨터에 손상을 줄 수 있습니다. 프로세스를 신뢰할 수 없는 이유가 있는 경우에는 **취소** 를 클릭하여 디버깅을 중지해야 합니다.

IIS 시나리오에서는 신뢰할 수 없는 사용자 지정 애플리케이션 풀을 사용하는 경우 해당 경고가 표시될 수 있습니다.

합법적인 시나리오를 디버그할 때 해당 경고를 표시하지 않으려면:

1. Visual Studio를 닫습니다.

1. `DisableAttachSecurityWarning` 레지스트리 키 값을 1로 설정합니다.

   `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger`에서 키를 찾거나 만들고 1로 설정합니다.

   Visual Studio 2017부터, 전체 레지스트리 설정을 보려면 프라이빗 레지스트리 하이브를 로드해야 합니다. 자세한 내용은 [Visual Studio 2017 레지스트리를 검사하는 방법](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md)을 참조하세요. Visual Studio를 시작하기 전에 프라이빗 레지스트리 하이브를 언로드해야 합니다.

1. Visual Studio를 다시 시작합니다.

1. 시나리오의 디버깅을 마친 후 이 값을 0으로 다시 설정하고 Visual Studio를 다시 시작합니다.

"신뢰할 수 있는 사용자"에는 사용자 자신을 비롯하여 `aspnet`, `localsystem`, `networkservice` 및 `localservice`와 같은 .NET Framework가 설치된 컴퓨터에 일반적으로 정의되어 있는 표준 사용자 집합도 포함됩니다.

## <a name="uielement-list"></a>UI 요소 목록

 이름 - 디버그하도록 요청된 어셈블리의 이름입니다.

 사용자 - 현재 사용자입니다.

 연결 - 연결하여 계속 디버그합니다.

 연결 안 함 - 프로세스에 연결하지 않습니다.

## <a name="see-also"></a>참조
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [디버거 보안](../debugger/debugger-security.md)
