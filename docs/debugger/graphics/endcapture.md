---
title: EndCapture | Microsoft Docs
description: VsgDbg 클래스의 EndCapture 메서드를 사용하여 BeginCapture로 시작된 캡처 간격을 종료합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f7733eb9bed86bc450e4438ce34054312b13db5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880283"
---
# <a name="endcapture"></a>EndCapture
`BeginCapture`로 시작된 캡처 간격을 종료합니다.

## <a name="syntax"></a>구문

```C++
void EndCapture();
```

## <a name="remarks"></a>설명
 캡처 간격은 일반적으로 특정 그리기 호출 종류에 대한 그래픽 정보만 호출하려고 할 때와 같이 한 프레임의 하위 집합을 확장합니다. 캡처 간격이 존재하는 호출을 확장하는 경우 그래픽 정보의 두 프레임이 캡처됩니다. 첫 번째 프레임은 `BeginCapture`에 대한 호출과 존재하는 호출 간에 간격을 확장하고 두 번째 프레임은 존재하는 호출 이후 첫 번째 Direct3D 이벤트와 `EndCapture`에 대한 호출 간의 간격을 확장합니다.

 간격을 캡처하려면 그래픽 정보를 캡처하고 기록하도록 앱을 준비해야 합니다. 즉, `BeginCapture` 또는 `EndCapture`를 호출하기 전에 `VsgDbg` 클래스의 인스턴스를 통해 [Init](init.md)를 호출했어야 합니다.

## <a name="see-also"></a>참조
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)