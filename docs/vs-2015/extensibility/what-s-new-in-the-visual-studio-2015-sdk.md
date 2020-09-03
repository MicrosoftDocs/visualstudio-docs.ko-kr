---
title: Visual Studio 2015 SDK의 새로운 기능 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917324"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK의 새로운 기능&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual studio SDK에는 visual Studio 2015, Visual Studio 2015 업데이트 및 Visual Studio 2017에 대해 다음과 같은 새롭고 업데이트 된 기능이 포함 되어 있습니다.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Visual Studio 2017부터 사용자 지정 프로젝트 및 항목 템플릿 검색을 더 이상 수행하지 않습니다. 대신 확장에서는 해당 템플릿의 설치 위치를 설명하는 템플릿 매니페스트 파일을 제공해야 합니다. Visual Studio 2017을 사용하여 VSIX 확장을 업데이트할 수 있습니다. MSI를 사용하여 확장을 배포하는 경우 템플릿 매니페스트 파일을 직접 생성해야 합니다. 자세한 내용은 [사용자 지정 Visual Studio용 프로젝트 및 항목 템플릿 2017 업그레이드](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015)를 참조 하세요. 템플릿 매니페스트 스키마는 [Visual Studio 템플릿 매니페스트 스키마 참조](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)에 설명 되어 있습니다.

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK 업데이트 1
 업데이트 1에는 색 테마 및 Visual Studio 이미지 서비스에서 확장이 잘 작동 하는 데 도움이 되는 도구가 포함 되어 있습니다.

 이러한 [항목은 다음과](../extensibility/internals/vssdk-utilities.md) 같습니다.

- [색 테마 지정 도구](../extensibility/internals/color-theming-tools.md) 를 통해 Visual Studio에 대 한 사용자 지정 색을 만들고 편집할 수 있습니다.

- [이미지 서비스 도구](../extensibility/internals/image-service-tools.md) 를 사용 하 여 Visual Studio 이미지 매니페스트 파일을 사용할 수 있습니다.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual studio에 visual studio SDK를 추가 하는 새로운 방법
 Visual Studio 2015부터 Visual Studio SDK를 별도로 다운로드할 필요가 없습니다. 대신 일반 설치 프로세스의 일부로 설치 하거나 나중에 설치 하도록 선택할 수 있습니다. VSIX 솔루션을 열거나 만들 때 Visual Studio는 Visual Studio 확장성 도구을 설치 하 라는 메시지를 표시 합니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="new-ways-of-creating-extensions"></a>새 확장을 만드는 방법
 Visual Studio 2015 SDK부터 사용 중인 프로그래밍 언어에 따라 확장을 만들 수 있는 다양 한 옵션이 있습니다.

### <a name="visual-c-and-visual-basic"></a>Visual C# 및 Visual Basic
 C # 및 Visual Basic의 경우 Vspackage, 메뉴 명령, 도구 창, 편집기 분류자, 편집기 장식 및 편집기 여백 확장을 만들 수 있는 전체 범위의 프로젝트 항목 템플릿이 있습니다. 이러한 중 하나 또는 모두를 표준 VSIX 프로젝트에 추가할 수 있습니다. 자세한 내용은 다음을 참조하십시오.

- [메뉴 명령을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)

- [도구 창으로 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)

- [편집기 항목 템플릿을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [로 확장 만들기](../extensibility/creating-an-extension-with-a-vspackage.md)

     VSPackage 마법사는 더 이상 c # 또는 Visual Basic 확장을 만들 필요가 없습니다.

### <a name="c"></a>C++
 C + +의 경우 VSPackage 마법사는 메뉴 명령, 도구 창 및 사용자 지정 편집기를 지원 합니다. **Visual C++/확장성**의 **새 프로젝트** 대화 상자에서 해당 파일을 찾습니다.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>NuGet을 통한 VS SDK 참조 어셈블리
 확장성 및 확장성 프로젝트의 공유를 향상 하기 위해 NuGet 버전의 VS SDK 참조 어셈블리를 사용할 수 있습니다.  이러한 기능은 [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) 에서 게시 한 [nuget.org](https://www.nuget.org/) 에서 사용할 수 있으며 Visual Studio **참조/nuget 패키지 관리** 대화 상자를 통해 프로젝트 또는 솔루션에 쉽게 추가할 수 있습니다. VS SDK [메타 패키지](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)를 사용 하 여 특정 확장성 어셈블리에 개별 참조를 추가 하거나 한 번에 모든 vs sdk 참조 어셈블리를 추가할 수 있습니다. NuGet에 대 한 자세한 내용은 [Nuget 개요](/nuget/) 및 [대화 상자를 사용 하 여 nuget 패키지 관리](/nuget/consume-packages/install-use-packages-visual-studio)를 참조 하세요.

 VS SDK 참조 어셈블리의 NuGet 버전을 사용 하는 경우 다른 사용자가 VS SDK를 설치 하 여 프로젝트를 열고 빌드할 필요가 없습니다.  NuGet 참조 어셈블리 및 VS SDK 빌드 도구는 해당 프로젝트의 컴퓨터에 자동으로 설치 됩니다.

 VS SDK 항목 템플릿은 nuget을 사용 하 여 참조 및 빌드 도구에 대해 NuGet을 사용 하므로 기본적으로 NuGet의 이점을 얻을 수 있습니다.

> [!NOTE]
> VS SDK에 설치 된 참조 어셈블리를 프로젝트와 함께 계속 사용할 수 있습니다 ( \<Visual Studio Install Location> \ VSSDK\VisualStudioIntegration\Common\Assemblies에 있음). 기존 확장성 프로젝트는 NuGet 패키지를 사용 하도록 업그레이드 하지 않아도 됩니다.  프로젝트 **참조/참조 추가** 대화 상자는 VS SDK에서 설치 된 참조 어셈블리를 계속 사용 합니다.
>
> NuGet을 사용 하도록 기존 프로젝트를 수정 하려면 방법: 확장성 프로젝트를 NuGet 패키지로 업데이트 하는 섹션이 있는 [방법: vspackage을 Visual Studio 2015로 마이그레이션](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) 을 참조 하세요.

## <a name="light-bulbs"></a>연한 전구
 확장 코드를 작성 하는 가장 흥미로운 새로운 방법 중 하나는 Roslyn 프로젝트에 의해 제공 됩니다. 자세한 내용은 [Roslyn](https://github.com/dotnet/Roslyn)를 참조 하세요.

 Light 전구는 고가와 함께 제공 되는 새로운 기능입니다. Visual Studio 편집기에서 사용 되는 아이콘으로, 코드 리팩터링 작업 집합 또는 기본 제공 코드 분석기에서 식별 하는 문제에 대 한 수정 내용을 표시 하도록 확장 됩니다. 자세한 내용은 [연습: 전구 제안 표시](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)를 참조 하세요.

## <a name="updated-user-experience-guidelines"></a>업데이트 된 사용자 환경 지침
 Visual Studio에 대 한 새로운 확장 또는 기능 디자인 업데이트 되 고 확장 된 [Visual Studio 사용자 환경 지침](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)을 확인 하세요.  새 UI를 Visual Studio와 원활 하 게 통합 하는 데 필요한 [색 토큰](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [글꼴 크기](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [대화 상자 레이아웃 사양](../extensibility/ux-guidelines/layout-for-visual-studio.md)및 기타 지침을 찾을 수 있습니다.
