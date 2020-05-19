---
title: '오류: ASP.NET이 설치되어 있지 않음 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 7d754cc2bb7931cdcbdb42abeddd554390ba320c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737914"
---
# <a name="error-aspnet-not-installed"></a>오류: ASP.NET이 설치되어 있지 않음
이 오류는 디버깅하려는 컴퓨터에 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]이 제대로 설치되어 있지 않을 때 발생합니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]이 설치되지 않았거나 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]을 먼저 설치하고 나중에 IIS를 설치했을 수 있습니다.

### <a name="to-reinstall-aspnet"></a>ASP.NET을 다시 설치하려면

1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    여기서, *version*은 컴퓨터에 설치된 .NET Framework의 버전 번호(예: v1.0.370)입니다. 프레임워크 버전은 `\WINDOWS\Microsoft.NET\Framework` 디렉터리에서 확인할 수 있습니다.

   > [!NOTE]
   > Windows Server 2003에서는 제어판의 **프로그램 추가 또는 제어**를 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]을 설치할 수 있습니다.

## <a name="see-also"></a>참조
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
