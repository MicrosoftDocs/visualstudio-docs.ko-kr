---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e30d9cc9df592cc6feb97c14449dbc6a122ec63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149365"
---
# <a name="exception_state"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

예외 상태를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>멤버  
 EXCEPTION_NONE  
 예외에서 중지 하지 마십시오.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 예외가 처음 발생할 때 중지 됩니다. 예외 이벤트를 설명할 때이 플래그는 예외 이벤트가 첫째 예외 이벤트 임을 나타냅니다.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 두 번째 예외 발생 시 중지 합니다. 예외 이벤트를 설명할 때 예외 이벤트는 두 번째 예외 이벤트 임을 나타냅니다.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 사용자 모드 예외를 처음으로 실행 하는 경우 중지 합니다. 예외 이벤트를 설명할 때 예외 이벤트는 첫 번째 사용자 예외 이벤트 임을 나타냅니다.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 사용자 모드 예외가 catch 되지 않은 경우 중지 합니다. 예외 이벤트를 설명할 때 예외 이벤트가 catch 되지 않은 사용자 모드 예외 이벤트 임을 나타냅니다.  
  
 EXCEPTION_STOP_ALL  
 예외를 중지 합니다. 예외 이벤트를 설명할 때 사용 되지 않습니다.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 예외 이벤트를 설명할 때에서 예외를 계속할 수 없음을 나타냅니다.  
  
 EXCEPTION_CODE_SUPPORTED  
 예외에 지원 코드가 있음을 나타냅니다. 예외를 표시 하는 데 사용 됩니다.  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 예외 코드가 16 진수로 표시 되어야 함을 나타냅니다. 예외를 표시 하는 데 사용 됩니다.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 예외 코드가 JustMyCode을 지원함을 나타냅니다. 예외를 표시 하는 데 사용 됩니다.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 관리 코드 디버거가 예외를 처리 해야 함을 나타냅니다. 설정 되지 않은 경우 기본 디버거는 예외를 처리 합니다. 이는 [Setallexceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 메서드에 전달 되며 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조에는 사용 되지 않습니다.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 사용 하지 않는 경우 사용 하지 마십시오.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 사용 하지 않는 경우 사용 하지 마십시오.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 사용 하지 않는 경우 사용 하지 마십시오.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 사용 하지 않는 경우 사용 하지 마십시오.  
  
## <a name="remarks"></a>설명  
 `dwState`예외의 상태와이에 대해 수행할 수 있는 작업을 나타내기 위해 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조체의 멤버로 사용 됩니다.  
  
 이러한 값은 모든 예외의 상태를 설정 하기 위해 [Setallexceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 메서드에도 전달 됩니다.  
  
 이러한 플래그는 비트 or와 함께 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
