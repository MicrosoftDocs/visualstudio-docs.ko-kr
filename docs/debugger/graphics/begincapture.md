---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736151"
---
# <a name="begincapture"></a>BeginCapture
`EndCapture`로 종료되는 캡처 간격을 시작합니다.

## <a name="syntax"></a>구문

```C++
void BeginCapture();
```

## <a name="remarks"></a>설명
 캡처 간격은 일반적으로 특정 그리기 호출 종류에 대한 그래픽 정보만 호출하려고 할 때와 같이 한 프레임의 하위 집합을 확장합니다. 캡처 간격이 존재하는 호출을 확장하는 경우 그래픽 정보의 두 프레임이 캡처됩니다. 첫 번째 프레임은 `BeginCapture`에 대한 호출과 존재하는 호출 간에 간격을 확장하고 두 번째 프레임은 존재하는 호출 이후 첫 번째 Direct3D 이벤트와 `EndCapture`에 대한 호출 간의 간격을 확장합니다.

 간격을 캡처하려면 그래픽 정보를 캡처하고 기록하도록 앱을 준비해야 합니다. 즉, `BeginCapture` 또는 `EndCapture`를 호출하기 전에 `VsgDbg` 클래스의 인스턴스를 통해 [Init](init.md)를 호출했어야 합니다.

## <a name="see-also"></a>참조
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)