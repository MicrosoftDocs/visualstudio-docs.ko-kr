---
title: Exe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe2930e0947bf0fa69408dc81c19d058d6cdd870
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164270"
---
# <a name="exe"></a>Exe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exe는 .exe 또는 .dll 파일의 전역 범위를 나타내므로 어휘 또는 클래스 부모가 없는 유일한 기호입니다. 태그에는 파일당 기호가 하나만 있습니다 `SymTagExe` . [IDiaSession:: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) 메서드는 기호를 반환 합니다.  
  
## <a name="properties"></a>속성  
 다음 표에서는이 기호 형식에 유효한 속성을 보여 줍니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|이 실행 파일의 보존 기간입니다.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` 이 실행 파일의입니다.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` 이 실행 파일에 연결 된 기호 파일에 C 형식이 포함 된 경우 (DIA SDK v 8.0 이상 에서만)|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` 이 실행 파일에 연결 된 기호 파일에서 전용 기호를 제거 하는 경우 (DIA SDK v 8.0 이상 에서만)|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|대상 CPU ( [CV_CPU_TYPE_e 열거형](../../debugger/debug-interface-access/cv-cpu-type-e.md) 값 중 하나)를 나타내는 값입니다.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|.Exe 파일의 이름입니다.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|실행 파일의 서명입니다.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|.Exe 파일 .pdb 또는 dbg 파일의 전체 경로입니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|`SymTagExe` [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나를 반환 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSession:: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
