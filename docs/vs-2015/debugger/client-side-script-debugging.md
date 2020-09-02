---
title: 클라이언트 쪽 스크립트 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6405a35068b7be7ac93eb91f4d9100e6a840b0bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702375"
---
# <a name="client-side-script-debugging"></a>클라이언트 쪽 스크립트 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 디버거는 ASP.NET 페이지의 클라이언트 쪽 스크립트에서 오류를 찾아 수정하기 위한 포괄적인 디버깅 환경을 제공합니다.  
  
## <a name="opening-script-documents"></a>스크립트 문서 열기  
 **솔루션 탐색기** 에서 서버 쪽 및 클라이언트 쪽 스크립트 문서 목록을 볼 수 있습니다. **솔루션 탐색기**에서는 원하는 모든 스크립트 문서를 열 수 있습니다. 자세한 내용은 [방법: 스크립트 문서 보기](../debugger/how-to-view-script-documents.md)를 참조하세요.  
  
## <a name="breakpoint-mapping"></a>중단점 매핑  
 Visual Studio에서는 서버 쪽 코드를 직접 디버깅할 수 없지만 서버 쪽 파일에서 중단점을 설정할 수 있습니다. Visual Studio는 클라이언트 쪽 파일에서 해당하는 위치에 중단점을 자동으로 매핑하고 클라이언트 쪽 코드에서 매핑된 중단점을 만듭니다.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>스크립트에 자동 또는 수동으로 연결  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 스크립트를 디버깅하려면 디버거를 디버깅할 스크립트에 연결해야 합니다. 이 작업은 수동 또는 자동으로 수행할 수 있습니다.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버거 인터페이스를 통해 연결할 실행 스크립트 프로세스를 선택하면 디버거를 수동으로 연결할 수 있습니다. 자세한 내용은 [How to: Attach to Script](../debugger/how-to-attach-to-script.md)을 참조하세요.  
  
 다음 중 한 가지가 발생하면 디버거가 스크립트에 자동으로 연결됩니다.  
  
- 스크립트에 설정한 중단점을 적중합니다.  
  
- 스크립트 코드에서 VBScript `Stop` 문 또는 JScript `debugger` 문을 적중합니다.  
  
- 브라우저 또는 서버에서 스크립트에 구문 또는 런타임 오류가 발생합니다. 이렇게 되면 디버깅 시작 옵션이 포함된 대화 상자가 표시됩니다.  
  
  디버거를 수동으로 스크립트에 연결하는 경우 스크립트 프로세스는 중단될 때까지 계속 실행됩니다. 이 경우 **디버그** 메뉴에서 **중단** 을 선택하면 프로세스를 중단할 수 있습니다.  
  
  디버거가 자동으로 연결되는 경우 스크립트 실행은 중단점, `Stop` 문 또는 `debugger` 문이 있는 줄, 오류가 발생한 줄 또는 Internet Explorer에서 디버깅을 시작하도록 선택한 지점에서 중단됩니다.  
  
  이 위치에서 일반 디버거 기능을 사용하여 디버깅을 시작할 수 있습니다. 예를 들어 **단계** 명령을 사용하면 계속해서 코드를 한 줄씩 실행할 수 있습니다. **호출 스택** 창을 사용하여 스크립트 흐름을 보고 제어할 수 있습니다. 그리고 변수 창이나 **직접 실행** 창을 사용하면 변수 및 속성을 보거나 변경할 수 있습니다.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>스크립트 디버깅에 대한 자세한 오류 메시지  
 Visual Studio는 일반적인 스크립트 디버깅 문제에 대한 자세한 오류 메시지를 제공합니다. 이러한 메시지는 Internet Explorer에 수동으로 연결하는 경우가 아니면 표시되지 않습니다. Internet Explorer가 자동으로 열릴 때 오류 조건이 발생하는 경우에는 오류 메시지를 볼 수 있도록 수동으로 연결해 보십시오.  
  
## <a name="debugging-ajax-script-applications"></a>AJAX 스크립트 애플리케이션 디버깅  
 AJAX 사용 웹 애플리케이션은 스크립트 코드를 매우 많이 사용하며 특수한 디버깅 문제를 발생시키는 경우가 많습니다. AJAX 디버깅 기술에 대한 자세한 내용은 다음 항목을 참조하십시오.  
  
 [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)에서는 원하는 모든 스크립트 문서를 열 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [ASP.NET 및 AJAX 응용 프로그램 디버깅](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [스크립트 디버깅에 대 한 제한 사항](../debugger/limitations-on-script-debugging.md)   
 [변수 창](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [직접 실행 창](../ide/reference/immediate-window.md)   
 [Ajax 응용 프로그램 디버깅 및 추적 개요](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
