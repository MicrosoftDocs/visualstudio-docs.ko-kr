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
ms.openlocfilehash: 5c702aaaa51d86e2b8aac18a6b55201be03a635f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903324"
---
# <a name="create-custom-project-and-item-templates"></a>사용자 지정 프로젝트 및 항목 템플릿 만들기

Visual Studio SDK에는 사용자 지정 프로젝트 템플릿 및 사용자 지정 항목 템플릿을 만드는 프로젝트 템플릿이 포함 되어 있습니다. 이러한 템플릿에는 몇 가지 일반적인 매개 변수 대체가 포함 되며 zip 파일로 빌드됩니다. 자동으로 배포 되지 않으며 실험적 인스턴스에서 사용할 수 없습니다. 생성 된 zip 파일을 사용자 템플릿 디렉터리에 복사 해야 합니다.

템플릿 생성 템플릿을 사용 하면 더 큰 확장에 템플릿을 포함할 수 있습니다. 이렇게 하면 소스 파일에 대해 버전 제어를 구현 하 고 하나의 VSIX 패키지에 템플릿 프로젝트 그룹을 빌드할 수 있습니다.

NuGet 패키지를 설치 하도록 템플릿을 구성할 수도 있습니다. 자세한 내용은 [Visual Studio 템플릿의 NuGet 패키지](/nuget/visual-studio-extensibility/visual-studio-templates)를 참조 하세요.

기본 템플릿 생성 시나리오의 경우 압축 파일에 출력 되는 **템플릿 내보내기** 마법사를 사용 해야 합니다. 기본 템플릿 만들기에 대 한 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조 하세요.

> [!NOTE]
> Visual Studio 2017부터 사용자 지정 프로젝트 및 항목 템플릿을 검색 하는 작업이 더 이상 수행 되지 않습니다. 대신 확장은 이러한 템플릿의 설치 위치를 설명 하는 템플릿 매니페스트 파일을 제공 해야 합니다. Visual Studio 2017을 사용 하 여 VSIX 확장을 업데이트할 수 있습니다. MSI를 사용 하 여 확장을 배포 하는 경우 템플릿 매니페스트 파일을 직접 생성 해야 합니다. 자세한 내용은 [Visual Studio 2017에 대 한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)를 참조 하세요. 템플릿 매니페스트 스키마는 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)에 설명 되어 있습니다.

## <a name="create-a-project-template"></a>프로젝트 템플릿 만들기

1. 프로젝트 템플릿 프로젝트를 만듭니다. "프로젝트 템플릿"을 검색 하 고 c # 또는 Visual Basic 버전을 선택 하 여 **새 프로젝트** 대화 상자에서 프로젝트 템플릿을 찾을 수 있습니다.

     템플릿은 클래스 파일, 아이콘, *.vstemplate* 파일, *projecttemplate. .Vbproj* 또는 *projecttemplate .csproj*라는 편집 가능한 프로젝트 파일, 그리고 일반적으로 다른 프로젝트 형식에 의해 생성 되는 (예: *리소스 .resx* 파일, *AssemblyInfo* 파일 및 *설정* 파일) 일부 파일을 생성 합니다. 각 코드 파일에는 해당 하는 경우 공통 매개 변수 대체가 포함 됩니다.

![프로젝트 템플릿 프로젝트 선택](media/project-template-selection.png)

2. 프로젝트에 필요에 따라 프로젝트에서 항목을 추가 및 제거 합니다. 편집 가능한 프로젝트 파일, *AssemblyInfo* 파일 또는 *.vstemplate* 파일을 제거 하지 마십시오.

3. 추가 및 삭제를 반영 하도록 *.vstemplate* 파일을 업데이트 합니다. [프로젝트](../extensibility/project-element-visual-studio-templates.md) 요소는 템플릿에 포함할 각 파일에 대해 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소를 포함 해야 합니다.

4. 코드 파일 및 기타 사용자 지향 콘텐츠를 수정 하 고 적절 한 매개 변수 대체를 추가 합니다.

5. 필요에 따라 생성 된 콘텐츠를 수정 합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio에서 템플릿을 포함 하는 *.zip* 파일을 만듭니다. 배포 되지 않으며 실험적 인스턴스에서 사용할 수 없습니다.

## <a name="create-an-item-template"></a>항목 템플릿 만들기

1. 항목 템플릿 프로젝트를 만듭니다.

     템플릿은 클래스 파일, 아이콘, *.vstemplate* 파일 및 *AssemblyInfo* 파일을 생성 합니다. 클래스 파일에는 몇 가지 일반적인 매개 변수 대체가 포함 되어 있습니다.

2. 프로젝트에 필요에 따라 프로젝트에서 항목을 추가 및 제거 합니다.

3. 추가 및 삭제를 반영 하도록 *.vstemplate* 파일을 업데이트 합니다. [프로젝트](../extensibility/project-element-visual-studio-templates.md) 요소는 템플릿에 포함할 각 파일에 대해 [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) 요소를 포함 해야 합니다.

4. 코드 파일 및 기타 사용자 지향 콘텐츠를 수정 하 고 적절 한 매개 변수 대체를 추가 합니다.

5. 필요에 따라 생성 된 콘텐츠를 수정 합니다.

6. 프로젝트를 빌드합니다.

     Visual Studio에서 템플릿을 포함 하는 압축 된 파일을 만듭니다. 배포 되지 않으며 실험적 인스턴스에서 사용할 수 없습니다.

## <a name="deployment"></a>배포

### <a name="to-deploy-the-project-or-item-template"></a>프로젝트 또는 항목 템플릿을 배포 하려면

1. VSIX 프로젝트를 만듭니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조 하세요.

2. VSIX 프로젝트를 시작 프로젝트로 설정 합니다. **솔루션 탐색기**에서 VSIX 프로젝트 노드를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **시작 프로젝트로 설정**을 선택 합니다.

3. 프로젝트 템플릿 프로젝트를 VSIX 프로젝트의 자산으로 설정 합니다. *Source.extension.vsixmanifest* 파일을 엽니다. **자산** 탭으로 이동 하 고 **새로 만들기**를 클릭 합니다.

    1. **유형** 필드를 **VisualStudio** 또는 **VisualStudio**로 설정 합니다.

    2. 원본에서 **현재 솔루션의 프로젝트** 옵션을 선택한 다음 템플릿이 포함 된 프로젝트를 선택 합니다.

4. 솔루션을 빌드하고 **f5**키를 누릅니다. 실험적 인스턴스가 나타납니다.

5. 프로젝트 템플릿 프로젝트의 경우 **새** 프로젝트 대화 상자 (**파일**  >  **새로 만들기**  >  **프로젝트**)의 Visual c # 또는 Visual Basic 노드에 프로젝트 템플릿이 표시 되어야 합니다. 항목 템플릿 프로젝트의 경우 **새 항목 추가** 대화 상자에 나열 된 항목 템플릿이 표시 되어야 합니다. **새 항목 추가** 대화 상자를 보려면 **솔루션 탐색기**에서 프로젝트 노드를 선택 하 고 **Add**  >  **새 항목**추가를 클릭 합니다.

## <a name="see-also"></a>참조

- [Visual Studio 템플릿 참조](../ide/creating-project-and-item-templates.md)
- [Visual Studio 템플릿의 NuGet 패키지](/nuget/visual-studio-extensibility/visual-studio-templates)
