---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159306"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디스어셈블리에 대 한 플래그를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>멤버  
 DF_DOCUMENTCHANGE  
 이 명령이 이전 문서와 다른 문서에 있음을 나타냅니다.  
  
 DF_DISABLED  
 이 명령이 실행 되지 않음을 나타냅니다.  
  
 DF_INSTRUCTION_ACTIVE  
 이 명령이 실행할 다음 명령 중 하나 (둘 이상 있을 수 있음) 임을 나타냅니다.  
  
 DF_DATA  
 이 명령이 실제 데이터 (코드 아님) 임을 나타냅니다.  
  
 DF_HASSOURCE  
 이 명령에 소스가 있음을 나타냅니다. 프로 파일링 또는 가비지 수집 코드와 같은 일부 지침에는 해당 소스가 없습니다.  
  
 DF_DOCUMENT_CHECKSUM  
 필드에 `bstrDocumentUrl` 문서 URL 뒤에 체크섬 데이터가 포함 되어 있음을 나타냅니다. 체크섬 데이터가 저장 되는 방법에 대 한 [Disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) 구조는 설명 섹션을 참조 하세요.  
  
## <a name="remarks"></a>설명  
 `dwFlags` [Disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) 구조의 멤버로 사용 됩니다.  
  
 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
