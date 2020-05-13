---
title: 이데버그알리아스2::겟앱도메인 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736407"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
응용 프로그램 도메인의 식별자를 검색합니다.

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
【아웃】 응용 프로그램 도메인 식별자를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 응용 프로그램을 다시 시작하고 새 응용 프로그램 도메인을 만들 때마다 응용 프로그램 도메인 식별자가 변경됩니다.

## <a name="see-also"></a>참조
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
