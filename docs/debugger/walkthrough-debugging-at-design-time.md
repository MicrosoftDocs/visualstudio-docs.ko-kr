---
title: 디자인 타임 시 디버그 | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bc5d08e8b0ae71acb846e1e863e24e8b8def0ee
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183563"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Visual Studio(C#, C++/CLI, Visual Basic, F#)에서 디자인 타임 시 디버그

앱이 실행 중인 시간 대신 디자인 타임에 코드를 디버그하려면 **즉시 실행** 창을 사용할 수 있습니다.

선언적 데이터 바인딩 시나리오와 같이 XAML 디자이너에서 앱 뒤의 XAML 코드를 디버그하려면 **디버그** > **프로세스**에 연결을 사용할 수 있습니다.

## <a name="use-the-immediate-window"></a>즉시 실행 창 사용

앱을 실행하지 않고 Visual Studio **즉시 실행** 창을 사용하여 함수나 서브루틴을 실행할 수 있습니다. 함수 또는 서브루틴에 중단점이 포함된 경우 Visual Studio는 중단점에서 중단됩니다. 그런 다음 디버거 창을 사용하여 프로그램 상태를 조사할 수 있습니다. 이 기능을 ‘디자인 타임에 디버깅’이라고 합니다.

다음은 Visual Basic에 있는 예입니다. C#, F# 및 C++/CLI 앱에서 디자인 타임에 **즉시 실행** 창을 사용할 수도 있습니다.

1. 다음 코드를 빈 Visual Basic 콘솔 앱에 붙여넣습니다.

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. **End Function** 줄에 중단점을 설정합니다.

1. **디버그** > **창** > **즉시 실행**을 선택하여 **즉시 실행** 창을 엽니다. `?MyFunction`을 창에 입력한 다음, **Enter** 키를 누릅니다.

   중단점에 도달하고 **로컬** 창의 **MyFunction** 값이 **1**입니다. 앱이 중단 모드에 있는 동안 호출 스택과 기타 디버깅 창을 검사할 수 있습니다.

1. Visual Studio 도구 모음에서 **계속**을 선택합니다. 앱이 종료되면 **즉시 실행** 창에 **1**이 반환됩니다. 여전히 디자인 모드에 있는지 확인합니다.

1. **직접 실행 창**에 `?MyFunction`을 다시 입력하고 **Enter** 키를 누릅니다. 중단점에 도달하고 **로컬** 창의 **MyFunction** 값이 **2**입니다.

1. **계속**을 선택하지 않고 **즉시 실행** 창에 `?MySub()`를 입력한 다음, **Enter** 키를 누릅니다. 중단점에 도달하고 **로컬** 창의 **MyFunction** 값이 **3**입니다. 앱이 중단 모드에 있는 동안 앱 상태를 검사할 수 있습니다.

1. **계속**을 선택합니다. 중단점에 다시 도달하고 **로컬** 창의 **MyFunction** 값이 이제 **2**입니다. **즉시 실행** 창에 **식을 계산했지만 값이 없습니다.** 라고 표시됩니다.

1. **계속**을 다시 선택합니다. 앱이 종료되고 **즉시 실행** 창에 **2**가 반환됩니다. 여전히 디자인 모드에 있는지 확인합니다.

1. **즉시 실행** 창의 내용을 지우려면 창 내부를 마우스 오른쪽 단추로 클릭하고 **모두 지우기**를 선택합니다.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>XAML 디자이너에 연결하여 디자인 타임에 사용자 지정 XAML 컨트롤 디버그

1. Visual Studio에서 솔루션 또는 프로젝트를 엽니다.

1. 솔루션/프로젝트를 빌드합니다.

1. 디버그할 사용자 지정 컨트롤이 포함된 XAML 페이지를 엽니다.

   UWP 프로젝트가 Windows 빌드 16299 이상을 대상으로 하는 경우 이 단계에서 *UwpSurface.exe* 프로세스를 시작합니다. WPF 프로젝트가 Windows 빌드 16299 이상을 대상으로 하는 경우 이 단계에서 *WpfSurface.exe* 프로세스를 시작합니다. WPF 또는 UWP가 Windows 빌드 16299 이전 버전인 경우 이 단계에서 *XDesProc.exe* 프로세스를 시작합니다. 

1. Visual Studio의 두 번째 인스턴스를 엽니다. 두 번째 인스턴스에서 솔루션 또는 프로젝트를 열지 마세요.

1. Visual Studio의 두 번째 인스턴스에서 **디버그** 메뉴를 열고 **프로세스에 연결...** 을 선택합니다.

1. 프로젝트 형식(이전 단계 참조)에 따라 사용 가능한 프로세스 목록에서 *UwpSurface.exe*, *WpfSurface.exe* 또는 *XDesProc.exe* 프로세스를 선택합니다.

1. **프로세스에 연결** 대화 상자의 **연결 대상** 필드에서 디버그하려는 사용자 지정 컨트롤에 올바른 코드 형식을 선택합니다.

   사용자 지정 컨트롤을 .NET 언어로 작성한 경우 **관리됨(CoreCLR)** 과 같은 적절한 .NET 코드 형식을 선택합니다. 사용자 지정 컨트롤을 C++로 작성한 경우 **원시**를 선택합니다.

1. **연결** 단추를 클릭하여 Visual Studio의 두 번째 인스턴스를 연결합니다.

1. Visual Studio의 두 번째 인스턴스에서 디버그하려는 사용자 지정 컨트롤과 연결된 코드 파일을 엽니다. 전체 솔루션 또는 프로젝트가 아닌 파일만 열어야 합니다.

1. 이전에 연 파일에 필요한 중단점을 배치합니다.

1. Visual Studio의 첫 번째 인스턴스에서 디버그하려는 사용자 지정 컨트롤이 들어 있는 XAML 페이지(이전 단계에서 연 페이지)를 닫습니다.

1. Visual Studio의 첫 번째 인스턴스에서 이전 단계에서 닫은 XAML 페이지를 엽니다. 그러면 Visual Studio의 두 번째 인스턴스에서 설정한 첫 번째 중단점에서 디버거가 중지됩니다.

1. Visual Studio의 두 번째 인스턴스에서 코드를 디버그합니다.

## <a name="see-also"></a>참조
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [디버거 보안](../debugger/debugger-security.md)