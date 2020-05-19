---
title: VsgDbg::VsgDbg(생성자) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae94a7cb9572a0975dc1c3717275c384c2e45978
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734756"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg(생성자)
그래픽 진단의 사용자 앱 구성 요소를 준비하거나 준비하지 않고 `VsgDbg` 클래스의 인스턴스를 생성하여 지정된 Boolean 매개 변수에 따라 그래픽 정보를 캡처하고 기록합니다.

## <a name="syntax"></a>구문

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>매개 변수
 `bDefaultInit` 그래픽 정보를 캡처하고 기록하기 위해 그래픽 진단의 사용자 앱 구성 요소가 준비되도록 지정하려면 `true`이고, 이번에 그래픽 정보를 캡처하고 기록하기 위해 앱을 준비해서는 안 되도록 지정하려면 `false`입니다.

## <a name="remarks"></a>설명
 생성자가 `true`로 설정된 `bDefaultInit`로 호출되는 경우 그래픽 로그 파일의 파일 이름이 앱에 `vsgcapture.h`가 포함되기 전에 `DONT_SAVE_VSGLOG_TO_TEMP` 및 `VSG_DEFAULT_RUN_FILENAME` 전처리기 기호가 정의되는 방식에 따라 결정됩니다.

 `bDefaultInit`이 `false`로 설정된 상태로 생성자가 호출되면 `Init` 함수를 호출하여 나중에 그래픽 정보를 캡처하고 기록하도록 그래픽 진단의 사용자 앱 구성 요소를 준비할 수 있습니다.

## <a name="see-also"></a>참조
- [VsgDbg::~VsgDbg(소멸자)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)