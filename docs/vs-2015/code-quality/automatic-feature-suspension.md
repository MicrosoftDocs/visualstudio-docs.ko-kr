---
title: 자동 기능 일시 중단 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c80ba76ba2da978c9cb475299ba0fc9e614120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655145"
---
# <a name="automatic-feature-suspension"></a>자동 기능 일시 중단
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
사용 가능한 시스템 메모리가 200MB 미만이 면 Visual Studio에서 코드 편집기에 다음 메시지를 표시 합니다.

 ![경고 텍스트 전체 솔루션 분석 일시 중단](../code-quality/media/fsa-alert.png "FSA_Alert")

 Visual Studio는 메모리 부족 상태를 검색 하면 안정적으로 유지 하기 위해 특정 고급 기능을 자동으로 일시 중단 합니다. 이 고급 기능 일시 중단 경고가 표시 되 면 Visual Studio는 이전과 같이 계속 작동 하지만 성능이 약간 저하 됩니다.

 메모리 부족 상태에서 다음이 발생 합니다.

- Visual c # 및 Visual Basic에 대 한 전체 솔루션 분석을 사용할 수 없습니다.

- Visual c # 및 Visual Basic에 대 한 GC ( [가비지 수집](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) ) 낮은 대기 시간 모드를 사용할 수 없습니다.

- Visual Studio 캐시가 플러시됩니다.

## <a name="improve-visual-studio-performance"></a>Visual Studio 성능 향상
 대량 솔루션 또는 메모리 부족 상태를 처리할 때 Visual Studio 성능을 개선 하는 방법에 대 한 팁과 요령은 [대기업의 성능 고려 사항](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)을 참조 하세요.

## <a name="full-solution-analysis-suspended"></a>전체 솔루션 분석 일시 중단 됨
 기본적으로 전체 솔루션 분석은 Visual Basic에 대해 사용 하도록 설정 되 고 Visual c #에서는 사용 하지 않도록 설정 됩니다. 그러나 메모리 부족 상태에서는 옵션 대화 상자의 설정에 관계 없이 Visual Basic 및 Visual c # 모두에 대해 전체 솔루션 분석을 자동으로 사용할 수 없습니다. 그러나 옵션 대화 상자에서 **전체 솔루션 분석 사용** 확인란을 선택 하거나 Visual Studio를 다시 시작 하 여 정보 표시줄이 나타날 때 **다시 설정** 단추를 선택 하 여 전체 솔루션 분석을 다시 사용 하도록 설정할 수 있습니다. 옵션 대화 상자는 항상 현재 전체 솔루션 분석 설정을 표시 합니다. 자세한 내용은 [방법: 전체 솔루션 분석 사용 및 사용 안 함](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)을 참조 하세요.

## <a name="gc-low-latency-disabled"></a>GC 낮은 대기 시간 사용 안 함
 GC 낮은 대기 시간 모드를 다시 사용 하도록 설정 하려면 Visual Studio를 다시 시작 합니다.  기본적으로 Visual Studio는 입력할 때마다 gc가 낮은 대기 시간 모드를 설정 하 여 사용자가 GC 작업을 차단 하지 않도록 합니다. 그러나 메모리 부족 상태에서 Visual Studio가 자동 일시 중단 경고를 표시 하는 경우에는 해당 세션에 대해 GC 낮은 대기 시간 모드를 사용할 수 없습니다. Visual Studio를 다시 시작 하면 기본 GC 동작이 다시 활성화 됩니다. 자세한 내용은 <xref:System.Runtime.GCLatencyMode>를 참조하세요.

## <a name="visual-studio-caches-flushed"></a>Visual Studio 캐시 플러시

모든 Visual Studio 캐시는 즉시 비워지고 현재 개발 세션을 계속 하거나 Visual Studio를 다시 시작 하는 경우 다시 채우기가 시작 됩니다. 플러시된 캐시는 다음 기능에 대 한 캐시를 포함 합니다.

- 모든 참조 찾기

- 다음 탐색

- Using 추가

또한 내부 Visual Studio 작업에 사용 되는 캐시도 지워집니다.

> [!NOTE]
> 자동 기능 일시 중단 경고는 세션당 한 번만 발생 하는 것이 아니라 솔루션 별로 한 번만 발생 합니다. 즉, Visual Basic에서 Visual c # (또는 그 반대로)로 전환 하 고 다른 메모리 부족 상태를 실행 하는 경우 다른 자동 기능 일시 중단 경고를 얻을 수 있습니다.

## <a name="see-also"></a>추가 정보

- [방법: 전체 솔루션 분석 사용 설정 및 해제](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [가비지 수집 기본 사항](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [대량 솔루션에 대 한 성능 고려 사항](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)