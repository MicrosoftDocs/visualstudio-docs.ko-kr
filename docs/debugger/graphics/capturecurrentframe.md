---
title: CaptureCurrentFrame | Microsoft Docs
description: VsgDbg 클래스의 CaptureCurrentFrame 메서드를 사용하여 그래픽 로그 파일에 현재 프레임의 나머지 부분을 캡처합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d86ac7d23fa209560222415dce50f4e5ac508
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727946"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
그래픽 로그 파일에 현재 프레임의 나머지 부분을 캡처합니다.

## <a name="syntax"></a>구문

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>설명
 다른 캡처가 현재 진행 중인 경우(예: `BeginCapture` 함수에 의해 시작된 캡처) 해당 캡처를 완료하고 그래픽 로그에 다른 프레임으로 기록합니다. 이후에 즉시 그래픽 진단에서 다른 프레임으로도 기록되는 현재 프레임의 나머지 부분 캡처를 시작합니다. 현재 프레임의 끝은 호출로 표시됩니다.

 프레임을 캡처하려면 그래픽 정보를 캡처하고 기록하도록 앱을 준비해야 합니다. 즉, `CaptureCurrentFrame`을 호출하기 전에 `VsgDbg` 클래스의 인스턴스를 통해 [Init](init.md)을 호출해야 합니다.

## <a name="see-also"></a>참조
- [Init](init.md)
- [BeginCapture](begincapture.md)