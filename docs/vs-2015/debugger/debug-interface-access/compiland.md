---
title: Compiland | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 579ac6a70b379364870425e78cee41ac0840a214
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164003"
---
# <a name="compiland"></a>컴파일 대상
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

`SymTagCompiland`.Exe 파일에 연결 된 각 Compiland에 대해 하나의 기호가 있습니다. Compiland 정보는 태그가 있는 기호 간에 분할 되며 `SymTagCompiland` 추가 Compiland 기호를 로드 하지 않고 검색할 수 있으며 태그를 사용 하 여 기호 `SymTagCompilandDetails` 를 추가 기호를 로드 해야 할 수도 있습니다.  
  
## <a name="properties"></a>속성  
 다음 표에서는이 기호 형식에 유효한 속성을 보여 줍니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` 컴파일하는 동안 편집 하며 계속 하기를 사용 하도록 설정한 경우|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|.Exe 파일에 대 한 기호입니다.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호의 ID입니다.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|개체가 로드 된 라이브러리 또는 개체 파일의 이름입니다.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Compiland 개체 파일의 파일 이름입니다.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|원본 파일의 이름입니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|`SymTagCompiland` [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나를 반환 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
