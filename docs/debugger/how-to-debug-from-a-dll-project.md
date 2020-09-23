---
title: DLL 프로젝트에서 디버그 | Microsoft Docs
ms.date: 10/10/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1102eb61f6cfda42f6e4e879f5c592c0c064ce0
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852141"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>방법: Visual Studio의 DLL 프로젝트에서 디버그(C#, C++, Visual Basic, F#)

DLL 프로젝트를 디버그하는 한 가지 방법은 DLL 프로젝트 속성에서 호출 앱을 지정하는 것입니다. 그런 다음 DLL 프로젝트 자체에서 디버깅을 시작할 수 있습니다. 이 방법이 작동하려면 구성하는 것과 같은 위치에 있는 동일한 DLL을 앱에서 호출해야 합니다. 앱이 다른 버전의 DLL을 찾아서 로드하는 경우 해당 버전에는 중단점이 포함되어 있지 않습니다. DLL을 디버그하는 다른 방법은 [DLL 프로젝트 디버깅](../debugger/debugging-dll-projects.md)을 참조하세요.

관리형 앱에서 네이티브 DLL을 호출하거나 네이티브 앱이 관리형 DLL을 호출하는 경우 DLL 및 호출하는 앱을 모두 디버그할 수 있습니다. 자세한 내용은 [방법: 혼합 모드에서 디버그](../debugger/how-to-debug-in-mixed-mode.md).

네이티브 및 관리형 DLL 프로젝트는 호출 앱을 지정하는 설정이 다릅니다.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>네이티브 DLL 프로젝트에서 호출 앱 지정

1. **솔루션 탐색기**에서 C++ DLL 프로젝트를 선택합니다. **속성** 아이콘을 선택하고 **Alt**+**Enter**를 누르거나 마우스 오른쪽 단추를 클릭하여 **속성**을 선택합니다.

1. **\<Project> 속성 페이지** 대화 상자에서 창의 맨 위에 있는 **구성** 필드가 **디버그**로 설정되어 있는지 확인합니다.

1. **구성 속성** > **디버깅**을 선택합니다.

1. **실행할 디버거** 목록에서 **로컬 Windows 디버거** 또는 **원격 Windows 디버거**를 선택합니다.

1. **명령** 또는 **원격 명령** 상자에서 호출 앱의 정규화된 경로와 파일 이름(예: *.exe* 파일)을 추가합니다.

   ![디버그 속성 창](../debugger/media/dbg-debugging-properties-dll.png "디버그 속성 창")

1. 필요한 프로그램 인수를 **명령 인수** 상자에 추가합니다.

1. **확인**을 선택합니다.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>관리형 DLL 프로젝트에서 호출 앱 지정

1. **솔루션 탐색기**에서 C# 또는 Visual Basic DLL 프로젝트를 선택합니다. **속성** 아이콘을 선택하고 **Alt**+**Enter**를 누르거나 마우스 오른쪽 단추를 클릭하여 **속성**을 선택합니다.

1. 창의 맨 위에 있는 **구성** 필드가 **디버그**로 설정되어 있는지 확인합니다.

1. **시작 작업**에서 다음을 수행합니다.

   - .NET Framework DLL의 경우 **시작 외부 프로그램**을 선택하고 호출 앱의 정규화된 경로와 이름을 추가합니다.

   - 또는 **URL로 브라우저 시작**을 선택하고 로컬 ASP.NET 앱의 URL을 입력합니다.

   - .NET Core DLL의 경우 **디버그** 속성 페이지가 다릅니다. **시작** 드롭다운에서 **실행 파일**을 선택한 다음 호출 앱의 정규화된 경로와 이름을 **실행 파일** 필드에 추가합니다.

1. **명령줄 인수** 또는 **애플리케이션 인수** 필드에 필요한 명령줄 인수를 추가합니다.

   ![C# 디버그 속성 창](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# 디버그 속성 창")

1. **파일** > **선택한 항목 저장** 또는 **Ctrl**+**S**를 사용하여 변경 내용을 저장합니다.

## <a name="debug-from-the-dll-project"></a>DLL 프로젝트에서 디버그

1. DLL 프로젝트에서 중단점을 설정합니다.

1. DLL 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

1. **솔루션 구성** 필드가 **디버그**로 설정되어 있는지 확인합니다. **F5** 키를 누르거나, 녹색 **시작** 화살표를 클릭하거나, **디버그** > **디버깅 시작**을 선택합니다.

디버깅이 중단점에 도달하지 않는 경우 DLL 출력(기본적으로 *\<project>\Debug* 폴더)이 호출 앱이 호출하는 위치인지 확인합니다.

## <a name="see-also"></a>참조
- [DLL 프로젝트 디버깅](../debugger/debugging-dll-projects.md)
- [C# 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)