---
title: '오류: 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8dcb8fa757f1cccf2f3aef6c2520e0c61da0b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682671"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>오류: 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없음
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 오류 메시지는 다음과 같습니다.  
  
 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없습니다. 원격 프로시저가 실행되기 전에 디버거에 알리지 않았습니다.  
  
 이 오류는 웹 서비스를 한 단계씩 실행하려 할 때 발생할 수 있습니다. [한 단계씩 XML Web Services 실행](https://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)을 참조하세요. 이 오류는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 이 잘못 설정된 경우에 발생할 수 있습니다.  
  
 가능한 원인은 다음과 같습니다.  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션의 web.config 파일에서 디버그 모드를 "true"로 설정하지 않았습니다. [ASP.NET 애플리케이션의 디버그 모드](../debugger/how-to-enable-debugging-for-aspnet-applications.md)를 참조하세요.  
  
- Visual Studio가 설치된 후 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 버전이 설치되었습니다. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 은 Visual Studio보다 먼저 설치해야 합니다. 이 문제를 해결하려면 Windows **제어판**, **프로그램 및 기능** 을 사용하여 Visual Studio 설치를 복구합니다.  
  
## <a name="see-also"></a>관련 항목  
 [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
