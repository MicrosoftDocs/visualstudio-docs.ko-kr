---
title: 'IDebugDisassemblyStream2:: Seek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d774cc0bf6bca1278423249960bbc5233aa6ad37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203019"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 위치에 상대적인 지정 된 수의 명령을 디스어셈블리 스트림에서 읽기 포인터를 이동 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwSeekStart`  
 진행 검색 프로세스를 시작할 상대 위치를 지정 하는 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) 열거형의 값입니다.  
  
 `pCodeContext`  
 진행 검색 작업이 상대적인 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다. 이 매개 변수는 인 경우에만 사용 됩니다 `dwSeekStart`  =  `SEEK_START_CODECONTEXT` . 그렇지 않으면이 매개 변수는 무시 되 고 null 값일 수 있습니다.  
  
 `uCodeLocationId`  
 진행 검색 작업의 기준이 되는 코드 위치 식별자입니다. 이 매개 변수는 인 경우 사용 됩니다 `dwSeekStart`  =  `SEEK_START_CODELOCID` . 그렇지 않으면이 매개 변수는 무시 되 고 0으로 설정할 수 있습니다. 코드 위치 식별자에 대 한 설명은 [Getcodelocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) 메서드에 대 한 설명 섹션을 참조 하세요.  
  
 `iInstructions`  
 진행 에 지정 된 위치를 기준으로 이동할 명령의 수입니다 `dwSeekStart` . 뒤로 이동 하는 경우이 값은 음수일 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`검색 위치가 사용 가능한 명령 목록을 벗어난 지점에 있는 경우를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 검색이 목록의 시작 부분 앞의 위치에 있는 경우 읽기 위치는 목록의 첫 번째 명령으로 설정 됩니다. 참조를 목록 끝 뒤의 위치로 이동 하면 읽기 위치가 목록의 마지막 명령으로 설정 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
