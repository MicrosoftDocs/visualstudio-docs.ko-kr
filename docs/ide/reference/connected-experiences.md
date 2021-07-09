---
title: Visual Studio의 연결 환경
description: 연결 환경이 클라이언트 머신에서 인터넷에 연결되어 고객에게 서비스를 제공합니다.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 689fc40be8aee959023777a3fac6d9134ee979ea
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222892"
---
# <a name="connected-experiences-in-visual-studio"></a>**Visual Studio의 연결 환경** #

Visual Studio는 더욱 효과적으로 코딩할 수 있도록 설계된 클라이언트 소프트웨어 애플리케이션과 연결 환경으로 구성됩니다. 연결 환경의 예로는 [NuGet](/nuget/consume-packages/install-use-packages-visual-studio) 패키지 업데이트하기, [IntelliCode](/visualstudio/intellicode/overview) 제안 선택하기, [Live Share](/visualstudio/liveshare/quickstart/share)를 통해 다른 개발자와 협업하기 등이 있습니다. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>연결 환경을 사용할 수 있는지 선택 ##

어느 연결 환경을 사용할지 선택할 수 있습니다. 특정 연결 환경을 사용하려면 Visual Studio EULA 이외의 추가적인 약관에 동의해야 합니다. 이러한 환경은 Microsoft 소유 온라인 서비스일 수도 있고 타사 소유 서비스일 수도 있습니다. 예를 들어, GitHub 연결 환경을 사용할 때는 [GitHub 개인정보처리방침](https://docs.github.com/github/site-policy/github-privacy-statement)과 [GitHub 서비스 약관](https://docs.github.com/github/site-policy/github-terms-of-service), [GitHub 회사 서비스 약관](https://docs.github.com/github/site-policy/github-corporate-terms-of-service) 또는 [추가 제품 약관](https://docs.github.com/github/site-policy/github-additional-product-terms)이 적용됩니다. [문제를 보고](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)할 때는 [Microsoft 사용 약관](https://www.microsoft.com/legal/terms-of-use) 및 [Microsoft 개인정보처리방침](https://privacy.microsoft.com/en-us/privacystatement)에 동의해야 합니다. NuGet 서비스를 사용할 때는 [NuGet 사용 약관](https://www.nuget.org/policies/Terms) 및 [Microsoft 개인정보처리방침](https://privacy.microsoft.com/en-us/privacystatement)에 동의해야 합니다. 

Visual Studio를 설치할 때 [선택적으로 설치할 워크로드 및 구성 요소를 선택할 수 있습니다](/visualstudio/install/install-visual-studio). 워크로드 및 구성 요소는 타사 소프트웨어를 사용할 수 있으며, 각각의 기능에 따라 연결 환경의 사용을 지원할 수 있습니다. 예를 들어, [Azure 개발 워크로드를 다운로드하면 클라우드 앱을 Azure에 게시할 수 있습니다](https://visualstudio.microsoft.com/vs/features/azure/). 설치 선택 사항에 따라 도구 및 옵션 메뉴를 사용하여 연결 환경에 연결하고 구성하고 이를 사용할 수 있습니다. 예를 들어, 서버에 연결하고, Azure 서비스 인증을 추가하고, IntelliCode 또는 LiveShare 설정을 변경할 수 있습니다.  

조직의 [방화벽 설정](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)을 사용하여 서비스에 대한 연결을 사용하거나 사용하지 않도록 설정할 수도 있습니다. 엔드포인트에 대한 연결을 사용하지 않도록 설정하면 관련 Visual Studio 기능의 성능에 부정적인 영향을 주거나 기능을 비활성화하게 될 수 있습니다. 

마지막으로, Visual Studio Marketplace에서는 Microsoft 또는 타사의 연결 환경을 지원하는 확장을 제공합니다. Visual Studio Marketplace에는 [Visual Studio Marketplace 사용 약관](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) 및 [Microsoft 개인정보처리방침](https://privacy.microsoft.com/en-us/privacystatement)이 적용됩니다. 각 확장을 사용할 때는 해당 제품과 관련된 특정 사용 약관 및 개인정보처리방침에 동의해야 합니다.  


## <a name="required-service-data"></a>필요한 서비스 데이터 ##

필요한 서비스 데이터에는 기본 서비스를 보호하고 최신 상태로 유지하고 예상대로 동작하도록 하는 데 필요한 연결된 환경의 운영과 관련된 정보가 포함될 수 있습니다. 콘텐츠를 분석하는 연결된 환경(예: IntelliCode)을 사용하도록 선택한 경우 모델을 위해 선택한 코드 또한 연결된 환경을 제공하기 위해 전송되고 처리됩니다. 필요한 서비스 데이터에는 연결된 환경이 작업(예: NuGet 패키지 업데이트)을 수행하는 데 필요한 정보도 포함될 수 있습니다. 특정 서비스를 사용할지를 선택하여 필요한 서비스 데이터를 관리할 수 있습니다. 서비스를 사용하지 않으면 필요한 서비스 데이터가 수집되지 않습니다. 

진단 데이터는 디바이스에서 실행되는 소프트웨어와 관련이 있으므로 필요한 서비스 데이터는 진단 데이터와 다릅니다. [진단 데이터에 대한 개인 정보 설정은 VSCEIP(Visual Studio 사용자 환경 개선 프로그램) 참여 여부에 따라 제어되지만](/visualstudio/ide/visual-studio-experience-improvement-program) 이 설정은 필요한 서비스 데이터가 전송되는지에는 영향을 주지 않습니다. 

## <a name="diagnostic-data-collection"></a>진단 데이터 수집 ##

진단 데이터는 Visual Studio를 최신 상태로 안전하게 유지하고 문제를 검색, 진단, 해결하고 제품을 개선하는 데 사용됩니다. 진단 데이터는 사용자 디바이스에서 실행되는 Visual Studio 클라이언트 소프트웨어에 대해 수집되어 Microsoft로 전송됩니다.

옵트아웃할 경우 선택적 진단 데이터 수집을 옵트아웃하는 것입니다. Visual Studio가 안전하고 최신 상태이고 예상 대로 작동하는지 확인하려면 일부 진단 데이터 수집이 필요합니다. [VSCEIP](/visualstudio/ide/visual-studio-experience-improvement-program) 옵트아웃을 선택하더라도 필요한 진단 데이터 수집 여부에는 영향을 주지 않습니다. 
