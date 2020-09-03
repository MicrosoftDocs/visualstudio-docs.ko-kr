---
title: 확장 개발 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d62a4c6cc45681fe6a66ae57df2e1da1d1cc12e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850592"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio Extensions 확장 기능 개발 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이전에 Visual Studio 확장을 작성 한 적이 없는 경우 몇 가지 질문이 있을 수 있습니다. 여기에는 가장 일반적인 몇 가지 항목이 나열 되어 있습니다. 원하는 정보가 표시 되지 않으면 사용자 의견 단추를 사용 합니다 (화면 맨 아래에서**이 페이지가 도움이 되었나요?** ).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Visual Studio 확장을 개발 하는 데 필요한 소프트웨어는 무엇 인가요?
 Visual studio 확장을 개발 하려면 visual studio 2015 외에도 visual studio 2015 SDK를 설치 해야 합니다.   Visual Studio 2015 SDK를 일반 설치의 일부로 설치 하거나 나중에 설치할 수 있습니다. Visual Studio SDK를 설치 하는 방법에 대 한 자세한 내용은 [Visual STUDIO sdk](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio 확장을 사용 하 여 어떤 종류의 작업을 수행할 수 있나요?
 서로 다른 Visual Studio 확장을 발견 하는 경우에는 하늘 제한이 제공 됩니다. 물론 대부분의 확장은 코드를 작성 하는 데 사용할 수 있지만이 경우에는 그렇지 않습니다. 빌드할 수 있는 확장 종류에 대 한 몇 가지 예는 다음과 같습니다.

- 구문 색 지정, IntelliSense, 컴파일러 및 디버그 지원을 통해 Visual Studio에 포함 되지 않은 언어 지원

- 추가 템플릿, 코드 리팩터링, 새 대화 상자 또는 도구 창을 사용 하 여 핵심 IDE 환경을 확장 하는 생산성 도구

- 데이터 디자인 또는 클라우드 지원과 같은 시나리오를 위한 도메인별 디자이너

  확장의 예제를 보려면 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)를 확인 하세요. [Visual Studio 오픈 소스 확장](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md)을 살펴볼 수도 있습니다.

## <a name="which-visual-studio-features-can-i-extend"></a>어떤 Visual Studio 기능을 확장할 수 있나요?
 이론적으로는 메뉴, 도구 모음, 명령, 창, 솔루션, 프로젝트, 편집기 등을 비롯 한 Visual Studio의 일부만 확장할 수 있습니다.

 실제로 대부분의 사용자가 확장 하려는 기능이 명령, 메뉴 및 도구 모음, 창, IntelliSense 및 프로젝트입니다. 관련 섹션에 대 한 링크는 다음과 같습니다.

- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md): Visual Studio 메뉴 및 도구 모음에 고유한 항목을 추가 합니다. 이러한 기능을 사용 하 여 새 Visual Studio 기능 또는 고유한 외부 도우미 응용 프로그램을 시작할 수 있습니다. 메뉴 항목에 대 한 사용자 지정 바로 가기를 제공할 수도 있습니다.

- [도구 창 확장 및 사용자 지정](../extensibility/extending-and-customizing-tool-windows.md): 기존 도구 창을 확장 하거나 사용자 고유의 도구 창을 만듭니다. 예를 들어 **속성**에 새 속성을 추가 하거나 새 도구 창을 만들어 추가 기능을 추가할 수 있습니다.

- [편집기 및 언어 서비스 확장](../extensibility/editor-and-language-service-extensions.md): Visual Studio 언어용으로 제공 된 IntelliSense의 고유한 사용자 지정 항목을 추가 하거나 새 프로그래밍 언어에 대 한 지원을 만들 수 있습니다. 새 문 완성, 제안 및 새 QuickInfo 도구 설명을 만들 수 있습니다. Light 전구를 사용 하면 새 프로그래밍 언어를 지원 하기 위해 리팩터링 제안 사항 및 코드 수정을 추가할 수 있습니다.

- [프로젝트 확장](../extensibility/extending-projects.md)

- [사용자 설정 및 옵션 확장](../extensibility/extending-user-settings-and-options.md)

- [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)

- [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Shell(격리)](../extensibility/visual-studio-isolated-shell.md)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> 이상에서 제공 하는 프로젝트 템플릿은 무엇 인가요?
 두 가지 주요 확장 유형은 Vspackage 및 MEF 확장입니다. 일반적으로 VSPackage 확장은 명령, 도구 창 및 프로젝트를 사용 하거나 확장 하는 확장에 사용 됩니다. MEF 확장은 Visual Studio 편집기를 확장 하거나 사용자 지정 하는 데 사용 됩니다.

 Visual c # 및 Visual Basic 확장의 경우 새 항목은 메뉴 명령, 도구 창 및 편집기 확장을 만드는 새 항목 템플릿과 함께 사용할 수 있는 빈 VSIX 프로젝트 템플릿을 제공 합니다. 자세한 내용은 [Visual Studio 2015 SDK의 새로운 기능](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)을 참조 하세요. 이 템플릿을 사용 하 여 다른 사용자에 게 배포 하기 위해 프로젝트 템플릿, 코드 조각 및 기타 아티팩트를 패키지할 수도 있습니다.

 C + +의 경우 VSPackage 마법사는 메뉴 명령, 도구 창 및 사용자 지정 편집기를 추가 하는 코드를 제공 합니다.

 격리 된 셸 템플릿은 사용자가 직접 브랜드 및 배포할 수 있는 Visual Studio Shell 버전의 확장을 패키지 하는 데 사용 됩니다. 다음 항목에서는 각 종류의 확장을 시작 하는 방법을 보여 줍니다.

- 메뉴 명령: [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)

- 도구 창: [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)

- 편집기 확장: [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- 기본 Vspackage: [VSPackage를 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX 프로젝트 템플릿: [Vsix 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)

- Visual Studio 격리 셸: [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Visual Studio와 같은 확장을 가져올 어떻게 할까요? 있나요?
 [Visual Studio 사용자 환경 지침](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)에서 확장에 대 한 UI를 디자인 하는 데 유용한 팁을 확인 하세요.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>어디에서 나를 수 있나요?
 이전 섹션에 나열 된 각 링크에는 특정 기능을 구현 하는 방법을 보여 주는 단계별 연습이 있습니다. [Visual Studio 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples)에서 GitHub의 오픈 소스에 대 한 진한 샘플을 찾을 수도 있습니다.

## <a name="how-can-i-distribute-my-extension"></a>내 확장을 배포 하려면 어떻게 해야 하나요?
 다른 컴퓨터에 확장을 설치 하거나 친구에 게 .vsix 파일로 보낼 수 있습니다 .이 파일을 두 번 클릭 하 여 설치 합니다. VSIX 패키지에 대 한 자세한 내용은 [Visual Studio 확장](../extensibility/shipping-visual-studio-extensions.md)제공에서 확인할 수 있습니다.

 Visual Studio 갤러리에 확장을 게시 하 여 많은 수의 Visual Studio 고객이 볼 수도 있습니다. 갤러리에 대 한 확장을 패키징하는 예제는 [연습: Visual Studio 확장 게시](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)를 참조 하세요. 갤러리에서 게시 하기 위해 수행 해야 하는 작업에 대 한 자세한 내용은 [Visual Studio 용 제품 및 확장](https://visualstudiogallery.msdn.microsoft.com/)을 참조 하세요.
