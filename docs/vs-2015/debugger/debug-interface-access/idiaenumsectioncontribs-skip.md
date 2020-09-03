---
title: 'IDiaEnumSectionContribs:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 55dd45244779ca341a4228adf3256d42616e66d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189944"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

열거형 시퀀스에서 지정 된 개수의 섹션 기여를 건너뜁니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 건너뛸 열거 시퀀스의 섹션 기여 수입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 `S_OK` 되 고, 그렇지 않으면 `S_FALSE` 건너뛸 섹션 기여도가 더 이상 없는 경우를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
