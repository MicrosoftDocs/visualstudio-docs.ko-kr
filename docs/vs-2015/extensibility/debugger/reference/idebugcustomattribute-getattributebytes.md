---
title: 'IDebugCustomAttribute:: GetAttributeBytes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7813e8e3131b04dc7174b5b666950dd68a6060a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569072"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

특성 정보를 바이트의 blob으로 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppBlob`  
 [in, out] 특성 바이트를 사용 하 여 채워진 배열입니다.  
  
 `pdwLen`  
 [in, out] 배열에 반환할 최대 바이트 수를 지정 `ppBlob` 하 고 배열에 실제로 기록 되는 바이트 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 `ppBlob`사용할 수 있는 특성 바이트 수를 반환 하려면 매개 변수를 null 값으로 설정 합니다. 그런 다음 배열을 할당 하 고이 배열을 `ppBlob` 매개 변수에 전달 합니다.  
  
 특성 바이트는 사용자 지정 특성의 원시 데이터를 나타냅니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
