---
title: 그래픽 API 및 메모리 통계 | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa808e76e6655c5d57108c923b19794d0398b80c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735570"
---
# <a name="graphics-api-and-memory-statistics"></a>그래픽 API 및 메모리 통계
<!-- VERSIONLESS -->
Visual Studio 2017 이상에서는 그래픽 API 통계 및 메모리 통계 도구를 지원합니다.  이 두 가지 도구를 사용하면 다양한 리소스의 GPU 메모리 사용량뿐만 아니라 Direct3D API 사용에 관한 다양한 정보를 볼 수 있습니다.

## <a name="graphics-api-statistics"></a>그래픽 API 통계
Visual Studio 그래픽 진단의 그래픽 API 통계를 사용하여 수행된 모든 Direct3D 호출 및 각 호출 개수를 볼 수 있습니다.  창을 보려면 **보기 > API 통계** 메뉴 항목을 선택합니다.

![API 통계](media/gfx_diag_api_statistics.png)

이 도구는 인지하지 못한 상태에서 수행 중인 DirectX 호출이나 너무 자주 수행 중인 호출을 검색하는 데 유용할 수 있습니다.

창을 마우스 오른쪽 단추로 클릭하여 모든 데이터를 CSV로 복사한 다음, 추가 분석을 위해 Excel 같은 항목에 붙여넣을 수 있습니다.

## <a name="memory-statistics"></a>메모리 통계
이 도구는 그래픽 드라이버가 프레임에서 만드는 리소스에 대해 할당하는 메모리의 양을 표시합니다.  이 창을 보려면 **보기 > 메모리 통계** 메뉴 항목을 선택합니다.

![메모리 통계](media/gfx_diag_memory_statistics.png)

**GPU 할당** 열에는 **이벤트** 열에 표시되는 이벤트에 사용되는 메모리의 양이 표시됩니다.  조사식 아이콘 ![조사식 아이콘](media/gfx_watch.png)을 선택하여 선택된 이벤트의 [리소스 기록](graphics-event-list.md#resource-history)을 볼 수도 있습니다.

API 통계 도구와 마찬가지로 창을 마우스 오른쪽 단추로 클릭하여 모든 데이터를 CSV로 복사한 다음, 추가 분석을 위해 Excel 같은 항목에 붙여넣을 수 있습니다.

## <a name="see-also"></a>참조
- [그래픽 진단(DirectX 그래픽 디버그)](visual-studio-graphics-diagnostics.md)
- [리소스 기록](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->