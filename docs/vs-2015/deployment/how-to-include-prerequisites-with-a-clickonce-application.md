---
title: '방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 포함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557680"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>방법: ClickOnce 애플리케이션을 사용하여 필수 구성 요소 포함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 필요한 구성 요소 소프트웨어를 배포하기 전에 먼저 이러한 필수 구성 요소용 설치 관리자 패키지를 개발 컴퓨터로 다운로드해야 합니다. 응용 프로그램을 게시 하 고 **내 응용 프로그램과 동일한 위치에서 필수 구성 요소 다운로드**를 선택 하면 설치 관리자 패키지가 **패키지** 폴더에 없는 경우 오류가 발생 합니다.  
  
> [!NOTE]
> .NET Framework에 대 한 설치 관리자 패키지를 추가 하려면 [개발자를 위한 .NET Framework 배포 가이드](/dotnet/framework/deployment/deployment-guide-for-developers)를 참조 하세요.  
  
## <a name="Package"></a> Package.xml을 사용하여 설치 관리자 패키지를 추가하려면  
  
1. 파일 탐색기에서 **패키지** 폴더를 엽니다.  
  
     기본적으로, 경로는 32비트 시스템의 경우 C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages이고 64비트 시스템의 경우 C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages입니다.  
  
2. 추가하려는 필수 구성 요소에 대한 폴더를 연 다음, 설치된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 버전의 언어 폴더를 엽니다(예: 영어는 **en**).  
  
3. 메모장에서 **Package.xml** 파일을 엽니다.  
  
4. `http://go.microsoft.com/fwlink`를 포함 하는 **Name** 요소를 찾아 URL을 복사 합니다. **LinkID** 부분을 포함합니다.  
  
    > [!NOTE]
    > **이름** 요소에 `http://go.microsoft.com/fwlink`포함 되지 않은 경우 필수 조건에 대 한 루트 폴더에서 **system.xml** 파일을 열고 **fwlink** 문자열을 찾습니다.  
  
    > [!IMPORTANT]
    > 일부 필수 구성 요소에는 여러 개의 설치 관리자 패키지가 있습니다(예: 32비트 또는 64비트 시스템). 여러 **이름** 요소에 **fwlink**가 있을 경우 각각에 대해 나머지 단계를 반복해야 합니다.  
  
5. 브라우저의 주소 표시줄에 URL을 붙인 다음, 실행 또는 저장하라는 메시지가 표시되면 **저장**을 선택합니다.  
  
     이 단계에서는 설치 관리자 파일을 컴퓨터에 다운로드합니다.  
  
6. 필수 구성 요소의 루트 폴더에 파일을 복사합니다.  
  
     예를 들어, Windows Installer 4.5 필수 구성 요소의 경우 파일을 \Packages\WindowsInstaller4_5 폴더에 복사합니다.  
  
     이제 애플리케이션으로 설치 관리자 패키지를 배포할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: ClickOnce 애플리케이션을 사용하여 필수 조건 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
