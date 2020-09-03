---
title: 스레드 및 프로세스 동시성 데이터 수집 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 39f33f2df5ad4723a612a44d1d0301bd60ed80d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331615"
---
# <a name="collect-thread-and-process-concurrency-data"></a>스레드 및 프로세스 동시성 데이터 수집

Visual Studio 프로파일링 도구의 동시성 프로파일링 방법을 사용하면 프로파일링된 애플리케이션의 함수가 리소스에 액세스하기 위해 대기하도록 하는 모든 동기화 이벤트에 대한 정보가 포함된 리소스 경합 데이터를 수집할 수 있습니다.

다음 절차 중 하나를 사용하여 동시성 프로파일링 방법을 지정할 수 있습니다.

- 프로파일링 마법사의 첫 번째 페이지에서 **동시성**을 클릭합니다.
- 성능 세션에 대한 속성 대화 상자의 **일반** 페이지에서 **동시성**을 선택합니다.
- **성능 탐색기** 도구 모음의 **메서드** 목록에서 **동시성**을 클릭합니다.

## <a name="common-tasks"></a>일반 작업

성능 세션의 _성능 세션_**속성 페이지** 대화 상자에서 추가 옵션을 지정할 수 있습니다. 이 대화 상자를 열려면

- **성능 탐색기**에서 성능 세션 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

다음 표의 작업에서는 동시성 방법을 사용하여 프로파일링할 때 _성능 세션_**속성 페이지** 대화 상자에서 지정할 수 있는 옵션을 설명합니다.

|Task|관련 내용|
|----------|---------------------|
|**일반** 페이지에서 생성된 프로파일링 데이터(.vsp) 파일에 대한 이름 지정 세부 정보를 지정합니다.|- [방법: 성능 데이터 파일 이름 옵션 설정](../profiling/how-to-set-performance-data-file-name-options.md)|
|**시작** 페이지에서 코드 솔루션에.여러 .exe 프로젝트가 있는 경우 시작할 애플리케이션을 지정합니다.|- [방법: 시작할 이진 파일 지정](../profiling/how-to-specify-the-binary-to-start.md)|
|**계층 상호 작용** 페이지에서 프로파일링 실행에 ADO.NET 호출 데이터를 추가합니다.|- [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)|
|**Windows 카운터** 페이지에서 프로파일링 데이터에 표시로 추가할 운영 체제 성능 카운터를 하나 이상 지정합니다.|- [방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)|
|**고급** 페이지에서, 애플리케이션 모듈이 여러 버전을 사용하는 경우 프로파일링할 .NET Framework 런타임의 버전을 지정합니다. 기본적으로 첫 번째 로드된 버전이 프로파일링됩니다.|- [방법: .NET Framework 런타임 지정](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
