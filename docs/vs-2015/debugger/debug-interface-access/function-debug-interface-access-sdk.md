---
title: 함수 (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fb1355dfebaad4230c349c0c7b30ae400ecdaa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692178"
---
# <a name="function-debug-interface-access-sdk"></a>함수(디버그 인터페이스 액세스 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

각 함수는 기호로 식별 됩니다 `SymTagFunction` .  
  
## <a name="properties"></a>속성  
 다음 표에서는이 기호 형식에 유효한 속성을 보여 줍니다.  
  
|속성|`Data type`|설명|  
|--------------|-----------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|함수가 멤버 함수인 경우 [CV_access_e 열거형](../../debugger/debug-interface-access/cv-access-e.md)값 중 하나입니다.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|위치의 오프셋 부분 자세한 내용은 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)을 참조 하세요.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Location의 Section 부분 자세한 내용은 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)을 참조 하세요.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|함수가 멤버 함수인 경우 클래스에 대 한 기호입니다.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|클래스 부모 기호의 ID입니다.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` 함수가 상수로 표시 되 면입니다.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` 함수가 사용자 지정 호출 규칙을 사용 하는 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` 함수가 far 반환을 수행 하는 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` 함수에서 할당 된 메모리 함수를 사용 하는 경우 (uinnder DIA SDK V 8.0 이상)|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` 함수에 c + + 스타일 예외 처리 (DIA SDK V 8.0 이상 에서만)가 포함 된 경우|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` 함수에 비동기 예외 처리가 포함 된 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` 함수가 인라인 어셈블리를 포함 하는 경우 (DIA SDK V 8.0 이상에만 해당)|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` 함수가 [vjmp](https://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f) 호출을 포함 하는 경우 (DIA SDK v 8.0 이상 에서만)|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` 함수가 보안 검사를 포함 하는 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` 함수에 Win32 스타일의 구조적 예외 처리가 포함 된 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` 함수에 [setjmp](https://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2) 호출이 포함 된 경우 (DIA SDK v 8.0 이상 에서만)|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` 함수에 인터럽트 반환이 있는 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` 함수가 virtual 인 경우|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` 함수가 [인라인, __inline \_ _forceinline](../../misc/inline-inline-forceinline.md) 특성 중 하나로 표시 되 면입니다.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` 함수가 [naked](https://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) 특성으로 표시 되는 경우 (DIA SDK v 8.0 이상 에서만)|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` 함수가 정적 함수 이면 (DIA SDK V 8.0 이상 에서만)입니다.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|위치에서 시작 하는 함수 코드의 바이트 수입니다.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|바깥쪽 compiland 기호입니다.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호의 ID입니다.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|함수에는 정적 또는 메타 데이터 위치를 사용할 수 있습니다. 자세한 내용은 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)를 참조 하세요.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|함수의 이름입니다.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` 함수가 인라인 함수가 아닌 경우 (n DIA SDK V 8.0 이상)|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` 함수에 연결할 수 없는 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` 함수가 값을 반환 하지 않는 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` 함수가 버퍼 보안 검사를 사용 하 여 컴파일 되었지만 스택 순서 지정이 수행 되지 않은 경우|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` 코드에 최적화 된 코드에 대 한 디버그 정보가 있는 경우 (DIA SDK V 8.0 이상 에서만)|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` if 함수는 순수 가상 함수입니다.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|모듈 내에서이 함수의 상대 위치입니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|`SymTagFunction` [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나를 반환 합니다.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|함수에 대 한 메타 데이터 토큰입니다.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|함수 시그니처의 기호입니다.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|형식 기호의 ID입니다.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` 함수가 정렬 되어 있지 않으면입니다.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|데코레이팅되지 않은 함수 이름 형식 (DIA SDK v 8.0 이상 에서만)|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|데코레이팅되지 않은 형식의 함수 이름 (DIA SDK v 8.0 이상 에서만)의 일부 또는 전부입니다.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` 가상 함수인 경우입니다.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|실행 가능 이미지 내에서이 함수의 위치입니다.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|가상 함수인 경우 가상 함수 테이블의 오프셋입니다.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` 함수가 volatile로 표시 되 면입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [CV_access_e 열거형](../../debugger/debug-interface-access/cv-access-e.md)   
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)   
 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)
