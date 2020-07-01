---
title: .NET 메모리 할당 및 수명 데이터 수집 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1c256fcedf3ea1733f620a18528704fe455d1131
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331713"
---
# <a name="collect-net-memory-allocation-and-lifetime-data"></a>.NET 메모리 할당 및 수명 데이터 수집

Visual Studio 프로파일링 도구는 .NET 메모리 할당 및 개체 수명 데이터의 수집을 지원하므로, 애플리케이션에서 메모리 관련 성능 문제를 감지하는 데 도움이 됩니다.

- .NET 메모리 할당에 대한 데이터에는 할당된 .NET Framework 메모리 개체의 크기와 수가 포함됩니다.

- 개체 수명 데이터에는 3개의 가비지 수집 세대에서 회수된 .NET Framework 메모리 개체의 크기와 수가 포함됩니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

샘플링 또는 계측 프로파일링 방법을 사용하여 데이터를 수집할 수 있습니다.

- 샘플링 방법을 사용하면 프로파일러에서 시작되었거나 연결된 프로세스에 의해 생성되는 모든 .NET 메모리 할당 및 개체를 추적합니다.

- 계측 방법을 사용하면 프로파일러에서 계측된 모듈에 의해 생성되는 .NET 메모리 할당 및 개체만 추적합니다.

> [!IMPORTANT]
> 샘플링 방법을 사용하여 .NET 메모리 데이터(할당, 개체 수명 또는 둘 다)를 수집하는 경우 모든 사용자 지정 샘플링 이벤트가 무시되며 적절한 메모리 할당 이벤트가 데이터를 수집하는 데 사용됩니다.

.NET 메모리 할당의 프로파일링을 사용하도록 설정하면 할당 뷰도 사용하도록 설정할 수 있습니다. .NET 수명 데이터의 프로파일링을 사용하도록 설정하면 개체 수명 뷰도 사용하도록 설정할 수 있습니다. 자세한 내용은 [할당 뷰](../profiling/dotnet-memory-allocations-view.md) 및 [개체 수명 뷰](../profiling/object-lifetime-view.md)를 참조하세요.

프로파일링 도구의 명령줄 도구를 사용하여 .NET 메모리 데이터를 수집하는 방법에 대한 자세한 내용은 [명령줄에서 프로파일링 방법 사용](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)에서 .NET 메모리 방법을 사용하여 메모리 할당 및 개체 수명 데이터 수집을 참조하세요.

## <a name="to-collect-net-memory-data"></a>.NET 메모리 데이터를 수집하려면

1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

2. ‘성능 세션’ **속성 페이지** 대화 상자에서 **일반** 탭을 클릭하고 **.NET 개체 할당 정보 수집** 확인란을 선택합니다. 

3. .NET 개체 수명 데이터를 수집하려면 **추가적으로 .NET 개체 수명 정보 수집** 확인란을 선택합니다.

## <a name="common-tasks"></a>일반 작업

성능 세션의 _성능 세션_**속성 페이지** 대화 상자에서 추가 옵션을 지정할 수 있습니다. 이 대화 상자를 열려면

- **성능 탐색기**에서 성능 세션 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

다음 표의 작업에서는 .NET 메모리 데이터를 수집할 때 _성능 세션_**속성 페이지** 대화 상자에 지정할 수 있는 옵션을 설명합니다.

|작업|관련 내용|
|----------|---------------------|
|**일반** 페이지에서 생성된 프로파일링 데이터(.vsp) 파일에 대한 이름 지정 세부 정보를 지정합니다.|- [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [방법: 성능 데이터 파일 이름 옵션 설정](../profiling/how-to-set-performance-data-file-name-options.md)|
|**시작** 페이지에서 코드 솔루션에 .여러 .exe 프로젝트가 있는 경우 시작할 애플리케이션을 선택합니다.|- [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)|
|**계층 상호 작용** 페이지에서 프로파일링 실행에 ADO.NET 호출 데이터를 추가합니다.|- [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)|
|**Windows 이벤트** 페이지에서 샘플링 데이터로 수집할 ETW(Windows용 이벤트 추적) 이벤트를 하나 이상 지정합니다.|- [방법: ETW(Windows용 이벤트 추적) 데이터 수집](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|**Windows 카운터** 페이지에서 프로파일링 데이터에 표시로 추가할 운영 체제 성능 카운터를 하나 이상 지정합니다.|- [방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)|
|**고급** 페이지에서, 애플리케이션 모듈이 여러 버전을 사용하는 경우 프로파일링할 .NET Framework 런타임의 버전을 지정합니다. 기본적으로 첫 번째 로드된 버전이 프로파일링됩니다.|- [방법: .NET Framework 런타임 지정](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>계측 작업

다음 표의 작업은 계측 방법을 사용하여 프로파일링과 관련된 **속성 페이지** 대화 상자의 옵션입니다.

|작업|관련 내용|
|----------|---------------------|
|**이진** 페이지에서 모듈의 계측된 복사본에 대한 위치를 지정합니다. 기본적으로 원래 이진 파일이 백업 폴더로 이동됩니다.|- [방법: 계측된 이진 파일 재배치](../profiling/how-to-relocate-instrumented-binaries.md)|
|**계측** 페이지에서 작은 함수가 프로파일링되지 않도록 제외하여 프로파일링 오버헤드를 줄이고, JavaScript 코드를 ASP.NET 웹 페이지에 프로파일링하고, 계측 프로세스 전후에 명령 프롬프트에서 실행할 명령을 지정합니다.|- [방법: 계측에서 간단한 함수 제외 또는 포함](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [방법: 웹 페이지에서 JavaScript 코드 프로파일링](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [방법: 계측 전 명령 및 계측 후 명령 지정](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|**CPU 카운터** 페이지에서 프로파일링 데이터에 추가할 프로세서 성능 카운터를 하나 이상 지정합니다.|- [방법: CPU 카운터 데이터 수집](../profiling/how-to-collect-cpu-counter-data.md)|
|**고급** 페이지에서 특정 함수를 포함하거나 제외하는 옵션 등 원하는 추가 VSInstr.exe 옵션을 지정합니다. VSInstr 옵션에 대한 자세한 내용은 [VSInstr](../profiling/vsinstr.md)을 참조하세요.|- [방법: 추가 계측 옵션 지정](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [방법: 특정 함수로 계측 제한](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>참조

[성능 세션 구성](../profiling/configuring-performance-sessions.md)
[방법: 수집 방법 선택](../profiling/how-to-choose-collection-methods.md)
[성능 세션 속성](../profiling/performance-session-properties.md)
