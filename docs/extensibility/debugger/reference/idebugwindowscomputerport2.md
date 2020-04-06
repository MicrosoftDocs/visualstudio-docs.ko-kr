---
title: 아이디버그윈도우컴퓨터포트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ef4162469651e4b69502d3a9639d1e86c62e0b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718218"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
대상 컴퓨터에 대한 정보를 쿼리할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 세션 디버그 관리자의 포트 개체에 의해 구현됩니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugWindowsComputerPort2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[컴퓨터 정보 받기](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|디버거가 실행 중인 컴퓨터에 대한 정보를 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
