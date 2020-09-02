---
title: 'IDiaLoadCallback2:: RestrictOriginalPathAccess | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 970a188b5d72353dbb3ccf64fd74f3354f1ba888
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151956"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

원본 디버그 디렉터리에서 .pdb 파일을 찾을 수 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이외의 모든 반환 코드는 `S_OK` 원래 디버그 디렉터리에서 .pdb 파일을 찾을 수 없습니다. 원본 디버그 디렉터리는 디버깅을 설정할 때 실행 파일로 컴파일되는 기호 파일의 경로입니다. 이 경로는 실행 파일이 있는 경로와 동일할 필요는 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
