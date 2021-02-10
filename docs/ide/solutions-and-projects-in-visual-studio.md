---
title: 솔루션 및 프로젝트에 대한 자세한 정보
description: Visual Studio 프로젝트 및 솔루션, 템플릿에서 새 프로젝트를 만드는 방법, 솔루션 탐색기에서 프로젝트를 보고 관리하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 473c3ca0e4a9998d6a320e384bf39b4b5e037085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878502"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio의 솔루션 및 프로젝트

이 페이지에서는 Visual Studio의 ‘프로젝트’ 및 ‘솔루션’ 개념에 대해 설명합니다.  솔루션 탐색기 도구 창과 새 프로젝트를 만드는 방법에 대해서도 간략하게 설명합니다.

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 프로젝트 및 솔루션](/visualstudio/mac/projects-and-solutions)을 참조하세요.

## <a name="projects"></a>프로젝트

Visual Studio에서 앱이나 웹 사이트를 만드는 경우 ‘프로젝트’에서 시작합니다. 논리적인 측면에서 프로젝트에는 실행 파일, 라이브러리 또는 웹 사이트로 컴파일되는 모든 파일이 포함됩니다. 이러한 파일에는 소스 코드, 아이콘, 이미지, 데이터 파일 등이 포함될 수 있습니다. 프로젝트에도 프로그램이 통신하는 여러 서비스 또는 구성 요소에 필요할 수 있는 컴파일러 설정 및 기타 구성 파일이 포함되어 있습니다.

### <a name="project-file"></a>프로젝트 파일

Visual Studio는 [MSBuild](../msbuild/msbuild.md)를 사용하여 솔루션의 각 프로젝트를 빌드하고, 각 프로젝트에는 MSBuild 프로젝트 파일이 포함됩니다. 파일 확장명은 C# 프로젝트(.csproj), Visual Basic 프로젝트(.vbproj), 데이터베이스 프로젝트(.dbproj)와 같이 프로젝트 형식을 반영합니다. 프로젝트 파일은 콘텐츠, 플랫폼 요구 사항, 버전 관리 정보, 웹 서버 또는 데이터베이스 서버 설정, 수행할 작업 등을 포함하여 MSBuild에서 프로젝트를 빌드하는 데 필요한 모든 정보와 지침이 포함된 XML 문서입니다.

프로젝트 파일은 [MSBuild XML 스키마](../msbuild/msbuild-project-file-schema-reference.md)를 기반으로 합니다. Visual Studio에서 최신 [SDK 스타일 프로젝트 파일](../msbuild/how-to-use-project-sdk.md)의 내용을 살펴보려면, **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **\<projectname\> 편집** 을 선택합니다. 해당 스타일의 다른 프로젝트와 .NET Framework의 내용을 살펴보려면, **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드** 를 선택하여 프로젝트를 먼저 언로드합니다. 그런 다음, 프로젝트를 마우스 오른쪽 단추로 클릭하고 **\<projectname\> 편집** 을 선택합니다.

> [!NOTE]
> Visual Studio에서 코드를 편집, 빌드, 디버그하기 위해 솔루션이나 프로젝트를 사용할 필요는 없습니다. Visual Studio에서 소스 파일이 들어 있는 폴더를 열고 편집을 시작하면 됩니다. 자세한 내용은 [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)을 참조하세요.

### <a name="create-new-projects"></a>새 프로젝트 만들기

새 프로젝트를 만드는 가장 쉬운 방법은 원하는 프로젝트 형식에 맞는 프로젝트 템플릿을 사용하는 것입니다. 프로젝트 템플릿에는 미리 생성된 코드 파일, 구성 파일, 자산, 설정의 기본 세트가 포함됩니다. **파일** > **새로 만들기** > **프로젝트** 를 사용하여 프로젝트 템플릿을 선택합니다. 자세한 내용은 [새 프로젝트 만들기](create-new-project.md)를 참조하세요.

새 프로젝트를 만드는 데 사용할 수 있는 사용자 지정 프로젝트 템플릿을 만들 수도 있습니다. 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조하세요.

새 프로젝트를 만들면 Visual Studio에서 기본 위치인 *%USERPROFILE%\source\repos* 에 저장합니다. 이 위치를 변경하려면 **도구** > **옵션** > **프로젝트 및 솔루션** > **위치** 로 이동합니다. 자세한 내용은 [옵션 대화 상자: 프로젝트 및 솔루션 > 위치](./reference/projects-solutions-locations-options.md)를 참조하세요.

## <a name="solutions"></a>솔루션

프로젝트는 *솔루션* 에 포함되어 있습니다. 이름과 달리 솔루션은 "정답"이 아닙니다. 이는 간단히 빌드 정보, Visual Studio 창 설정 및 특정 프로젝트와 관련이 없는 기타 파일과 함께 하나 이상의 관련된 프로젝트를 위한 컨테이너입니다.

### <a name="solution-file"></a>솔루션 파일

Visual Studio에서는 두 가지 파일 형식( *.sln* 및 *.suo*)을 사용하여 솔루션 관련 설정을 저장합니다.

|확장명|이름|설명|
|---------------|----------|-----------------|
|.sln|Visual Studio 솔루션|솔루션에서 프로젝트, 프로젝트 항목 및 솔루션 항목을 구성합니다.|
|.suo|솔루션 사용자 옵션|중단점과 같은 사용자 수준 설정 및 사용자 지정을 저장합니다.|

> [!IMPORTANT]
> 솔루션은 고유한 형식을 가진 텍스트 파일( *.sln* 확장명)로 설명되고 직접 편집할 수 없습니다. 반대로 *.suo* 파일은 파일 탐색기의 기본 설정으로는 표시되지 않는 숨겨진 파일입니다. 숨겨진 파일을 표시하려면 파일 탐색기의 **보기** 메뉴에서는 **숨겨진 항목** 확인란을 선택합니다.

### <a name="solution-folder"></a>솔루션 폴더

"솔루션 폴더"는 **솔루션 탐색기** 에만 있는 가상 폴더이며 솔루션에서 프로젝트를 그룹화하는 데 사용할 수 있습니다. 컴퓨터에서 솔루션 파일을 찾으려면 **도구** > **옵션** > **프로젝트 및 솔루션** > **위치** 로 이동합니다. 자세한 내용은 [옵션 대화 상자: 프로젝트 및 솔루션 > 위치](./reference/projects-solutions-locations-options.md)를 참조하세요.

> [!TIP]
> 처음부터 프로젝트 및 솔루션을 만들고 단계별 지침 및 샘플 코드를 사용하여 완료하는 예제는 [프로젝트 및 솔루션 소개](../get-started/tutorial-projects-solutions.md)를 참조하세요.

## <a name="solution-explorer"></a>솔루션 탐색기

새 프로젝트를 만든 후에 **솔루션 탐색기** 를 사용하여 프로젝트와 솔루션 및 연결된 항목을 보고 관리할 수 있습니다. 다음 그림은 두 프로젝트가 포함되어 있으며, C# 솔루션을 사용하는 **솔루션 탐색기** 를 보여 줍니다.

::: moniker range="vs-2017"

![두 프로젝트가 있는 솔루션 탐색기의 스크린샷](../ide/media/vs2015_solution_explorer.png)

**솔루션 탐색기** 의 위쪽에 있는 도구 모음에는 솔루션 보기를 폴더 보기로 전환하고 숨겨진 파일을 표시하고 모든 노드를 축소하는 등의 작업을 위한 단추가 있습니다.

::: moniker-end

::: moniker range="vs-2019"

![Visual Studio 2019의 프로젝트 두 개가 있는 솔루션 탐색기의 스크린샷](../ide/media/solution-explorer.png)

**솔루션 탐색기** 위쪽에 있는 도구 모음에는 솔루션 보기를 폴더 보기로 전환하고 보류 중인 변경 내용을 필터링하고 모든 파일을 표시하고 모든 노드를 축소하고 [속성](managing-project-and-solution-properties.md) 페이지를 표시하고 [코드 편집기](writing-code-in-the-code-and-text-editor.md)에서 코드를 미리 보는 등의 작업을 위한 단추가 있습니다.

::: moniker-end

대부분의 메뉴 명령은 **솔루션 탐색기** 에 있는 다양한 항목의 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴에서 사용할 수 있습니다. 이러한 명령에는 프로젝트 빌드, NuGet 패키지 관리, 참조 추가, 파일 이름 바꾸기, 테스트 실행 등이 포함됩니다.

ASP.NET Core 프로젝트의 경우에는 파일이 **솔루션 탐색기** 에 중첩되는 방식을 사용자 지정할 수 있습니다. 자세한 내용은 [솔루션 탐색기에서 파일 중첩 사용자 지정](file-nesting-solution-explorer.md)을 참조하세요.

> [!TIP]
> 솔루션 탐색기를 닫은 후 다시 열려면 메뉴 모음에서 **보기** > **솔루션 탐색기** 를 선택하거나 **Ctrl**+**Alt**+**L** 을 누릅니다. 그리고, 사이드 탭을 닫은 후 해당 탭을 기본 위치로 복원하려면 메뉴 모음에서 **창** > **창 레이아웃 다시 설정** 을 선택합니다.

> [!NOTE]
> Visual Studio에 표시되는 애플리케이션 이미지와 아이콘을 보려면 [**Visual Studio 이미지 라이브러리**](https://www.microsoft.com/download/details.aspx?id=35825)를 다운로드합니다.

## <a name="see-also"></a>추가 정보

- [프로젝트 및 솔루션 소개](../get-started/tutorial-projects-solutions.md)
- [프로젝트 및 솔루션 속성 관리](managing-project-and-solution-properties.md)
- [Visual Studio의 필터링된 솔루션](filtered-solutions.md)
- [프로젝트 포팅, 마이그레이션 및 업그레이드](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio IDE 오류 문제 해결을 위한 리소스](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [프로젝트 및 솔루션(Mac용 Visual Studio)](/visualstudio/mac/projects-and-solutions)