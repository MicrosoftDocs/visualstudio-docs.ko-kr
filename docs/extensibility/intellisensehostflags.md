---
title: 인텔리센스호스트플래그 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710263"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
IntelliSense 호스트 플래그를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>매개 변수

|멤버|설명|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|컨텍스트 버퍼는 읽기 전용입니다.|
|`IHF_NOSEPARATESUBJECT`|제목 텍스트가 없습니다. 컨텍스트 버퍼에는 IntelliSense 대상(의미)이 포함되어 있습니다. `!IHF_READONLYCONTEXT`|
|`IHF_SINGLELINESUBJECT`|제목 텍스트는 다중 줄로 할 수 없습니다.|
|`IHF_FORCECOMMITTOCONTEXT`|`CanCommitIntoReadOnlyBuffer`와 같습니다.|
|`IHF_OVERTYPE`|편집(제목 또는 컨텍스트)은 오버타입 모드에서 수행해야 합니다.|

## <a name="requirements"></a>요구 사항
 싱글파일편집기.idl

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.TextManager.Interop>
