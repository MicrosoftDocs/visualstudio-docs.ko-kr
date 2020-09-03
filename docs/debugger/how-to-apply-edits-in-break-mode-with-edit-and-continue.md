---
title: 편집하며 계속하기를 사용하여 중단 모드에서 편집 적용 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acdd5b85c77b177dfb5f6d8129594967e902337c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350303"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>방법: 편집하며 계속하기를 사용하여 중단 모드에서 편집 적용(Visual Basic)
편집하며 계속하기를 사용하면 실행을 중지한 후에 다시 시작하지 않고도 중단 모드에서 코드를 편집한 다음 계속 진행할 수 있습니다.

디버그하는 동안 편집하며 계속하기 사용의 제한 사항은 [지원되는 코드 변경(C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)을 참조하세요.

### <a name="to-edit-code-in-break-mode"></a>중단 모드에서 코드를 편집하려면

1. 다음 중 한 가지 방법으로 중단 모드를 시작합니다.

    - 코드에 중단점을 설정한 다음, **디버그** 메뉴에서 **디버깅 시작**을 선택하고 애플리케이션이 중단점에 도달할 때까지 기다립니다.

         또는

    - 디버깅을 시작한 다음, **디버그** 메뉴에서 **모두 중단**을 선택합니다.

         또는

    - 예외가 발생하면 **예외 도우미**에서 **편집 사용**을 선택합니다.

2. 지원되는 코드를 원하는 대로 변경합니다.

     자세한 내용은 [지원되는 코드 변경(C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)을 참조하세요.

    > [!NOTE]
    > 편집하며 계속하기에서 허용되지 않는 코드 변경 작업을 수행하면 자주색 물결선이 편집 내용 아래에 밑줄로 표시되고 해당 작업이 작업 목록에 나타납니다. 잘못된 코드 변경 내용을 취소하지 않으면 코드 실행을 계속 진행할 수 없습니다.

3. **디버그** 메뉴에서 **계속**을 클릭하여 실행을 다시 시작합니다.

     적용한 편집 내용이 프로젝트에 통합된 상태로 코드가 실행됩니다.

## <a name="see-also"></a>참조
- [지원되는 코드 변경(C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [편집하며 계속하기(Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
