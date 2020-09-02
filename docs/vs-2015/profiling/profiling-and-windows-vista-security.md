---
title: 프로파일링 및 Windows Vista 보안 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7e485bc6289634e1bb6d4b4106d54c8dc82096b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683695"
---
# <a name="profiling-and-windows-vista-security"></a>프로파일링 및 Windows Vista 보안
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

컴퓨터 관리자가 사용 가능하도록 설정한 [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] 사용자 액세스 권한 설정에 따라 개별 사용자에게 해당 컴퓨터에서 프로세스를 프로파일링하기 위한 보안 권한이 있을 수 있습니다. 다음 예제에서는 사용자 간에 가능한 차이점을 보여 줍니다.  
  
- 관리자가 드라이버 및 서비스를 시작하도록 설정한 경우 일부 사용자는 고급 프로파일링 기능에 액세스할 수 있습니다.  
  
- 도메인 사용자는 샘플 프로파일링에만 액세스가 가능할 수 있습니다.  
  
- 일부 사용자는 다른 모든 사용자에 대해 프로파일링 액세스를 거부할 수 있습니다.  
  
  자세한 내용은 [VSPerfCmd](../profiling/vsperfcmd.md)의 ADMIN 옵션을 참조하세요.  
  
## <a name="cross-session-profiling"></a>상호 세션 프로파일링  
 *상호 세션 프로파일링*은 다른 로그온 세션에서 실행되는 프로세스를 프로파일링하는 기능입니다. 대부분의 서비스가 세션 0에서 실행되며 사용자는 세션 0을 직접 실행할 수 없는 경우를 예로 들어 보겠습니다. 이 경우 성능 탐색기 도구 모음의 **프로세스에 연결** 단추나 VSPerfCmd 명령줄 도구의 /attach 옵션을 사용하면 다른 로그온 세션의 대다수 프로세스를 프로파일링할 수 있습니다.  
  
 상호 프로세스 프로파일링 표시 여부 옵션을 설정하면 사용 가능한 프로세스 목록을 확인할 수 있습니다. **프로세스에 연결**을 클릭하면 표시되는 **프로세스에 연결** 창에서 다음과 같은 옵션을 사용할 수 있습니다.  
  
- **모든 사용자의 프로세스 표시**  
  
     이 옵션을 선택하지 않으면 현재 사용자가 소유한 프로세스만 목록에 표시됩니다. **모든 사용자의 프로세스 표시**를 선택하면 모든 사용자의 프로세스가 목록에 표시됩니다.  
  
- **모든 세션의 프로세스 표시**  
  
     이 옵션을 선택하지 않으면 현재 세션의 프로세스가 목록에 표시됩니다. 이 옵션을 선택하면 모든 세션의 프로세스가 목록에 표시됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [간단한](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [방법: 실행 중인 프로세스에 연결](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)
