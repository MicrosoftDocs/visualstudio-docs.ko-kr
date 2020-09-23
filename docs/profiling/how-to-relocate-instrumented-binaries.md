---
title: 계측된 이진 파일 재배치 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 13fa5c3413e620e43a695e205a0523dce23e90b4
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851348"
---
# <a name="how-to-relocate-instrumented-binaries"></a>방법: 계측된 이진 파일 재배치

계측하는 동안 애플리케이션 성능을 측정하기 위해 프로브가 이진 파일에 삽입됩니다. 계측된 이진 파일을 재배치하도록 선택하면 원본 이진 파일의 복사본이 계측되어 지정한 위치에 배치됩니다. 이 옵션은 프로파일러에서 원본 이진 파일의 이름을 바꾸지 않으려는 경우에 유용합니다. 이진 파일을 재배치하지 않으면 이진 파일의 원래 버전을 덮어씁니다.

## <a name="to-relocate-instrumented-binary"></a>계측된 이진 파일을 재배치하려면

1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

2. **속성 페이지**에서 **이진 파일** 속성을 클릭합니다.

3. **계측된 이진 파일 재배치** 확인란을 선택합니다.

4. 계측된 이진 파일의 위치를 지정합니다.

## <a name="see-also"></a>참조

[성능 세션 구성](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
