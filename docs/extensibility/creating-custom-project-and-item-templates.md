---
title: 사용자 지정 프로젝트 및 항목 템플릿 만들기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d520c92e84286ab05f13ad140a9e2e5a3454e09
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248578"
---
# <a name="create-custom-project-and-item-templates"></a>사용자 지정 프로젝트 및 항목 템플릿 만들기

Visual Studio SDK에는 사용자 지정 프로젝트 템플릿 및 사용자 지정 항목 템플릿을 만드는 프로젝트 템플릿이 포함되어 있습니다. 해당 템플릿은 몇 가지 일반적인 매개 변수 대체를 포함하며 zip 파일로 빌드합니다. 자동으로 배포되지 않으며 실험적 인스턴스에서는 사용할 수 없습니다. 생성된 zip 파일은 사용자 템플릿 디렉터리에 복사해야 합니다.

템플릿 생성 템플릿을 사용하면 더 큰 확장에 템플릿을 포함할 수 있습니다. 따라서 소스 파일의 버전 제어를 구현하고 템플릿 프로젝트 그룹을 하나의 VSIX 패키지로 빌드할 수 있습니다.

NuGet 패키지를 설치할 템플릿을 구성할 수도 있습니다. 자세한 내용은 [Visual Studio 템플릿의 NuGet 패키지](/nuget/visual-studio-extensibility/visual-studio-templates)를 참조하세요.

기본 템플릿 생성 시나리오에서는 압축 파일로 출력되는 **템플릿 내보내기** 마법사를 사용해야 합니다. 기본 템플릿 만들기에 대한 자세한 내용은 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조하세요.

> [!NOTE]
> Visual Studio 2017부터 사용자 지정 프로젝트 및 항목 템플릿 검색을 더 이상 수행하지 않습니다. 대신 확장에서는 해당 템플릿의 설치 위치를 설명하는 템플릿 매니페스트 파일을 제공해야 합니다. Visual Studio 2017을 사용하여 VSIX 확장을 업데이트할 수 있습니다. MSI를 사용하여 확장을 배포하는 경우 템플릿 매니페스트 파일을 직접 생성해야 합니다. 자세한 내용은 [Visual Studio 2017용 사용자 지정 프로젝트 및 항목 템플릿 업그레이드](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)를 참조하세요. 템플릿 매니페스트 스키마는 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)에 설명되어 있습니다.

## <a name="create-a-project-template"></a>프로젝트 템플릿 만들기

1. 프로젝트 템플릿 프로젝트를 만듭니다. **새 프로젝트** 대화 상자에서 “프로젝트 템플릿”을 검색하고 C# 또는 Visual Basic 버전을 선택하여 프로젝트 템플릿을 찾을 수 있습니다.

     템플릿은 클래스 파일, 아이콘, *.vstemplate* 파일, *ProjectTemplate.vbproj* 또는 *ProjectTemplate.csproj*라는 편집 가능한 프로젝트 파일 및 일반적으로 기타 프로젝트 형식에서 생성되는 *resources.resx* 파일, *AssemblyInfo* 파일, *.settings* 파일 등의 몇몇 파일을 생성합니다. 각 코드 파일에는 해당하는 경우 일반 매개 변수 대체가 포함됩니다.

![프로젝트 템플릿 프로젝트 선택](media/project-template-selection.png)

2. 프로젝트의 필요에 따라 프로젝트에서 항목을 추가하거나 제거합니다. 편집 가능한 프로젝트 파일인 *AssemblyInfo* 파일 또는 *.vstemplate* 파일을 제거하지 마세요.

3. 추가 및 삭제를 반영하도록 *.vstemplate* 파일을 업데이트합니다. [Project](../extensibility/project-element-visual-studio-templates.md) 요소는 템플릿에 포함할 각 파일의 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소를 포함해야 합니다.

4. 코드 파일 및 기타 사용자 대상 콘텐츠를 수정하고 적절한 매개 변수 대체를 추가합니다.

5. 필요에 따라 생성된 콘텐츠를 수정합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio에서 템플릿을 포함하는 *.zip* 파일을 만듭니다. 해당 템플릿은 배포되지 않으며 실험적 인스턴스에서 사용할 수 없습니다.

## <a name="create-an-item-template"></a>항목 템플릿 만들기

1. 항목 템플릿 프로젝트를 만듭니다.

     해당 템플릿은 클래스 파일, 아이콘, *.vstemplate* 파일 및 *AssemblyInfo* 파일을 생성합니다. 클래스 파일에는 몇 가지 일반 매개 변수 대체가 포함됩니다.

2. 프로젝트의 필요에 따라 프로젝트에서 항목을 추가하거나 제거합니다.

3. 추가 및 삭제를 반영하도록 *.vstemplate* 파일을 업데이트합니다. [Project](../extensibility/project-element-visual-studio-templates.md) 요소는 템플릿에 포함할 각 파일의 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소를 포함해야 합니다.

4. 코드 파일 및 기타 사용자 대상 콘텐츠를 수정하고 적절한 매개 변수 대체를 추가합니다.

5. 필요에 따라 생성된 콘텐츠를 수정합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio에서 템플릿을 포함하는 압축 파일을 만듭니다. 해당 템플릿은 배포되지 않으며 실험적 인스턴스에서 사용할 수 없습니다.

## <a name="deployment"></a>배포

### <a name="to-deploy-the-project-or-item-template"></a>프로젝트 또는 항목 템플릿을 배포하려면

1. VSIX 프로젝트를 만듭니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조하세요.

2. VSIX 프로젝트를 시작 프로젝트로 설정합니다. **솔루션 탐색기**에서 VSIX 프로젝트 노드를 선택하고 누른 채(또는 마우스 오른쪽 단추로 클릭하고) **시작 프로젝트로 설정**을 선택합니다.

3. 프로젝트 템플릿 프로젝트를 VSIX 프로젝트의 자산으로 설정합니다. *.vsixmanifest* 파일을 엽니다. **자산** 탭으로 이동하고 **새로 만들기**를 선택합니다.

    1. **형식** 필드를 **Microsoft.VisualStudio.ProjectTemplate** 또는 **Microsoft.VisualStudio.ItemTemplate**으로 설정합니다.

    2. 소스에서 **현재 솔루션의 프로젝트** 옵션을 선택한 다음 해당 템플릿이 포함된 프로젝트를 선택합니다.

4. 솔루션을 빌드하고 **F5** 키를 누릅니다. 실험적 인스턴스가 나타납니다.

5. 프로젝트 템플릿 프로젝트의 경우 **새 프로젝트** 대화 상자(**파일** > **새로 만들기** > **프로젝트**)에서 Visual C# 또는 Visual Basic 노드에 프로젝트 템플릿이 표시됩니다. 항목 템플릿 프로젝트의 경우 **새 항목 추가** 대화 상자에 항목 템플릿이 표시됩니다. **새 항목 추가** 대화 상자를 보려면 **솔루션 탐색기**에서 프로젝트 노드를 선택하고 **추가** > **새 항목**을 선택합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio 템플릿 참조](../ide/creating-project-and-item-templates.md)
- [Visual Studio 템플릿의 NuGet 패키지](/nuget/visual-studio-extensibility/visual-studio-templates)
