---
title: 서버 (Visual Studio SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ed2ce924b22827a82a67664e3e473f0930a87e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199400"
---
# <a name="servers-visual-studio-sdk"></a>서버(Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면에서 **서버**는 다음과 같습니다.  
  
- 는 포트 및 포트 공급자의 컨테이너 이며 포트 및 포트 공급자를 세션 디버그 관리자 (SDM) 및 디버그 엔진에 전달 하는 데 사용 됩니다.  
  
- 이름으로 자신을 식별 하 고 해당 포트 및 포트 공급자를 열거할 수 있습니다.  
  
- 는 Visual Studio 에서만 구현 되는 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스로 표시 됩니다 .이 인터페이스는 visual studio를 실행 하는 각 인스턴스에 대해 하나의 서버 인스턴스만 구현 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [포트](../../extensibility/debugger/ports.md)   
 [포트 공급자](../../extensibility/debugger/port-suppliers.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
