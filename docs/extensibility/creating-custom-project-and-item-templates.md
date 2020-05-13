---
title: 사용자 지정 프로젝트 및 항목 템플릿 만들기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739458"
---
# <a name="create-custom-project-and-item-templates"></a>사용자 지정 프로젝트 및 항목 템플릿 만들기

Visual Studio SDK에는 사용자 지정 프로젝트 템플릿과 사용자 지정 항목 템플릿을 만드는 프로젝트 템플릿이 포함되어 있습니다. 이러한 템플릿에는 몇 가지 일반적인 매개 변수 대체가 포함되어 있으며 zip 파일로 빌드됩니다. 자동으로 배포되지 않으며 실험 인스턴스에서 사용할 수 없습니다. 생성된 zip 파일을 사용자 템플릿 디렉토리에 복사해야 합니다.

템플릿 만들기 템플릿을 사용하면 더 큰 확장에 템플릿을 포함할 수 있습니다. 이렇게 하면 원본 파일에 대한 버전 제어를 구현하고 템플릿 프로젝트 그룹을 하나의 VSIX 패키지로 빌드할 수 있습니다.

NuGet 패키지를 설치하도록 템플릿을 구성할 수도 있습니다. 자세한 내용은 [Visual Studio 템플릿의 NuGet 패키지를](/nuget/visual-studio-extensibility/visual-studio-templates)참조하십시오.

기본 템플릿 만들기 시나리오의 경우 압축된 파일에 출력되는 **템플릿 내보내기** 마법사를 사용해야 합니다. 기본 템플릿 만들기에 대한 자세한 내용은 [프로젝트 및 항목 템플릿 만들기를](../ide/creating-project-and-item-templates.md)참조하십시오.

> [!NOTE]
> Visual Studio 2017부터 는 사용자 지정 프로젝트 및 항목 템플릿에 대한 검색이 더 이상 수행되지 않습니다. 대신 확장은 이러한 템플릿의 설치 위치를 설명하는 템플릿 매니페스트 파일을 제공해야 합니다. Visual Studio 2017을 사용하여 VSIX 확장을 업데이트할 수 있습니다. If you deploy your extension using an MSI, you must generate the template manifest files by hand. 자세한 내용은 [Visual Studio 2017에 대한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드를](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)참조하십시오. 템플릿 매니페스트 스키마는 [Visual Studio 템플릿 매니페스트 스키마 참조에](../extensibility/visual-studio-template-manifest-schema-reference.md)설명되어 있습니다.

## <a name="create-a-project-template"></a>프로젝트 템플릿 만들기

1. 프로젝트 템플릿 프로젝트를 만듭니다. "프로젝트 템플릿"을 검색하고 C# 또는 Visual Basic 버전을 선택하여 **새 프로젝트** 대화 상자에서 프로젝트 템플릿을 찾을 수 있습니다.

     템플릿은 클래스 파일, 아이콘, *.vstemplate* 파일, *ProjectTemplate.vbproj* 또는 *ProjectTemplate.csproj라는*편집 가능한 프로젝트 파일 및 일반적으로 다른 프로젝트 유형(예: *resources.resx* 파일, *AssemblyInfo* 파일 및 *.settings 파일)에* 의해 생성되는 일부 파일을 생성합니다. 각 코드 파일에는 적절한 경우 공통 매개 변수 대체가 포함되어 있습니다.

![프로젝트 템플릿 프로젝트 선택](media/project-template-selection.png)

2. 프로젝트에 필요한 대로 프로젝트에서 항목을 추가하고 제거합니다. 편집 가능한 프로젝트 파일, *AssemblyInfo* 파일 또는 *.vstemplate* 파일을 제거하지 마십시오.

3. 추가 및 삭제를 반영하도록 *.vstemplate* 파일을 업데이트합니다. [프로젝트](../extensibility/project-element-visual-studio-templates.md) 요소에는 템플릿에 포함될 각 파일에 대한 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소가 포함되어야 합니다.

4. 코드 파일 및 기타 사용자 대면 콘텐츠를 수정하고 적절한 매개 변수 대체를 추가합니다.

5. 필요에 따라 생성된 콘텐츠를 수정합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio는 템플릿을 포함하는 *.zip* 파일을 만듭니다. 배포되지 않으며 실험 인스턴스에서 사용할 수 없습니다.

## <a name="create-an-item-template"></a>항목 템플릿 만들기

1. 항목 템플릿 프로젝트를 만듭니다.

     템플릿은 클래스 파일, 아이콘, *.vstemplate* 파일 및 *AssemblyInfo* 파일을 생성합니다. 클래스 파일에는 몇 가지 일반적인 매개 변수 대체가 포함되어 있습니다.

2. 프로젝트에 필요한 대로 프로젝트에서 항목을 추가하고 제거합니다.

3. 추가 및 삭제를 반영하도록 *.vstemplate* 파일을 업데이트합니다. [프로젝트](../extensibility/project-element-visual-studio-templates.md) 요소에는 템플릿에 포함될 각 파일에 대한 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소가 포함되어야 합니다.

4. 코드 파일 및 기타 사용자 대면 콘텐츠를 수정하고 적절한 매개 변수 대체를 추가합니다.

5. 필요에 따라 생성된 콘텐츠를 수정합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio는 템플릿을 포함하는 압축된 파일을 만듭니다. 배포되지 않으며 실험 인스턴스에서 사용할 수 없습니다.

## <a name="deployment"></a>배포

### <a name="to-deploy-the-project-or-item-template"></a>프로젝트 또는 항목 템플릿을 배포하려면

1. VSIX 프로젝트를 만듭니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조하십시오.

2. VSIX 프로젝트를 시작 프로젝트로 설정합니다. 솔루션 **탐색기에서**VSIX 프로젝트 노드를 선택하고 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정을**선택합니다.

3. 프로젝트 템플릿 프로젝트를 VSIX 프로젝트의 자산으로 설정합니다. *.vsixmanifest 파일을 엽니다.* **자산** 탭으로 이동하여 **새**을 클릭합니다.

    1. **입력** 필드를 **Microsoft.VisualStudio.ProjectTemplate** 또는 **Microsoft.VisualStudio.ItemTemplate로**설정합니다.

    2. 소스의 경우 **현재 솔루션 옵션에서 A 프로젝트를** 선택한 다음 템플릿이 포함된 프로젝트를 선택합니다.

4. 솔루션을 빌드하고 **F5를**누릅니다. 실험 인스턴스가 나타납니다.

5. 프로젝트 템플릿 프로젝트의 경우 새 **프로젝트** 대화 상자(새**New** > **프로젝트****파일)에** > 나열된 프로젝트 템플릿이 Visual C# 또는 Visual Basic 노드에 표시됩니다. 항목 템플릿 프로젝트의 경우 새 항목 **추가** 대화 상자에 나열된 항목 템플릿이 표시됩니다. **솔루션 탐색기에서** **새 항목 추가** 대화 상자를 보려면 프로젝트 노드를 선택하고 새**항목** **추가를** > 클릭합니다.

## <a name="see-also"></a>참조

- [비주얼 스튜디오 템플릿 참조](../ide/creating-project-and-item-templates.md)
- [비주얼 스튜디오 템플릿에서 NuGet 패키지](/nuget/visual-studio-extensibility/visual-studio-templates)
