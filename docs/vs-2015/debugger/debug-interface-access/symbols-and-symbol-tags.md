---
title: 기호 및 기호 태그 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 625752125d3c68e9f03afd41cd549995fbc3272e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193544"
---
# <a name="symbols-and-symbol-tags"></a>기호 및 기호 태그
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

컴파일된 프로그램에 대 한 디버그 정보는 프로그램 데이터베이스 (.pdb) 파일에 DIA (디버그 인터페이스 액세스) SDK Api를 사용 하 여 액세스할 수 있는 기호로 저장 됩니다. 모든 기호에는 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 및 [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) 속성이 있습니다. `symTag`속성은 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거형에서 정의한 기호의 종류를 나타냅니다. `symIndexId`속성은 `DWORD` 기호의 모든 인스턴스에 대 한 고유 식별자를 포함 하는 값입니다.  
  
 기호에는 기호에 대 한 추가 정보 뿐만 아니라 다른 기호 ( [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) 또는 [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)에 대 한 참조)를 지정할 수 있는 속성도 있습니다. 참조가 포함 된 속성을 쿼리하면 참조가 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체로 반환 됩니다. 이러한 속성은 항상 동일한 이름으로 다른 속성과 쌍을 이룹니다. [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) 및 [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)와 같이 "Id"를 사용 하 여 접미사가 붙습니다. 기호 [위치](../../debugger/debug-interface-access/symbol-locations.md), [기호 형식의 어휘 계층](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)및 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) 에 있는 테이블은 다양 한 종류의 기호에 대 한 속성을 간략하게 설명 합니다. 이러한 속성에는 관련 된 정보나 다른 기호에 대 한 참조가 있을 수 있습니다. 속성은 `*Id` 관련 속성의 숫자 서 수 식별자 이므로 추가 토론에서 생략 됩니다. 이러한 매개 변수는 매개 변수 설명이 필요한 경우에만 참조 됩니다.  
  
 속성에 액세스 하려고 할 때 오류가 발생 하지 않고 symbol 속성에 값이 할당 된 경우 속성의 "get" 메서드는를 반환 합니다 `S_OK` . 의 반환 값은 `S_FALSE` 속성이 현재 기호에 대해 유효 하지 않음을 나타냅니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)  
 기호에 포함 될 수 있는 다양 한 종류의 위치를 설명 합니다.  
  
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 파일, 모듈, 함수 등의 어휘 계층 구조를 구성 하는 기호 형식을 설명 합니다.  
  
 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 클래스, 배열 및 함수 반환 형식과 같은 다양 한 언어 요소에 해당 하는 기호 형식을 설명 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버그 인터페이스 액세스 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
