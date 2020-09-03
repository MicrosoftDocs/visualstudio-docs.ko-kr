---
title: 'IDebugAlias2:: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca8f2311b58fc7e73f9eb4f4c14f993c88b9a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736407"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
응용 프로그램 도메인에 대 한 식별자를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>매개 변수
`pappDomainId`\
제한이 응용 프로그램 도메인 식별자를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 응용 프로그램 도메인 식별자는 응용 프로그램이 다시 시작 되 고 새 응용 프로그램 도메인이 만들어질 때마다 변경 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
