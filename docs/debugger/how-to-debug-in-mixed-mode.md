---
title: 방법 - 혼합 모드에서 디버그 | Microsoft Docs
ms.date: 11/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53a40c4dc615b5e1b6a3caef3a99be5ab0b56327
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350110"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>방법: 혼합 모드에서 디버그(C#, C++, Visual Basic)

다음 절차에서는 관리 및 네이티브 코드에 디버깅을 사용하는 방법을 설명합니다. 이러한 디버깅을 혼합 모드 디버깅이라고도 합니다. 혼합 모드 디버깅 시나리오는 다음 두 가지가 있습니다.

- DLL을 호출하는 앱은 네이티브 코드로 작성되고 DLL은 관리 코드로 되어 있습니다.

- DLL을 호출하는 앱은 관리 코드로 작성되고 DLL은 네이티브 코드로 되어 있습니다. 이 시나리오에 대해 자세히 설명하는 자습서는 [관리 및 네이티브 코드 디버그](../debugger/how-to-debug-managed-and-native-code.md)를 참조하세요.

호출하는 앱 프로젝트의 **속성** 페이지에서 관리형 디버거 및 네이티브 디버거 둘 다 사용하도록 설정할 수 있습니다. 설정은 네이티브 앱과 관리형 앱 간에 서로 다릅니다.

호출하는 앱의 프로젝트에 액세스할 수 없는 경우 DLL 프로젝트에서 DLL을 디버그할 수 있습니다. DLL 프로젝트만 디버그하려면 혼합 모드에서 수행하지 않아도 됩니다. 자세한 내용은 [방법: DLL 프로젝트에서 디버그](../debugger/how-to-debug-from-a-dll-project.md)를 참조하세요.

> [!NOTE]
> 표시되는 대화 상자와 명령은 Visual Studio 설정이나 버전에 따라 이 문서에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** > **설정 가져오기 및 내보내기**를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>네이티브 호출 앱에 혼합 모드 디버깅 사용

1. **솔루션 탐색기**에서 C++ 프로젝트를 선택하고, **속성** 아이콘을 클릭하거나 **Alt**+**Enter**를 누르거나 마우스 오른쪽 단추를 클릭하여 **속성**을 선택합니다.

1. **\<Project> 속성 페이지** 대화 상자에서 **구성 속성**을 확장하고 **디버깅**을 선택합니다.

1. **디버거 형식**을 **혼합** 또는 **자동**으로 설정합니다.

1. **확인**을 선택합니다.

   ![혼합 모드 디버깅 사용](../debugger/media/dbg-mixed-mode-from-native.png "혼합된 모드 디버깅 사용")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>관리형 호출 앱에 혼합 모드 디버깅 사용

1. **솔루션 탐색기**에서 C# 또는 Visual Basic 프로젝트를 선택하고, **속성** 아이콘을 선택하거나 **Alt**+**Enter**를 누르거나 마우스 오른쪽 단추를 클릭하여 **속성**을 선택합니다.

1. **디버그** 탭을 선택하고 **네이티브 코드 디버깅 사용**을 선택합니다.

1. 속성 페이지를 닫아서 변경 내용을 저장합니다.

   ![네이티브 코드 디버깅 사용](../debugger/media/dbg-mixed-mode-from-csharp.png "네이티브 코드 디버깅 사용")

> [!NOTE]
> Visual Studio 2017부터 시작하는 대부분의 Visual Studio 버전에서는 프로젝트 속성 대신 *launchSettings.json* 파일을 사용하여 .NET Core 앱에서 네이티브 코드에 대한 혼합 모드 디버깅을 사용하도록 설정합니다. 자세한 내용은 [관리 및 네이티브 코드 디버그](../debugger/how-to-debug-managed-and-native-code.md)를 참조하세요.

## <a name="see-also"></a>참조

- [방법: DLL 프로젝트에서 디버그](../debugger/how-to-debug-from-a-dll-project.md)