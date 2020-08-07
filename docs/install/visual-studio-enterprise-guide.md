---
title: Visual Studio 엔터프라이즈 가이드
description: 엔터프라이즈 환경에서 Visual Studio를 설정하고 문제를 해결합니다.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3d223d6e1e6ed3bf4b75b1c66bcc0f9dc897cfed
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87434320"
---
# <a name="visual-studio-enterprise-guide"></a>Visual Studio 엔터프라이즈 가이드
Visual Studio에서 회사를 운영하는 동안 시간을 절약하려면 이 가이드를 참조하세요. 본 엔터프라이즈 가이드는 일반적인 엔터프라이즈 시나리오에서 Visual Studio를 설치 또는 업데이트하고, 문제 발생 시 차단을 해제하고, 추가 도움이 필요한 경우 문제를 보고하는 방법을 알아보는 데 도움이 되는 팁을 제공합니다. 

## <a name="get-started"></a>시작 
네트워크 및 오프라인 환경에서 엔터프라이즈에 Visual Studio를 배포하는 방법을 알아봅니다. 

- **네트워크 환경에서의 엔터프라이즈 배포 옵션에 대해 알아봅니다**. [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)는 시스템 관리자를 위한 시나리오 기반 지침을 제공합니다. 

- **[문제 해결 팁 확인](troubleshooting-installation-issues.md)** . Visual Studio 설치 또는 업데이트 방법에 대한 도움말을 확인하고, 차단된 경우 문제를 보고하는 방법을 알아봅니다. 이러한 팁에는 대부분의 온라인 또는 오프라인 설치 문제를 해결할 수 있는 단계별 지침이 포함되어 있습니다. 

- **[Visual Studio의 오프라인 설치 파일 만들기](create-an-offline-installation-of-visual-studio.md)** . 인터넷에 연결되어 있지 않거나 인터넷 연결이 제한적인 경우 Visual Studio를 설치하기 위한 옵션을 확인합니다. 

- **[부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)** . 제품 및 패키지 매니페스트를 만들어 사용자 지정 부트스트래퍼 패키지를 만드는 방법을 알아봅니다. 

- **[Visual Studio를 배포할 때 제품 키를 자동으로 적용](automatically-apply-product-keys-when-deploying-visual-studio.md)** . Visual Studio의 배포를 자동화하는 데 사용되는 스크립트의 일부로 제품 키를 프로그래밍 방식으로 적용할 수 있습니다. Visual Studio를 설치하는 동안 또는 설치가 완료된 후에 디바이스에서 프로그래밍 방식으로 제품 키를 설정할 수 있습니다. 

## <a name="install-visual-studio"></a>Visual Studio 설치 

일반적인 엔터프라이즈 시나리오에서 Visual Studio를 설치하는 방법을 알아봅니다. 

- **[명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)** . 다양한 매개 변수를 사용하여 Visual Studio 설치를 제어하거나 사용자 지정합니다. 설치 프로세스를 자동화하거나 나중에 사용할 설치 파일의 캐시를 만듭니다. 

- **[Visual Studio 설치를 위한 명령줄 매개 변수 예제](command-line-parameter-examples.md)를 참조하세요**. 명령줄 매개 변수를 사용하여 Visual Studio를 설치하는 방법을 보여 주는 몇 가지 예제를 확인하고 필요에 맞게 사용자 지정할 수 있습니다. 

- **[방화벽 또는 프록시 서버 배후에서 Visual Studio와 Azure 서비스 설치 및 사용](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)** . 조직에서 방화벽 또는 프록시 서버와 같은 보안 조치를 사용하는 경우, Visual Studio와 Azure 서비스를 설치 및 사용할 때 최상의 경험을 얻으려면 특정 포트 및 프로토콜을 열고 특정 도메인 URL을 "허용 목록"에 추가하는 것이 좋습니다. 

- **[Visual Studio의 네트워크 설치 파일 만들기](create-a-network-installation-of-visual-studio.md)** . 초기 설치 파일과 모든 제품 업데이트를 단일 폴더에 캐시합니다.  

## <a name="update-visual-studio"></a>Visual Studio 업데이트 

Visual Studio를 성공적으로 업데이트하고 업데이트 문제를 해결하는 방법을 알아봅니다. 

- **[Visual Studio 2017의 네트워크 기반 설치 업데이트](update-a-network-installation-of-visual-studio.md)** . 최신 제품 업데이트를 사용하여 Visual Studio의 네트워크 설치 레이아웃을 업데이트합니다. 이후 해당 레이아웃을 Visual Studio의 최신 업데이트에 대한 설치 지점으로 사용하거나 이미 클라이언트 워크스테이션에 배포된 설치를 유지 관리하는 데 사용할 수 있습니다.

- **[서비스 기준선에서 Visual Studio 업데이트](update-servicing-baseline.md)** . 기준선 업데이트의 가치를 이해하고, 부 버전과 서비스 업데이트 간의 차이점을 알아봅니다. 

- **[최소 오프라인 레이아웃을 사용하여 Visual Studio 업데이트](update-minimal-layout.md)** . 인터넷에 연결되지 않은 컴퓨터의 경우 최소 레이아웃을 만드는 것이 오프라인 Visual Studio 인스턴스를 업데이트하는 가장 쉽고 빠른 방법입니다.

- **[Visual Studio를 복구](repair-visual-studio.md)하여 업데이트 문제 해결**. 경우에 따라 Visual Studio 설치가 손상되거나 훼손됩니다. 복구는 업데이트를 포함하여 모든 설치 작업에서 설치 시간 문제를 해결하는 데 유용합니다. 

- **[Windows 보안 기준](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) 준수**. Microsoft는 고객에게 Windows 10 및 Windows Server와 같은 안전한 운영 체제와 Microsoft Edge와 같은 안전한 앱을 제공하기 위해 노력하고 있습니다. 해당 제품의 보안 보증 외에도, 환경을 세밀하게 관리할 수 있도록 다양한 구성 기능도 제공합니다. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조 

- [Visual Studio 생산성 가이드](../ide/productivity-features.md)



