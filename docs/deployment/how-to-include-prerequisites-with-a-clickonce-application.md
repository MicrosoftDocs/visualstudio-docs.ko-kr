---
title: 필수 구성 조건 포함(ClickOnce 앱)
description: 개발 컴퓨터용 ClickOnce 애플리케이션에 배포하기 위한 필수 구성 조건의 설치 관리자 패키지를 얻는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b41529182b7cca8cea8f94206601b7a818d35420
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877743"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>방법: ClickOnce 애플리케이션을 사용하여 필수 구성 요소 포함
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션에 필요한 구성 요소 소프트웨어를 배포하기 전에 먼저 이러한 필수 구성 요소용 설치 관리자 패키지를 개발 컴퓨터로 다운로드해야 합니다. 애플리케이션을 게시하고 **내 애플리케이션과 동일한 위치에서 필수 구성 요소 다운로드** 를 선택할 경우, 설치 관리자 패키지가 **패키지** 폴더에 있지 않으면 오류가 발생합니다.

> [!NOTE]
> .NET Framework 대한 설치 관리자 패키지를 추가하려면 [개발자용 .NET Framework 배포 가이드를 참조하세요.](/dotnet/framework/deployment/deployment-guide-for-developers)

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Package.xml을 사용하여 설치 관리자 패키지를 추가하려면

1. 파일 탐색기에서 **패키지** 폴더를 엽니다.

    기본적으로 경로는 `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` 입니다.

>[!NOTE]
> Visual Studio 2019 업데이트 7 릴리스 부트스트래퍼 패키지부터 *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages* 경로 아래에서도 부트스트래퍼 패키지가 검색됩니다.

2. 추가하려는 필수 구성 요소에 대한 폴더를 연 다음, 설치된 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 버전의 언어 폴더를 엽니다(예: 영어는 **en**).

3. 메모장에서 *Package.xml* 파일을 엽니다.

4. 가 포함된 **Name** 요소를 찾고 `http://go.microsoft.com/fwlink` URL을 복사합니다. **LinkID** 부분을 포함합니다.

   > [!NOTE]
   > **Name** 요소가 없으면 `http://go.microsoft.com/fwlink` 필수 구성 요소에 대한 루트 폴더에서 **Product.xml** 파일을 열고 **fwlink** 문자열을 찾습니다.

   > [!IMPORTANT]
   > 일부 필수 구성 요소에는 여러 개의 설치 관리자 패키지가 있습니다(예: 32비트 또는 64비트 시스템). 여러 **이름** 요소에 **fwlink** 가 있을 경우 각각에 대해 나머지 단계를 반복해야 합니다.

5. 브라우저의 주소 표시줄에 URL을 붙인 다음, 실행 또는 저장하라는 메시지가 표시되면 **저장** 을 선택합니다.

    이 단계에서는 설치 관리자 파일을 컴퓨터에 다운로드합니다.

6. 필수 구성 요소의 루트 폴더에 파일을 복사합니다.

    예를 들어 .NET Framework 4.7.2 필수 조건의 경우 *파일을 \Packages\DotNetFX472* 폴더에 복사합니다.

    이제 애플리케이션으로 설치 관리자 패키지를 배포할 수 있습니다.

## <a name="see-also"></a>참조
- [방법: ClickOnce 애플리케이션을 사용하여 필수 구성 조건 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
