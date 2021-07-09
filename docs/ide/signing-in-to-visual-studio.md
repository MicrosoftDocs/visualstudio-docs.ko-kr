---
title: 로그인
description: Visual Studio에 로그인하는 방법을 알아봅니다.
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1335ab3d8f679f00fb7f52420d378baa1f2bd905
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222996"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Windows의 Visual Studio에 로그인

반드시 로그인할 필요는 없지만 로그인하면 다양한 이점이 제공됩니다. 로그인하면 Visual Studio 환경을 맞춤 설정하고 최적화하고 보강할 수 있습니다. 

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio에 로그인](/visualstudio/mac/signing-in)을 참조하세요.

::: moniker range="vs-2017"

> [!WARNING]
> 조건부 액세스를 사용하도록 구성된 리소스를 사용하려면 Visual Studio 2019 업데이트 16.6 이상으로 업그레이드합니다. 자세한 내용은 [다단계 인증이 필요한 계정으로 Visual Studio를 사용하는 방법](work-with-multi-factor-authentication.md)을 참조하세요.
> Visual Studio 2017을 사용하여 조건부 액세스를 위해 구성된 리소스에 액세스하면 인증 환경이 저하되어 동일한 Visual Studio 세션 내에서 재인증을 여러 번 수행해야 할 수 있습니다. 
> 
::: moniker-end

## <a name="benefits"></a>혜택

다음은 로그인 후 예상할 수 있고 수행할 수 있는 작업의 전체 목록입니다.

|이점|설명|
|---|---|
|Visual Studio 평가판 기간 연장|30일의 평가판 기간으로 제한되는 대신 **추가로 90일 동안** Visual Studio Professional 또는 Visual Studio Enterprise를 사용할 수 있습니다. <br/>[평가판 버전 확장 또는 라이선스 업데이트](../ide/how-to-unlock-visual-studio.md)를 참조하세요.|
|Visual Studio 잠금 해제(Visual Studio 구독 또는 Azure DevOps 조직)|Visual Studio 구독 또는 Azure DevOps 조직과 연결된 계정을 사용하는 경우 Visual Studio를 잠금 해제합니다.<br/>[평가판 버전 확장 또는 라이선스 업데이트](../ide/how-to-unlock-visual-studio.md)를 참조하세요.|
|Visual Studio 설정 동기화|원하는 디바이스에서 Visual Studio에 로그인하면 키 바인딩, 창 레이아웃, 색 테마 등의 사용자 지정 설정이 즉시 적용됩니다. <br/>[Visual Studio에서 설정 동기화](../ide/synchronized-settings-in-visual-studio.md)를 참조하세요.|
|서비스에 자동으로 연결|IDE에서 동일한 계정의 자격 증명을 묻는 메시지를 다시 표시하지 않고 Azure 및 Azure DevOps Services 등의 서비스에 연결합니다.|
|계속해서 Visual Studio Community Edition 사용|Community Edition 설치에서 라이선스를 입력하라는 메시지가 표시되면 IDE에 로그인하여 계속해서 Visual Studio Community를 **별도의 비용 없이** 사용할 수 있습니다. |
|'Visual Studio Dev Essentials' 받기|이 프로그램은 무료 소프트웨어 제품, 교육, 지원 등을 포함합니다. <br/>[Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/)를 참조하세요.|


## <a name="how-to-sign-in"></a>로그인 방법 

Visual Studio를 처음 열 때 로그인하고 기본적인 등록 정보를 입력하라는 메시지가 나타납니다.

![로그인 프롬프트](../ide/media/vs2019_signinpopup.png)

1. 자신을 가장 잘 나타내는 Microsoft 계정이나 회사 또는 학교 계정을 선택합니다. 이러한 계정이 없으면 로그인 단추 아래 링크를 클릭하여 무료로 Microsoft 계정을 만들 수 있습니다. 문제가 있는 경우 [Microsoft 계정을 등록하려면 어떻게 하나요?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)를 참조하세요.

2. Visual Studio에서 사용할 UI 설정과 색 테마를 선택합니다. Visual Studio가 이러한 설정을 기억하고 로그인한 모든 Visual Studio 환경에서 이 설정을 동기화합니다. 동기화된 설정 목록은 [동기화된 설정](../ide/synchronized-settings-in-visual-studio.md)을 참조하세요. 나중에 Visual Studio에서 **도구** > **옵션** 메뉴를 열어 설정을 변경할 수 있습니다.
   설정을 제공한 후 Visual Studio가 시작되고 로그인되면 시작할 수 있습니다. 
   
1. 로그인되어 있는지 여부를 확인하려면 Visual Studio 환경의 오른쪽 위 모서리에서 이름을 찾습니다.

![현재 VS2019에 로그인한 사용자](../ide/media/vs2019_username.png)

처음 Visual Studio를 열 때 로그인하지 않도록 선택하더라도 나중에 쉽게 로그인할 수 있습니다. Visual Studio 환경의 오른쪽 위 모서리에서 **로그인** 링크를 찾습니다.

![로그인하지 않은 사용자](../ide/media/vs2019_usernotsignedin.png)

로그아웃하지 않으면 시작할 때마다 자동으로 Visual Studio에 로그인되고 동기화된 설정의 모든 변경 내용이 자동으로 적용됩니다. 로그아웃하려면 Visual Studio 환경의 오른쪽 위 모서리에서 프로필 이름이 있는 아이콘을 클릭하고 **계정 설정** 명령을 선택한 후 **로그아웃** 링크를 선택합니다. 다시 로그인하려면 Visual Studio 환경의 오른쪽 위 모서리에서 **로그인** 명령을 선택합니다.

## <a name="update-your-profile"></a>프로필 업데이트

1. **파일** > **계정 설정** 으로 이동하여 **Visual Studio 프로필 관리** 링크를 선택합니다.

1. 브라우저 창에서 **프로필 편집** 을 선택하고 원하는 대로 설정을 변경합니다.

1. 완료되면 **변경 내용 저장** 을 선택합니다.

## <a name="troubleshooting"></a>문제 해결

도움을 받으려면 [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/) 페이지를 참조하세요.
