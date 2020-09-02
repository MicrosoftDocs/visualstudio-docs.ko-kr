---
title: IDebugComPlusSymbolProvider | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733468"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
관리 코드와 관련 된 메서드를 사용 하 여 COM + 기호 공급자를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기 (EE)에 유용한 인터페이스와 디버그 엔진 (DE)에서 사용 하려는 인터페이스 사이에는 분리 되지 않지만 다음 메서드는 개발자만의 관심을 가질 수 있습니다. AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, Loadsymbols Sfromstream, ReplaceSymbols, UnloadSymbols 및 UpdateSymbols.

## <a name="methods"></a>메서드
 [Idebug기호 공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|응용 프로그램 도메인 식별자가 지정 된 경우 지정 된 모듈에 대해 디버그 기호가 로드 되는지 여부를 결정 합니다.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|지정 된 기본 형식에서 형식을 만듭니다.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|지정 된 모듈의 문서 위치를 디버그 주소 배열에 매핑합니다.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|디버그 주소가 지정 된 경우 지정 된 배열에 대 한 형식 정보를 검색 합니다.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|해당 모듈 및 응용 프로그램 도메인이 지정 된 어셈블리의 이름을 검색 합니다.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|지정 된 프로그래밍 언어로 구현 된 지정 된 특성을 사용 하 여 클래스를 검색 합니다.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|지정 된 모듈에서 지정 된 특성을 사용 하 여 클래스를 검색 합니다.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|응용 프로그램 진입점을 검색 합니다.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|지정 된 선 오프셋을 나타내는 함수 내의 주소를 검색 합니다.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|메서드 집합에 대 한 지역 변수의 레이아웃을 검색 합니다.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|지정 된 토큰에 연결 된 메타 데이터 개체의 이름을 반환 합니다.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|지정 된 모듈의 지정 된 부모 특성을 사용 하 여 디버그 기호를 검색 합니다.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|비관리 코드에서 사용할 기호 판독기를 검색 합니다.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|디버그 주소가 지정 된 경우 기호 형식을 검색 합니다.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|지정 된 디버그 주소의 함수가 삭제 되었는지 여부를 확인 합니다.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|지정 된 디버그 주소의 함수를 오래 된 것으로 간주 하는지 여부를 확인 합니다.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|지정 된 디버거 주소에서 코드를 숨길지 여부를 결정 합니다.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|지정 된 디버그 기호를 메모리에 로드 합니다.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|데이터 스트림이 지정 된 경우 디버그 기호를 로드 합니다.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|현재 디버그 기호를 지정 된 데이터 스트림의 코드로 바꿉니다.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|지정 된 모듈의 디버그 기호를 메모리에서 언로드합니다.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|지정 된 데이터 스트림을 사용 하 여 메모리의 디버그 기호를 업데이트 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
