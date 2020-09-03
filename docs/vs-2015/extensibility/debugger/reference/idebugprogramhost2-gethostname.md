---
title: 'IDebugProgramHost2:: GetHostName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb7ceae40282115dc455691789c3882a1620e829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165121"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 프로그램의 호스팅 프로세스에 대 한 제목, 이름 또는 파일 이름을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwType`  
 진행 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) 열거형의 값입니다.  
  
 `pbstrHostName`  
 제한이 호스팅 프로세스의 요청 된 이름을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드의 일반적인 구현에서는 `dwType` 매개 변수가 무시 되 고 호스트 컴퓨터의 이름이 반환 됩니다. 또 다른 가능한 구현은 `dwType` [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) 메서드 호출에 매개 변수를 전달 하 여 이름을 가져오는 것입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
