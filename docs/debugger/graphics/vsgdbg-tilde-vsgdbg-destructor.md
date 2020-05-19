---
title: VsgDbg::~VsgDbg(소멸자) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734790"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg(소멸자)
`VsgDbg` 클래스의 인스턴스를 제거합니다. 그래픽 정보가 활발히 기록되고 있는 경우 그래픽 로그 파일은 종료되고 닫히며 그래픽 정보를 활발히 캡처하는 동안 사용된 리소스는 해제됩니다.

## <a name="syntax"></a>구문

```C++
~VsgDbg();
```

## <a name="see-also"></a>참조
- [VsgDbg::VsgDbg(생성자)](vsgdbg-vsgdbg-constructor.md)