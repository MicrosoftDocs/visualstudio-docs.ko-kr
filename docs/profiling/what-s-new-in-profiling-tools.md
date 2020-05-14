---
title: Visual Studio 2017에서 프로파일링의 새로운 기능 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 0512c6e95f0a26184593f7af5ba08c31c33a3299
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128333"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]에 포함된 프로파일링 도구의 새로운 기능

진단 도구에는 수정해야 하는 앱의 문제를 식별하는 데 사용할 수 있는 새로운 시각화가 포함되어 있습니다. 이제는 진단 도구에 ASP.NET 앱 지원이 포함됩니다.

자세한 내용은 [[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 릴리스 정보](/visualstudio/releasenotes/vs2017-relnotes)를 참조하세요.

성능 분석을 위한 주요 영역을 중점적으로 확인할 수 있는 **요약** 탭이 도구에 추가되었습니다. 이 탭에서는 발생한 이벤트의 수를 확인하고, 힙의 스냅샷을 생성하고, CPU 사용량 데이터 수집을 빠르게 활성화할 수 있습니다. 이 뷰에는 모든 [Application Insights](/azure/azure-monitor/app/visual-studio) 또는 [UI 분석](/visualstudio/releasenotes/vs2017-relnotes) 이벤트가 표시됩니다. 또한 Visual Studio Enterprise의 경우 이 뷰에는 IntelliTrace 이벤트도 표시됩니다.

![진단 도구 요약 탭](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

CPU 사용량 도구에는 성능 문제를 발생시킬 가능성이 가장 높은 기능을 식별하는 데 사용할 수 있는 [새로운 시각화](../profiling/Beginners-Guide-to-Performance-Profiling.md)가 포함되어 있습니다. 새로운 **호출자/호출 수신자** 뷰에서는 선택한 함수와의 함수 호출 비용을 조사할 수 있습니다.

![진단 도구 호출자/호출 수신자 뷰](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>참조

- [Visual Studio의 프로필](../profiling/index.yml)
- [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)