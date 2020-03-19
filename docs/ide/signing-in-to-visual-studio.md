---
title: Visual Studio에 로그인
titleSuffix: ''
ms.custom: seodec18
ms.date: 03/10/2020
ms.topic: conceptual
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1033d4167c03951a642656807aeb9cca83116651
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79132723"
---
# <a name="sign-in-to-visual-studio"></a>Visual Studio에 로그인

개인 설정 계정에 로그인하면 Visual Studio의 개발 환경을 자신에게 맞게 설정하고 최적화할 수 있습니다.

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio에 로그인](/visualstudio/mac/signing-in)을 참조하세요.

## <a name="why-should-i-sign-in-to-visual-studio"></a>Visual Studio에 로그인해야 하는 이유는 무엇인가요?

로그인하면 Visual Studio 환경이 향상됩니다. 몇 가지 예를 들자면, 로그인한 후에는 여러 디바이스에서 [설정을 동기화](synchronized-settings-in-visual-studio.md)하고 평가판을 연장하고 Azure 서비스에 자동으로 연결할 수 있습니다.

다음은 로그인 후 예상할 수 있고 수행할 수 있는 작업의 전체 목록입니다.
- **Visual Studio 평가 기간 연장** – 평가 기간을 30일로 제한하지 않고 추가로 90일 동안 Visual Studio Professional 또는 Visual Studio Enterprise를 사용할 수 있습니다. 자세한 내용은 [평가판 버전 확장 또는 라이선스 업데이트](../ide/how-to-unlock-visual-studio.md)를 참조하세요.

- **Visual Studio Community 버전 잠금 해제** - Community Edition 설치에서 라이선스를 입력하라는 메시지가 표시되는 경우 IDE에 로그인하여 직접 잠금을 해제합니다.

- **Visual Studio 구독 또는 Azure DevOps 조직과 연결된 계정을 사용하는 경우 Visual Studio를 잠금 해제합니다**. 자세한 지침은 [평가판 버전 확장 또는 라이선스 업데이트](../ide/how-to-unlock-visual-studio.md)를 참조하세요.

- **Visual Studio Dev Essentials 프로그램에 액세스** - 이 프로그램은 무료 소프트웨어 제품, 교육, 지원 등을 포함합니다. 자세한 내용은 [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) 를 참조하세요.

- **Visual Studio 설정 동기화** – 아무 디바이스에서나 Visual Studio에 로그인하면 키 바인딩, 창 레이아웃 및 색 테마 등의 사용자 지정 설정이 즉시 적용됩니다. [Visual Studio에서 설정 동기화](../ide/synchronized-settings-in-visual-studio.md)를 참조하세요.

- IDE에서 동일한 계정의 자격 증명을 묻는 메시지를 다시 표시하지 않고 **Azure 및 Azure DevOps Services 등의 서비스에 자동으로 연결**합니다.

## <a name="how-to-sign-in-to-visual-studio"></a>Visual Studio에 로그인하는 방법

Visual Studio를 처음 열 때 로그인하고 기본적인 등록 정보를 입력하라는 메시지가 나타납니다. 

![로그인 프롬프트](../ide/media/vs2019_signinpopup.png)

자신을 가장 잘 나타내는 Microsoft 계정이나 회사 또는 학교 계정을 선택해야 합니다. 이러한 계정이 없으면 로그인 단추 아래 링크를 클릭하여 무료로 Microsoft 계정을 만들 수 있습니다. 문제가 있는 경우 [Microsoft 계정을 등록하려면 어떻게 하나요?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)를 참조하세요.

그런 다음 Visual Studio에서 사용할 UI 설정과 색 테마를 선택합니다. Visual Studio가 이러한 설정을 기억하고 로그인한 모든 Visual Studio 환경에서 이 설정을 동기화합니다. 동기화된 설정 목록은 [동기화된 설정](../ide/synchronized-settings-in-visual-studio.md)을 참조하세요. 나중에 Visual Studio에서 **도구** > **옵션** 메뉴를 열어 설정을 변경할 수 있습니다.

설정을 제공한 후 Visual Studio가 시작되고 로그인되면 시작할 수 있습니다. 로그인되어 있는지 여부를 확인하려면 Visual Studio 환경의 오른쪽 위 모서리에서 이름을 찾습니다.

![현재 VS2019에 로그인한 사용자](../ide/media/vs2019_username.png)

처음 Visual Studio를 열 때 로그인하지 않도록 선택하더라도 나중에 쉽게 로그인할 수 있습니다. Visual Studio 환경의 오른쪽 위 모서리에서 **로그인** 링크를 찾습니다. 

![로그인하지 않은 사용자](../ide/media/vs2019_usernotsignedin.png)

로그아웃하지 않으면 시작할 때마다 자동으로 Visual Studio에 로그인되고 동기화된 설정의 모든 변경 내용이 자동으로 적용됩니다. 로그아웃하려면 Visual Studio 환경의 오른쪽 위 모서리에서 프로필 이름이 있는 아이콘을 클릭하고 **계정 설정** 명령을 선택한 후 **로그아웃** 링크를 선택합니다. 다시 로그인하려면 Visual Studio 환경의 오른쪽 위 모서리에서 **로그인** 명령을 선택합니다.

## <a name="to-change-your-profile-information"></a>프로필 정보를 변경하려면

1. **파일** > **계정 설정**으로 이동하여 **Visual Studio 프로필 관리** 링크를 선택합니다.

1. 브라우저 창에서 **프로필 편집**을 선택하고 원하는 대로 설정을 변경합니다.

1. 완료되면 **변경 내용 저장**을 선택합니다.

## <a name="troubleshooting"></a>문제 해결

로그인하는 동안 문제가 발생해 도움이 필요하면 [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/) 페이지를 참조하세요.

## <a name="see-also"></a>참조

* [평가판 버전 확장 또는 라이선스 업데이트](../ide/how-to-unlock-visual-studio.md)
* [Visual Studio IDE 개요](../get-started/visual-studio-ide.md)
* [로그인(Mac용 Visual Studio)](/visualstudio/mac/signing-in)
* [활성화(Mac용 Visual Studio)](/visualstudio/mac/activation)
