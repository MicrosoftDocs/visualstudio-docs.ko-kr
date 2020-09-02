---
title: 사용자 지정 프로젝트 및 항목 템플릿 만들기
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197403"
---
# <a name="creating-custom-project-and-item-templates"></a>사용자 지정 프로젝트 및 항목 템플릿 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK에는 사용자 지정 프로젝트 템플릿 및 사용자 지정 항목 템플릿을 만드는 프로젝트 템플릿이 포함 되어 있습니다. 해당 템플릿은 몇 가지 일반적인 매개 변수 대체를 포함하며 zip 파일로 빌드합니다. 자동으로 배포되지 않으며 실험적 인스턴스에서는 사용할 수 없습니다. Zip 파일을 다음 위치에 복사 합니다.

템플릿 생성 템플릿을 사용하면 더 큰 확장에 템플릿을 포함할 수 있습니다. 확장에 템플릿을 포함 하면 소스 파일에 대 한 버전 제어를 구현 하 고 하나의 VSIX 패키지로 템플릿 프로젝트 그룹을 빌드할 수 있습니다.

기본 템플릿 생성 시나리오에서는 압축 파일로 출력되는 **템플릿 내보내기** 마법사를 사용해야 합니다. 기본 템플릿 만들기에 대 한 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조 하세요.

Visual Studio 2017부터 사용자 지정 프로젝트 및 항목 템플릿을 검색 하는 작업이 더 이상 수행 되지 않습니다. 대신 확장에서는 해당 템플릿의 설치 위치를 설명하는 템플릿 매니페스트 파일을 제공해야 합니다. 미리 보기 2 설치를 사용 하 여 VSIX 확장을 업데이트할 수 있습니다. MSI를 사용하여 확장을 배포하는 경우 템플릿 매니페스트 파일을 직접 생성해야 합니다. 자세한 내용은 [Upgrade Custom Visual Studio용 프로젝트 및 항목 템플릿 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015)을 참조 하세요. 템플릿 매니페스트 스키마는 [Visual Studio 템플릿 매니페스트 스키마 참조](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)에 설명 되어 있습니다.

## <a name="create-a-project-template"></a>프로젝트 템플릿 만들기

1. 프로젝트 템플릿 프로젝트를 만듭니다. **새 프로젝트** 대화 상자의 Visual Basic 또는 Visual c # **확장성** 폴더에서 프로젝트 템플릿을 찾을 수 있습니다.

     템플릿은 클래스 파일, 아이콘, .vstemplate 파일, ProjectTemplate.vbproj 또는 ProjectTemplate.csproj라는 편집 가능한 프로젝트 파일 및 일반적으로 기타 프로젝트 형식에서 생성되는 resources.resx 파일, AssemblyInfo 파일, .settings 파일 등의 몇몇 파일을 생성합니다. 각 코드 파일에는 해당하는 경우 일반 매개 변수 대체가 포함됩니다.

2. 프로젝트의 필요에 따라 프로젝트에서 항목을 추가하거나 제거합니다. 편집 가능한 프로젝트 파일인 AssemblyInfo 파일 또는 .vstemplate 파일을 제거하지 마세요.

3. 추가 및 삭제를 반영하도록 .vstemplate 파일을 업데이트합니다. [Project](../extensibility/project-element-visual-studio-templates.md) 요소는 템플릿에 포함할 각 파일의 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소를 포함해야 합니다.

4. 코드 파일 및 기타 사용자 대상 콘텐츠를 수정하고 적절한 매개 변수 대체를 추가합니다.

5. 필요에 따라 생성된 콘텐츠를 수정합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio에서 템플릿을 포함하는 .zip 파일을 만듭니다. 해당 템플릿은 배포되지 않으며 실험적 인스턴스에서 사용할 수 없습니다.

## <a name="create-an-item-template"></a>항목 템플릿 만들기

1. 항목 템플릿 프로젝트를 만듭니다.

     해당 템플릿은 클래스 파일, 아이콘, .vstemplate 파일 및 AssemblyInfo 파일을 생성합니다. 클래스 파일에는 몇 가지 일반 매개 변수 대체가 포함됩니다.

2. 프로젝트의 필요에 따라 프로젝트에서 항목을 추가하거나 제거합니다.

3. 추가 및 삭제를 반영하도록 .vstemplate 파일을 업데이트합니다. [Project](../extensibility/project-element-visual-studio-templates.md) 요소는 템플릿에 포함할 각 파일의 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소를 포함해야 합니다.

4. 코드 파일 및 기타 사용자 대상 콘텐츠를 수정하고 적절한 매개 변수 대체를 추가합니다.

5. 필요에 따라 생성된 콘텐츠를 수정합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio에서 템플릿을 포함하는 압축 파일을 만듭니다. 해당 템플릿은 배포되지 않으며 실험적 인스턴스에서 사용할 수 없습니다.

## <a name="deploy-the-project-or-item-template"></a>프로젝트 또는 항목 템플릿 배포

1. VSIX 프로젝트를 만듭니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조 하세요.

2. VSIX 프로젝트를 시작 프로젝트로 설정합니다. **솔루션 탐색기**에서 VSIX 프로젝트 노드를 선택하고 마우스 오른쪽 단추를 클릭하여 **시작 프로젝트로 설정**을 선택합니다.

3. 프로젝트 템플릿 프로젝트를 VSIX 프로젝트의 자산으로 설정합니다. .vsixmanifest 파일을 엽니다. **자산** 탭으로 이동 하 고 **새로 만들기**를 클릭 합니다.

    1. **형식** 필드를 **Microsoft.VisualStudio.ProjectTemplate** 또는 **Microsoft.VisualStudio.ItemTemplate**으로 설정합니다.

    2. 소스에서 **현재 솔루션의 프로젝트** 옵션을 선택한 다음 해당 템플릿이 포함된 프로젝트를 선택합니다.

4. 솔루션을 빌드하고 F5 키를 누릅니다. 실험적 인스턴스가 나타납니다.

5. 프로젝트 템플릿 프로젝트의 경우 **새 프로젝트** 대화 상자 (**파일/새로 만들기/프로젝트**)의 Visual c # 또는 Visual Basic 노드에 프로젝트 템플릿이 표시 되어야 합니다. 항목 템플릿 프로젝트의 경우 새 항목 추가 대화 상자에 나열 된 항목 템플릿이 표시 되어야 합니다. **솔루션 탐색기**에서 프로젝트 노드를 선택 하 고 **추가/새 항목**을 클릭 합니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio 템플릿 참조](../ide/visual-studio-template-reference.md)