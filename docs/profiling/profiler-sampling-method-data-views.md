---
title: 프로파일러 샘플링 방법 데이터 뷰 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling data views
- sampling data views
ms.assetid: 798de693-e43a-4056-aff5-48310c2172c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8d845d84d421ca44f5b936df0a7138fefa848d8d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772164"
---
# <a name="profiler-sampling-method-data-views"></a>프로파일러 샘플링 방법 데이터 뷰
이 섹션에서는 샘플링 방법을 사용하여 생성된 프로파일러 데이터 파일의 뷰와 보고서에 대한 참조 정보를 제공합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="in-this-section"></a>섹션 내용
- [요약 뷰](../profiling/summary-view-sampling-data.md)

 샘플 수집 시 가장 자주 실행하는 함수와 가장 많은 개별 작업을 수행하는 함수를 나열합니다.

- [호출 트리 뷰](../profiling/call-tree-view-sampling-data.md)

 함수의 실행 경로를 계층 구조 트리에 표시합니다.

- [모듈 뷰](../profiling/modules-view-sampling-data.md)

 프로파일링 데이터를 모듈별로 구성하고 함수, 소스 코드 줄, 샘플이 수집될 때 실행되고 있던 명령을 나열합니다.

- [호출자/호출 수신자 뷰 - 샘플링 데이터](../profiling/caller-callee-view-sampling-data.md)

 선택한 함수와 해당 함수를 호출한 함수 및 선택한 함수가 호출한 함수에 대한 프로파일링 데이터를 표시합니다.

- [함수 뷰](../profiling/functions-view-sampling-data.md)

 함수별로 프로파일링을 정리하고 샘플이 수집될 때 실행되고 있던 함수를 나열합니다.

- [줄 뷰](../profiling/lines-view-sampling-data.md)

 샘플이 수집될 때 실행되고 있던 소스 코드 줄을 나열합니다.

- [IP(명령 포인터) 뷰](../profiling/instruction-pointers-ips-view-sampling-data.md)

 샘플이 수집될 때 실행되고 있던 소스 코드 줄을 나열합니다.

## <a name="reference"></a>참조
- [프로세스 뷰](../profiling/process-view.md)

 프로세스 및 스레드 시작/종료 시간을 나열합니다.

- [표시 뷰](../profiling/marks-view.md)

 프로파일링 데이터 파일에 삽입된 ETW 및 샘플링 이벤트가 표시됩니다.

- [함수 정보 뷰](../profiling/function-details-view.md)

 선택한 함수와 해당 함수를 호출한 함수 및 해당 함수가 호출한 함수의 관계에 대한 그래픽 차트를 표시합니다.

## <a name="related-sections"></a>관련 단원
- [계측 방법 데이터 뷰](../profiling/instrumentation-method-data-views.md)

 계측 방법을 사용하여 생성된 프로파일러 데이터 파일의 뷰와 보고서에 대한 참조 정보입니다.

- [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)

 .NET 메모리 데이터를 포함하는 프로파일러 데이터 파일의 뷰와 보고서에 대한 참조 정보입니다.

## <a name="see-also"></a>참고 항목
- [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)
