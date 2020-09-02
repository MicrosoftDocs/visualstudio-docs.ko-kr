---
title: ASP.NET 및 AJAX 응용 프로그램 디버깅 | Microsoft Docs
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
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0645cd28e6124e31e19b03489661c6828799cf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686739"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>ASP.NET 및 AJAX 애플리케이션 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 디버깅하는 방법은 Windows Form 또는 다른 Windows 애플리케이션을 디버깅하는 방법과 비슷합니다. 두 종류의 애플리케이션 모두 컨트롤과 이벤트를 포함하기 때문입니다. 그러나 이 두 종류의 애플리케이션 간에는 기본적인 차이점도 있습니다.  
  
- 웹 애플리케이션에서는 상태 추적이 더 복잡합니다.  
  
- Windows 애플리케이션에서 디버깅할 코드는 대부분 한 위치에 있으며, 웹 애플리케이션에서는 코드가 클라이언트와 서버에 있을 수 있습니다. 반면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 코드는 모두 서버에 있으며 클라이언트에 JavaScript 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 코드가 있을 수도 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [ASP.NET 디버깅 준비](../debugger/preparing-to-debug-aspnet.md)  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션을 디버깅할 수 있도록 설정하는 데 필요한 단계를 설명합니다.  
  
 [웹 애플리케이션 디버깅](../debugger/debugging-web-applications.md)  
 AJAX 사용 스크립트 애플리케이션을 포함하여 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션을 디버깅하는 방법에 대해 설명합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 예외를 디버깅하려면 내 코드만 옵션을 활성화해야 하는 이유에 대해 설명합니다.  
  
 [Ajax 응용 프로그램 디버깅 및 추적 개요](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 AJAX 코드를 디버깅하는 데 유용할 수 있는 일부 기술 및 도구에 대해 설명합니다.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 IntelliTrace를 사용하면 자주 애플리케이션을 다시 시작하지 않고도 애플리케이션의 상태를 기록하고 검토할 수 있으므로 코드를 보다 빠르게 디버깅할 수 있습니다. 애플리케이션의 실행 중에 발생하는 이벤트 및 호출에 대한 정보를 확인하고 해당 시점에서 디버깅을 시작할 수 있습니다. Visual Studio Ultimate가 있어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [웹 응용 프로그램 및 스크립트 디버깅](../debugger/debugging-web-applications-and-script.md)   
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)   
 [디버거 기본 사항](../debugger/debugger-basics.md)
