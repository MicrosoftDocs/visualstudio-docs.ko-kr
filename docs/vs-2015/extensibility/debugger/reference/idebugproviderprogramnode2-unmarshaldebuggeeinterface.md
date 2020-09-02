---
title: 'IDebugProviderProgramNode2:: UnmarshalDebuggeeInterface | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3007d13ec3eae46511e4775497d0aad5b6325b2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146260"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로세스 경계를 넘어 지정 된 인터페이스를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `riid`  
 진행 가져올 인터페이스의 GUID입니다.  
  
 `ppvObject`  
 제한이 원하는 인터페이스를 구현 하는 개체를 반환 합니다. [C + +] 원하는 인터페이스 형식으로 직접 캐스팅할 수 있습니다. [C #] 메서드를 사용 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 하 여 원하는 인터페이스를 가져옵니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 디버그 엔진이 프로세스 공간에서 실행 중이 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 고 디버깅 중인 프로그램이 자체 프로세스 공간에서 실행 되는 경우에 사용 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
