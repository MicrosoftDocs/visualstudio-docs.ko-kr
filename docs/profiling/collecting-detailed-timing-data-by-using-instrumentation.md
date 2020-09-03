---
title: 계측을 사용하여 자세한 타이밍 데이터 수집 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 682ae4bf31f44f3dff5f6dfadf7b8c316d9d9721
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331854"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>계측을 사용하여 자세한 타이밍 데이터 수집
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 계측 방법은 모듈의 복사본에 프로파일링 코드를 삽입합니다. 코드는 프로파일링 실행 중 모듈의 각 함수 시작, 종료 및 함수 호출을 기록합니다. 계측 방법은 코드의 한 섹션에 대한 자세한 타이밍 정보를 수집하고 입력 및 출력 작업이 애플리케이션 성능에 미치는 영향을 이해하는 데 유용합니다.

 다음 절차 중 하나를 사용하여 계측 방법을 지정할 수 있습니다.

- 프로파일링 마법사의 첫 페이지에서 **계측**을 선택합니다.

- **성능 탐색기** 도구 모음의 **메서드** 목록에서 **계측**을 클릭합니다.

- 성능 세션에 대한 속성 대화 상자의 **일반** 페이지에서 **계측**을 선택합니다.

## <a name="common-tasks"></a>일반 작업
 성능 세션의 _성능 세션_**속성 페이지** 대화 상자에서 추가 옵션을 지정할 수 있습니다. 이 대화 상자를 열려면

- **성능 탐색기**에서 성능 세션 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

  다음 표의 작업에서는 계측 방법을 사용하여 프로파일링할 때 _성능 세션_**속성 페이지** 대화 상자에서 지정할 수 있는 옵션에 대해 설명합니다.

|Task|관련 내용|
|----------|---------------------|
|**일반** 페이지에서 .NET 메모리 할당 및 수명 데이터를 추가하고 생성된 프로파일링 데이터(.vsp) 파일에 대한 이름 지정 세부 정보를 지정합니다.|-   [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [방법: 성능 데이터 파일 이름 옵션 설정](../profiling/how-to-set-performance-data-file-name-options.md)|
|**시작** 페이지에서 사용자 솔루션에 여러 .exe 프로젝트가 있는 경우 시작할 애플리케이션 및 시작 순서를 지정합니다.|-   [방법: 시작할 이진 파일 지정](../profiling/how-to-specify-the-binary-to-start.md)|
|**이진** 페이지에서 모듈의 계측된 복사본에 대한 위치를 지정합니다. 기본적으로 원래 이진 파일이 백업 폴더로 이동됩니다.|-   [방법: 계측된 이진 파일 재배치](../profiling/how-to-relocate-instrumented-binaries.md)|
|**계층 상호 작용** 페이지에서 프로파일링 실행에 ADO.NET 호출 데이터를 추가합니다.|-   [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)|
|**계측** 페이지에서 작은 함수가 프로파일링되지 않도록 제외하여 프로파일링 오버헤드를 줄이고, JavaScript 코드를 ASP.NET 웹 페이지에 프로파일링하고, 계측 프로세스 전후에 명령 프롬프트에서 실행할 명령을 지정합니다.|-   [방법: 계측에서 간단한 함수 제외 또는 포함](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [방법: 웹 페이지에서 JavaScript 코드 프로파일링](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [방법: 계측 전 명령 및 계측 후 명령 지정](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|**CPU 카운터** 페이지에서 프로파일링 데이터에 추가할 프로세서 성능 카운터를 하나 이상 지정합니다.|-   [방법: CPU 카운터 데이터 수집](../profiling/how-to-collect-cpu-counter-data.md)|
|**Windows 이벤트** 페이지에서 샘플링 데이터로 수집할 ETW(Windows용 이벤트 추적) 이벤트를 하나 이상 선택합니다.|-   [방법: ETW(Windows용 이벤트 추적) 데이터 수집](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|**Windows 카운터** 페이지에서 프로파일링 데이터에 표시로 추가할 운영 체제 성능 카운터를 하나 이상 지정합니다.|-   [방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)|
|**고급** 페이지에서 특정 함수를 포함하거나 제외하는 옵션 등 VSInstr 계측 프로그램에 전달하려는 추가 옵션을 지정합니다.|-   [방법: 추가 계측 옵션 지정](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [방법: 특정 함수로 계측 제한](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
