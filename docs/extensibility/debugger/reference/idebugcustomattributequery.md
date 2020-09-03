---
title: IDebugCustomAttributeQuery | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 598db5ad711c8b61339e188311c1a437a24d013c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732616"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
메서드 또는 형식에 대 한 사용자 지정 특성에 대 한 쿼리를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|해당 이름이 지정 된 사용자 지정 특성을 검색 합니다.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|지정 된 사용자 지정 특성이 정의 되어 있는지 여부를 확인 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
