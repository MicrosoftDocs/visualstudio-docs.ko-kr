---
title: 포트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153694"
---
# <a name="ports"></a>포트
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면에서 **포트**는 다음과 같습니다.  
  
- 는 서버에서 실행 되는 프로세스 집합의 컨테이너입니다. 예를 들어 포트는 직렬 케이블 또는 네트워크로 연결 되지 않은 컴퓨터에 의해 Windows CE 기반 장치에 대 한 연결을 나타낼 수 있습니다. 로컬 포트 라고 하는 하나의 특수 포트에는 로컬 컴퓨터에서 실행 되는 모든 프로세스가 포함 됩니다.  
  
- 이름 또는 식별자를 기준으로 자신을 식별할 수 있습니다.  
  
- 는 포트에서 실행 되는 모든 프로세스를 열거 하 고 이러한 프로세스를 시작 및 종료할 수 있습니다.  
  
- 는 [Addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)에 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 인수를 전달 하 여 만든 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스로 표시 됩니다.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 모든 Windows 기반 프로세스 (네이티브 및 관리)를 처리 하는 기본 포트를 제공 합니다. Windows 기반이 아닌 외부 장치를 사용 하 여 연결 하려면 사용자 지정 포트를 구현 해야 합니다. 이러한 사용자 지정 포트를 제공 하려면 사용자 지정 포트 공급자도 구현 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [서버용](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [프로세스만](../../extensibility/debugger/processes.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
