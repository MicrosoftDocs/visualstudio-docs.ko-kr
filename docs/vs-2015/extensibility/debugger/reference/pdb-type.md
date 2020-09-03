---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad4b6a06a2a145daa85d780f4d23dfac9bebf7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205106"
---
# <a name="pdb_type"></a>PDB_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 구조는 PDB 기호에서 가져온 필드 형식에 대 한 정보를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 ulAppDomainID  
 기호를 가져온 응용 프로그램의 ID입니다. 이는 응용 프로그램의 인스턴스를 고유 하 게 식별 하는 데 사용 됩니다.  
  
 guidModule  
 이 필드를 포함 하는 모듈의 GUID입니다.  
  
 symid  
 이 필드에 해당 하는 기호의 ID입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체는 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) `dwKind` 구조체의 필드가 `TYPE_INFO` `TYPE_KIND_PDB` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거형의 값)로 설정 된 경우 TYPE_INFO 구조체에서 합집합의 일부로 표시 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
