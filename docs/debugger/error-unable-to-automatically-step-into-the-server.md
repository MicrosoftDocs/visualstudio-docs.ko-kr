---
title: 오류 - 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없음 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 647f51314d5506e817fa6982aa693b62f62125cf
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599909"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>오류: 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없음
이 오류 메시지는 다음과 같습니다.

 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없습니다. 원격 프로시저가 실행되기 전에 디버거에 알리지 않았습니다.

 이 오류는 웹 서비스를 한 단계씩 실행하려 할 때 발생할 수 있습니다. [한 단계씩 XML Web Services 실행](/previous-versions/zc57803s(v=vs.100))을 참조하세요. 이 오류는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 이 잘못 설정된 경우에 발생할 수 있습니다.

 가능한 원인은 다음과 같습니다.

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션의 web.config 파일에서 디버그 모드를 "true"로 설정하지 않았습니다. [ASP.NET 애플리케이션의 디버그 모드](../debugger/how-to-enable-debugging-for-aspnet-applications.md)를 참조하세요.

- Visual Studio가 설치된 후 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 버전이 설치되었습니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 은 Visual Studio보다 먼저 설치해야 합니다. 이 문제를 해결하려면 Windows **제어판 >프로그램 및 기능**을 사용하여 Visual Studio 설치를 복구합니다.

## <a name="see-also"></a>참조
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)