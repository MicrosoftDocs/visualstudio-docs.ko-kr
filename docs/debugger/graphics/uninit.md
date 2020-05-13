---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734814"
---
# <a name="uninit"></a>UnInit
그래픽 로그 파일을 종료하고 닫고 앱이 그래픽 정보를 기록하는 동안 사용된 리소스를 확보합니다.

## <a name="syntax"></a>구문

```C++
void UnInit();
```

## <a name="remarks"></a>설명
 `UnInit` 클래스의 인스턴스가 소멸될 때 `VsgDbg` 가 자동으로 호출됩니다. `VsgDbg` 인스턴스가 그래픽 정보를 기록하지 않는 경우 아무런 영향이 없습니다.

 `UnInit` 클래스의 인스턴스에서 `VsgDbg`가 호출된 경우 `Init`를 호출하여 새 그래픽 로그 파일을 만들고 `UnInit`를 호출하여 종료할 수 있습니다. 동일한 `VsgDbg` 인스턴스를 사용하여 원하는 횟수만큼 이 작업을 반복하여 여러 독립 그래픽 로그 파일을 만들 수 있습니다.

## <a name="see-also"></a>참조
- [Init](init.md)