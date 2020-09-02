---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97a38b4296668cb287f34e5b1afcbd7c90477011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153217"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중단점 요청에 대해 검색할 정보를 지정 하는 유효한 값을 열거 합니다. 이 열거형은 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 열거형을 확장 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 BPREQI90_BPLOCATION  
 `bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 또는 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조체의 (중단점 위치) 필드를 초기화 하거나 사용 합니다.  
  
 BPREQI90_LANGUAGE  
 `guidLanguage`또는 구조체의 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_PROGRAM  
 `pProgram`또는 구조체의 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_PROGRAMNAME  
 `bstrProgramName`또는 구조체의 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_THREAD  
 `pThread`또는 구조체의 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_THREADNAME  
 `bstrThreadName`또는 구조체의 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_PASSCOUNT  
 `bpPassCount`또는 구조체의 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_CONDITION  
 `bpCondition`또는 구조체의 (중단점 조건) 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_FLAGS  
 `dwFlags`또는 구조체의 필드를 초기화 하거나 `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_ALLOLDFIELDS  
 구조체의에 대 한 모든 필드를 초기화 하거나 사용 `BP_REQUEST_INFO` 합니다.  
  
 BPREQI90_VENDOR  
 구조체의 필드를 초기화 하거나 사용 `guidVendor` `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_CONSTRAINT  
 구조체의 필드를 초기화 하거나 사용 `bstrConstraint` `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_TRACEPOINT  
 구조체의 필드를 초기화 하거나 사용 `bstrTracepoint` `BP_REQUEST_INFO2` 합니다.  
  
 BPREQI90_MACROTRACEPOINT  
 구조체의 필드를 초기화 하거나 사용 `bstrMacroTracepoint` `BP_REQUEST_INFO2` 합니다. BPREQI_ALLFIELDS는이 필드를 포함 하지 않습니다.  
  
 BPREQI90_ALLFIELDS  
 구조체의 모든 필드를 지정 합니다 `BP_REQUEST_INFO2` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg90  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
