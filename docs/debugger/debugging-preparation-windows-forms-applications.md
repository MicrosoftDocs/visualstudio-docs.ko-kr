---
title: Windows Forms 앱 디버깅 준비 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9e98411a009ea4345b567cbc38e6cf94c037323
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916390"
---
# <a name="debugging-preparation-windows-forms-applications"></a>디버깅 준비 중: Windows Forms 응용 프로그램
Windows Forms 프로젝트 템플릿은 Windows Forms 애플리케이션을 만듭니다. 이러한 형식의 애플리케이션은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 쉽게 디버깅할 수 있습니다. 자세한 내용은 [Windows 애플리케이션 프로젝트 만들기](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))를 참조하세요.

 프로젝트 템플릿을 사용하여 Windows Forms 프로젝트를 만들면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서는 디버그 및 릴리스 구성에 필요한 설정을 자동으로 만듭니다. 필요하면 이 설정을 변경할 수 있습니다. 이러한 설정은 **\<프로젝트 이름> 속성 페이지** 대화 상자(Visual Basic의 **내 프로젝트**)에서 변경할 수 있습니다.

 자세한 내용은 [권장 속성 설정](../debugger/managed-debugging-recommended-property-settings.md)을 참조하세요.

 다음 표에서는 권장 속성 설정을 하나 더 보여 줍니다.

### <a name="configuration-properties-in-debug-tab"></a>디버그 탭의 구성 속성

|**속성 이름**|**설정**|
|-----------------------|-----------------|
|**시작 작업**|-   대부분의 경우 **시작 프로젝트**로 설정합니다. 디버깅(일반적으로 DLL 디버깅)을 시작할 때 다른 실행 파일을 시작하려면 **시작 외부 프로그램**으로 설정합니다.|

 Windows Forms 애플리케이션을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 내에서 디버깅하거나 이미 실행 중인 애플리케이션에 연결하여 디버깅할 수 있습니다. 연결에 대한 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>C#, F# 또는 Visual Basic Windows Forms 애플리케이션을 디버깅하려면

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 프로젝트를 엽니다.

2. 필요한 중단점을 만듭니다.

    Windows Forms 애플리케이션은 이벤트 구동 애플리케이션이므로 중단점은 이벤트 처리기 코드에 배치되거나 이벤트 처리기 코드에서 호출하는 메서드에 배치됩니다. 중단점이 배치되는 일반적인 이벤트는 다음과 같습니다.

   1. Click, Enter 같이 컨트롤에 연결된 이벤트

   2. Load, Activated 같이 애플리케이션 시작 및 종료에 연결된 이벤트

   3. 포커스 및 유효성 검사 이벤트

      자세한 내용은 [Windows Forms에서 이벤트 처리기 만들기](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms)를 참조하세요.

3. **디버그** 메뉴에서 **시작**을 클릭합니다.

4. [디버거 소개](../debugger/debugger-feature-tour.md)에 설명된 기술을 사용하여 디버그합니다.

## <a name="see-also"></a>참조
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [C#, F#, and Visual Basic Project Types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)(C#, F# 및 Visual Basic 프로젝트 형식)
- [방법: 디버그 및 릴리스 구성 설정](../debugger/how-to-set-debug-and-release-configurations.md)
- [C# 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)