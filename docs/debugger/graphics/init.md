---
title: Init | Microsoft Docs
description: VsgDbg의 Init() 메서드를 사용하여 그래픽 정보를 기록하는 그래픽 진단의 앱 내 구성 요소를 준비합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 094f4f3c64570a0af5396e903541c70a919cc0d3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996190"
---
# <a name="init"></a>Init
그래픽 정보를 그래픽 로그 파일에 캡처하고 기록하도록 그래픽 진단의 사용자 앱 구성 요소를 준비합니다.

## <a name="syntax"></a>구문

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>매개 변수
 `vsgLogGetter` 함수, 함수 포인터, 람다 또는 함수 개체와 같이 매개 변수를 `wchar_t`로 구성된 버퍼의 길이 및 해당 버퍼에 대한 포인터로 취급하고 `void`를 반환합니다. 호출되면 호출 가능한 엔터티는 그래픽 정보를 기록하는 데 사용할 파일 이름을 결정하고 반환하기 전에 이를 지정된 버퍼에 씁니다.

## <a name="remarks"></a>설명
 생성자의 `Init` 매개 변수를 `VsgDbg`로 지정하여 `bDefaultInit` 클래스의 인스턴스를 생성할 때 `true` 함수가 자동으로 호출되고, 그렇지 않으면 `Init`를 명시적으로 먼저 호출해야 그래픽 정보를 캡처하고 기록할 수 있습니다.

 `UnInit`를 호출하여 활성 그래픽 로그 파일을 종료하고 닫은 다음 `Init`를 다시 호출하여 더 많은 그래픽 정보를 새 그래픽 로그 파일에 캡처하고 기록할 수 있습니다. 동일한 `VsgDbg` 인스턴스를 사용하여 원하는 횟수만큼 이 작업을 반복하여 여러 독립 그래픽 로그 파일을 만들 수 있습니다.

## <a name="see-also"></a>참조
- [UnInit](init.md)