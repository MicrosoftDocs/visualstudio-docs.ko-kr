---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ebdc5518579223a0081f30a0affd3a45e91604e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198768"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!`**편집 하며 계속 하기** 를 사용할 수 없는 이유를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 ENCUN_NONE  
 편집 하며 계속 하기를 사용할 수 없는 특별 한 이유가 없습니다.  
  
 ENCUN_INTEROP  
 InterOp 호출 중에는 편집 하며 계속 하기를 사용할 수 없습니다.  
  
 ENCUN_SQLCLR  
 CLR (공용 언어 런타임)을 사용 하는 SQL 프로시저 호출 중에는 편집 하며 계속 하기를 사용할 수 없습니다.  
  
 ENCUN_MINIDUMP  
 미니 덤프를 처리 하는 동안에는 편집 하며 계속 하기를 사용할 수 없습니다.  
  
 ENCUN_EMBEDDED  
 포함 된 코드를 처리 하는 경우 편집 하며 계속 하기를 사용할 수 없습니다.  
  
 ENCUN_ATTACH  
 세션이 디버거를 통해 시작 되지 않고 연결 되어 있기 때문에 편집 하며 계속 하기를 사용할 수 없습니다.  
  
 ENCUN_WIN64  
 64 비트 Windows 코드를 처리 하는 동안에는 편집 하며 계속 하기를 사용할 수 없습니다.  
  
## <a name="remarks"></a>설명  
 이 열거형은에서 내부용으로 사용 됩니다 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] . 사용자 지정 포트 공급자에 의해 구현 되는 [Getencon 상태](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) 및 [disableenc](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) 메서드는 항상를 반환 해야 합니다 `E_NOTIMPL` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .idl  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
