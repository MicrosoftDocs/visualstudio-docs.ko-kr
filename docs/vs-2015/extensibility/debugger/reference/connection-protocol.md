---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 72ed9b8a747814d9537739c8dc27e5f113547756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561862"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 서버와 디버그 패키지 (DE) 간에 통신 하는 데 사용 되는 프로토콜을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 CONNECTION_NONE  
 서버에 연결 되지 않았습니다.  
  
 CONNECTION_UNKNOWN  
 연결 되었지만 알 수 없는 유형입니다.  
  
 CONNECTION_LOCAL  
 로컬 서버에 연결 합니다.  
  
 CONNECTION_PIPE  
 명명 된 파이프를 통해 연결 합니다.  
  
 CONNECTION_TCPIP  
 연결에서 TCP/IP를 사용 합니다.  
  
 CONNECTION_HTTP  
 연결에서 HTTP (웹 서버를 통해)를 사용 합니다.  
  
 CONNECTION_OTHER  
 다른 유형의 연결이 설정 되었습니다 .이 값은 현재 사용 되지 않습니다.  
  
## <a name="remarks"></a>설명  
 이러한 값은 [Getconnectionprotocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) 메서드에서 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
