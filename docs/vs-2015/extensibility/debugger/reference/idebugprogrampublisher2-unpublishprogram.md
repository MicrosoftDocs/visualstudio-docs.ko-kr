---
title: 'IDebugProgramPublisher2:: UnpublishProgram | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05efc566cec0e7e885b16a4bb7c7e7d6256ac7b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146276"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로그램을 디버그할 수 없게 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pDebuggeeInterface`  
 진행 `IUnknown` 프로그램에 대 한 인터페이스입니다. 이 값은 # [program](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) 메서드에 제공 되는 값과 같으며 제거 되는 프로그램을 고유 하 게 식별 합니다. 즉, 쿠키로 사용 됩니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 디버그 엔진 및 세션 디버그 관리자가 프로그램을 사용할 수 있도록 하려면 # [program](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) 메서드를 사용 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
