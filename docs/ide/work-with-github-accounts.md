---
title: Visual Studio에서 GitHub 계정 작업
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: GitHub 계정으로 Visual Studio를 사용하는 방법을 알아봅니다.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 845b663a3a0828806766fa0609e45efafabec50a
ms.sourcegitcommit: e8a13978131f257d91ce37c5a2e0d153a4c400ef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704035"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Visual Studio에서 GitHub 계정 작업

공용 GitHub 또는 GitHub Enterprise 계정이 있는 경우 계정을 Visual Studio 키 집합에 추가할 수 있습니다. 계정을 추가하면 Visual Studio에서 바로 GitHub 리포지토리에 액세스하고 리포지토리를 만들어 플랫폼 통합의 이점을 활용할 수 있습니다.

## <a name="adding-public-github-accounts"></a>공용 GitHub 계정 추가

이미 Microsoft 계정이나 회사 또는 학교 계정을 사용하여 Visual Studio에 로그인했다면 공용 GitHub 계정을 추가할 수 있습니다.

1. Visual Studio 환경의 오른쪽 위 모서리에서 사용자의 이니셜이 있는 아이콘을 선택합니다. 그런 다음 **계정 설정...** 을 선택하여 계정을 관리합니다. **파일** > **계정 설정** 으로 이동하여 계정 설정 대화 상자를 열어도 됩니다.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="계정 설정":::

2. **모든 계정** 하위 메뉴에서 더하기 기호를 선택하여 계정을 추가하고 **GitHub** 를 선택합니다.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="GitHub 계정 추가 선택":::

3. GitHub 자격 증명으로 로그인할 수 있는 브라우저로 리디렉션됩니다. 로그인하면 브라우저에서 성공 창이 표시되고 Visual Studio로 돌아갈 수 있게 됩니다.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="브라우저의 성공 창":::

4. **모든 계정** 하위 메뉴에 계정 두 개가 존재합니다.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="두 계정 모두 표시":::

다른 계정으로 Visual Studio에 로그인하지 않았다면 Visual Studio 환경 오른쪽 위에 있는 **로그인** 링크를 선택합니다. **파일** > **계정 설정** 으로 이동하여 계정 설정 대화 상자를 열어도 됩니다. 그런 다음 위의 지침에 따라 GitHub 계정을 추가합니다.

![로그인하지 않은 사용자](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>GitHub Enterprise 계정 추가

기본적으로 Visual Studio에는 공용 GitHub 계정만 활성화됩니다.

1. GitHub Enterprise 계정을 활성화하려면 **도구** > **옵션** 으로 이동하고 **계정** 옵션을 검색합니다.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="계정 옵션 메뉴":::

2. 그런 다음 확인란을 선택하여 **GitHub Enterprise 서버 계정을 포함합니다**. 이후에 **계정 설정** 으로 이동하여 GitHub 계정을 추가하면 GitHub와 GitHub Enterprise의 옵션이 모두 표시됩니다.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="GitHub Enterprise로 로그인":::

3. GitHub Enterprise 서버 주소를 입력하고 **브라우저로 로그인** 을 선택합니다. 여기서 GitHub Enterprise 자격 증명을 사용하여 로그인할 수 있습니다.

## <a name="see-also"></a>참조

- [여러 사용자 계정으로 작업](work-with-multiple-user-accounts.md)
- [Visual Studio에 로그인](signing-in-to-visual-studio.md)
