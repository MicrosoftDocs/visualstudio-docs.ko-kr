---
title: 다단계 인증이 필요한 계정 작업
ms.date: 05/27/2020
ms.topic: conceptual
description: 다단계 인증이 필요한 계정으로 Visual Studio를 사용하는 방법을 알아봅니다.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 699580689bcf00d00d2a6e07f814be4d1265bb1d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283548"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>다단계 인증이 필요한 계정으로 Visual Studio를 사용하는 방법

외부 게스트 사용자와 협업하는 경우 **MFA(다단계 인증)** 와 같은 **CA(조건부 액세스)** 정책으로 앱과 데이터를 보호하는 것이 좋습니다.  

이 정책을 사용하도록 설정하면 게스트 사용자는 사용자 이름과 암호만으로는 리소스에 액세스할 수 없고 추가 보안 요구 사항을 충족해야 합니다. 조직의 멤버에게 MFA 정책을 사용하는 것과 같은 방법으로 MFA 정책을 테넌트, 앱 또는 개별 게스트 사용자 수준에서 적용할 수 있습니다. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>MFA 정책으로 Visual Studio 환경이 어떤 영향을 받나요?
16.6 이전의 Visual Studio 버전은 MFA와 같은 CA 정책을 사용하도록 설정하고 둘 이상의 테넌트와 연결된 계정과 함께 사용할 경우 인증 환경이 저하될 수 있습니다.

이러한 문제로 인해 Visual Studio 인스턴스에서 하루에 여러 번 재인증을 요청할 수 있습니다. 동일한 Visual Studio 세션 동안에도 이전에 인증된 테넌트에서 자격 증명을 다시 입력해야 할 수 있습니다.

## <a name="using-visual-studio-with-mfa-policies"></a>MFA 정책과 함께 Visual Studio 사용
16.6 릴리스에서는 사용자가 MFA와 같은 CA 정책을 통해 보호되는 리소스에 액세스할 수 있는 방법을 간소화하는 새로운 기능이 Visual Studio 2019에 추가되었습니다. 이 향상된 워크플로를 사용하려면 Visual Studio 계정을 추가하고 다시 인증하는 메커니즘으로 시스템의 기본 웹 브라우저 사용을 옵트인해야 합니다.  

> [!WARNING]
> 이 워크플로를 사용하지 않으면 저하된 환경이 트리거되어 Visual Studio 계정을 추가하거나 다시 인증할 때 여러 추가 인증 프롬프트가 표시될 수 있습니다. 

### <a name="enabling-system-web-browser"></a>시스템 웹 브라우저 사용

> [!NOTE] 
> 최상의 환경을 위해 이 워크플로를 진행하기 전에 시스템의 기본 웹 브라우저 데이터를 지우는 것이 좋습니다. 또한 Windows 10 설정의 **회사 또는 학교 액세스**에 회사 또는 학교 계정이 있는 경우 제대로 인증되었는지 확인하세요.

이 워크플로를 사용하도록 설정하려면 Visual Studio의 옵션 대화 상자 **(도구 > 옵션...)** 로 이동한 후 **계정** 탭을 선택하고 **다음을 사용하여 계정 추가 및 다시 인증:** 드롭다운에서 **시스템 웹 브라우저**를 선택합니다. 

:::image type="content" source="media/select-system-web-browser.png" alt-text="메뉴에서 시스템 웹 브라우저를 선택합니다.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>MFA 정책을 사용하는 추가 계정에 로그인 
시스템 웹 브라우저 워크플로를 사용하도록 설정했으면 평소대로 계정 설정 대화 상자 **(파일 > 계정 설정...)** 를 통해 Visual Studio에 로그인하거나 계정을 추가할 수 있습니다.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Visual Studio에 새 개인 설정 계정을 추가합니다." border="false":::

이 작업을 수행하면 시스템의 기본 웹 브라우저가 열리고, 계정에 로그인하고 필요한 MFA 정책의 유효성을 검사하라는 메시지가 표시됩니다.

개발 활동 및 리소스 구성에 따라 세션 중에 자격 증명을 다시 입력하라는 메시지가 표시될 수 있습니다. 이 문제는 새 리소스를 추가하거나 이전에 CA/MFA 권한 부여 요구 사항을 충족하지 않고 리소스에 액세스를 시도하는 경우에 발생할 수 있습니다.

> [!NOTE] 
> 최상의 환경을 위해 리소스에 대해 모든 CA/MFA 정책의 유효성을 검사할 때까지 브라우저를 열어 두세요. 브라우저를 닫으면 이전에 빌드된 MFA 상태가 손실될 수 있으며 추가 권한 부여 프롬프트가 표시될 수 있습니다.

## <a name="reauthenticating-an-account"></a>계정 다시 인증  
계정에 문제가 있는 경우 Visual Studio에서 계정 자격 증명을 다시 입력하라는 메시지가 표시될 수 있습니다.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Visual Studio 계정을 다시 인증합니다.":::

**자격 증명 다시 입력**을 클릭하면 시스템의 기본 웹 브라우저가 열리고 자격 증명을 자동으로 새로 고치려고 합니다. 실패하면 계정에 로그인하고 필요한 CA/MFA 정책의 유효성을 검사하라는 메시지가 표시됩니다.

> [!NOTE] 
> 최상의 환경을 위해 리소스에 대해 모든 CA/MFA 정책의 유효성을 검사할 때까지 브라우저를 열어 두세요. 브라우저를 닫으면 이전에 빌드된 MFA 상태가 손실될 수 있으며 추가 권한 부여 프롬프트가 표시될 수 있습니다.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Visual Studio에서 특정 Azure Active Directory 테넌트 사용을 옵트아웃하는 방법

Visual Studio 2019 버전 16.6에서는 유연하게 특정 테넌트를 필터링하여 Visual Studio에서 숨길 수 있습니다. 필터링하면 해당 테넌트로 인증할 필요가 없어질 뿐 아니라 관련 리소스에 액세스할 수도 없게 됩니다. 

테넌트가 여럿이지만 특정 하위 집합을 대상으로 지정하여 개발 환경을 최적화하려는 경우 이 기능이 유용합니다. 또한 특정 CA/MFA 정책의 유효성을 검사할 수 없는 경우에도 잘못된 테넌트를 필터링할 수 있으므로 도움이 될 수 있습니다. 

### <a name="how-to-filter-out-a-tenant"></a>테넌트를 필터링하는 방법
Visual Studio 계정과 연결된 테넌트를 필터링하려면 계정 설정 대화 상자 **(파일 > 계정 설정...)** 를 열고 **필터 적용**을 클릭합니다. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="필터를 적용합니다." border="false":::

**계정 필터링** 대화 상자가 표시되며 계정과 함께 사용할 테넌트를 선택할 수 있습니다. 

:::image type="content" source="media/select-filter-account.png" alt-text="필터링할 계정을 선택합니다.":::

## <a name="see-also"></a>참조

- [Visual Studio에 로그인](signing-in-to-visual-studio.md)
- [Mac용 Visual Studio에 로그인](/visualstudio/mac/signing-in)
- [여러 사용자 계정으로 작업](work-with-multiple-user-accounts.md)
