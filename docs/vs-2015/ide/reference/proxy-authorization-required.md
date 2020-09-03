---
title: 프록시 권한 필요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297822"
---
# <a name="proxy-authorization-required"></a>프록시 권한 필요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프록시 **권한 필요** 오류는 일반적으로 사용자가 프록시 서버를 통해 Visual Studio online 리소스에 연결 하 고 프록시 서버에서 호출을 차단 하는 경우 발생 합니다.

이 오류를 해결 하려면 다음 단계 중 하나 이상을 시도 합니다.

- Visual Studio를 다시 시작합니다. 프록시 인증 대화 상자가 나타납니다. 대화 상자에서 자격 증명을 입력합니다.

- 위의 단계를 수행해도 문제가 해결되지 않으면 프록시 서버에서 https://go.microsoft.com 주소가 아닌 *.visualStudio.com 주소에 대한 자격 증명을 입력하라는 메시지를 표시하기 때문일 수 있습니다. 이러한 서버에 대해 다음 Url을 허용 목록에 추가 하 여 Visual Studio에서 모든 로그인 시나리오를 차단 해제 해야 합니다.

  - *.windows.net

  - *.microsoftonline.com

  - *.visualStudio.com

  - *.microsoft.com

  - *.live.com

- https://go.microsoft.com https://go.microsoft.com Visual Studio가 다시 시작 될 때 주소 및 서버 끝점 모두에 대해 프록시 인증 대화 상자가 표시 되도록 허용 목록에서 주소를 제거할 수 있습니다.

- 프록시를 사용 하 여 기본 자격 증명을 사용 하려면 다음을 수행 합니다.

   1. **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (또는 **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**)에서 devenv.exe.config(devenv.exe 구성 파일)를 찾습니다.

   2. 구성 파일에서 `<system.net>` 블록을 찾아 다음 코드를 추가합니다.

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      에서 네트워크에 대 한 올바른 프록시 주소를 삽입 `proxyaddress="<http://<yourproxy:port#>` 합니다.

- [이 블로그 게시물](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) 의 지침에 따라 프록시를 사용할 수 있는 코드를 추가 합니다.
