---
title: '방법: 편집하며 계속하기 설정/해제 | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430528"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>방법: 편집하며 계속하기 설정/해제(C#, VB, C++)

**편집하며 계속하기**는 디자인 타임에 Visual Studio **옵션** 대화 상자에서 사용하거나 사용하지 않도록 설정할 수 있습니다. **편집하며 계속하기**는 디버그 빌드에서만 작동합니다. 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

네이티브 C++의 경우 **편집하며 계속하기**를 실행하려면 `/INCREMENTAL` 옵션을 사용해야 합니다. C++의 기능 요구 사항에 대한 자세한 내용은 이 [블로그 게시물](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) 및 [편집하며 계속하기(C++)](../debugger/edit-and-continue-visual-cpp.md)를 참조하세요.

**편집하며 계속하기를 사용하거나 사용하지 않도록 설정하려면:**

1. 디버그 세션을 진행 중인 경우 디버깅을 중지합니다(**디버그** > **디버깅 중지** 또는 **Shift**+**F5**).

1. **도구** > **옵션**(또는 **디버그** > **옵션**) > **디버깅** > **일반**에서 오른쪽 창의 **편집하며 계속하기**를 선택합니다.

    > [!NOTE]
    > IntelliTrace를 사용하도록 설정되어 있고 IntelliTrace 이벤트 및 호출 정보를 모두 수집하는 경우 편집하며 계속하기를 사용하지 않도록 설정됩니다. 자세한 내용은 [IntelliTrace](../debugger/intellitrace.md)를 참조하세요.

1. C++ 코드의 경우 **네이티브 편집하며 계속하기 사용**이 선택되었는지 확인하고 다음과 같은 추가 옵션을 설정합니다.
    - **계속할 때 변경 내용 적용(네이티브 전용)**

      이 옵션을 선택하면 중단 상태에서 계속해서 디버그하면 Visual Studio에서는 코드 변경 내용을 자동으로 컴파일하고 적용합니다. 이 옵션을 선택하지 않으면 **디버그** > **코드 변경 내용 적용**을 사용하여 변경 내용을 적용할 수 있습니다.

    - **부실 코드 경고(네이티브 전용)**

      이 옵션을 선택하면 부실 코드에 대한 경고가 표시됩니다.

1. **확인**을 클릭합니다.
