---
title: 보안 문제 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704415"
---
# <a name="security-issues"></a>보안 문제
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio를 사용 하 여 프로그램을 디버깅 하려면 개발자가 프로그램을 실행 하는 데 필요한 권한만 있으면 됩니다. 여기에는 대부분의 상황에 대 한 원격 디버깅이 포함 됩니다. 인터넷 정보 서비스와 같은 다른 서비스와 관련 된 경우에는 더 높은 수준의 사용 권한이 필요할 수 있습니다.  
  
 Visual Studio가 실행 되는 동안 프로세스 디버그 관리자 (PDM)는 로컬 컴퓨터의 디버그 프로세스를 추적 합니다. 원격으로 msvsmon.exe 이라는 프로그램은 원격 디버깅을 처리 하 고 PDM을 사용할 수 있도록 하기 위해 개발자가 시작 합니다. msvsmon.exe은 서비스가 아니므로 수동으로 시작 해야 해당 컴퓨터에서 원격 디버깅을 사용할 수 있습니다. Visual Studio (또는 msvsmon.exe)가 실행 되 고 있지 않으면 디버깅을 위해 프로세스가 추적 되지 않습니다.  
  
 즉, 개발자는 특별 한 권한 없이 시작 된 프로그램을 디버그할 수 있습니다. 개발자는 다른 사람이 동일한 보안 그룹의 멤버인 경우 다른 사용자가 시작한 프로세스를 디버그할 수도 있습니다. 원격 디버깅을 사용 하도록 설정 하려면 필요한 파일을 원격 컴퓨터에 복사 하 고 msvsmon.exe를 시작 해야 합니다 (자세한 내용은 [장치에서 원격 도구 설정](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) 참조).  
  
## <a name="see-also"></a>관련 항목  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)   
 [프로세스 디버그 관리자](../../extensibility/debugger/process-debug-manager.md)   
 [디바이스에서 원격 도구 설정](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
