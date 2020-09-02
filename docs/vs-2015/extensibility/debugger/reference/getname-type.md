---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 648f84b106dab7aa6e38cc3e45e59162a216a875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160134"
---
# <a name="getname_type"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

검색할 파일의 이름 유형을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>멤버  
 GN_NAME  
 문서 또는 컨텍스트의 이름을 지정 합니다.  
  
 GN_FILENAME  
 문서 또는 컨텍스트의 전체 경로를 지정 합니다.  
  
 GN_BASENAME  
 문서 또는 컨텍스트의 전체 경로 대신 기본 파일 이름을 지정 합니다.  
  
 GN_MONIKERNAME  
 모니커 형식의 문서 또는 컨텍스트의 고유 이름을 지정 합니다.  
  
 GN_URL  
 문서 또는 컨텍스트의 URL 이름을 지정 합니다.  
  
 GN_TITLE  
 문서의 제목을 지정 합니다 (있는 경우).  
  
 GN_STARTPAGEURL  
 프로세스의 시작 페이지 URL을 가져옵니다.  
  
## <a name="remarks"></a>설명  
 이러한 값은 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)및 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 메서드에 매개 변수로 전달 되어 반환할 이름 유형을 지정 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
