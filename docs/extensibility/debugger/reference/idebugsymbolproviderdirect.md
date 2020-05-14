---
title: 아이디버그 심볼공급자직접 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718909"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
메타데이터 및 코어 기호 인터페이스에 직접 액세스할 수 있는 기호 공급자를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>메서드
 이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|디버그 주소가 지정된 응용 프로그램 도메인 식별자를 검색합니다.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|기호 그룹의 모듈에 대한 정보를 검색합니다.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|기호 공급자가 구성원인 기호 그룹에 대한 정보를 검색합니다.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|메타데이터 가져오기 정보를 검색합니다.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|지정된 디버그 주소에서 메서드에 대한 정보를 검색합니다.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|관리되지 않는 코드에 대한 기호 판독기를 검색합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 대부분의 다른 기호 공급자 인터페이스 대신 사용할 수 있습니다. 메타데이터 및 `CorSym` 인터페이스에 직접 액세스할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
