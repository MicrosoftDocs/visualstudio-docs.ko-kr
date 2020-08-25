---
title: MPSA(Microsoft 제품 및 서비스 계약)에서 Visual Studio 구독 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/03/2020
ms.topic: conceptual
description: MPSA(Microsoft 제품 및 서비스 계약)에서 Visual Studio 구독
ms.openlocfilehash: 6ce2208e6d1028e1e697b216d41cdd825dfc0d33
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247319"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>MPSA(Microsoft 제품 및 서비스 계약)에서 Visual Studio 구독
MPSA 프로그램을 통해 Visual Studio 구독을 구매한 경우 Visual Studio 구독 관리자가 되어 구독을 다른 사용자에게 할당하기 전에 기억해야 할 몇 가지가 있습니다. 이미 관리자로 설정되어 있으면 Visual Studio 구독 [관리 포털](https://manage.visualstudio.com/)로 직접 이동할 수 있습니다.

이제 MPSA 고객은 VLSC(볼륨 라이선스 서비스 센터)와 유사한 기능을 지원하는 [비즈니스 센터](https://businessaccount.microsoft.com/Customer)라는 새 포털에서 MPSA를 통해 구매한 자산을 관리합니다. 이러한 기능에는 라이선스 요약, 주문, 다운로드, 키, 사용자 등의 보기가 포함됩니다. 그러나 MPSA에서 Visual Studio 구독은 마치 클라우드 서비스처럼 동작합니다. 또한 비즈니스 센터는 MSA(Microsoft 계정) 대신 회사 계정을 사용하여 로그인합니다. 조직이 Office 365 또는 Azure Active Directory같은 클라우드 서비스를 사용하고 사용자 전자 메일이 이러한 두 서비스 중 하나에 속한 경우 이는 이미 회사 계정입니다. 이 계정을 사용하면 기존 암호를 사용하여 비즈니스 센터에 등록할 수 있습니다. 조직에서 클라우드 서비스를 사용하지 않고 전자 메일도 회사 계정이 아닌 경우라도 기존 암호를 사용해 비즈니스 센터에 등록할 수 있습니다.

또한 Visual Studio 구독 [관리 포털](https://manage.visualstudio.com/)에서는 일단 Visual Studio 구독 관리자가 되면 구독을 구독자에게 할당할 수 있습니다. MPSA에서 Visual Studio 구독자는 Visual Studio 구독 관리 포털인 해당 관리 포털에 프로비저닝해야 합니다. 이렇게 하려면 테넌트(예: contoso.onmicrosoft.com)에 구매 계정을 연결해야 합니다.

테넌트에는 두 가지 유형(관리형 테넌트 및 비관리형 테넌트)이 있습니다. 관리형 테넌트는 조직에서 관리자가 이미 관리하고 있는 테넌트를 가리킵니다.

비관리형 테넌트는 관리자가 할당되지 않은 테넌트로서 Office 365 같은 온라인 서비스에는 사용할 수 없습니다. 또한 비관리형 테넌트는 회사 계정이 아닌 전자 메일을 사용하여 비즈니스 센터에 등록할 때 만들어집니다. 비즈니스 센터에 등록할 때 암호를 만들도록 요청받는 경우 이는 전자 메일이 회사 계정이 아니며 비관리형 테넌트를 만들었다는 의미입니다.

테넌트 연결을 완료하기 전에 Visual Studio 구독 관리자가 되는 데 필요한 몇 가지 요구 사항/단계가 있습니다.

## <a name="pre-tenant-association-managed-tenant"></a>사전 테넌트 연결(관리되는 테넌트)
- 비즈니스 센터에 등록된 사용자여야 합니다.
- 사용자는 자신이 속한 테넌트 내에서 사용자 관리자(최소한) 또는 전역 관리자여야 합니다. (회사가 이미 클라우드 서비스를 사용하는 경우 해당됩니다). Visual Studio 구독 관리자가 되려면 두 역할 중 하나가 필요합니다.
- 사용자는 자신의 테넌트에 구매 계정을 연결할 수 있으려면 자신이 속한 테넌트의 전역 관리자여야 합니다.
- 비즈니스 센터에서 사용자는 계정 관리자여야 합니다.
- [Azure](https://portal.azure.com/)의 사용자 프로필(및 다른 모든 사용자)에서 "국가 또는 지역" 필드는 해당 지역(예: 미국, 캐나다 등)에 따라 적절하게 채워야 합니다. 

> [!NOTE]
> Visual Studio 구독 관리자로 만들려는 사용자 모두는 조건 2와 5를 충족하는 데 필요하므로 비즈니스 센터의 사용자가 될 것을 요구받지 않습니다.

위의 조건을 모두 충족하면 아래 단계에 따라 사용자는 자신의 테넌트에 구매 계정을 연결할 수 있습니다.
1. [비즈니스 센터](https://businessaccount.microsoft.com/Customer)에 로그인합니다.
2. **계정** 탭을 선택하고 **도메인 연결**을 선택합니다.
3. **구매 계정**(1 초과 구매 계정이 있는 경우)을 선택합니다.
4. **테넌트**(예: contoso.onmicrosoft.com)를 선택합니다.
5. **도메인 연결**을 선택합니다.

연결 시 필요한 조건을 충족한 모든 사용자는 일반적으로 몇 분 이내에 Visual Studio 구독 관리자로서 프로비저닝됩니다. 그러나 때로는 최대 24시간이 걸릴 수도 있습니다. 테넌트가 프로비저닝되면 Visual Studio 구독 관리 포털에 액세스할 수 있게 됩니다. 24시간 보다 오래 걸릴 경우 다음 단계에 따라 MPSA 고객 지원 팀에 문의하세요.
1. <https://www.microsoft.com/licensing/mpsa/default> 에 연결합니다.
2. 페이지 맨 위에 있는 **자세히** 메뉴를 선택합니다. 
3. **지원**을 선택합니다.
4. **라이선스 지원**을 선택합니다.
5. 요구 사항에 가장 잘 맞는 지원 옵션을 선택합니다. 

> [!NOTE]
> (연결 후에) 2단계 및 5단계 조건을 충족하는 새 사용자가 있는 경우 MPSA 고객 지원팀에 문의해야 합니다. MPSA 고객 지원 팀은 새 Visual Studio 구독 관리자를 프로비전하기 위한 지원을 제공합니다.

## <a name="tenant-association-unmanaged"></a>테넌트 연결(관리되지 않는)
위에서 설명한 것처럼 회사 계정이 아닌(“Azure AD”(Azure Active Directory)에 등록되지 않은) 전자 메일을 사용하여 비즈니스 센터에 등록한 경우 테넌트 연결이 약간 달라집니다. 이른 바 “도메인 인수”를 수행해야 합니다. 이 프로세스 동안 사용자 스스로 전역 관리자가 되어 관리되지 않는 테넌트에서 관리되는 테넌트로 변경해야 합니다.

이 프로세스에 대한 자세한 내용은 [빠른 시작 안내](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx)를 참조합니다. 도메인 인수 과정을 안내해 줄 *"온라인 서비스 설치 및 사용"* 이라는 가이드를 다운로드합니다. 이 작업이 완료되면 사용자의 구매 계정이 테넌트에 연결됩니다.

> [!NOTE]
> 도메인 인수 과정을 완료한 후 사용자는 사전 테넌트 연결(관리되는)에 대한 섹션에서 다섯 단계의 모든 조건을 준수해야 합니다. 이러한 조건이 충족되면 추가 Visual Studio 구독 관리자를 프로비전하기 위해 MPSA 고객 지원 팀에 문의해야 합니다.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
Visual Studio 구독 관리에 대해 자세히 알아보세요.
- [개별 구독 할당](assign-license.md)
- [여러 구독 할당](assign-license-bulk.md)
- [구독 편집](edit-license.md)
- [구독 삭제](delete-license.md)
- [최대 사용량 확인](maximum-usage.md)
