---
title: 솔루션 및 프로젝트
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b1783adadd1bfab32bfbbdcfb5ae28df7c0aae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661190"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio의 솔루션 및 프로젝트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 앱, 애플리케이션, 웹 사이트, 웹앱, 스크립트, 플러그인 등을 만들 때 *프로젝트*에서 시작합니다. 논리적인 측면에서 프로젝트에는 모든 소스 코드 파일, 아이콘, 이미지, 데이터 파일 및 실행 가능한 프로그램 또는 웹 사이트로 컴파일되는 기타 모든 항목이 포함되어 있거나 컴파일을 수행하는 데 필요한 기타 항목이 포함되어 있습니다.  프로젝트에도 프로그램이 통신하는 여러 서비스 또는 구성 요소에 필요할 수 있는 모든 컴파일러 설정 및 기타 구성 파일이 포함되어 있습니다.

 리터럴 관점에서 프로젝트는 "포함"된 모든 항목의 경로 및 모든 빌드 설정과 함께 가상 폴더 계층 구조를 정의하는 XML 파일(*.vbproj, \*.csproj, \*.vcxproj)입니다. Visual Studio에서 프로젝트 파일은 솔루션 탐색기에서 프로젝트 내용 및 설정을 표시하는 데 사용됩니다. 프로젝트를 컴파일할 때 MSBuild 엔진은 프로젝트 파일을 사용하여 실행 파일을 만듭니다. 또한 다른 출력 제품으로 프로젝트를 사용자 지정할 수 있습니다.

 프로젝트는 논리적인 의미와 파일 시스템에서 *솔루션*내에 포함되어 있으며, 이 솔루션에는 빌드 정보, Visual Studio 창 설정 및 프로젝트와 관련이 없는 기타 파일과 함께 하나 이상의 프로젝트가 있을 수 있습니다. 리터럴 관점에서 솔루션은 자체 고유한 형식을 가진 텍스트 파일로, 일반적으로 것은 직접 편집할 수 없습니다.

 솔루션에는 프로젝트에 참여한 각 사용자에 대한 설정, 기본 설정 및 구성 정보를 저장하는 연결된 *.suo 파일이 있습니다.

 다음 다이어그램은 프로젝트와 솔루션 및 프로젝트와 솔루션에 논리적으로 포함된 항목 간의 관계를 보여줍니다.

 ![Visual Studio 프로젝트 및 솔루션](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 사용자 지정 프로젝트 및 항목 템플릿을 만들 수도 있습니다. 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조하세요.

## <a name="creating-new-projects"></a>새 프로젝트 만들기
 새 프로젝트를 만드는 가장 쉬운 방법은 사전 정의된 프로젝트 템플릿으로 시작하는 것입니다. 이 템플릿은 특정 프로그래밍 언어로 특정 유형의 애플리케이션이나 웹 사이트 만들기를 시작하는 미리 생성된 코드 파일, config 파일, 자산 및 설정 기본 세트로 구성되어 있습니다. 이러한 템플릿은 주 메뉴에서 **파일 &#124; 새로 만들기 &#124; 프로젝트** 또는 **파일 &#124; 새로 만들기 &#124; 웹 사이트**를 선택하면 표시되는 **새 프로젝트 대화 상자**에서 확인할 수 있습니다. 자세한 내용은 [Creating Solutions and Projects](../ide/creating-solutions-and-projects.md) 및  [NIB 템플릿에서 프로젝트 만들기](https://msdn.microsoft.com/7c36d86a-6b79-4480-8228-0f925f1204b2)를 참조하세요.

## <a name="managing-projects-in-solution-explorer"></a>솔루션 탐색기에서 프로젝트 관리
 새 프로젝트를 만든 후에 **솔루션 탐색기** 를 사용하여 프로젝트와 솔루션 및 연결된 항목을 보고 관리합니다. 다음 그림은 두 프로젝트가 포함되어 있으며, C# 솔루션을 사용하는 서버 탐색기를 보여줍니다.

 ![솔루션 탐색기](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>섹션 내용

- [솔루션 및 프로젝트 만들기](../ide/creating-solutions-and-projects.md)

- [프로젝트 항목 추가 및 제거](../ide/adding-and-removing-project-items.md)

- [프로젝트 및 솔루션 속성 관리](../ide/managing-project-and-solution-properties.md)

- [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md)

- [응용 프로그램 속성](../ide/application-properties.md)

- [어셈블리 및 매니페스트 서명 관리](../ide/managing-assembly-and-manifest-signing.md)

- [방법: 응용 프로그램 아이콘 지정 (Visual Basic, c #)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

- [특정 대상 .NET Framework 버전 지정](../ide/targeting-a-specific-dotnet-framework-version.md)

- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>관련 항목
 [Visual Studio IDE](../ide/visual-studio-ide.md)
