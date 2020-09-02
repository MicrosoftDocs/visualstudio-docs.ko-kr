---
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb8074317e52b43806a61d6486c53d7409333e2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153411"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중단점 요청에 대 한 중단점의 위치 유형을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>멤버  
 BPLT_NONE  
 중단점 위치를 지정 하지 않습니다.  
  
 BPLT_FILE_LINE  
 중단점의 위치 형식을 파일 줄로 지정 합니다.  
  
 BPLT_FUNC_OFFSET  
 중단점의 위치 유형을 함수 오프셋으로 지정 합니다.  
  
 BPLT_CONTEXT  
 중단점의 위치 유형을 컨텍스트로 지정 합니다.  
  
 BPLT_STRING  
 중단점의 위치 유형을 문자열로 지정 합니다.  
  
 BPLT_ADDRESS  
 중단점의 위치 유형을 주소로 지정 합니다.  
  
 BPLT_RESOLUTION  
 중단점의 위치 유형을 해상도로 지정 합니다.  
  
 BPLT_CODE_FILE_LINE  
 중단점의 위치 유형을 소스 코드 줄로 지정 합니다.  
  
 BPLT_CODE_FUNC_OFFSET  
 중단점의 위치 유형을 코드 함수 오프셋으로 지정 합니다.  
  
 BPLT_CODE_CONTEXT  
 중단점의 위치 형식을 코드 컨텍스트로 지정 합니다.  
  
 BPLT_CODE_STRING  
 중단점의 위치 유형을 코드 문자열로 지정 합니다.  
  
 BPLT_CODE_ADDRESS  
 중단점의 위치 유형을 코드 주소로 지정 합니다.  
  
 BPLT_DATA_STRING  
 중단점의 위치 유형을 데이터 문자열로 지정 합니다.  
  
 BPLT_TYPE_MASK  
 값에서 중단점 형식을 추출할 수 있도록 비트 마스크를 지정 합니다.  
  
 BPLT_LOCATION_TYPE_MASK  
 는 비트 마스크를 지정 하므로 중단점 위치 형식을 값에서 추출할 수 있습니다.  
  
## <a name="remarks"></a>설명  
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) 메서드에 매개 변수로 전달 됩니다.  
  
 중단점 위치 형식은 중단점 형식과 위치 형식으로 구성 됩니다. 즉, 중단점 위치 형식은 단순히 중단점 형식 (예: `BPT_CODE` ) 또는 위치 형식 (예:)이 되지 않습니다 `BPLT_FILE_LINE` . 현재 지원 되는 모든 중단점 위치 형식에 대해 미리 정의 된 상수는이 열거형에 포함 됩니다 ( `BPLT_CODE_FILE_LINE` 부터 `BPLT_DATA_STRING` ).  
  
 `BPT_CODE` 및 `BPT_DATA` 는 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) 열거형의 멤버입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
