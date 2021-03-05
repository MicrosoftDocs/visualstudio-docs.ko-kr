---
description: 배열의 차원 수가 지정 된 경우 각 인덱스의 기본 인덱스 (하한값)를 검색 합니다.
title: 'IDebugArrayObject2:: GetBaseIndices | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3ec8c0081205637ae228c426ac29d0523602439
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167791"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
배열의 차원 수가 지정 된 경우 각 인덱스의 기본 인덱스 (하한값)를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>매개 변수
`dwRank`\
진행 배열의 차원 수 (차수)입니다.

`dwIndices`\
제한이 배열의 기본 인덱스 (하한값)입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 예를 들어이 함수는 다음 c # 코드에서 만든 배열에 대해 ' 5 '를 반환 합니다.

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>참고 항목
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
