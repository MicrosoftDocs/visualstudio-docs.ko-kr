---
title: CompilandEnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandEnv symbol
ms.assetid: 808404bb-ece1-47f1-b9ea-c76d4d86ddd9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dfa9f1efa266a95e0580717b06cee4b9d2a7725
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164437"
---
# <a name="compilandenv"></a>CompilandEnv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

컴파일러가 기호와 함께 추가 환경 변수를 포함할 수 있습니다. `SymTagCompilandEnv`이러한 각 변수에는 하나의 기호가 있습니다.  
  
## <a name="properties"></a>속성  
 다음 표에서는이 기호 형식에 유효한 속성을 보여 줍니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|부모 compiland 기호입니다.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호의 ID입니다.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|변수의 이름입니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|`SymTagCompilandEnv` [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나를 반환 합니다.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|변수의 문자열 반환 내용 ( `VT_BSTR` )입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
