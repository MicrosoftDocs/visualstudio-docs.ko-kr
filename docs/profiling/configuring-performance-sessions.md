---
title: 성능 세션 구성 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bdf1c372ffcb3ad3a0ebf102827565853947e2b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777870"
---
# <a name="configure-performance-sessions"></a>성능 세션 구성
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구를 사용하여 다양한 애플리케이션 종류에 대한 성능 데이터를 수집할 수 있습니다. 이 섹션에서는 성능 세션 및 대상 이진 파일의 성능 Wizardand 속성을 사용하여 관심 있는 데이터를 수집하도록 프로파일링 도구를 구성하는 방법을 보여 줍니다. 프로파일링 도구 구성 속성을 사용하여 프로파일링 실행에서 수집되는 데이터의 양을 제어할 수도 있습니다. 자세한 내용은 [데이터 수집 제어](../profiling/controlling-data-collection.md)를 참조하세요.

> [!NOTE]
> 대부분의 경우, 성능 마법사의 기본 속성을 사용하는 것이 프로파일링 데이터를 수집하는 효과적인 방법입니다. 자세한 내용은 [초보자를 위한 성능 프로파일링 지침](../profiling/beginners-guide-to-performance-profiling.md) 및 [시작](../profiling/getting-started-with-performance-tools.md)을 참조하세요.

## <a name="common-tasks"></a>일반 작업

| Task | 관련 내용 |
| - | - |
| **기본 프로파일링 옵션 설정:** Microsoft 기호 서버를 사용하도록 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]를 구성해야 합니다. 이를 통해 현재 버전의 Windows 및 다른 Microsoft 애플리케이션에 대한 함수 및 매개 변수 이름과 같은 기호에 액세스할 수 있습니다. 프로파일링 도구 및 프로파일링 데이터 파일의 이름에 대한 시스템 권한 등 프로파일링 세션을 시작하기 전에 다른 일반 옵션을 지정할 수도 있습니다. | -   [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [방법: 기호 정보 직렬화](../profiling/how-to-serialize-symbol-information.md)<br />-   [방법: 현재 세션 설정](../profiling/how-to-set-the-current-session.md)<br />-   [방법: 권한 설정](../profiling/how-to-set-permissions.md)<br />-   [방법: 성능 데이터 파일 이름 옵션 설정](../profiling/how-to-set-performance-data-file-name-options.md) |
| **수집하려는 데이터 지정:** 프로파일링 세션을 구성하는 데 사용하는 절차는 프로파일링할 대상 애플리케이션의 유형 및 수집하려는 성능 데이터의 유형에 따라 달라집니다. | -   [방법: 수집 방법 선택](../profiling/how-to-choose-collection-methods.md)<br />-   [샘플링을 사용하여 성능 통계 수집](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [방법: 웹 페이지에서 JavaScript 코드 프로파일링](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [스레드 및 프로세스 동시성 데이터 수집](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [추가 성능 데이터 수집](../profiling/collecting-additional-performance-data.md) |
| **고급 구성 옵션 설정:** CLR(공용 언어 런타임)의 여러 버전을 로드하는 .NET Framework 애플리케이션을 프로파일링할 때 프로파일링할 버전을 지정할 수 있습니다. 성능 세션에 여러.exe 파일이 있는 경우 이진의 시작 순서를 설정할 수 있습니다. | -   [방법: .NET Framework 런타임 지정](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [방법: 시작할 이진 파일 지정](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>관련 단원
- [데이터 수집 제어](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>참고 항목
- [성능 탐색기](../profiling/performance-explorer.md)
