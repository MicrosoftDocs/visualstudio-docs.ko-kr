---
title: 'IEnumDebugReferenceInfo2:: GetCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::GetCount
helpviewer_keywords:
- IEnumDebugReferenceInfo2::GetCount
ms.assetid: e62706e0-d2cd-48fb-8fdf-444463c651ab
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f59d6dd43653f4a6f970e9e4530123c6a54d861d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147811"
---
# <a name="ienumdebugreferenceinfo2getcount"></a>IEnumDebugReferenceInfo2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

열거형의 요소 수를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcelt`  
 제한이 열거형의 요소 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 `Next` ,, `Clone` `Skip` 및 `Reset` 메서드만 구현 해야 함을 지정 하는 일반적인 COM 열거 인터페이스의 일부가 아닙니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
