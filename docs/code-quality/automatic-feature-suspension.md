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
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 236a95cd8d4af8da91199bf79e7c9fe3aa0d49af
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769483"
---
# <a name="automatic-feature-suspension"></a>자동 기능 일시 중단

사용 가능한 시스템 메모리가 200 MB 미만이 면 Visual Studio에서 코드 편집기에 다음 메시지를 표시 합니다.

![경고 텍스트 전체 솔루션 분석 일시 중단](../code-quality/media/fsa_alert.png)

Visual Studio는 메모리 부족 상태를 검색 하면 안정적으로 유지 하기 위해 특정 고급 기능을 자동으로 일시 중단 합니다. Visual Studio는 이전 처럼 계속 작동 하지만 성능이 저하 됩니다.

메모리 부족 상태에서 다음 작업이 수행 됩니다.

- Visual c # 및 Visual Basic에 대 한 라이브 코드 분석은 최소 범위로 줄어듭니다.

- Visual c # 및 Visual Basic에 대 한 GC ( [가비지 수집](/dotnet/standard/garbage-collection/index) ) 대기 시간이 짧은 모드를 사용할 수 없습니다.

- Visual Studio 캐시가 플러시됩니다.

## <a name="improve-visual-studio-performance"></a>Visual Studio 성능 향상

대량 솔루션 또는 메모리 부족 상태를 처리할 때 Visual Studio 성능을 개선 하는 방법에 대 한 팁과 요령은 [대기업의 성능 고려 사항](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)을 참조 하세요.

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>라이브 코드 분석이 최소 범위로 축소 됨

기본적으로 라이브 코드 분석은 열린 문서 및 프로젝트에 대해 실행 됩니다. 이 분석 범위를 사용자 지정 하 여 현재 문서로 줄이거나 전체 솔루션으로 늘릴 수 있습니다. 자세한 내용은 [방법: 관리 코드에 대 한 라이브 코드 분석 범위 구성](./configure-live-code-analysis-scope-managed-code.md)을 참조 하세요. 메모리 부족 상태에서 Visual Studio는 라이브 분석 범위를 현재 문서로 강제로 줄입니다. 그러나 표시 되는 경우 정보 표시줄에서 **다시 사용** 단추를 선택 하거나 Visual Studio를 다시 시작 하 여 원하는 분석 범위를 다시 활성화할 수 있습니다. 옵션 대화 상자에는 항상 현재 라이브 코드 분석 범위 설정이 표시 됩니다.

## <a name="gc-low-latency-disabled"></a>GC 낮은 대기 시간 사용 안 함

GC 낮은 대기 시간 모드를 다시 사용 하도록 설정 하려면 Visual Studio를 다시 시작 합니다. 기본적으로 Visual Studio는 입력할 때마다 gc가 낮은 대기 시간 모드를 설정 하 여 사용자가 GC 작업을 차단 하지 않도록 합니다. 그러나 메모리 부족 상태에서 Visual Studio가 자동 일시 중단 경고를 표시 하는 경우에는 해당 세션에 대해 GC 낮은 대기 시간 모드를 사용할 수 없습니다. Visual Studio를 다시 시작 하면 기본 GC 동작이 다시 활성화 됩니다. 자세한 내용은 <xref:System.Runtime.GCLatencyMode>를 참조하세요.

## <a name="visual-studio-caches-flushed"></a>Visual Studio 캐시 플러시

현재 개발 세션을 계속 하거나 Visual Studio를 다시 시작 하면 모든 Visual Studio 캐시가 즉시 비워지고 다시 채우기가 시작 됩니다. 플러시된 캐시는 다음과 같은 기능에 대 한 캐시를 포함 합니다.

- 모든 참조 찾기

- 다음 탐색

- Using 추가

또한 내부 Visual Studio 작업에 사용 되는 캐시도 지워집니다.

> [!NOTE]
> 자동 기능 일시 중단 경고는 세션당 한 번만 발생 하는 것이 아니라 솔루션 별로 한 번만 발생 합니다. 즉, Visual Basic에서 Visual c # (또는 그 반대로)로 전환 하 고 다른 메모리 부족 상태를 실행 하는 경우 다른 자동 기능 일시 중단 경고를 얻을 수 있습니다.

## <a name="see-also"></a>참고 항목

- [방법: 관리 코드에 대 한 라이브 코드 분석 범위 구성](./configure-live-code-analysis-scope-managed-code.md)
- [가비지 수집 기본 사항](/dotnet/standard/garbage-collection/fundamentals)
- [대량 솔루션에 대 한 성능 고려 사항](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
