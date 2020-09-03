---
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d34b1b6519407e02d4340a5108ef03cece12b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202773"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

소스 파일에서 지정 된 위치에 대 한 코드 경로 목록을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszHint`  
 진행 IDE의 **소스** 또는 **디스어셈블리** 뷰에서 커서 아래의 단어입니다.  
  
 `pStart`  
 진행 현재 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.  
  
 `pFrame`  
 진행 현재 중단점과 연결 된 스택 프레임을 나타내는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 개체입니다.  
  
 `fSource`  
 진행 `TRUE` **소스** 뷰에는 0이 아닌 ()이 고, 디스어셈블리 뷰에서는 0 ( `FALSE` )입니다. **Disassembly**  
  
 `ppEnum`  
 제한이 코드 경로 목록을 포함 하는 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) 개체를 반환 합니다.  
  
 `ppSafety`  
 제한이 선택한 코드 경로를 건너뛰는 경우 중단점으로 설정할 추가 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체를 반환 합니다. 이는 short-circuit 부울 식의 경우에 발생할 수 있습니다 (예:).  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 코드 경로는 프로그램 실행에서 현재 지점으로 가져오기 위해 호출 된 메서드 또는 함수의 이름을 설명 합니다. 코드 경로 목록은 호출 스택을 나타냅니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
