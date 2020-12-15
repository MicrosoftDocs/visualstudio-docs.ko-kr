---
title: IntelliSenseHostFlags | Microsoft Docs
description: IntelliSenseHostFlags 열거형은 IntelliSense 호스트 플래그를 지정 합니다. 이 문서에서는 열거형 값에 대해 설명 합니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b206cc4aa7c1ff388d6868fa8a0533d15da094ff
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487506"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
IntelliSense 호스트 플래그를 지정 합니다.

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

|멤버|Description|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|컨텍스트 버퍼는 읽기 전용입니다.|
|`IHF_NOSEPARATESUBJECT`|제목 텍스트가 없습니다. 컨텍스트 버퍼에 IntelliSense 대상 (함축)이 포함 되어 있습니다 `!IHF_READONLYCONTEXT` .|
|`IHF_SINGLELINESUBJECT`|제목 텍스트는 여러 줄을 사용할 수 없습니다.|
|`IHF_FORCECOMMITTOCONTEXT`|`CanCommitIntoReadOnlyBuffer`와 동일합니다.|
|`IHF_OVERTYPE`|편집 (주체 또는 컨텍스트)은 겹쳐쓰기 모드에서 수행 해야 합니다.|

## <a name="requirements"></a>요구 사항
 SingleFileeditor. idl

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.TextManager.Interop>
