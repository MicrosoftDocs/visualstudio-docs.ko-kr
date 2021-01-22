---
title: 원격 도구 다운로드 차단 해제
description: Windows Server에서 원격 도구의 다운로드 차단을 해제합니다. 해당 작업은 기본 IE 보안 설정 때문에 시간이 오래 걸릴 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54d85ee7df7f4038cc78b10f83be79e524d3bfd2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205647"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>방법: Windows Server에서 원격 도구 다운로드 차단 해제

Windows Server에서 Internet Explorer의 기본 보안 설정을 사용하면 원격 도구와 같은 구성 요소를 다운로드하는 데 시간이 오래 걸릴 수 있습니다.

* Internet Explorer에서 보안 강화 구성이 사용하도록 설정되어 있으므로 리소스를 포함하는 도메인을 명시적으로 허용한 경우(즉, 신뢰할 수 있는 경우)를 제외하면 웹 사이트를 열고 웹 리소스에 액세스할 수 없습니다. 해당 설정을 사용하지 않도록 설정할 수 있지만 보안 위험을 초래할 수 있으므로 권장하지 않습니다.

* Windows Server 2016에서는 **인터넷 옵션** > **보안** > **인터넷** > **사용자 지정 수준** > **다운로드** 의 기본 설정으로 파일 다운로드를 사용하지 않도록 설정할 수도 있습니다. Windows Server에서 원격 도구를 직접 다운로드하도록 선택하는 경우 파일 다운로드를 사용하도록 설정해야 합니다.

Windows Server에서 도구를 다운로드하려면 다음 작업 중 하나를 수행하는 것이 좋습니다.

* Visual Studio를 실행하는 컴퓨터와 같은 다른 컴퓨터에 원격 도구를 다운로드한 다음 *.exe* 파일을 Windows Server에 복사합니다.

* Visual Studio 컴퓨터의 [파일 공유](../debugger/remote-debugging.md#fileshare_msvsmon)에서 원격 디버거를 실행합니다.

* Windows Server에서 원격 도구를 직접 다운로드하고 신뢰할 수 있는 사이트 추가 메시지가 나오면 수락합니다. 최신 웹사이트에는 종종 많은 타사 리소스가 포함되므로 많은 메시지가 표시될 수 있습니다. 또한 리디렉션된 링크를 수동으로 추가해야 할 수 있습니다. 다운로드를 시작하기 전에 신뢰할 수 있는 사이트 중 일부를 추가하도록 선택할 수 있습니다. **인터넷 옵션 > 보안 > 신뢰할 수 있는 사이트 > 사이트** 로 이동하여 다음 사이트를 추가합니다.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  my.visualstudio.com에 있는 이전 버전의 디버거의 경우 다음과 같은 다른 사이트를 추가하여 로그인이 성공하는지 확인합니다.

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    원격 도구를 다운로드하는 동안 이러한 도메인을 추가하도록 선택하는 경우 메시지가 표시되면 **추가** 를 선택합니다.

    ![차단된 콘텐츠 대화 상자](../debugger/media/remotedbg-blocked-content.png)

    소프트웨어를 다운로드하는 경우 다양한 웹 사이트 스크립트 및 리소스를 로드하는 권한을 부여하라는 추가 요청을 받습니다. my.visualstudio.com에서는 다른 도메인을 추가하여 로그인이 성공하는지 확인하는 것이 좋습니다.