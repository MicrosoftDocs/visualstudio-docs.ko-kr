---
title: DA0503 - 프로파일링 중인 프로세스에 대한 평균 작업 세트(바이트) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b6717f524f6a2d3f9f09290ac9bfbd8f02fc23fb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544549"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: 프로파일링되고 있는 프로세스의 평균 작업 세트(바이트)

|항목|값|
|-|-|
|규칙 ID|DA0503|
|범주|리소스 모니터링|
|프로파일링 방법|모두|
|메시지|이 정보는 참고용으로만 수집됩니다. Process Working Set 카운터는 프로파일링하고 있는 프로세스의 실제 메모리 사용량을 측정합니다. 보고된 값은 모든 측정 간격에 걸쳐 계산된 평균값입니다.|
|규칙 유형|정보|

 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.

## <a name="rule-description"></a>규칙 설명
 이 메시지는 프로세스가 현재 사용 중인 실제 메모리의 평균 크기(바이트)를 보고합니다(작업 집합). 프로세스 작업 집합은 현재 실제 메모리에 있는 프로세스 주소 공간의 페이지를 나타냅니다.

 보고된 값에는 프로세스가 참조한 공유 메모리 세그먼트의 상주 페이지가 포함됩니다. 프로세스가 참조하는 공유 DLL은 계산되는 공유 메모리 세그먼트에 포함됩니다. 공유 메모리 세그먼트 때문에 프로세스 작업 집합의 값은 프로세스가 할당한 가상 메모리 크기보다 클 수 있습니다.

 보고된 값은 프로파일링되는 프로세스가 활성 상태였던 모든 측정 간격에 대한 평균입니다.

 프로세스 작업 집합의 크기는 프로세스가 적극적으로 사용하는 가상 메모리 크기를 반영합니다. 또한 애플리케이션을 실행할 수 있는 실제 메모리(또는 RAM)의 크기 및 해당 실제 메모리에 대한 실행 중인 다른 프로세스의 경합이 이 크기에 영향을 미칩니다. 실제 메모리가 제한될 경우 운영 체제에서는 주기적으로 프로세스 작업 집합에서 많은 비활성 페이지를 잘라내는 방식으로 모든 활성 프로세스에서 메모리 사용량을 분산하려고 하므로 프로세스 작업 집합의 값이 크게 달라질 수 있습니다.

 프로세스 작업 집합에 대한 자세한 내용은 MSDN의 Windows 메모리 관리 설명서에 있는 [Working Set](/windows/win32/memory/working-set)(작업 집합)를 참조하세요.

## <a name="how-to-use-rule-data"></a>규칙 데이터를 사용하는 방법
 규칙 값을 사용하여 프로그램의 여러 가지 버전이나 빌드에 대한 성능을 비교하거나 여러 가지 프로파일링 시나리오에서 애플리케이션의 성능을 파악합니다.

 [오류 목록] 창에서 메시지를 두 번 클릭하여 프로파일링 데이터의 [표시 뷰](../profiling/marks-view.md)로 이동합니다. **Process\Working Set** 및 **Memory\Pages/sec** 열을 찾습니다. 두 개의 열을 비교하여 증가한 페이징 IO 활동과 관련된 것 같은 특정 프로그램 실행 단계가 있는지 확인합니다.
