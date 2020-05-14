---
title: 자동 기능 일시 중단
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431243"
---
# <a name="automatic-feature-suspension"></a>자동 기능 일시 중단

사용 가능한 시스템 메모리가 200MB 이하인 경우 Visual Studio는 코드 편집기에서 다음 메시지를 표시합니다.

![전체 솔루션 분석을 일시 중단하는 경고 텍스트](../code-quality/media/fsa_alert.png)

Visual Studio에서 메모리 부족 상태를 감지하면 특정 고급 기능을 자동으로 일시 중단하여 안정적으로 유지됩니다. Visual Studio는 이전과 마찬가지로 계속 작동하지만 성능이 저하됩니다.

메모리부족 조건에서는 다음과 같은 작업이 수행됩니다.

- Visual C# 및 Visual Basic에 대한 라이브 코드 분석이 최소 범위로 줄어듭니다.

- 시각적 C# 및 Visual Basic에 대한 [가비지](/dotnet/standard/garbage-collection/index) 수집(GC) 대기 시간 낮음 모드는 사용할 수 없습니다.

- Visual Studio 캐시가 플러시됩니다.

## <a name="improve-visual-studio-performance"></a>비주얼 스튜디오 성능 향상

대규모 솔루션 또는 메모리 부족 조건을 처리할 때 Visual Studio 성능을 개선하는 방법에 대한 팁과 요령은 [대규모 솔루션에 대한 성능 고려 사항을](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)참조하십시오.

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>라이브 코드 분석이 최소한의 범위로 줄어듭니다.

기본적으로 라이브 코드 분석은 열려 있는 문서 및 프로젝트에 대해 실행됩니다. 이 분석 범위를 현재 문서로 축소하거나 전체 솔루션으로 늘리도록 사용자 지정할 수 있습니다. 자세한 내용은 [관리 코드에 대한 라이브 코드 분석 범위를 구성하는 방법을](./configure-live-code-analysis-scope-managed-code.md)참조하십시오. 메모리가 부족한 상태에서 Visual Studio는 라이브 분석 범위를 현재 문서로 축소하도록 강제합니다. 그러나 정보 표시줄에서 **다시 활성화** 단추를 선택하거나 Visual Studio를 다시 시작하여 기본 설정 분석 범위를 다시 활성화할 수 있습니다. 옵션 대화 상자에는 항상 현재 라이브 코드 분석 범위 설정이 표시됩니다.

## <a name="gc-low-latency-disabled"></a>GC 대기 시간 낮음 사용 안 함

GC 대기 시간 낮음 모드를 다시 사용하려면 Visual Studio를 다시 시작합니다. 기본적으로 Visual Studio는 입력할 때마다 GC 대기 시간 낮음 모드를 사용하여 입력이 GC 작업을 차단하지 않도록 합니다. 그러나 메모리 부족 조건으로 인해 Visual Studio에서 자동 일시 중단 경고가 표시되면 해당 세션에 대해 GC 대기 시간이 짧은 모드가 비활성화됩니다. Visual Studio를 다시 시작하면 기본 GC 동작이 다시 활성화됩니다. 자세한 내용은 <xref:System.Runtime.GCLatencyMode>을 참조하세요.

## <a name="visual-studio-caches-flushed"></a>비주얼 스튜디오 캐시 플러시

현재 개발 세션을 계속하거나 Visual Studio를 다시 시작하면 모든 Visual Studio 캐시가 즉시 비워지지만 다시 채우기 시작합니다. 플러시된 캐시에는 다음 기능에 대한 캐시가 포함됩니다.

- 모든 참조 찾기

- 다음 탐색

- 사용 추가

또한 내부 Visual Studio 작업에 사용되는 캐시도 지워집니다.

> [!NOTE]
> 자동 기능 일시 중단 경고는 세션별로 가아닌 솔루션별로 한 번만 발생합니다. 즉, Visual Basic에서 Visual C#(또는 그 반대)로 전환하고 메모리부족 상태가 다른 경우 다른 자동 기능 일시 중단 경고를 받을 수 있습니다.

## <a name="see-also"></a>참고 항목

- [방법: 관리 코드에 대한 라이브 코드 분석 범위 구성](./configure-live-code-analysis-scope-managed-code.md)
- [가비지 수집 기본 사항](/dotnet/standard/garbage-collection/fundamentals)
- [대규모 솔루션에 대한 성능 고려 사항](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
