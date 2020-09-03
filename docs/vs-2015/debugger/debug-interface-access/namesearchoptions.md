---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d721ebc5849fc459d24173ad0500b4b1c12260f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182974"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호 및 파일 이름에 대 한 검색 옵션을 지정 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>요소  
 `nsNone`  
 지정된 옵션이 없습니다.  
  
 `nsfCaseSensitive`  
 대/소문자를 구분 하는 이름 일치를 적용 합니다.  
  
 `nsfCaseInsensitive`  
 대/소문자를 구분 하지 않는 이름 일치를 적용 합니다.  
  
 `nsfFNameExt`  
 는 이름을 경로로 처리 하 고 파일 이름 확장명을 적용 합니다.  
  
 `nsfRegularExpression`  
 별표 (*) 및 물음표 (?)를 와일드 카드로 사용 하 여 대/소문자를 구분 하는 이름 일치를 적용 합니다.  
  
 `nsfUndecoratedName`  
 데코레이팅되지 않은 이름과 데코레이팅된 이름을 모두 포함 하는 기호에만 적용 됩니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값은 다음 메서드에 전달 됩니다.  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>요구 사항  
 헤더: dia2  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession:: findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
