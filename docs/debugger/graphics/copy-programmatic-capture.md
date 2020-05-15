---
title: 복사(프로그래밍 방식 캡처) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895956"
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