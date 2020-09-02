---
title: IDiaSymbol::get_builtInKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a18567472edc15c39505acda9e5c4896d56c0f12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149786"
---
# <a name="idiasymbolget_builtinkind"></a>IDiaSymbol::get_builtInKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

HLSL 형식의 기본 제공 종류를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT get_buildInKind(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 `DWORD` HLSL 형식의 기본 제공 종류를 보유 하는에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
