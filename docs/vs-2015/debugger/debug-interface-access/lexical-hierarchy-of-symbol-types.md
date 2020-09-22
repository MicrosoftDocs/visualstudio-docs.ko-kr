---
title: 기호 형식의 어휘 계층 구조 Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e70b83046c41b13cb51324eb63e81b26a118a81f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841947"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>기호 형식의 어휘 계층 구조
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음 표에서는 어휘 계층 구조에 있는 기호 형식을 보여 줍니다.  
  
## <a name="symbol-types"></a>기호 형식  
  
|기호 형식|Description|  
|-----------------|-----------------|  
|[주석](../../debugger/debug-interface-access/annotation.md)|프로그램 코드에서 주석이 추가 된 위치를 지정 합니다.|  
|[차단](../../debugger/debug-interface-access/block.md)|함수에서 중첩 된 범위를 지정 합니다.|  
|`Compiland`|`compiland`.Exe 파일에 연결 된를 지정 합니다.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|추가 compiland 정보를 로드 해야 할 수 있는 compiland 데이터를 지정 하므로 검색 하는 데 런타임 오버 헤드가 발생 합니다.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Compiland를 컴파일할 때 중요 한 추가 환경 변수를 지정 합니다.|  
|[사용자 지정(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|사용자 정의 기호를 지정 합니다.|  
|[데이터(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|이러한 변수를 매개 변수, 지역 변수, 전역 변수 및 클래스 멤버로 지정 합니다.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|데이터의 전역 범위를 지정 합니다. 전체 .exe 또는 .dll 파일에 해당 합니다.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|디버깅이 종료 되는 정의 된 지점이 있는 함수를 지정 합니다.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|디버깅이 시작 될 정의 된 지점이 있는 함수를 지정 합니다.|  
|[함수(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|함수를 지정 합니다.|  
|[레이블(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|프로그램 코드의 위치를 지정 합니다.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|실행 프로그램을 빌드할 때 표시 되는 외부 기호를 지정 합니다.|  
|[썽크](../../debugger/debug-interface-access/thunk.md)|을 지정 합니다 `thunk` .|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|식별자를 지정 합니다 `namespace` .|  
  
> [!NOTE]
> 기호 유형에 따라 추가 기호 속성을 사용할 수 있습니다. 이러한 속성은 개별 기호 항목에 나열 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [기호 및 기호 태그](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)
