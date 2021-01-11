---
title: 레지스터 값 편집 | Microsoft Docs
description: 레지스터 창(주소 수준 디버깅을 사용하도록 설정한 경우에만 사용 가능)에서 해당 값을 편집하여 레지스터의 내용을 수정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f83f67f57e67080f97a6df434f8dfc008e36892
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903547"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>방법: 레지스터 값 편집(C#, C++, Visual Basic, F#)

레지스터 창은 **옵션** 대화 상자의 **디버깅** 노드에서 주소 수준 디버깅을 활성화한 경우에만 사용할 수 있습니다.

### <a name="to-change-the-value-of-a-register"></a>레지스터 값을 변경하려면

1. **레지스터** 창에서 탭 키 또는 마우스를 사용하여 변경하려는 값으로 삽입 지점을 이동합니다. 입력하기 시작할 때 덮어 쓰려는 값 앞에 커서가 있어야 합니다.

2. 새 값을 입력합니다.

    > [!CAUTION]
    > 레지스터 값을 변경하면(특히 EIP 및 EBP 레지스터에서) 프로그램 실행에 변경된 값이 적용됩니다.

    > [!CAUTION]
    > 부동 소수점 값을 편집하면 소수 부분이 10진수에서 이진수로 변환되면서 약간의 오차가 발생할 수 있습니다. 겉보기에 변화가 없는 편집 작업을 수행하는 경우에도 부동 소수점 변수의 LSB 중 일부가 변경될 수 있습니다.

## <a name="see-also"></a>참조
- [방법: 레지스터 창 사용](../debugger/how-to-use-the-registers-window.md)