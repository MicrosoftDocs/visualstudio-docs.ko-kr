---
title: 줄 뷰 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 25dbb0beb600f7f043ae006e09ac48b9b64d613b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773983"
---
# <a name="lines-view"></a>줄 뷰
줄 뷰는 샘플링 방법을 사용하여 수집한 프로파일러 데이터에만 사용할 수 있습니다. 이 뷰는 계측을 사용하여 수집한 데이터에 사용할 수 없습니다.

 프로필 데이터를 샘플링하기 위해 줄 뷰는 샘플이 수집될 때 직접 실행되고 있던 함수에서 문을 식별합니다. .NET 메모리 데이터에 대해 줄 뷰는 메모리를 할당하는 문을 식별합니다.

 소스 파일에서는 하나의 문이 소스 파일의 여러 줄에 걸쳐 있거나 한 줄에 여러 문이 포함될 수 있습니다.

 문은 다음에 의해 식별됩니다.

- 함수 문이 포함된 소스 파일.

- 문이 포함된 함수.

- 문이 시작되는 소스 줄.

- 문이 시작되는 소스 줄의 문자.

- 문이 끝나는 소스 줄.

- 문이 끝나는 소스 줄의 문자.

## <a name="see-also"></a>참고 항목
- [줄 뷰](../profiling/lines-view-sampling-data.md)
- [줄 뷰 - 샘플링](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [줄 뷰](../profiling/lines-view-contention-data.md)
