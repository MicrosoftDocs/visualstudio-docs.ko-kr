---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ec01ebc32472e315fe2c905ecfd2cfef0f4bbe1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541013"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  관리되는 VSTO 추가 기능이 언로드되기 바로 전에 호출됩니다.

## <a name="syntax"></a>구문

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>반환 값
 메서드가 성공적으로 완료되었는지 여부를 나타내는 HRESULT 값입니다.

## <a name="remarks"></a>설명
 이 메서드는 현재 버전의 Microsoft Office에서 호출되지 않습니다. 이 메서드는 나중에 사용하도록 예약됩니다.

## <a name="see-also"></a>참고 항목
- [IManagedAddin 인터페이스](../vsto/imanagedaddin-interface.md)
- [IManagedAddIn::Load](../vsto/imanagedaddin-load.md)
