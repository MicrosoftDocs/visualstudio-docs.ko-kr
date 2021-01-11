---
title: 복사(프로그래밍 방식 캡처) | Microsoft Docs
description: VsgDbg 클래스의 Copy 메서드를 사용하여 활성 그래픽 로그(.vsglog) 파일의 내용을 새 파일에 복사합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727846"
---
# <a name="copy-programmatic-capture"></a>복사(프로그램 방식 캡처)
활성 그래픽 로그(.vsglog) 파일 내용을 새 파일에 복사합니다.

## <a name="syntax"></a>구문

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>매개 변수
 `szNewVSGLog` 새 그래픽 로그 파일 이름입니다.

## <a name="remarks"></a>설명
 그래픽 정보를 새 파일에 복사하려면 이미 캡처한 일부 그래픽 정보가 있어야 합니다. 그렇지 않으면 아무 것도 실행되지 않습니다.