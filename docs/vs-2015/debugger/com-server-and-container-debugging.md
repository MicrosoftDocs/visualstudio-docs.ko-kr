---
title: COM 서버 및 컨테이너 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 631b1d35a0878bfc362b03751f35909839c7da19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161562"
---
# <a name="com-server-and-container-debugging"></a>COM 서버 및 컨테이너 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

COM 애플리케이션은 프로그래머가 직접 제어할 수 없는 많은 작업을 수행합니다. DLL 사이의 통신, 개체 사용 횟수, 클립보드 작업 등 제한된 몇 가지 영역에서 프로그램이 비정상적으로 작동할 수 있습니다. 이러한 문제가 발생하면 먼저 문제가 발생한 위치를 추적해야 합니다.  
  
 Visual Studio 디버거에서는 컨테이너와 서버 사이를 이동하면서 단계적으로 실행할 수 있습니다. RPC(원격 프로시저 호출) 사이에서 단계별 실행도 가능합니다.  
  
## <a name="debugging-a-com-server-and-container-in-the-same-solution"></a><a name="BKMK_COMServerandContainerintheSameSolution"></a> 동일한 솔루션의 COM 서버 및 컨테이너 디버깅  
 동일한 솔루션 내에서 프로젝트 두 개를 사용하여 COM 서버와 컨테이너를 디버깅할 수 있습니다. 각 프로젝트에 적절한 중단점을 설정하고 디버깅하십시오. 컨테이너에서는 중단점에 도달하여 서버가 호출될 경우 디버깅이 완료되어 서버 코드가 반환될 때까지 대기합니다.  
  
 COM 컨테이너 디버깅은 표준 프로그램 디버깅과 유사합니다. 그러나 컨테이너 애플리케이션으로 데이터를 끌어 오는 경우처럼 콜백을 실행하는 이벤트가 디버깅될 때는 한 가지 차이점이 있습니다. 이 경우에는 콜백 함수에 중단점을 설정해야 합니다.  
  
## <a name="debugging-a-server-application-without-container-information"></a><a name="BKMK_ServerApplicationWithoutContainerInformation"></a> 컨테이너 정보 없이 서버 애플리케이션 디버깅  
 컨테이너 애플리케이션에 대한 디버깅 정보가 없거나 필요하지 않은 경우에는 다음 3단계 절차를 통해 서버 애플리케이션 디버깅을 시작할 수 있습니다.  
  
1. 일반적인 애플리케이션처럼 서버 디버깅을 시작합니다.  
  
2. 원하는 대로 중단점을 설정합니다.  
  
3. 컨테이너 애플리케이션을 시작합니다.  
  
## <a name="debugging-a-server-and-domain-isolation-sdi-application"></a><a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> SDI(서버 및 도메인 격리) 애플리케이션 디버깅  
 SDI 서버 애플리케이션을 디버깅할 때는 C/C++, C# 또는 Visual Basic 프로젝트에 대한 *프로젝트* 속성 페이지 대화 상자의 **명령줄 인수** 속성에서 `/Embedding` 또는 `/Automation`을 지정해야 합니다.  
  
 이 명령줄 인수를 사용하면 컨테이너에서 실행하는 것처럼 디버거에서 서버 애플리케이션을 실행할 수 있습니다. 그런 다음 프로그램 관리자나 파일 관리자에서 컨테이너를 시작하면 컨테이너는 디버거에서 시작된 서버 인스턴스를 사용합니다.  
  
 *프로젝트* 속성 페이지 대화 상자에 액세스하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, 바로 가기 메뉴에서 속성을 선택합니다. 명령줄 인수 속성을 찾으려면 구성 속성 범주를 확장하고 디버깅 페이지를 클릭하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [COM 및 ActiveX 디버깅](../debugger/com-and-activex-debugging.md)
