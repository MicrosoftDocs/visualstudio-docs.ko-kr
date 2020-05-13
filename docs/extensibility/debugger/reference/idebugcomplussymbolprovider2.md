---
title: 아이디버그컴플러스심볼라이더2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28c68398b69196f53c4f8792f3479d403cbebcda
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733239"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
관리 되는 코드에 특정 메서드와 COM + 기호 공급자를 나타냅니다 및 **IDebugComPlus Symbol**[공급자를](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)확장 합니다.

## <a name="syntax"></a>구문

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>메서드
 [IDebugComPlusSymbol공급자](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) 인터페이스의 메서드 외에도 이 인터페이스는 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|지정된 메서드에 선 정보가 있는지 확인합니다.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|이름이 지정된 형식을 검색합니다.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|토큰이 지정된 형식을 검색합니다.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|지정된 디버그 주소가 시퀀스 지점인지 확인합니다.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|지정된 콜백 방법을 사용하여 디버그 기호를 로드합니다.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|**ICorDebugModule** 개체가 지정된 데이터 스트림에서 디버그 기호를 로드합니다.|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|**ICorDebugModule** 개체가 지정된 디버그 기호를 로드합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
