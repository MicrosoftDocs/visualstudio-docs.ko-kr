---
title: 'IDebugProgram2:: GetDebugProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b86a1aa144e553b126445a865330a8edb786ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187909"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로그램의 속성을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppProperty`  
 제한이 프로그램의 속성을 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드에서 반환 하는 속성은 프로그램에 따라 다릅니다. 프로그램에서 두 개 이상의 속성을 반환 해야 하는 경우이 메서드에서 반환 되는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체는 추가 속성의 컨테이너 이며 [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드를 호출 하면 모든 속성의 목록이 반환 됩니다.  
  
 프로그램은 인터페이스를 통해 설명할 수 있는 추가 속성의 개수와 형식을 노출할 수 있습니다 `IDebugProperty2` . IDE는 제네릭 속성 브라우저 사용자 인터페이스를 통해 추가 프로그램 속성을 표시할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
