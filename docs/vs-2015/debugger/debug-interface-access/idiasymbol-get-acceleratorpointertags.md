---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149835"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C++ AMP 액셀러레이터 스텁 함수에 해당 하는 액셀러레이터 포인터 태그 값을 모두 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cnt`  
 진행 출력 배열의 크기 `pPointerTags` 입니다.  
  
 `pcnt`  
 제한이 C++ AMP 액셀러레이터 스텁 함수의 액셀러레이터 포인터 태그 수입니다.  
  
 `pPointerTags`  
 제한이 `DWORD` C++ AMP 액셀러레이터 스텁 함수의 액셀러레이터 포인터 태그 값으로 채워지는 배열 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 `IDiaSymbol` C++ AMP 액셀러레이터 스텁 함수에 해당 하는 인터페이스에서 호출 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
