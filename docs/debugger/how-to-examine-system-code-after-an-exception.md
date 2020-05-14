---
title: 예외 발생 후 시스템 코드 검사 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98f3eb98024e20350151904f297f7e7b4d6f1fea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733380"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>방법: 예외 발생 후 시스템 코드 검사
예외가 발생하면 예외의 원인을 확인하기 위해 시스템 호출 내부 코드를 검사할 수 있습니다. 다음 절차에서는 시스템 코드에 대해 로드된 기호가 없거나 내 코드만을 사용하는 경우 이러한 작업을 수행하는 방법에 대해 설명합니다.

### <a name="to-examine-system-code-following-an-exception"></a>예외 발생 후 시스템 코드를 검사하려면

1. **호출 스택** 창에서 마우스 오른쪽 단추를 클릭한 다음, **외부 코드 표시**를 클릭합니다.

     내 코드만을 사용하지 않는 경우에는 바로 가기 메뉴에서 이 옵션을 사용할 수 없으며 기본적으로 시스템 코드가 표시됩니다.

2. **호출 스택** 창에 표시되는 외부 코드 프레임을 마우스 오른쪽 단추로 클릭합니다.

3. **다음에서 기호 로드**를 가리킨 다음, **Microsoft 기호 서버**를 클릭합니다.

    1. 내 코드만을 사용하는 경우 내 코드만을 이제 사용하지 않는다는 대화 상자가 표시되는데 이는 시스템 호출을 한 단계씩 실행하는 데 필요한 조치입니다.

    2. **공용 기호 다운로드** 대화 상자가 표시됩니다. 다운로드가 완료되면 이 대화 상자는 사라집니다.

4. 이제 **호출 스택** 창 및 다른 창에서 시스템 코드를 검사할 수 있습니다. 예를 들어 호출 스택 프레임을 두 번 클릭하여 월본 또는 **디스어셈블리** 창에서 코드를 볼 수 있습니다.

## <a name="see-also"></a>참조
- [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)