---
title: GitHub 계정으로 Visual Studio 구독 로그인 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/09/2020
ms.topic: conceptual
description: GitHub 계정으로 Visual Studio 구독에 로그인하는 방법을 알아봅니다.
ms.openlocfilehash: 722eeae315a8b4a6bd93fb1048846b147b294afa
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233225"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>GitHub 계정으로 Visual Studio 구독 로그인 

Visual Studio 구독에 로그인하는 단계는 사용 중인 계정의 종류에 따라 다릅니다. 예를 들어 회사 또는 학교에서 제공한 Microsoft 계정(MSA) 또는 전자 메일 주소를 사용할 수 있습니다. 2019년 1월 현재 GitHub 계정을 사용하여 일부 구독에 로그인할 수도 있습니다. 

이 문서에서는 GitHub 계정으로 로그인하는 단계를 소개합니다.

## <a name="signing-in-with-your-github-account"></a>GitHub 계정으로 로그인

GitHub ID 지원을 통해 기존 GitHub 계정을 신규 또는 기존 Microsoft 계정에 대한 자격 증명으로 사용하여 GitHub 계정을 Microsoft 계정과 연결할 수 있습니다. 

GitHub로 로그인하는 경우 Microsoft는 GitHub 계정과 연결된 이메일 주소가 기존 개인 또는 엔터프라이즈 Microsoft 계정과 일치하는지 확인합니다. 주소가 엔터프라이즈 계정과 일치하면 해당 계정으로 대신 로그인하라는 메시지가 나타납니다. 주소가 개인 계정과 일치하는 경우 GitHub 계정을 해당 개인 계정에 로그인하는 방법으로 추가해 드립니다.

GitHub 및 Microsoft 계정 자격 증명이 연결된 후에는 개인 Microsoft 계정을 사용할 수 있는 모든 경우(예: Azure 사이트, Office 앱 및 Xbox)에 해당 단일 로그인을 사용할 수 있습니다. 또한 이메일 주소가 초대장의 주소와 일치한다고 가정하면 Azure Active Directory 게스트 로그인 시 해당 계정을 Microsoft 계정으로 사용할 수도 있습니다.

> [!NOTE]
> GitHub ID를 Microsoft 계정에 연결하더라도 Microsoft에 코드 액세스 권한이 부여되지 않습니다. Azure DevOps 및 Visual Studio와 같은 앱이 코드 리포지토리에 액세스해야 하는 경우 이 액세스에 대해 구체적 동의를 부여해 달라는 메시지가 표시됩니다. 

### <a name="frequently-asked-questions"></a>질문과 대답
다음 FAQ는 GitHub 계정 자격 증명을 사용하여 Visual Studio 구독에 로그인하는 과정에서 마주칠 수 있는 질문에 답합니다.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>Q: GitHub 암호를 잊어버렸습니다.  어떻게 해야 내 계정에 액세스할 수 있나요?
A:  [암호 재설정](https://github.com/password_reset)으로 이동하여 GitHub 계정을 복구할 수 있습니다. 또는 [계정 복구](https://account.live.com/password/reset)에서 GitHub 계정 이메일 주소를 입력하여 GitHub에 연결된 Microsoft 계정을 복구할 수 있습니다.

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>Q: 내 GitHub 계정을 삭제했습니다.  이제 어떻게 해야 Microsoft 계정(MSA)에 액세스할 수 있나요?
A: MSA의 다른 자격 증명(암호, Authenticator 앱 또는 보안 키)이 없는 경우 연결된 이메일 주소를 사용하여 Microsoft 계정을 복구할 수 있습니다. 시작하려면 [계정 복구](https://account.live.com/password/reset)로 이동합니다. 나중에 저희가 사용자를 로그인하도록 조치하는 방법을 알 수 있도록 사용자의 계정에 암호를 추가해야 합니다. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>Q: 로그인 페이지에 "GitHub로 로그인" 옵션이 없습니다.  어떻게 하면 내 GitHub 자격 증명을 사용하여 로그인할 수 있나요?
A:  GitHub에 연결된 Microsoft 계정을 만들 때 선택한 GitHub 계정 이메일 주소를 입력하세요. 그러면 저희가 사용자의 정보를 조회하여 로그인할 GitHub로 안내해 드립니다. 또는 로그인 페이지에 로그인 옵션 링크가 있는 경우 해당 링크를 클릭한 후 표시되는 **GitHub로 로그인** 단추를 사용하세요. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>Q: GitHub로 일부 앱과 제품에 로그인할 수 없습니다.  이유
A:  모든 Microsoft 제품의 로그인 페이지에서 GitHub.com에 액세스할 수 있는 것은 아닙니다(예: Xbox 콘솔). 그 대신 사용자가 연결된 GitHub 계정에서 이메일 주소를 입력할 때 저희가 본인 여부를 확인할 수 있는 코드를 해당 주소로 보내드립니다. 동일한 계정에 다른 로그인 방법으로 로그인하는 것은 여전히 가능합니다. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>Q:  내 GitHub 계정과 연결한 Microsoft 계정에 암호를 추가했습니다.  이것이 문제가 되나요?
A:  전혀 그렇지 않습니다. 이 경우 GitHub 암호는 변경되지 않습니다. 단지 Microsoft 계정에 로그인하는 또 다른 방법이 생겼을 뿐입니다. 사용자가 이메일 주소를 사용하여 로그인할 때마다 Microsoft 계정 암호로 로그인하거나 GitHub로 로그인하는 방법 중에서 선택할 수 있습니다. 암호를 추가해야 하는 경우 GitHub 계정에 대한 암호와 다른 암호를 지정할 것을 적극 권장합니다.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>Q: GitHub를 사용하여 만든 계정에 Authenticator 앱을 추가하려고 합니다.  이것은 가능한가요?
A:  가능합니다. 이메일 주소를 사용하여 앱을 다운로드하고 로그인하기만 하면 됩니다. 이메일 주소를 사용하여 로그인하는 경우 자격 증명으로 [Authenticator 앱](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) 또는 GitHub를 선택하라는 메시지가 표시됩니다.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>Q: 내 GitHub 및 Microsoft 계정(MSA)에서 모두 2단계 인증을 사용하도록 설정했지만 내 MSA에 로그인할 때 여전히 두 번 인증하라는 요구를 받습니다.  이유
A: 보안 제한사항 때문에 Microsoft는 사용자가 GitHub에서 2단계 확인을 사용하도록 설정했더라도 GitHub로 로그인하는 것을 1단계 확인으로 계산합니다. 따라서 Microsoft 계정에 대해 다시 인증해야 합니다. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>Q:  내 Microsoft 계정과 GitHub 계정이 연결되었는지 어떻게 알 수 있나요?
A:  계정 별칭(이메일 주소, 전화 번호, Skype 이름)을 사용하여 로그인할 때마다 계정에 대한 모든 로그인 방법이 표시됩니다. GitHub가 보이지 않는다면 GitHub를 아직 설정하지 않은 것입니다.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>Q:  어떻게 하면 내 Microsoft 계정과 GitHub 계정의 연결을 해제할 수 있나요? 
A:  account.microsoft.com의 [보안 탭](https://account.microsoft.com/security)으로 이동하고 **추가 보안 옵션**을 클릭하여 GitHub 계정의 연결을 해제합니다. GitHub 계정의 연결을 해제하면 GitHub로 로그인하는 방법이 제거되며 Visual Studio에서 모든 GitHub 리포지토리에 대한 액세스가 제거됩니다. 다른 Microsoft 제품은 사용자의 GitHub 계정에 대한 액세스를 별도로 요청할 수 있으므로 여기서 액세스를 제거해도 모든 제품에서 액세스가 제거되는 것은 아닙니다. GitHub 프로필의 [애플리케이션 권한](https://github.com/settings/applications) 페이지로 이동하고 해당 페이지에 나열된 앱에서 동의를 취소하세요.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>Q:  내 GitHub 계정을 사용하여 로그인을 시도했지만 대신 사용해야 하는 Microsoft ID가 이미 있다는 메시지가 나타납니다.  이유가 무엇입니까?
A:  GitHub 계정에 Azure Active Directory 이메일 주소가 있다면 Azure에 액세스하고 GitHub 코드를 사용하여 CI 파이프라인을 실행할 수 있는 Microsoft ID가 이미 있는 것입니다. 해당 계정을 사용하면 Azure 리소스 및 빌드 파이프라인이 조직 경계 내에 확실히 유지됩니다. 그러나 개인 작업을 수행하는 경우 GitHub 계정에 개인 이메일 주소를 지정하여 언제나 해당 계정에 액세스할 수 있도록 하는 것이 좋습니다. 이렇게 수행한 후 다시 로그인을 시도하고 회사 또는 학교 게정에 로그인하라는 메시지가 나타날 때 **다른 이메일 주소 사용**을 선택하세요. 그러면 해당 개인 이메일 주소를 사용하여 새 Microsoft 계정을 만들 수 있습니다.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
구독 포털에 성공적으로 로그인한 후에는 https://my.visualstudio.com/benefits 에서 혜택 페이지를 방문하여 사용자가 이용할 수 있는 유용한 도구, 서비스 및 제안을 살펴보는 것이 좋습니다.  
