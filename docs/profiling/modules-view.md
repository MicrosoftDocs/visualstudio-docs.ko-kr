---
title: 모듈 뷰 | Microsoft Docs
description: 모듈 뷰에 프로파일링 데이터의 모듈을 나열하는 방법을 알아봅니다. 각 모듈은 계층 트리의 루트 노드입니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 412b40fdb38e4931bcefb05bde8d695955d6c05a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879737"
---
# <a name="modules-view"></a>모듈 뷰
모듈 뷰는 프로파일링 데이터의 모듈을 나열합니다. 각 모듈은 계층 트리의 루트 노드입니다. 모듈의 프로파일링된 함수는 모듈 노드 아래에 나열됩니다. 프로파일링 데이터가 샘플링 방법을 사용하여 수집된 경우 줄 정보는 함수 노드 아래에 나열되고 명령 포인터 데이터는 줄 노드 아래에 나열됩니다.

 모듈 성능 데이터의 뷰를 표시하거나 닫으려면 모듈 이름을 확장하거나 축소합니다.

 열을 추가 또는 제거하려면 보고서 창을 오른쪽 단추로 클릭한 다음 **열 추가/제거** 를 선택합니다. 열 이름을 클릭하면 데이터를 정렬할 수 있습니다. 자세한 내용은 [방법: 보고서 보기 열 사용자 지정](../profiling/how-to-customize-report-view-columns.md)을 참조하세요.

 모듈 뷰에서 사용할 수 있는 열은 데이터를 수집하는 데 사용된 프로파일링 방법(샘플링 또는 계측) 및 프로파일링 실행 시 .NET 메모리 데이터가 수집되었는지 여부에 따라 달라집니다.

## <a name="see-also"></a>추가 정보
- [모듈 뷰](../profiling/modules-view-sampling-data.md)
- [모듈 뷰](../profiling/modules-view-instrumentation-data.md)
- [모듈 뷰 - 계측](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [모듈 뷰 - 샘플링](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [모듈 뷰](../profiling/modules-view-contention-data.md)
