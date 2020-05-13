---
title: 성능 세션 속성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b3bafa976c8e57f468a3f3f59a3b6b19308fd1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772204"
---
# <a name="performance-session-properties"></a>성능 세션 속성

**성능 세션**에서는 애플리케이션을 프로파일링하는 방식을 결정하는 설정을 구성할 수 있습니다. 또한 프로파일링 세션에 대해 생성되는 보고서도 저장됩니다.

**성능 마법사**를 실행하거나 세션을 수동으로 만드는 방법으로 **성능 세션**을 만듭니다. **성능 세션**을 만들고 나면 **성능 탐색기**에 **성능 세션**이 표시됩니다.

**성능 세션** 속성을 확인하려면 **성능 탐색기**에서 세션 이름을 선택하고 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.

성능 세션에는 다음 속성 페이지가 있습니다.

## <a name="general"></a>일반

이러한 설정을 사용하면 프로파일링 방법을 선택하고, .NET 개체 컬렉션 및 수명 데이터를 추가하고, 기본 보고서 위치 및 이름 지정 규칙을 지정할 수 있습니다.

자세한 내용은 다음을 참조하세요.

[방법: 수집 방법 선택](../profiling/how-to-choose-collection-methods.md)

[.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [방법: 성능 데이터 파일 이름 옵션 설정](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Launch

이러한 설정을 사용하면 이진 파일 목록에서 원하는 파일을 선택하고 이진 파일의 시작 순서를 지정할 수 있습니다.

자세한 내용은 [방법: 시작할 이진 파일 지정](../profiling/how-to-specify-the-binary-to-start.md)을 참조하세요.

## <a name="sampling"></a>샘플링

이러한 설정을 사용하면 프로파일링 방법으로 샘플링을 사용할 때 샘플링 이벤트와 샘플링 간격을 선택할 수 있습니다. 샘플링 이벤트를 사용하여 지정한 간격으로 프로파일링 데이터를 수집합니다. 예를 들어 샘플링 이벤트가 클록 주기이며 샘플링 간격이 10,000,000으로 설정되어 있으면 1천만 클록 주기마다 프로파일링 데이터를 수집합니다. 다음과 같은 네 가지 유형의 샘플 이벤트를 사용할 수 있습니다.

- 클록 주기 - CPU 바인딩 문제
- 페이지 폴트 - 메모리 관련 문제
- 시스템 호출 - I/O 관련 문제
- 성능 카운터 - 낮은 수준의 성능 문제
- 사용 가능한 성능 카운터에 따라 추가 샘플 이벤트를 지정할 수 있습니다.

자세한 내용은 [방법: 샘플링 이벤트 선택](../profiling/how-to-choose-sampling-events.md)을 참조하세요.

## <a name="binary"></a>이진
이러한 설정을 사용하면 계측된 이진 파일을 다른 위치로 옮길지 여부를 지정할 수 있습니다. 예를 들어 *My.DLL*을 프로파일링할 때 계측된 이진 파일을 옮기지 않도록 선택하면 *My.Orig.DLL*이라는 *My.DLL*의 백업 복사본이 만들어집니다. 그런 후에는 데이터를 수집하기 위한 프로브를 삽입하여 *My.DLL*이 수정됩니다. 계측된 이진 파일을 옮기도록 선택하면 원본 이진 파일 이름이 바뀌지 않으며 계측 중에 사용하기 위해 계측된 이진 파일이 지정한 위치에 복사됩니다.

자세한 내용은 [방법: 시작할 이진 파일 지정](../profiling/how-to-specify-the-binary-to-start.md)을 참조하세요.

## <a name="tier-interactions"></a>계층 상호 작용

자세한 내용은 [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)을 참조하세요.

## <a name="instrumentation"></a>계측

이러한 설정을 사용하면 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 페이지에서 JScript 코드의 성능 데이터를 수집하고 계측 프로세스 전이나 후에 발생하도록 할 **계측 전** 및 **계측 후** 이벤트를 지정할 수 있습니다.

자세한 내용은 다음을 참조하세요.

[방법: 웹 페이지에서 JavaScript 코드 프로파일링](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[방법: 계측 전 명령 및 계측 후 명령 지정](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>CPU 카운터

이러한 설정을 사용하면 계측 프로파일링 방법을 사용할 때 CPU 성능 카운터에 대한 데이터를 수집할 수 있습니다. 이식 가능한 성능 카운터는 CPU 디자인 또는 제조업체에 관계없이 사용할 수 있습니다. 플랫폼 이벤트는 CPU 디자인 및 제조업체별로 다릅합니다. 온칩 성능 카운터에 대한 자세한 내용은 특정 프로세서 설명서를 참조하세요.

자세한 내용은 [방법: CPU 카운터 데이터 수집](../profiling/how-to-collect-cpu-counter-data.md)을 참조하세요.

## <a name="windows-events"></a>Windows 이벤트

프로파일링 중에 이벤트 추적 공급자의 데이터를 수집할 수 있습니다. *VSPerfReport.exe* 명령줄 도구 `/calltrace` 옵션을 사용하면 데이터를 확인할 수 있습니다. ETW(Windows용 이벤트 추적)에 대한 자세한 내용은 [이벤트 추적 정보](/windows/win32/etw/about-event-tracing)를 참조하세요.

자세한 내용은 다음을 참조하세요.

[방법: ETW(Windows용 이벤트 추적) 데이터 수집](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md)

## <a name="windows-counters"></a>Windows 카운터

이 옵션을 사용하면 Windows 성능 모니터 카운터에서 데이터를 수집할 수 있습니다. 이 데이터를 수집하려면 레이블이 **Windows 성능 카운터 수집**인 확인란을 선택합니다. **수집 간격** 상자에서 수집 간격을 설정할 수 있습니다. **카운터 범주** 및 **인스턴스**도 사용할 수 있습니다. 일부 기본 Windows 성능 모니터 카운터를 사용할 수 있습니다.

 자세한 내용은 [방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)을 참조하세요.

## <a name="advanced"></a>고급

이러한 설정을 사용하면 [VSInstr](../profiling/vsinstr.md) 명령줄 프로파일링 도구의 옵션을 하나 이상 지정하여 계측 프로세스에 옵션을 추가할 수 있습니다. 애플리케이션이 여러 버전을 사용하는 경우에는 프로파일링할 공용 런타임 버전을 지정할 수도 있습니다.

자세한 내용은 다음을 참조하세요.

[방법: .NET Framework 런타임 지정](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[방법: 추가 계측 옵션 지정](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>참고 항목

[개요](../profiling/overviews-performance-tools.md)
[성능 세션 구성](../profiling/configuring-performance-sessions.md)
[데이터 컬렉션 제어](../profiling/controlling-data-collection.md)
