---
title: Microsoft Endpoint Configuration Manager를 사용하여 Visual Studio에 대한 관리자 업데이트를 사용하도록 설정
titleSuffix: ''
description: Visual Studio에 관리자 업데이트를 배포하는 방법에 대해 알아봅니다.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: affb5a0c78c1ad1e230c571485385d9f55fc2bec
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307455"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager를 사용하여 Visual Studio에 대한 관리자 업데이트를 사용하도록 설정

Microsoft Endpoint Configuration Manager(SCCM)는 소프트웨어 업데이트 관리 워크플로를 사용하여 Visual Studio 2017 및 Visual Studio 2019 관리자 업데이트를 관리할 수 있습니다.

> [!NOTE]
> 편의상 아래에서는 Visual Studio 2017, Visual Studio 2019, Visual Studio 2022 제품을 모두 ‘Visual Studio’라고 합니다.

Microsoft는 CDN(Content Delivery Network)에 새 Visual Studio 업데이트를 게시하는 경우 해당하는 관리자 업데이트 패키지를 Microsoft 업데이트 서버에 동시에 게시합니다. 이렇게 하면 관리자가 [MUC(Microsoft 업데이트 카탈로그)](https://www.catalog.update.microsoft.com/Home.aspx) 또는 [WSUS(Windows Server Update Services)](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)를 통해 Visual Studio 업데이트를 배포할 수 있습니다. Configuration Manager는 WSUS 카탈로그의 Visual Studio 관리자 업데이트를 사이트 서버로 동기화하도록 설정될 수 있으며, 그러면 업데이트를 다운로드하여 조직 전체의 Visual Studio 클라이언트 컴퓨터에 배포할 수 있습니다. Visual Studio의 각 릴리스에 있는 수정 사항에 대한 자세한 내용은 [릴리스 정보](/visualstudio/releases/2019/release-notes)를 참조하세요.

Configuration Manager를 통해 Visual Studio 관리자 업데이트를 배포하려면 다음 두 가지 초기 준비 단계를 수행해야 합니다.
1. Visual Studio 관리자 업데이트 알림을 받도록 Configuration Manager를 설정합니다. 
2. Configuration Manager에서 Visual Studio 관리자 업데이트를 받도록 또는 받지 않도록 클라이언트 컴퓨터를 설정합니다.

이러한 단계를 수행한 후 Configuration Manager의 소프트웨어 업데이트 관리 기능을 사용하여 Visual Studio 관리자 업데이트를 배포할 수 있습니다. Visual Studio 관리자 업데이트의 다양한 유형 및 특징은 조직 전체에서 배포해야 하는 시기 및 방법에 대한 지침을 제공하는 [관리자 업데이트 적용](../install/applying-administrator-updates.md)에 설명되어 있습니다. Configuration Manager 기능 및 옵션에 대한 자세한 내용은 [Microsoft Endpoint Configuration Manager에서 소프트웨어 업데이트 배포](/mem/configmgr/sum/deploy-use/deploy-software-updates)를 참조하세요.

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Visual Studio 관리자 업데이트 알림을 받도록 Configuration Manager 설정

Visual Studio 관리자 업데이트 알림을 받도록 Configuration Manager를 설정하려면 다음이 필요합니다.

* Microsoft Endpoint Configuration Manager(현재 분기) 및 WSUS(Windows Server Update Services)를 실행하는 현재 버전의 Windows Server 및 라이선스. WSUS만 사용하여 이러한 업데이트를 배포할 수는 없습니다. Configuration Manager와 함께 사용해야 합니다.

* 계층 구조의 최상위 WSUS 서버 및 최상위 Configuration Manager 사이트 서버가 [방화벽 또는 프록시 서버 배후에서 Visual Studio와 Azure 서비스 설치 및 사용](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)에 나열된 Visual Studio URL 및 포트에 대한 액세스 권한이 있어야 합니다.  

* Visual Studio 관리자 업데이트 패키지를 사용할 수 있으면 알림을 받도록 Microsoft Endpoint Configuration Manager를 구성해야 합니다.  이렇게 하려면 다음 단계를 사용합니다. 자세한 내용은 [Microsoft Endpoint Configuration Manager의 소프트웨어 업데이트 소개](/mem/configmgr/sum/understand/software-updates-introduction)를 참조하세요.

  1. Configuration Manager 콘솔에서 **관리**(왼쪽 아래)를 선택하고 **사이트 구성**(왼쪽 가운데), **사이트** 를 선택한 다음 사이트 서버를 선택합니다.

  2. 위쪽의 **홈** 탭 리본 메뉴에서 **설정** 그룹 단추를 선택하고 **사이트 구성 요소 구성** 을 선택한 다음 **소프트웨어 업데이트 지점** 을 선택합니다.

  3. **소프트웨어 업데이트 지점 구성 요소 속성** 대화 상자에서

        * **제품** 탭의 **개발자 도구, 런타임 및 재배포** 계층 구조 아래에서 동기화하려는 Visual Studio 버전을 선택합니다.

        * **분류** 탭에서 ‘보안 업데이트’, ‘기능 팩’ 및 ‘업데이트’가 선택되어 있는지 확인합니다.

  4. 그런 다음 **소프트웨어 라이브러리**(왼쪽 아래)를 선택하여 소프트웨어 업데이트를 WSUS 서버와 동기화한 다음 위쪽의 **홈** 탭 리본 메뉴에서 **소프트웨어 업데이트 동기화** 단추를 선택합니다. 소프트웨어 업데이트를 동기화하면 Configuration Manager 콘솔에 사용 가능한 Visual Studio 관리자 업데이트가 표시되고 콘솔에서 배포가 가능합니다.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Configuration Manager에서 Visual Studio 관리자 업데이트를 수신하는 클라이언트 컴퓨터의 기능을 사용하도록 설정(또는 사용하지 않도록 설정)

클라이언트 컴퓨터에서 Visual Studio 관리자 업데이트를 수락하도록 하려면 Visual Studio 클라이언트 탐지기 유틸리티가 제대로 설치되었는지 확인하고, 클라이언트에서 관리자 업데이트를 받을 수 있도록 레지스트리 키를 설정해야 합니다.  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio 클라이언트 탐지기 유틸리티

관리자 업데이트를 제대로 인식 및 수신하려면 클라이언트 컴퓨터에 [Visual Studio 클라이언트 탐지기 유틸리티](https://support.microsoft.com/help/5001148)를 설치해야 합니다. 이 유틸리티는 2020년 5월 12일 이후에 릴리스된 모든 Visual Studio 2017 및 Visual Studio 2019 제품 업데이트에 포함되어 있으며 모든 Visual Studio 관리자 업데이트에서 필수 구성 요소로 포함되어 있고 [Microsoft 업데이트 카탈로그](https://catalog.update.microsoft.com)에서는 독립적으로 설치할 수도 있습니다.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>클라이언트 컴퓨터에 관리자 의도 인코딩

클라이언트 컴퓨터에서 관리자 업데이트를 받도록 설정해야 합니다. 이 단계는 업데이트가 의도하지 않은 클라이언트 컴퓨터로 잘못 푸시되지 않도록 하는 데 필요합니다.

 **AdministratorUpdatesEnabled**   키는 관리자가 관리자의 의도를 인코딩하기 위해 설계되었습니다. 이 키는  [Visual Studio의 엔터프라이즈 배포에 대한 기본값 설정](/visualstudio/install/set-defaults-for-enterprise-deployments) 설명서에 설명된 대로 표준 Visual Studio 위치 중 하나에 있습니다. 이 키를 만들고 값을 설정하려면 클라이언트 컴퓨터에 대한 관리자 액세스 권한이 필요합니다.

* 클라이언트 컴퓨터에서 관리자 업데이트를 허용하도록 구성하려면 **AdministratorUpdatesEnabled** REG_DWORD 키를  **1** 로 설정합니다.
*  **AdministratorUpdatesEnabled** REG_DWORD 키가 **없거나 0으로 설정** 된 경우 관리자 업데이트가 클라이언트 컴퓨터에 적용되지 않도록 차단됩니다.

## <a name="feedback-and-support"></a>피드백 및 지원

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

다음 방법을 사용하여 Visual Studio 관리자 업데이트에 대한 피드백을 제공하거나 업데이트에 영향을 주는 문제를 보고할 수 있습니다.

* [Visual Studio 설치 및 업그레이드 문제 해결](../install/troubleshooting-installation-issues.md) 참고 자료를 참조합니다.
* [Visual Studio 설치 Q&A 포럼](/answers/topics/vs-setup.html)에서 커뮤니티에 질문하세요.
* [Visual Studio 지원 페이지](https://visualstudio.microsoft.com/vs/support/)로 이동하여 문제가 FAQ에 등록되어 있는지 확인합니다.  채팅 도움말의 [지원 링크](https://visualstudio.microsoft.com/vs/support/#talktous) 단추를 선택할 수도 있습니다.
* 관리자 업데이트 사용 경험에 대해 Visual Studio 팀에 [기능 피드백을 제공하거나 문제를 보고](https://aka.ms/vs/wsus/feedback)하세요.
* 조직의 Microsoft 담당 기술 계정 관리자에게 문의합니다.

## <a name="see-also"></a>참조

* [관리자 업데이트 적용](../install/applying-administrator-updates.md)
* [Visual Studio 관리자 가이드](../install/visual-studio-administrator-guide.md)
* [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 릴리스 정보](/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 릴리스 정보](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio 설치](../install/install-visual-studio.md)
* [Microsoft 업데이트 카탈로그 FAQ](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager(SCCM) 설명서](/mem/configmgr)
* [Microsoft 카탈로그에서 Configuration Manager로 업데이트 가져오기](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [WSUS(Windows Server Update Services) 설명서](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
