---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179196"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

스택 프레임 유형을 지정 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>요소  
 `FrameTypeFPO`  
 프레임 포인터 생략 FPO 정보를 사용할 수 있습니다.  
  
 `FrameTypeTrap`  
 커널 트랩 프레임입니다.  
  
 `FrameTypeTSS`  
 커널 트랩 프레임입니다.  
  
 `FrameTypeStandard`  
 표준 EBP 스택 프레임입니다.  
  
 `FrameTypeFrameData`  
 프레임 포인터 생략 프레임 데이터 정보를 사용할 수 있습니다.  
  
 `FrameTypeUnknown`  
 디버그 정보가 없는 프레임입니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값은 [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) 메서드를 호출 하 여 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
