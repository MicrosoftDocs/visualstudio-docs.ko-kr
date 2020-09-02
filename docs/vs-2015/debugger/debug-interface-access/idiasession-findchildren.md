---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150431"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이름 및 기호 형식과 일치 하는 지정 된 부모 식별자의 모든 자식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `parent`  
 진행 부모를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다. 이 부모 기호가 함수, 모듈 또는 블록인 경우에는 해당 어휘 자식이에서 반환 됩니다 `ppResult` . 부모 기호가 형식이 면 해당 클래스의 자식이 반환 됩니다. 이 매개 변수가 인 경우는 `NULL` `symtag` `SymTagExe` `SymTagNull` 전역 범위 (.exe 파일)를 반환 하는 또는로 설정 되어야 합니다.  
  
 `symtag`  
 진행 검색할 자식의 기호 태그를 지정 합니다. 값은 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거에서 가져옵니다. `SymTagNull`모든 자식을 검색 하려면로 설정 합니다.  
  
 `name`  
 진행 검색할 자식의 이름을 지정 합니다. `NULL`모든 자식을 검색 하려면로 설정 합니다.  
  
 `compareFlags`  
 진행 이름 일치에 적용 되는 비교 옵션을 지정 합니다. [Namesearchoptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md) 열거형의 값은 단독으로 사용 하거나 함께 사용할 수 있습니다.  
  
 `ppResult`  
 제한이 검색 된 자식 기호의 목록을 포함 하는 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="example"></a>예  
 다음 예에서는 `pFunc` name과 일치 하는 함수의 지역 변수를 찾는 방법을 보여 줍니다 `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>관련 항목  
 [설명은](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)
