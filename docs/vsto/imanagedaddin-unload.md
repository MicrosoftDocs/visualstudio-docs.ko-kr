---
title: IManagedAddin::Unload
description: 관리되는 VSTO 추가 기능이 언로드되기 바로 전에 호출됩니다.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e45fd9e6385388b9c6bc32098cf59799618d511b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469712"
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
