---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8001ced3ba2116ec8ff76ecdac2d0789304335e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547249"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

관리 코드 제네릭을 지 원하는 데 사용할 수 있는 필드 형식을 확장 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>메서드  
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|지정 된 확장 필드 종류를 검색 합니다.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|필드가 폐쇄형 형식을 나타내는지 여부를 확인 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: Sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
