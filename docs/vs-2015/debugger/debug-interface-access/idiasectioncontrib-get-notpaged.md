---
title: 'IDiaSectionContrib:: get_notPaged | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1899e59e6eb11b53757d28f9babc09739b1fdad3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151877"
---
# <a name="idiasectioncontribget_notpaged"></a>IDiaSectionContrib::get_notPaged
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

섹션에서 메모리를 페이징할 수 없는지 여부를 나타내는 플래그를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_notPaged (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 [out, retval] `TRUE` 섹션을 페이징할 수 없으면를 반환 하 고, 그렇지 않으면를 반환 `FALSE` 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`이 속성이 지원 되지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
