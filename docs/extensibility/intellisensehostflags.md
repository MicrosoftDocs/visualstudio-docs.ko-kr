---
title: IntelliSenseHostFlags | Microsoft Docs
description: IntelliSenseHostFlags 열거형은 IntelliSense 호스트 플래그를 지정합니다. 이 문서에서는 열거형 값에 대해 설명합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33345f86c69d0faeaa5863534e21eca5ecc176cc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902620"
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

|구성원|Description|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|컨텍스트 버퍼는 읽기 전용입니다.|
|`IHF_NOSEPARATESUBJECT`|제목 텍스트가 없습니다. 컨텍스트 버퍼에는 IntelliSense-target이 포함됩니다(을 `!IHF_READONLYCONTEXT` 의미함).|
|`IHF_SINGLELINESUBJECT`|주체 텍스트는 여러 줄로 지원되지 않습니다.|
|`IHF_FORCECOMMITTOCONTEXT`|`CanCommitIntoReadOnlyBuffer`와 동일합니다.|
|`IHF_OVERTYPE`|편집(주체 또는 컨텍스트)은 overtype 모드에서 수행해야 합니다.|

## <a name="requirements"></a>요구 사항
 SingleFileeditor.idl

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.TextManager.Interop>
