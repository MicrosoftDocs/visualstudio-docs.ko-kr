---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0dec9408d0cd1907a533a8cabe740832fe652398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555698"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

PDB 파일에 포함 된 소스 서버 정보를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 디버거 엔진에서 구현 되며 디버거 UI에서 사용 됩니다.  
  
## <a name="methods"></a>메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugSourceServerModule` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|원본 서버 정보의 배열을 검색 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
