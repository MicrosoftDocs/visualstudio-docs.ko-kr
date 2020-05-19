---
title: IntelliTrace 기능 | Microsoft Docs
ms.date: 09/19/2018
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcdb1b2b6dc4b64d180eb03fc76b26b4ef16e9d0
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911413"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>IntelliTrace 기능(C#, Visual Basic, C++)

IntelliTrace를 사용하여 애플리케이션의 이벤트 및 메서드 호출을 기록하고 실행 중 다양한 지점에서 상태(호출 스택 및 지역 변수 값)를 검사할 수 있습니다. 평소와 같이 디버깅을 시작하면 됩니다. IntelliTrace가 기본적으로 설정되어 있으므로 **이벤트** 탭 아래의 새로운 **진단 도구** 창에서 IntelliTrace가 기록하는 정보를 확인할 수 있습니다. 이벤트를 선택하고 **기록 디버깅 활성화**를 클릭하면 호출 스택 및 이 이벤트에 대해 기록된 로컬 변수를 볼 수 있습니다.

단계별 설명을 보려면 [연습: IntelliTrace 사용](../debugger/walkthrough-using-intellitrace.md)을 참조하세요.

IntelliTrace는 Visual Studio Enterprise Edition에서 사용할 수 있으며 Visual Studio Professional 또는 Community Edition에서는 사용할 수 없습니다.

IntelliTrace가 설정되어 있는지 확인하려면 **도구 > 옵션 > IntelliTrace** 옵션 페이지를 엽니다. **IntelliTrace 사용**은 기본적으로 선택되어 있어야 합니다.

> [!NOTE]
> **IntelliTrace** 옵션 페이지에 있는 모든 설정의 범위는 개별 프로젝트나 솔루션이 아니라 Visual Studio 전체입니다. 이 설정에서 변경된 내용은 Visual Studio의 모든 인스턴스, 모든 디버깅 세션 및 모든 프로젝트나 솔루션에 적용됩니다.

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a> IntelliTrace에서 기록하는 이벤트 선택(C#, Visual Basic)

특정 IntelliTrace 이벤트에 대한 기록을 설정하거나 해제할 수 있습니다.

디버그 중이면 디버깅을 중지합니다. **도구 > 옵션 > IntelliTrace > IntelliTrace 이벤트**로 이동합니다. IntelliTrace에서 기록하도록 지정할 이벤트를 선택합니다.

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a> 스냅샷 수집(C#, Visual Basic, C++)

이 기능은 기본적으로 사용하도록 설정되지 않지만, IntelliTrace는 모든 중단점 및 디버거 한 단계 실행 이벤트에서 애플리케이션의 스냅샷을 캡처할 수 있으며, 기록 디버깅 세션에서 해당 스냅샷을 볼 수 있습니다. 스냅샷은 전체 애플리케이션 상태를 보여 줍니다. 스냅샷 캡처를 사용하도록 설정하려면 **도구 > 옵션 > IntelliTrace > 일반**으로 이동하고 **IntelliTrace 스냅샷(관리 및 네이티브)** 을 선택합니다. 자세한 내용은 [IntelliTrace를 사용하여 이전 앱 상태 검사](../debugger/view-historical-application-state.md)를 참조하세요.

스냅샷은 Visual Studio Enterprise 2017 버전 15.5 이상에서 사용할 수 있으며 Windows 10 1주년 업데이트 이상이 필요합니다.  .NET Core 및 ASP.NET Core 앱의 경우 Visual Studio Enterprise 2017 버전 15.7이 필요합니다. Windows를 대상으로 하는 네이티브 앱의 경우 Visual Studio Enterprise 2017 버전 15.9 미리 보기 2가 필요합니다.

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a> IntelliTrace 이벤트 및 호출 정보 수집(C#, Visual Basic)

이 기능은 기본적으로 사용하도록 설정되어 있지 않지만, IntelliTrace는 이벤트를 통해 메서드 호출을 기록할 수 있습니다. 메서드 호출 컬렉션을 사용하도록 설정하려면 **도구 > 옵션 > IntelliTrace > 일반**으로 이동하고 **IntelliTrace 이벤트 및 호출 정보(관리만)** 를 선택합니다.

현재 .NET Core 및 ASP.NET Core 앱의 호출 정보는 사용할 수 없습니다.

이렇게 하면 호출 스택 이력을 참조하고 코드에서 호출을 통해 앞뒤로 이동할 수 있습니다. IntelliTrace는 메서드 이름, 메서드 시작/종료 지점, 특정 매개 변수 값, 반환 값 등의 데이터를 기록합니다.

> [!TIP]
> 이 옵션은 상당한 오버헤드를 추가하기 때문에 기본적으로 사용하도록 설정되어 있지 않습니다. IntelliTrace는 애플리케이션에서 발생하는 모든 메서드 호출을 가로채야 할 뿐만 아니라 이를 화면에 표시하거나 디스크에 보관하기 위해서는 훨씬 더 큰 데이터 세트을 처리해야 합니다.
>
> IntelliTrace가 기록하는 이벤트의 목록을 제한하고 수집하는 모듈 수를 최소한으로 유지하면 성능 오버헤드를 줄일 수 있습니다. 자세한 내용은 [IntelliTrace에서 기록하는 호출 정보의 양 제어](../debugger/intellitrace-features.md#ControlCallData)를 참조하세요.

### <a name="use-the-navigation-gutter"></a>탐색 여백 사용

코드 창의 왼쪽에 표시되는 탐색 여백을 사용할 수 있습니다. 탐색 여백 보이지 않으면 **도구 > 옵션 > IntelliTrace > 고급**으로 이동하고 **디버그 모드에서 탐색 여백 표시**를 선택합니다.

탐색 여백을 사용하면 기록 디버깅 모드에서 앞이나 뒤로 이동하며 메서드 호출 및 이벤트를 탐색할 수 있습니다. 기록 디버깅에 대한 자세한 내용은 [기록 디버깅](../debugger/historical-debugging.md)을 참조하세요. 다음과 같은 명령이 있습니다.

|||
|-|-|
|**여기에 디버거 컨텍스트 설정**|디버깅 컨텍스트를 표시되는 호출 기간으로 설정합니다.<br /><br /> 이 아이콘은 현재 호출 스택에만 나타납니다.|
|**호출 사이트로 돌아가기**|포인터와 디버깅 컨텍스트를 현재 함수가 호출된 지점으로 다시 이동합니다.<br /><br /> 라이브 디버깅 모드에 있는 경우 이 명령은 기록 디버깅을 설정합니다. 원래 실행이 중단되었던 지점으로 다시 이동하면 기록 디버깅이 해제되고 라이브 디버깅이 설정됩니다.|
|**이전 호출 또는 IntelliTrace 이벤트로 이동**|포인터와 디버깅 컨텍스트를 이전 호출 또는 이벤트 지점으로 다시 이동합니다.<br /><br /> 라이브 디버깅 모드에 있는 경우 이 명령은 기록 디버깅을 설정합니다.|
|**들어가기**|현재 선택한 함수를 한 단계씩 실행합니다.<br /><br /> 이 명령은 기록 디버깅 모드에 있는 경우에만 사용할 수 있습니다.|
|**다음 호출 또는 IntelliTrace 이벤트로 이동**|포인터와 디버깅 컨텍스트를 IntelliTrace 데이터가 있는 다음 호출 또는 이벤트로 이동합니다.<br /><br /> 이 명령은 기록 디버깅 모드에 있는 경우에만 사용할 수 있습니다.|
|**라이브 모드로 이동**|라이브 디버깅 모드로 돌아갑니다.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>IntelliTrace에서 줄 또는 메서드 검색

메서드 호출 정보가 사용하도록 설정된 경우에만 메서드를 검색할 수 있습니다. 특정 줄 또는 메서드에 대해 IntelliTrace 기록을 검색할 수 있습니다. 디버거 실행이 중단된 동안 함수 본문 내부를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴를 표시하거나 **IntelliTrace에서 이 줄 검색** 또는 **IntelliTrace에서 이 메서드 검색**을 클릭합니다.

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a> IntelliTrace에서 기록하는 호출 정보의 양 제어

기본적으로 IntelliTrace는 솔루션에 사용되는 모든 모듈에 대한 정보를 기록합니다. IntelliTrace에서 관심 있는 모듈에 대한 호출 정보만 기록하게 설정할 수 있습니다. **도구 > 옵션 > IntelliTrace > 모듈**에서 IntelliTrace에 포함할 모듈이나 IntelliTrace에서 제외할 모듈을 지정할 수 있습니다. IntelliTrace는 지정한 모듈에서 발생하는 이벤트만 수집하며 관심 있는 모듈 내에서 발생한 메서드 호출만 수집합니다.

여러 모듈을 추가하려면 문자열의 시작이나 끝 부분에 와일드카드 문자 *를 사용합니다. 모듈 이름에는 어셈블리 이름이 아닌 파일 이름을 사용합니다. 파일 경로는 사용할 수 없습니다.

모듈의 수를 최소로 유지합니다. 그러면 수집할 데이터의 양이 적기 때문에 성능이 높아집니다. 또한 검토할 데이터가 적기 때문에 UI의 노이즈가 줄어듭니다.

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a> 파일에 IntelliTrace 데이터 저장(C#, Visual Basic, C++)

디버그하는 동안 애플리케이션이 중단 상태일 때 **디버그 > IntelliTrace > IntelliTrace 세션 저장**으로 이동하여 IntelliTrace에서 수집된 데이터를 저장할 수 있습니다. 애플리케이션이 계속 실행 중이거나 디버깅을 중지한 경우에는 해당 메뉴 항목이 비활성화되어 IntelliTrace에서 수집된 데이터를 저장할 수 없게 됩니다.

**도구 > 옵션 > IntelliTrace > 고급**으로 이동하고 **이 디렉터리에 IntelliTrace 기록 저장**을 선택하여 자동으로 파일에 저장하도록 IntelliTrace를 구성할 수 있습니다. 생성된 파일에 대해 집합 크기를 구성할 수도 있습니다. 그러면 공간이 부족할 때 IntelliTrace가 오래된 데이터를 덮어씁니다. Visual Studio는 자동으로 저장되고 Visual Studio 호스팅 프로세스(vshost.exe)가 켜져 있는 경우 각 IntelliTrace 세션에 대해 두 개의 파일을 만듭니다.

> [!TIP]
> 디스크 공간을 절약하려면 더 이상 필요하지 않을 경우 자동 파일 저장을 끕니다. 기존 파일은 삭제되지 않습니다. 필요에 따라 언제든지 상황에 맞는 메뉴를 사용하여 파일에 저장할 수 있습니다.

IntelliTrace 데이터를 파일에 저장하면 IntelliTrace가 수집한 프로세스별로 .itrace 파일이 하나씩 생깁니다. 그러면 **파일 > 열기 > 파일**로 이동한 후 파일 열기 대화 상자에서 .itrace 파일을 선택하여 Visual Studio에서 .itrace 파일을 열 수 있습니다. 자세한 내용은 [저장된 IntelliTrace 데이터 사용](../debugger/using-saved-intellitrace-data.md)을 참조하세요.

## <a name="blogs"></a>블로그

[Visual Studio Enterprise 2015의 IntelliTrace](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Visual Studio 2015에서 IntelliTrace를 사용하여 라이브 디버깅 연습(텍스트 편집기)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Visual Studio 2015에서 IntelliTrace를 사용하여 라이브 디버깅 연습(소셜 클럽)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[Visual Studio Enterprise 2015의 IntelliTrace가 이제 연결을 지원합니다!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[IntelliTrace 독립 실행형 수집기를 사용하여 Windows 서비스에서 데이터 수집](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[IntelliTrace 수집 계획 편집](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[사용자 지정 TraceSource 및 IntelliTrace를 사용하여 디버깅](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[Active Directory 계정에서 실행되는 IntelliTrace 독립 실행형 수집기 및 애플리케이션 풀](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>포럼

[Visual Studio 디버거](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>비디오

[IntelliTrace 환경](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Microsoft Visual Studio Ultimate 2015의 IntelliTrace를 사용하여 기록 디버그](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
