---
title: 호출자-호출 수신자 뷰 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bab816a0b71adef190a7d919b5ada7138a6a0e7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779716"
---
# <a name="callercallee-view"></a>호출자/호출 수신자 뷰
호출자/호출 수신자 뷰는 선택한 함수와 해당 부모 및 자식 함수에 대한 프로파일링 정보를 표시합니다. 호출자/호출 수신자 뷰에는 다음과 같은 세 개의 표가 포함되어 있습니다.

 **현재 함수**는 가운데 표에 표시되며, 선택한 함수에 대한 프로파일링 정보를 보여 줍니다. 값에는 프로파일링 실행 시 수집된 함수에 대한 모든 호출이 포함되어 있습니다.

 **현재 함수를 호출한 함수**는 위쪽 표에 표시되며, 호출자(부모) 함수의 호출에 의해 생성된 선택(현재) 함수 값의 수를 보여 줍니다.

 **현재 함수에서 호출된 함수**는 아래쪽 표에 표시되며, 현재 함수가 자식 함수를 호출한 경우 선택한 함수의 호출 수신자(자식) 함수에 대한 프로파일링 정보를 보여 줍니다.

 호출자/호출 수신자 뷰에서 사용할 수 있는 열은 데이터를 수집하는 데 사용된 프로파일링 방법(샘플링 또는 계측) 및 프로파일링 실행 시 .NET 메모리 데이터가 수집되었는지 여부에 따라 달라집니다.

 뷰의 다른 두 부분에 나열되는 함수 중 하나를 두 번 클릭하여 다른 함수를 선택하면 보고서 뷰의 가운데 부분에 현재 함수가 표시되도록 할 수 있습니다. 보고서 뷰는 자동으로 업데이트되어 변경 내용을 반영합니다.

 열 이름을 클릭하면 데이터를 정렬할 수 있습니다. 호출자/호출 수신자 뷰에 열을 추가할 수 있습니다. 자세한 내용은 [방법: 보고서 뷰 열 사용자 지정](../profiling/how-to-customize-report-view-columns.md)을 참조하세요.

## <a name="see-also"></a>참고 항목
- [호출자/호출 수신자 뷰 - 샘플링 데이터](../profiling/caller-callee-view-sampling-data.md)
- [호출자/호출 수신자 뷰 - 계측 데이터](../profiling/caller-callee-view-instrumentation-data.md)
- [호출자/호출 수신자 뷰 - .NET 메모리 계측 데이터](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [호출자/호출 수신자 뷰 - .NET 메모리 샘플링 데이터](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [호출자/호출 수신자 뷰 - 경합 데이터](../profiling/caller-callee-view-contention-data.md)
