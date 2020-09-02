---
title: 다른 사용자가 배포할 ClickOnce 응용 프로그램 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3307fc124f50e8c9f73749293c36f53be36c5e3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71252455"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>다른 사용자가 배포할 수 있는 ClickOnce 애플리케이션 만들기
ClickOnce 배포를 만드는 일부 개발자는 응용 프로그램 자체를 배포할 계획입니다. 대부분의 응용 프로그램은 ClickOnce를 사용 하 여 응용 프로그램을 패키지 한 다음 대기업 등의 고객에 게 파일을 전달 하기만 하면 됩니다. 고객은 네트워크에서 응용 프로그램을 호스트 하는 역할을 담당 하 게 됩니다. 이 항목에서는 버전 3.5 이전의 .NET Framework 버전에서 이러한 배포에 내재 된 문제 중 일부에 대해 설명 합니다. 그런 다음 .NET Framework 3.5의 새로운 "신뢰에 매니페스트 사용" 기능을 사용 하 여 제공 된 새 솔루션을 설명 합니다. 마지막으로, 이전 버전의 .NET Framework를 아직 사용 하 고 있는 고객에 게 ClickOnce 배포를 만들기 위한 권장 전략을 마칩니다.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>고객을 위한 배포 생성 관련 문제
 고객에 게 배포를 제공 하려는 경우 몇 가지 문제가 발생 합니다. 첫 번째 문제는 코드 서명과 관련이 있습니다. 네트워크를 통해 배포 하기 위해 ClickOnce 배포의 배포 매니페스트와 응용 프로그램 매니페스트는 모두 디지털 인증서를 사용 하 여 서명 되어야 합니다. 이렇게 하면 매니페스트에 서명할 때 개발자 인증서를 사용할지 아니면 고객의 인증서를 사용할지에 대 한 질문이 발생 합니다.

 ClickOnce 응용 프로그램의 id는 배포 매니페스트의 디지털 서명을 기반으로 하므로 사용할 인증서에 대 한 질문은 중요 합니다. 개발자가 배포 매니페스트에 서명 하면 고객이 대기업이 고 회사의 여러 부서가 사용자 지정 된 버전의 응용 프로그램을 배포 하는 경우 충돌이 발생할 수 있습니다.

 예를 들어, 놀이 동산에는 재무 부서와 인적 자원 부서가 있습니다. 두 부서 모두 SQL 데이터베이스에 저장 된 데이터에서 보고서를 생성 하는 Microsoft Corporation의 ClickOnce 응용 프로그램을 라이선스 합니다. Microsoft는 각 부서에 해당 데이터에 맞게 사용자 지정 된 응용 프로그램 버전을 제공 합니다. 응용 프로그램이 동일한 Authenticode 인증서로 서명 된 경우 두 응용 프로그램을 사용 하려고 시도 하는 사용자는 두 번째 응용 프로그램을 첫 번째 응용 프로그램과 동일 하 게 간주 하므로 오류가 발생 합니다. 이 경우 고객은 응용 프로그램에 의해 로컬로 저장 된 데이터의 손실을 예측할 수 없으며 원치 않는 부작용이 발생할 수 있습니다.

 코드 서명과 관련 된 추가 문제는 `deploymentProvider` 응용 프로그램 업데이트를 검색할 위치를 ClickOnce에 알려 주는 배포 매니페스트의 요소입니다. 이 요소는 서명 하기 전에 배포 매니페스트에 추가 해야 합니다. 이 요소를 나중에 추가 하는 경우 배포 매니페스트를 다시 서명 해야 합니다.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>고객이 배포 매니페스트에 서명 하도록 요구
 고유 하지 않은 배포 문제에 대 한 한 가지 해결책은 개발자가 응용 프로그램 매니페스트에 서명 하 고 고객은 배포 매니페스트에 서명 하는 것입니다. 이 접근 방식은 작동 하지만 다른 문제를 야기 합니다. Authenticode 인증서가 보호 된 자산을 유지 해야 하므로 고객은 인증서를 개발자에 게 제공 하 여 배포에 서명할 수 없습니다. 고객이 .NET Framework SDK에서 무료로 제공 되는 도구를 사용 하 여 배포 매니페스트 자체에 서명할 수 있지만, 고객이 제공 하거나 제공할 수 있는 것 보다 더 많은 기술 정보가 필요할 수 있습니다. 이러한 경우 개발자는 일반적으로 응용 프로그램, 웹 사이트 또는 응용 프로그램의 버전을 서명 하기 위해 제출할 수 있는 기타 메커니즘을 만듭니다.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>ClickOnce 응용 프로그램 보안에 대 한 고객 로그인의 영향
 개발자와 고객이 응용 프로그램 매니페스트에 서명 해야 한다는 것에 동의 하더라도 특히 신뢰할 수 있는 응용 프로그램 배포에 적용 되는 응용 프로그램의 id를 포함 하는 다른 문제가 발생 합니다. 이 기능에 대 한 자세한 내용은 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)를 참조 하세요. Microsoft Corporation에서 제공 하는 모든 응용 프로그램이 완전 신뢰로 실행 되도록 놀이 Works에서 클라이언트 컴퓨터를 구성 하려는 경우를 가정해 보겠습니다. 놀이 Works가 배포 매니페스트에 서명 하는 경우 ClickOnce는 놀이 Work의 보안 서명을 사용 하 여 응용 프로그램의 신뢰 수준을 결정 합니다.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>신뢰에 응용 프로그램 매니페스트를 사용 하 여 고객 배포 만들기
 .NET Framework 3.5의 ClickOnce에는 개발자와 고객이 매니페스트에 서명 하는 방법에 대 한 새로운 솔루션을 제공 하는 새로운 기능이 포함 되어 있습니다. ClickOnce 응용 프로그램 매니페스트는 `<useManifestForTrust>` 개발자가 응용 프로그램 매니페스트의 디지털 서명이 신뢰 결정을 내리는 데 사용 되어야 함을 나타낼 수 있는 라는 새 요소를 지원 합니다. 개발자는 *Mage.exe*, *MageUI.exe*, Visual Studio 등의 ClickOnce 패키징 도구를 사용 하 여 응용 프로그램 매니페스트에이 요소를 포함 하 고 해당 게시자 이름과 응용 프로그램의 이름을 매니페스트에 포함 합니다.

 를 사용 하는 경우 `<useManifestForTrust>` 인증 기관에서 발급 한 Authenticode 인증서를 사용 하 여 배포 매니페스트를 서명할 필요가 없습니다. 대신 자체 서명 된 인증서로 알려진 항목을 사용 하 여 서명할 수 있습니다. 자체 서명 된 인증서는 표준 .NET Framework SDK 도구를 사용 하 여 고객 또는 개발자가 생성 한 다음 표준 ClickOnce 배포 도구를 사용 하 여 배포 매니페스트에 적용 됩니다. 자세한 내용은 [makecert.exe](/windows/desktop/SecCrypto/makecert)를 참조 하세요.

 배포 매니페스트에 자체 서명 된 인증서를 사용 하면 여러 가지 이점이 있습니다. 고객이 자신의 Authenticode 인증서를 얻거나 만들 필요가 없도록 하 여 `<useManifestForTrust>` 고객에 대 한 배포를 간소화 하는 동시에 개발자가 응용 프로그램에서 자신의 브랜딩 id를 유지 관리할 수 있도록 합니다. 그 결과, 더 안전 하 고 고유한 응용 프로그램 id를 갖는 서명 된 배포 집합이 있습니다. 이렇게 하면 동일한 응용 프로그램을 여러 고객에 게 배포할 때 발생할 수 있는 잠재적인 충돌을 방지할 수 있습니다.

 을 사용 하 여 ClickOnce 배포를 만드는 방법에 대 한 단계별 정보는 `<useManifestForTrust>` [연습: 다시 서명할 필요가 없고 브랜딩 정보를 유지 하는 clickonce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)를 참조 하세요.

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>런타임에 신뢰의 응용 프로그램 매니페스트 작동 방법
 런타임에 신뢰에 응용 프로그램 매니페스트를 사용 하는 방법을 더 잘 이해 하려면 다음 예제를 참조 하세요. .NET Framework 3.5를 대상으로 하는 ClickOnce 응용 프로그램은 Microsoft에서 만듭니다. 응용 프로그램 매니페스트는 요소를 사용 하 `<useManifestForTrust>` 고 Microsoft에서 서명 합니다. 놀이 Works는 자체 서명 된 인증서를 사용 하 여 배포 매니페스트에 서명 합니다. 놀이 Works 클라이언트는 Microsoft에서 서명 된 모든 응용 프로그램을 신뢰 하도록 구성 됩니다.

 사용자가 배포 매니페스트에 대 한 링크를 클릭 하면 ClickOnce가 사용자의 컴퓨터에 응용 프로그램을 설치 합니다. 인증서 및 배포 정보는 클라이언트 컴퓨터에서 ClickOnce에 대해 고유 하 게 응용 프로그램을 식별 합니다. 사용자가 다른 위치에서 동일한 응용 프로그램을 다시 설치 하려고 하면 ClickOnce에서이 id를 사용 하 여 응용 프로그램이 클라이언트에 이미 있는지 확인할 수 있습니다.

 그런 다음 ClickOnce는 응용 프로그램 매니페스트에 서명 하는 데 사용 되는 Authenticode 인증서를 검사 하 여 ClickOnce에서 부여할 신뢰 수준을 결정 합니다. 놀이 Works는 Microsoft에서 서명한 응용 프로그램을 신뢰 하도록 클라이언트를 구성 했으므로이 ClickOnce 응용 프로그램에는 완전 신뢰가 부여 됩니다. 자세한 내용은 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)를 참조 하세요.

## <a name="create-customer-deployments-for-earlier-versions"></a>이전 버전에 대 한 고객 배포 만들기
 개발자가 이전 버전의 .NET Framework를 사용 하는 고객에 게 ClickOnce 응용 프로그램을 배포 하는 경우 어떻게 되나요? 다음 섹션에서는 몇 가지 권장 솔루션과 각 권장 사항에 대 한 장점과 단점을 요약 합니다.

### <a name="sign-deployments-on-behalf-of-customer"></a>고객을 대신 하 여 배포 서명
 개발자는 고객의 개인 키를 사용 하 여 고객을 대신 하 여 배포에 서명 하는 메커니즘을 만드는 방법을 사용할 수 있습니다. 이렇게 하면 개발자가 개인 키 또는 여러 배포 패키지를 관리할 필요가 없습니다. 개발자는 각 고객에 게 동일한 배포를 제공 합니다. 고객은 서명 서비스를 사용 하 여 환경에 맞게 사용자 지정 해야 합니다.

 이 방법의 한 가지 단점은 구현 하는 데 필요한 시간과 비용입니다. 이러한 서비스는 .NET Framework SDK에서 제공 하는 도구를 사용 하 여 작성할 수 있지만 제품 수명 주기에 더 많은 개발 시간을 추가 합니다.

 이 항목의 앞부분에서 설명한 것 처럼, 각 고객의 응용 프로그램 버전은 동일한 응용 프로그램 id를 갖게 되므로 충돌이 발생할 수 있습니다. 이 문제가 발생 하는 경우 개발자는 배포 매니페스트를 생성할 때 사용 되는 이름 필드를 변경 하 여 각 응용 프로그램에 고유한 이름을 지정할 수 있습니다. 그러면 응용 프로그램의 각 버전에 대해 별도의 id가 생성 되 고 잠재적 id 충돌은 제거 됩니다. 이 필드는 `-Name` Mage.exe의 인수 및 MageUI.exe의 **이름** 탭에 있는 **이름** 필드에 해당 합니다.

 예를 들어 개발자가 응용 프로그램 1 이라는 응용 프로그램을 만들었다고 가정 합니다. 응용 프로그램 1로 설정 된 이름 필드를 사용 하 여 단일 배포를 만드는 대신 개발자는 응용 프로그램 1-CustomerA, 응용 프로그램 1 등의이 이름에 대 한 고객과 관련 된 변형을 사용 하 여 여러 배포를 만들 수 있습니다.

### <a name="deploy-using-a-setup-package"></a>설치 패키지를 사용 하 여 배포
 두 번째 가능한 배포 전략은 ClickOnce 응용 프로그램의 초기 배포를 수행 하기 위해 Microsoft 설치 프로젝트를 생성 하는 것입니다. 이는 MSI 배포와 같이 설치 실행 파일 ()의 여러 가지 형식 중 하나로 제공 될 수 있습니다. EXE)를 사용 하거나 캐비닛 파일 (.cab)을 일괄 처리 스크립트와 함께 사용 합니다.

 개발자는이 기술을 사용 하 여 응용 프로그램 파일, 응용 프로그램 매니페스트 및 템플릿 역할을 하는 배포 매니페스트를 포함 하는 배포를 고객에 게 제공 합니다. 고객은 설치 프로그램을 실행 합니다 .이 프로그램은 배포 URL (사용자가 ClickOnce 응용 프로그램을 설치 하는 서버 또는 파일 공유 위치)과 디지털 인증서를 묻는 메시지를 표시 합니다. 설치 응용 프로그램은 업데이트 확인 간격과 같은 추가 ClickOnce 구성 옵션을 확인 하도록 선택할 수도 있습니다. 이 정보가 수집 되 면 설치 프로그램에서 실제 배포 매니페스트를 생성 하 고, 서명 하 고, ClickOnce 응용 프로그램을 지정 된 서버 위치에 게시 합니다.

 이러한 상황에서 고객은 배포 매니페스트에 서명 하는 세 가지 방법이 있습니다.

1. 고객은 CA (인증 기관)에서 발급 한 유효한 인증서를 사용할 수 있습니다.

2. 이 접근 방식에 따라 고객은 자체 서명 된 인증서를 사용 하 여 배포 매니페스트에 서명 하도록 선택할 수 있습니다. 이에 대 한 단점은 응용 프로그램이 사용자에 게 설치 여부를 묻는 메시지가 표시 될 때 "알 수 없는 게시자" 라는 단어를 표시 하는 것입니다. 그러나 소규모 고객이 인증 기관에서 발급 한 인증서에 필요한 시간과 비용을 소비 하지 않도록 하는 것이 장점입니다.

3. 마지막으로 개발자는 자체 서명 된 인증서를 설치 패키지에 포함할 수 있습니다. 이 항목의 앞부분에서 설명한 응용 프로그램 id의 잠재적인 문제를 소개 합니다.

   설치 배포 프로젝트 방법의 단점은 사용자 지정 배포 응용 프로그램을 빌드하는 데 필요한 시간과 비용입니다.

### <a name="have-customer-generate-deployment-manifest"></a>고객이 배포 매니페스트 생성
 세 번째 가능한 배포 전략은 응용 프로그램 파일 및 응용 프로그램 매니페스트를 고객에 게 전달 하는 것입니다. 이 시나리오에서 고객은 .NET Framework SDK를 사용 하 여 배포 매니페스트를 생성 하 고 서명 해야 합니다.

 이 방법의 단점은 고객이 .NET Framework SDK 도구를 설치 하 고 해당 도구를 사용 하는 데 숙련 된 개발자 또는 시스템 관리자가 있어야 한다는 것입니다. 일부 고객은 해당 파트에 대 한 기술적인 노력이 거의 필요 하지 않은 솔루션을 요구할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [다시 서명 하지 않고 테스트 및 프로덕션 서버용 ClickOnce 응용 프로그램 배포](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [연습: 다시 서명할 필요가 없고 브랜드 정보가 유지되는 ClickOnce 애플리케이션 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)