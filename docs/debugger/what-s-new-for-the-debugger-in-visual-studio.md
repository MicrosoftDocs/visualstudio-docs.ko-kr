---
title: Visual Studio 2017 디버거의 새로운 기능 | Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 523867a8f9aa074e9122c74deb8bcd91cddd8bee
ms.sourcegitcommit: 9a66f1c31cc9eba0b5231af72da1d18761a9c56a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75944222"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Visual Studio 2017 디버거의 새로운 기능

디버거에는 다음과 같은 새로운 기능이 포함되어 있습니다.

- 15.5 버전의 새로운 기능: **스냅샷 디버거**는 관심이 있는 코드가 실행될 때 프로덕션 상태 앱의 스냅샷을 생성합니다. 디버거가 스냅샷을 생성하도록 명령하려면 코드에서 snappoint와 logpoint를 설정합니다. 디버거를 통해 프로덕션 애플리케이션의 트래픽에 영향을 미치지 않으면서 정확히 무엇이 잘못되었는지를 볼 수 있습니다. 스냅샷 디버거를 사용하면 프로덕션 환경에서 발생하는 문제를 해결하는 데 걸리는 시간을 상당히 줄일 수 있습니다.

    스냅샷 컬렉션은 Azure App Service에서 실행되는 다음 웹앱에서 사용할 수 있습니다.

  * .NET Framework 4.6.1 이상에서 실행되는 ASP.NET 애플리케이션
  * Windows의 .NET Core 2.0 이상에서 실행되는 ASP.NET Core 애플리케이션

    자세한 내용은 [스냅샷 디버거를 사용하여 라이브 ASP.NET 앱 디버그](../debugger/debug-live-azure-applications.md)를 참조하세요.

- Visual Studio Enterprise 버전 15.5의 새로운 기능: **IntelliTrace 뒤로 이동**은 모든 중단점 및 디버거 단계 이벤트에서 애플리케이션의 스냅샷을 자동으로 생성합니다. 기록된 스냅샷을 통해 이전 중단점 또는 단계로 돌아가서 애플리케이션의 과거 상태를 볼 수 있습니다. IntelliTrace 뒤로 이동을 사용하면 이전 애플리케이션 상태를 보고 싶지만 디버깅을 다시 시작하거나 원하는 앱 상태를 다시 만들지 않으려는 경우에 시간을 절약할 수 있습니다.

    디버그 도구 모음의 **뒤로 가기**와 **앞으로 가기** 단추를 사용하여 이동하고 스냅샷을 볼 수 있습니다. 이 단추를 사용하여 **진단 도구** 창의 **이벤트** 탭에 나타나는 이벤트를 탐색할 수 있습니다.

    ![뒤로 이동 및 앞으로 이동 단추](../debugger/media/intellitrace-step-back-icons-description.png  "뒤로 이동 및 앞으로 이동 단추")

    자세한 내용은 [IntelliTrace를 사용하여 이전 앱 상태 검사](view-historical-application-state.md) 페이지를 참조하세요.

- **예외 도우미**는 이전 예외 도우미를 대체하며 오류가 발생한 비모달 대화 상자에 표시됩니다. **예외 도우미**는 모든 내부 예외에 대한 더 빠른 액세스, 디버거의 추가 분석(사용 가능한 경우) 및 예외의 **예외 설정**에 대한 즉각적인 액세스를 제공합니다. 예외 도우미는 표시해야 하는 항목을 차단하는 경우 부동 뷰로 끌 수도 있습니다.

    예를 들어 **NullReferenceException**은 이제 null 참조(추가 정보)가 있는 변수를 표시합니다.

    ![디버거의 예외 도우미](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    자세한 내용은 [Using the New Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/)(Visual Studio에서 새 예외 도우미 사용) 블로그 게시물을 참조하세요.

- 이제 코드 줄을 마우스로 가리킬 때 표시되는 **여기까지 실행** 녹색 화살표 아이콘을 선택하여 디버거에서 일시 중지된 상태로 코드 줄까지 실행할 수 있습니다. 이렇게 하면 임시 중단점을 설정하지 않아도 됩니다.

    ![디버거의 실행하려면 클릭](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- 예외 설정 대화 상자의 **조건 편집** 아이콘을 사용하거나 예외에서 마우스 오른쪽 단추 클릭 메뉴를 사용하여 **예외 설정** 대화 상자에서 예외에 대한 조건을 설정할 수 있습니다 현재 지원되는 조건에는 예외에 대해 포함하거나 제외할 모듈 이름이 포함됩니다.

    ![예외에 대한 조건](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- 프로세스에 연결 대화 상자에는 연결해야 하는 프로세스를 더 빠르게 식별할 수 있는 새 검색 기능이 포함됩니다.

    ![프로세스에 연결에서 검색](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

이러한 새 기능에 대한 자세한 내용은 [[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]의 릴리스 정보](/visualstudio/releasenotes/vs2017-relnotes)를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)