---
title: 포트 공급자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153710"
---
# <a name="port-suppliers"></a>포트 공급자
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면에서 **포트 공급자**는 다음과 같습니다.  
  
- 는 서버에 포함 되어 있으며 해당 서버에 대 한 요청에 포트를 제공 합니다.  
  
- 포함 하는 서버에서 포트를 추가 하 고 제거할 수 있습니다.  
  
- 는 서버에 제공 된 모든 포트를 열거할 수 있습니다.  
  
- 는 레지스트리를 통해 Visual Studio에 등록 된 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스로 표시 됩니다. 이 인터페이스는 [Getportsupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)를 호출 하 여 가져올 수 있습니다.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 기본 포트 공급자와 기본 포트를 제공 합니다. 사용자 지정 포트를 구현 해야 하는 경우 해당 사용자 지정 포트를 제공 하기 위해 사용자 지정 포트 공급자도 구현 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [서버용](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [포트](../../extensibility/debugger/ports.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
