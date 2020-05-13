---
title: 아이디버그컴플러스 심볼공급자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733468"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
관리 되는 코드에 특정 메서드와 COM + 기호 공급자를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 평가기 (EE)에 유용한 인터페이스와 디버그 엔진 (DE)에서 사용하려는 인터페이스 사이에는 분리가 없지만 다음 방법은 DE 개발자에게만 관심이 있을 것입니다: AreSymbolsLoaded, GetEntryPoint, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, 로드 심볼, 로드 심볼, 하중 기호, 대체 기호, 기호.

## <a name="methods"></a>메서드
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 인터페이스의 메서드 외에도 이 인터페이스는 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|응용 프로그램 도메인 식별자가 지정된 모듈에 대해 디버그 기호가 로드되는지 여부를 결정합니다.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|지정된 기본 형식에서 형식을 만듭니다.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|지정된 모듈의 문서 위치를 디버그 주소 배열에 매핑합니다.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|디버그 주소가 지정된 지정된 배열에 대한 형식 정보를 검색합니다.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|모듈 및 응용 프로그램 도메인이 지정된 어셈블리의 이름을 검색합니다.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|지정된 프로그래밍 언어로 구현되는 지정된 특성으로 클래스를 검색합니다.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|지정된 모듈에서 지정된 특성을 가진 클래스를 검색합니다.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|응용 프로그램 진입점을 검색합니다.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|지정된 줄 오프셋을 나타내는 함수 내에서 주소를 검색합니다.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|메서드 집합에 대 한 로컬 변수의 레이아웃을 검색합니다.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|메타데이터 개체가 지정된 지정된 토큰과 연결된 이름을 반환합니다.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|지정된 모듈에 대해 지정된 상위 특성을 가진 디버그 기호를 검색합니다.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|관리되지 않는 코드에서 사용할 기호 판독기를 검색합니다.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|디버그 주소가 지정된 기호 유형으로 검색합니다.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|지정된 디버그 주소의 함수가 삭제되는지 확인합니다.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|지정된 디버그 주소의 함수가 부실로 간주되는지 여부를 결정합니다.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|지정된 디버거 주소의 코드가 숨겨져 있는지 확인합니다.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|지정된 디버그 기호를 메모리에 로드합니다.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|데이터 스트림이 지정된 디버그 기호를 로드합니다.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|현재 디버그 기호를 지정된 데이터 스트림의 디버그 기호로 바꿉습니다.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|지정된 모듈에 대한 디버그 기호를 메모리에서 언로드합니다.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|지정된 데이터 스트림으로 메모리의 디버그 기호를 업데이트합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
