---
title: 편집하며 계속하기 사용(C#) | Microsoft Docs
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18d11f552d486fd9ebd7a95323e327324de14108
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851855"
---
# <a name="how-to-use-edit-and-continue-c"></a>방법: 편집하며 계속하기 사용(C#)
편집하며 계속하기를 사용하면 디버그 세션을 중지한 후 다시 시작하지 않고도 디버깅 중에 중단 모드에서 코드 변경을 수행하고 변경 내용을 적용할 수 있습니다.

편집하며 계속하기(C#)는 중단 모드에서 코드를 변경하면 자동으로 발생한 다음, **계속**, **단계** 또는 **다음 문 설정**을 사용하여 디버깅을 계속하거나 디버거 창에서 함수를 계산합니다.

자세한 내용은 [편집하며 계속하기(Visual C#)](../debugger/edit-and-continue-visual-csharp.md)를 참조하세요.

>[!NOTE]
>편집하며 계속하기는 SQL Server 최적화되거나 혼합된 코드 또는 CLR(공용 언어 런타임) 통합 코드에 대해 지원되지 않습니다. 지원되지 않는 다른 시나리오에 대한 자세한 내용은 [지원되는 코드 변경(C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)을 참조하세요. 이러한 시나리오 중 하나에서 편집하며 계속하기를 시도하면 편집하며 계속하기가 지원되지 않는다는 메시지 상자가 표시됩니다.

**편집하며 계속하기를 사용하거나 사용하지 않도록 설정하려면:**

1. 디버그 세션을 진행 중인 경우 디버깅을 중지합니다(**디버그** > **디버깅 중지** 또는 **Shift**+**F5**).

1. **도구** > **옵션**(또는 **디버그** > **옵션**) > **디버깅** > **일반**에서 **편집하며 계속하기 사용** 확인란을 선택하거나 선택 취소합니다.

설정은 디버그 세션을 시작하거나 다시 시작하면 적용됩니다.

**편집하며 계속하기를 사용하려면:**

1. 디버그하는 동안 중단 모드에서 소스 코드를 변경합니다.

1. **디버그** 메뉴에서 **계속**, **단계** 또는 **다음 문 설정**을 클릭하거나 디버거 창에서 함수를 계산합니다.

   새로운 컴파일된 코드를 사용하여 디버깅이 계속됩니다.

일부 유형의 코드 변경은 편집하며 계속하기에서 지원되지 않습니다. 자세한 내용은 [지원되는 코드 변경(C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)을 참조하세요.
