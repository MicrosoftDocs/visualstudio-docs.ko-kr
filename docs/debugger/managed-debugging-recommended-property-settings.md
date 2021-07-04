---
title: C#, VB의 권장 디버거 속성 설정 | Microsoft Docs
description: 모든 관리형 디버깅에 대해 동일해야 하는 빌드 및 컴파일 속성 설정을 확인합니다. 다른 설정은 프로젝트 형식에 따라 달라질 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c2262194dbb6a8f4b0a47b4fcfc7f9f696c60167
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390400"
---
# <a name="managed-debugging-recommended-property-settings"></a>관리 디버깅: 권장 속성 설정
일부 속성은 모든 관리되는 디버깅 시나리오에서 동일한 방식으로 설정해야 합니다.

 다음 표에는 권장 속성 설정이 나와 있습니다.

 여기에 나와 있지 않은 설정은 관리되는 프로젝트의 형식에 따라 서로 다를 수 있습니다. 예를 들어 **시작 작업** 은 Windows Forms 프로젝트와 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 프로젝트에서 서로 다르게 설정됩니다.

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>빌드(C#) 또는 컴파일(Visual Basic) 탭의 구성 속성

|**속성 이름**|**설정**|
|-----------------------|-----------------|
|**DEBUG 상수 정의**|C# 및 F#: 확인란을 선택합니다. 이렇게 하면 애플리케이션에서 Debug 클래스를 사용할 수 있습니다.|
|**TRACE 상수 정의**|C# 및 F#: 확인란을 선택합니다. 이렇게 하면 애플리케이션에서 Trace 클래스를 사용할 수 있습니다.|
|**코드 최적화**|C#, F# 및 Visual Basic: false로 설정합니다. 코드를 최적화하면, 생성되는 명령이 소스 코드에 직접 대응되지 않기 때문에 디버깅하기 어렵습니다. 최적화된 코드에만 나타나는 버그가 프로그램에서 발견될 경우에도 이 설정을 선택할 수 있지만, **디스어셈블리** 창에 표시되는 코드는 코드 편집기에 표시되는 코드와 일치하지 않는 최적화된 원본에서 생성된다는 점에 주의해야 합니다. 최적화된 코드를 디버깅하려면 내 코드만을 해제해야 합니다. [단계별 코드 실행을 내 코드만으로 제한](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)을 참조하세요.<br /><br /> 자세한 내용은 [C# 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md) 또는 [Visual Basic 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)을 참조하세요.|
|**출력 경로**|bin\Debug\\로 설정합니다.|
|**고급 컴파일 옵션**|Visual Basic만 다음 표에서 설명하는 고급 속성을 설정하려면 **고급** 을 클릭합니다.|

### <a name="advanced-compiler-settings-dialog-box"></a>고급 컴파일러 설정 대화 상자

|**속성 이름**|**설정**|
|-----------------------|-----------------|
|**최적화 사용**|false로 설정합니다. 그 이유에 관한 설명은 위 표의 **코드 최적화** 옵션 부분을 참조하세요.|
|**디버깅 정보 생성**|이 확인란을 선택하면 컴파일 시 /DEBUG 플래그가 설정됩니다. 이렇게 하면 디버깅을 진행하는 데 필요한 정보가 생성됩니다.|
|**DEBUG 상수 정의**|`DEBUG` 상수를 정의하려면 이 확인란을 선택합니다. 이렇게 하면 애플리케이션에 <xref:System.Diagnostics.Debug> 클래스를 사용할 수 있습니다.|
|**TRACE 상수 정의**|`TRACE` 상수를 정의하려면 이 확인란을 선택합니다. 이렇게 하면 애플리케이션에 <xref:System.Diagnostics.Trace> 클래스를 사용할 수 있습니다.|

## <a name="see-also"></a>참조
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [C#, F#, and Visual Basic Project Types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)(C#, F# 및 Visual Basic 프로젝트 형식)