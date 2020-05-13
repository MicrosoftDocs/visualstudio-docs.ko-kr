---
title: 비주얼 스튜디오 확장 개발 시작 | 마이크로 소프트 문서
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699735"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio Extensions 확장 기능 개발 시작

이전에 Visual Studio 확장을 작성한 적이 없는 경우 몇 가지 질문이 있을 수 있습니다. 우리는 여기에 가장 일반적인 것들 중 일부를 나열했습니다. 찾고 있는 정보가 표시되지 않으면 피드백**버튼(이 페이지가 도움이 됩니까?** 화면 하단)을 사용하여 원하는 내용을 요청합니다.

> [!NOTE]
> 이 문서는 Windows의 Visual Studio에 적용됩니다. Mac용 비주얼 스튜디오의 경우 [Mac용 시각적 스튜디오 확장을](/visualstudio/mac/extending-visual-studio-mac)참조하십시오. 비주얼 스튜디오 코드의 경우 [Visual Studio 코드 확장 API를](https://code.visualstudio.com/api)참조하십시오.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Visual Studio 확장을 개발하려면 어떤 소프트웨어가 필요합니까?

Visual Studio 확장을 개발하려면 Visual Studio 외에도 Visual Studio SDK를 설치해야 합니다. Visual Studio SDK를 일반 설정의 일부로 설치하거나 나중에 설치할 수 있습니다. Visual Studio SDK 설치에 대한 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio 확장 프로그램을 사용하면 어떤 작업을 수행할 수 있습니까?

다른 Visual Studio 확장을 상상할 때 하늘의 한계입니다. 물론 대부분의 확장에는 코드 작성과 관련이 있지만 그럴 필요는 없습니다. 다음은 빌드할 수 있는 확장의 종류에 대한 몇 가지 예입니다.

- 구문 색칠, IntelliSense, 컴파일러 및 디버그 지원을 통해 Visual Studio에 포함되지 않은 언어 지원

- 추가 템플릿, 코드 리팩터링, 새로운 대화 상자 또는 도구 창을 통해 핵심 IDE 환경을 확장하는 생산성 도구

- 데이터 디자인 또는 클라우드 지원과 같은 시나리오를 위한 도메인별 설계자

확장 의 예는 [Visual Studio 마켓플레이스를](https://marketplace.visualstudio.com/vs)확인하십시오. 많은 확장은 오픈 소스, 그리고 마켓 플레이스 는 그들의 GitHub 리포지토리에 대 한 링크를 포함.

## <a name="which-visual-studio-features-can-i-extend"></a>어떤 비주얼 스튜디오 기능을 확장할 수 있습니까?

이론적으로 메뉴, 도구 모음, 명령, 창, 솔루션, 프로젝트, 편집기 등 Visual Studio의 거의 모든 부분을 확장할 수 있습니다.

실제로 대부분의 사람들이 확장하려는 기능은 명령, 메뉴 및 도구 모음, 창, IntelliSense 및 프로젝트입니다. 관련 섹션에 대한 링크는 다음과 같습니다.

- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md): Visual Studio 메뉴 및 도구 모음에 사용자 고유의 항목을 추가합니다. 이를 사용하여 새로운 Visual Studio 기능 또는 사용자 고유의 외부 도우미 응용 프로그램을 시작할 수 있습니다. 메뉴 항목에 대한 사용자 지정 바로 가기를 제공할 수도 있습니다.

- [확장 및 사용자 정의 도구 창](../extensibility/extending-and-customizing-tool-windows.md): 기존 도구 창을 확장하거나 자신의 도구 창을 만들 수 있습니다. 예를 들어 **속성에**새 속성을 추가하거나 새 도구 창을 만들어 추가 기능을 추가할 수 있습니다.

- [편집기 및 언어 서비스 확장](../extensibility/editor-and-language-service-extensions.md): Visual Studio 언어에 제공된 IntelliSense에 사용자 고유의 사용자 지정을 추가하거나 새 프로그래밍 언어에 대한 지원을 만듭니다. 새 명령문 완료, 제안 및 새 QuickInfo 도구 설명을 만들 수 있습니다. 전구를 사용하면 리팩터링 제안 및 코드 수정 프로그램을 추가하여 새로운 프로그래밍 언어를 지원할 수 있습니다.

- [프로젝트 확장](../extensibility/extending-projects.md)

- [사용자 설정 및 옵션 확장](../extensibility/extending-user-settings-and-options.md)

- [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)

- [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Shell(격리)](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>VSSDK에서 제공하는 프로젝트 템플릿은 무엇입니까?
 확장의 두 가지 주요 유형은 VSPackage 및 MEF 확장입니다. 일반적으로 VSPackage 확장은 명령, 도구 창 및 프로젝트를 사용하거나 확장하는 확장에 사용됩니다. MEF 확장은 Visual Studio 편집기를 확장하거나 사용자 지정하는 데 사용됩니다.

 시각적 C# 및 Visual Basic 확장의 경우 VSSDK는 메뉴 명령, 도구 창 및 편집기 확장을 만드는 새 항목 템플릿과 함께 사용할 수 있는 빈 VSIX 프로젝트 템플릿을 제공합니다. 이 템플릿을 사용하여 프로젝트 템플릿, 코드 조각 및 기타 아티팩트를 다른 사용자에게 배포하도록 패키징할 수도 있습니다.

 C++의 경우 VSPackage 마법사는 메뉴 명령, 도구 창 및 사용자 지정 편집기를 추가하는 코드를 제공합니다.

 격리된 셸 템플릿은 직접 브랜드화하고 배포할 수 있는 Visual Studio 셸 버전에서 확장을 패키징하는 데 사용됩니다. 다음 항목에서는 각 종류의 확장을 시작하는 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주시면 됩니다.

- 메뉴 명령: [메뉴 명령을 통해 확장](../extensibility/creating-an-extension-with-a-menu-command.md) 만들기

- 도구 창: [도구 창을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)

- 편집기 확장: [편집기 항목 템플릿을 통해 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- 기본 VS패키지: [VS패키지로 확장 만들기](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX 프로젝트 템플릿: [VSIX 프로젝트 템플릿으로 시작하기](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>확장 프로그램을 Visual Studio처럼 보이게 하려면 어떻게 해야 하나요?
 [Visual Studio 사용자 환경 지침에서](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)확장을 위한 UI를 디자인하기 위한 훌륭한 팁을 얻을 수 있습니다.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK 코드의 예는 어디에서 찾을 수 있습니까?
 앞섹션에 나열된 각 링크에는 특정 기능을 구현하는 방법을 보여 주는 단계별 연습이 있습니다. 또한 비주얼 스튜디오 샘플에서 GitHub에서 오픈 소스 VSSDK 샘플을 찾을 수 [있습니다.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="how-can-i-distribute-my-extension"></a>내 확장을 배포하는 방법은 무엇입니까?
 다른 컴퓨터에 확장 프로그램을 설치하거나 .vsix 파일로 친구에게 보낼 수 있으며, 이 파일은 두 번 클릭하여 설치할 수 있습니다. [배송 비주얼 스튜디오 익스텐션에서](../extensibility/shipping-visual-studio-extensions.md)VSIX 패키지에 대한 자세한 내용을 확인할 수 있습니다.

 또한 많은 수의 Visual Studio 고객이 볼 수 있도록 Visual Studio 마켓플레이스에 확장을 게시할 수도 있습니다. 마켓플레이스에 대한 확장을 패키징하는 예는 [연습: Visual Studio 확장 게시를](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)참조하십시오. 마켓플레이스에 게시하기 위해 수행해야 하는 일에 대한 자세한 내용은 [Visual Studio용 제품 및 확장 프로그램을](/azure/devops/extend/overview?view=vsts)참조하십시오.

## <a name="see-also"></a>참조

- [Mac용 Visual Studio 확장](/visualstudio/mac/extending-visual-studio-mac)
- [비주얼 스튜디오 코드 확장](https://code.visualstudio.com/api)
