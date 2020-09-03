---
title: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56fac2be1e73de5df9da8aa13e6631c4cc9d1022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015896"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기
  SharePoint 프로젝트를 배포할 때 Visual Studio는 일련의 배포 단계를 특정 순서로 실행 합니다. Visual Studio에는 다양 한 기본 제공 배포 단계가 포함 되어 있지만 직접 만들 수도 있습니다.

 이 연습에서는 SharePoint를 실행 하는 서버에서 솔루션을 업그레이드 하는 사용자 지정 배포 단계를 만듭니다. Visual Studio에는 솔루션을 취소 하거나 추가 하는 등의 많은 작업에 대 한 기본 제공 배포 단계가 포함 되어 있지만 솔루션 업그레이드에 대 한 배포 단계는 포함 되어 있지 않습니다. 기본적으로 SharePoint 솔루션을 배포 하는 경우 Visual Studio는 먼저 솔루션을 취소 하 고 (이미 배포 된 경우) 전체 솔루션을 다시 배포 합니다. 기본 제공 배포 단계에 대 한 자세한 내용은 [SharePoint 솔루션 패키지 배포, 게시 및 업그레이드](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)를 참조 하세요.

 이 연습에서는 다음 작업을 수행합니다.

- 두 가지 주요 작업을 수행 하는 Visual Studio 확장을 만듭니다.

  - 확장은 SharePoint 솔루션을 업그레이드 하는 사용자 지정 배포 단계를 정의 합니다.

  - 확장은 지정 된 프로젝트에 대해 실행 되는 배포 단계 집합인 새 배포 구성을 정의 하는 프로젝트 확장을 만듭니다. 새 배포 구성에는 사용자 지정 배포 단계와 몇 가지 기본 제공 배포 단계가 포함 되어 있습니다.

- 확장 어셈블리가 호출 하는 두 개의 사용자 지정 SharePoint 명령을 만듭니다. SharePoint 명령은 SharePoint 용 서버 개체 모델에서 Api를 사용 하기 위해 확장 어셈블리에서 호출할 수 있는 메서드입니다. 자세한 내용은 [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.

- VSIX (Visual Studio Extension) 패키지를 빌드하여 두 어셈블리를 모두 배포 합니다.

- 새 배포 단계를 테스트 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터에서 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Windows, SharePoint 및 Visual Studio

- Visual Studio SDK입니다. 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 확장을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

  다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- SharePoint 용 서버 개체 모델 사용 자세한 내용은 [SharePoint Foundation 서버 쪽 개체 모델 사용](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14))을 참조 하세요.

- SharePoint 솔루션. 자세한 내용은 [솔루션 개요](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14))를 참조 하세요.

- SharePoint 솔루션 업그레이드. 자세한 내용은 [솔루션 업그레이드](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14))를 참조 하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 다음 세 개의 프로젝트를 만들어야 합니다.

- 확장을 배포할 VSIX 패키지를 만드는 VSIX 프로젝트입니다.

- 확장을 구현 하는 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 .NET Framework 4.5를 대상으로 해야 합니다.

- 사용자 지정 SharePoint 명령을 정의 하는 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 .NET Framework 3.5를 대상으로 해야 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

    > [!NOTE]
    > **확장성** 노드는 VISUAL Studio SDK를 설치 하는 경우에만 사용할 수 있습니다. 자세한 내용은이 항목의 앞부분에 있는 전제 조건 섹션을 참조 하세요.

4. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택 합니다.

5. **VSIX 프로젝트** 템플릿을 선택 하 고 프로젝트의 이름을 **upgradedeploymentstep**으로 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**솔루션 탐색기**에 **upgradedeploymentstep** 프로젝트를 추가 합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에서 UpgradeDeploymentStep 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **Windows** 노드를 선택 합니다.

3. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택 합니다.

4. **클래스 라이브러리** 프로젝트 템플릿을 선택 하 고 프로젝트 이름을 **deploymentstepextension**으로 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Deploymentstepextension** 프로젝트를 솔루션에 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint 명령 프로젝트를 만들려면

1. **솔루션 탐색기**에서 UpgradeDeploymentStep 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic**을 확장 하 고 **Windows** 노드를 선택 합니다.

3. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 3.5** 을 선택 합니다.

4. **클래스 라이브러리** 프로젝트 템플릿을 선택 하 고 프로젝트 이름을 **SharePointCommands**로 지정한 다음 **확인** 단추를 선택 합니다.

     Visual Studio에서 솔루션에 **SharePointCommands** 프로젝트를 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-projects"></a>프로젝트 구성
 사용자 지정 배포 단계를 만드는 코드를 작성 하기 전에 코드 파일 및 어셈블리 참조를 추가 하 고 프로젝트를 구성 해야 합니다.

#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension 프로젝트를 구성 하려면

1. **Deploymentstepextension** 프로젝트에서 다음 이름의 두 코드 파일을 추가 합니다.

    - UpgradeStep

    - DeploymentConfigurationExtension

2. DeploymentStepExtension 프로젝트에서 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

3. **프레임 워크** 탭에서 system.componentmodel 어셈블리에 대 한 확인란을 선택 합니다.

4. **확장** 탭에서 VisualStudio 어셈블리에 대 한 확인란을 선택 하 고 **확인** 단추를 선택 합니다.

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands 프로젝트를 구성 하려면

1. **SharePointCommands** 프로젝트에서 명령 이라는 코드 파일을 추가 합니다.

2. **솔루션 탐색기**에서 **SharePointCommands** 프로젝트 노드의 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

3. **확장** 탭에서 다음 어셈블리에 대 한 확인란을 선택한 다음 **확인** 단추 선택을 클릭 합니다.

    - Microsoft SharePoint

    - VisualStudio.

## <a name="define-the-custom-deployment-step"></a>사용자 지정 배포 단계 정의
 업그레이드 배포 단계를 정의 하는 클래스를 만듭니다. 배포 단계를 정의 하기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> . 사용자 지정 배포 단계를 정의할 때마다이 인터페이스를 구현 합니다.

#### <a name="to-define-the-custom-deployment-step"></a>사용자 지정 배포 단계를 정의 하려면

1. **Deploymentstepextension** 프로젝트에서 upgradestep 코드 파일을 열고 다음 코드를 붙여넣습니다.

    > [!NOTE]
    > 이 코드를 추가 하면 프로젝트에 컴파일 오류가 발생할 수 있지만 이후 단계에서 코드를 추가 하면 사라집니다.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>사용자 지정 배포 단계를 포함 하는 배포 구성 만들기
 몇 가지 기본 제공 배포 단계와 새로운 업그레이드 배포 단계를 포함 하는 새 배포 구성에 대 한 프로젝트 확장을 만듭니다. 이 확장을 만들면 SharePoint 개발자가 SharePoint 프로젝트의 업그레이드 배포 단계를 사용 하는 데 도움이 됩니다.

 배포 구성을 만들기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . SharePoint 프로젝트 확장을 만들 때마다이 인터페이스를 구현 합니다.

#### <a name="to-create-the-deployment-configuration"></a>배포 구성을 만들려면

1. **Deploymentstepextension** 프로젝트에서 deploymentstepextension 코드 파일을 열고 다음 코드를 붙여넣습니다.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>사용자 지정 SharePoint 명령 만들기
 SharePoint 용 서버 개체 모델을 호출 하는 두 개의 사용자 지정 명령을 만듭니다. 한 명령은 솔루션이 이미 배포 되어 있는지 여부를 확인 합니다. 다른 명령은 솔루션을 업그레이드 합니다.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint 명령을 정의 하려면

1. **SharePointCommands** 프로젝트에서 명령 코드 파일을 열고 다음 코드를 붙여넣습니다.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>검사점
 연습의이 시점에서 사용자 지정 배포 단계 및 SharePoint 명령에 대 한 모든 코드가 이제 프로젝트에 있습니다. 오류 없이 컴파일하도록 빌드 하세요.

#### <a name="to-build-the-projects"></a>프로젝트를 빌드하려면 다음을 수행하십시오.

1. **솔루션 탐색기**에서 **deploymentstepextension** 프로젝트에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.

2. **SharePointCommands** 프로젝트에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>확장을 배포할 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션의 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. 먼저 VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 빌드하여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 구성 하 고 만들려면

1. **솔루션 탐색기**의 **upgradedeploymentstep** 프로젝트에서 **source.extension.vsixmanifest** 파일에 대 한 바로 가기 메뉴를 열고 **열기**를 선택 합니다.

     Visual Studio가 매니페스트 편집기에서 파일을 엽니다. Source.extension.vsixmanifest 파일은 모든 VSIX 패키지에 필요한 source.extension.vsixmanifest 파일의 기반이 됩니다. 이 파일에 대 한 자세한 내용은 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)를 참조 하세요.

2. **제품 이름** 상자에 **SharePoint 프로젝트에 대 한 업그레이드 배포 단계**를 입력 합니다.

3. **작성자** 상자에 **Contoso**를 입력 합니다.

4. **설명** 상자에 **SharePoint 프로젝트에서 사용할 수 있는 사용자 지정 업그레이드 배포 단계**를 입력 합니다.

5. 편집기의 **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

6. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값 `MefComponent` 은 source.extension.vsixmanifest 파일의 요소에 해당 합니다. 이 요소는 VSIX 패키지에 있는 확장 어셈블리의 이름을 지정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

7. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

8. **프로젝트** 목록에서 **deploymentstepextension**을 선택 하 고 **확인** 단추를 선택 합니다.

9. 매니페스트 편집기에서 **새로 만들기** 단추를 다시 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

10. **유형** 목록에서 **SharePoint. Commands**를 입력 합니다.

    > [!NOTE]
    > 이 요소는 Visual Studio 확장에 포함 하려는 사용자 지정 확장 프로그램을 지정 합니다. 자세한 내용은 [Asset 요소 (VSX 스키마)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)를 참조 하세요.

11. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

12. **프로젝트** 목록에서 **SharePointCommands**를 선택한 다음 **확인** 단추를 선택 합니다.

13. 메뉴 모음에서 빌드 **Build**  >  **솔루션**빌드를 선택한 다음 솔루션이 오류 없이 컴파일되는지 확인 합니다.

14. UpgradeDeploymentStep 프로젝트에 대 한 빌드 출력 폴더에 이제 UpgradeDeploymentStep .vsix 파일이 포함 되어 있는지 확인 합니다.

     기본적으로 빌드 출력 폴더는 .입니다. 프로젝트 파일을 포함 하는 폴더 아래의 \bin\Debug 폴더

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>업그레이드 배포 단계 테스트 준비
 업그레이드 배포 단계를 테스트 하려면 먼저 SharePoint 사이트에 샘플 솔루션을 배포 해야 합니다. Visual Studio의 실험적 인스턴스에서 확장을 디버깅 하 여 시작 합니다. 그런 다음 배포 단계를 테스트 하는 데 사용할 목록 정의 및 목록 인스턴스를 만든 다음 SharePoint 사이트에 배포 합니다. 그런 다음 목록 정의 및 목록 인스턴스를 수정 하 고 다시 배포 하 여 기본 배포 프로세스에서 SharePoint 사이트의 솔루션을 덮어쓰는 방법을 보여 줍니다.

 이 연습의 뒷부분에서는 목록 정의 및 목록 인스턴스를 수정한 다음 SharePoint 사이트에서 업그레이드 합니다.

#### <a name="to-start-debugging-the-extension"></a>확장 디버깅을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작한 다음 UpgradeDeploymentStep 솔루션을 엽니다.

2. DeploymentStepExtension 프로젝트에서 UpgradeStep 코드 파일을 연 다음 및 메서드의 첫 번째 코드 줄에 중단점을 추가 `CanExecute` `Execute` 합니다.

3. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 하 여 디버깅을 시작 합니다.

4. Visual Studio는 SharePoint Projects\1.0에 대 한%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 배포 단계에 대 한 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 업그레이드 배포 단계를 테스트 합니다.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>목록 정의 및 목록 인스턴스를 사용 하 여 SharePoint 프로젝트를 만들려면

1. Visual Studio의 실험적 인스턴스에서, 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. 대화 상자의 맨 위에서 .NET Framework 버전 목록에 **.NET Framework 3.5** 이 표시 되는지 확인 합니다.

    및의 프로젝트에 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 는이 버전의 .NET Framework 필요 합니다.

4. 프로젝트 템플릿 목록에서 **SharePoint 2010 프로젝트**를 선택 하 고 프로젝트 이름을 **EmployeesListDefinition**로 지정한 다음 **확인** 단추를 선택 합니다.

5. **SharePoint 사용자 지정 마법사**에서 디버깅에 사용할 사이트의 URL을 입력 합니다.

6. **이 SharePoint 솔루션의 신뢰 수준**아래에서 **팜 솔루션으로 배포** 옵션 단추를 선택 합니다.

   > [!NOTE]
   > 업그레이드 배포 단계에서는 샌드박스가 적용 된 솔루션을 지원 하지 않습니다.

7. **마침** 단추를 선택합니다.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition 프로젝트를 만듭니다.

8. EmployeesListDefinition 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

9. **새 항목 추가-EmployeesListDefinition** 대화 상자에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

10. **목록** 항목 템플릿을 선택 하 고 **직원 목록의**이름을 지정한 다음 **추가** 단추를 선택 합니다.

     SharePoint 사용자 지정 마법사가 나타납니다.

11. **목록 설정 선택** 페이지에서 다음 설정을 확인 한 후 **마침** 단추를 선택 합니다.

    1. **직원 목록이** **목록에 대해 표시 하려는 이름** 상자에 나타납니다.

    2. **다음을 기준으로 사용자 지정 가능한 목록 만들기:** 옵션 단추를 선택 합니다.

    3. **기본 (비어 있음)** 은 다음을 **기준으로 사용자 지정 가능한 목록 만들기:** 목록에서 선택 합니다.

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 제목 열과 빈 단일 인스턴스를 사용 하 여 Employees 목록 항목을 만들고 목록 디자이너를 엽니다.

12. 목록 디자이너의 **열** 탭에서 **새 열 또는 기존 열 이름 입력** 행을 선택 하 고 **열 표시 이름** 목록에 다음 열을 추가 합니다.

    1. 이름

    2. 회사

    3. 회사 전화

    4. 전자 메일

13. 모든 파일을 저장 한 다음 목록 디자이너를 닫습니다.

14. **솔루션 탐색기**에서 **직원 목록** 노드를 확장 한 다음 **employees list Instance** 자식 노드를 확장 합니다.

15. *Elements.xml* 파일에서이 파일의 기본 xml을 다음 xml로 바꿉니다. 이 XML은 목록 이름을 **직원** 으로 변경 하 고 승 Hance 이라는 직원에 게 정보를 추가 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
        <Data>
          <Rows>
            <Row>
              <Field Name="Title">Hance</Field>
              <Field Name="FirstName">Jim</Field>
              <Field Name="Company">Contoso</Field>
              <Field Name="Business Phone">555-555-5555</Field>
              <Field Name="E-Mail">jim@contoso.com</Field>
            </Row>
          </Rows>
        </Data>
      </ListInstance>
    </Elements>
    ```

16. *Elements.xml* 파일을 저장 한 후 닫습니다.

17. EmployeesListDefinition 프로젝트에 대 한 바로 가기 메뉴를 열고 **열기** 또는 **속성**을 선택 합니다.

     속성 디자이너가 열립니다.

18. **SharePoint** 탭에서 **디버깅 후 자동 취소** 확인란의 선택을 취소 한 다음 속성을 저장 합니다.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>목록 정의 및 목록 인스턴스를 배포 하려면

1. **솔루션 탐색기**에서 **EmployeesListDefinition** 프로젝트 노드를 선택 합니다.

2. **속성** 창에서 **활성 배포 구성** 속성이 **기본값으로**설정 되어 있는지 확인 합니다.

3. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 합니다.

4. 프로젝트가 성공적으로 빌드되고, 웹 브라우저가 SharePoint 사이트에 열리고, 빠른 실행 표시줄의 **목록** 항목에 새 **직원** 목록이 포함 되 고, **직원** 목록에 승 Hance에 대 한 항목이 포함 되어 있는지 확인 합니다.

5. 웹 브라우저를 닫습니다.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>목록 정의 및 목록 인스턴스를 수정 하 고 다시 배포 하려면

1. EmployeesListDefinition 프로젝트에서 **Employee List Instance** 프로젝트 항목의 자식인 *Elements.xml* 파일을 엽니다.

2. `Data`요소와 해당 자식을 제거 하 여 목록에서 승 Hance의 항목을 제거 합니다.

     완료 되 면 파일은 다음 XML을 포함 해야 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
      </ListInstance>
    </Elements>
    ```

3. *Elements.xml* 파일을 저장 한 후 닫습니다.

4. **Employees 목록** 프로젝트 항목에 대 한 바로 가기 메뉴를 열고 **열기** 또는 **속성**을 선택 합니다.

5. 목록 디자이너에서 **보기** 탭을 선택 합니다.

6. **선택한 열** 목록에서 **첨부 파일**을 선택 하 고 < 키를 선택 하 여 해당 열을 **사용 가능한 열** 목록으로 이동 합니다.

7. 이전 단계를 반복 하 여 **선택한 열** 목록의 **근무처 Phone** 열을 **사용 가능한 열** 목록으로 이동 합니다.

     이 작업을 수행 하면 SharePoint 사이트에 있는 **Employees** 목록의 기본 보기에서 이러한 필드가 제거 됩니다.

8. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 하 여 디버깅을 시작 합니다.

9. **배포 충돌** 대화 상자가 표시 되는지 확인 합니다.

     이 대화 상자는 Visual Studio에서 솔루션이 이미 배포 된 SharePoint 사이트에 솔루션 (목록 인스턴스)을 배포 하려고 할 때 표시 됩니다. 이 대화 상자는이 연습의 뒷부분에서 업그레이드 배포 단계를 실행할 때 표시 되지 않습니다.

10. **배포 충돌** 대화 상자에서 **자동으로 확인** 옵션 단추를 선택 합니다.

     Visual Studio에서 SharePoint 사이트의 목록 인스턴스를 삭제 하 고 프로젝트에 목록 항목을 배포한 다음 SharePoint 사이트를 엽니다.

11. 빠른 실행 표시줄의 **목록** 섹션에서 **직원** 목록을 선택 하 고 다음 세부 정보를 확인 합니다.

    - **첨부 파일** 및 **집 전화** 열이 목록 보기에 표시 되지 않습니다.

    - 목록이 비어 있습니다. **기본** 배포 구성을 사용 하 여 솔루션을 다시 배포 하는 경우 **직원** 목록이 프로젝트의 비어 있는 새 목록으로 대체 되었습니다.

## <a name="test-the-deployment-step"></a>배포 단계 테스트
 이제 업그레이드 배포 단계를 테스트할 준비가 되었습니다. 먼저 SharePoint의 목록 인스턴스에 항목을 추가 합니다. 그런 다음 목록 정의 및 목록 인스턴스를 변경 하 고, SharePoint 사이트에서 업그레이드 하 고, 업그레이드 배포 단계가 새 항목을 덮어쓰지 않는지 확인 합니다.

#### <a name="to-manually-add-an-item-to-the-list"></a>목록에 항목을 수동으로 추가 하려면

1. SharePoint 사이트의 리본 메뉴에 있는 **목록 도구** 탭에서 **항목** 탭을 선택 합니다.

2. **새** 그룹에서 **새 항목**을 선택 합니다.

     또는 항목 목록 자체에서 **새 항목 추가** 링크를 선택할 수 있습니다.

3. **직원-새 항목** 창의 **제목** 상자에 **시설 관리자**를 입력 합니다.

4. **이름** 상자에 **Andy**을 입력 합니다.

5. **회사** 상자에 **Contoso**를 입력 합니다.

6. **저장** 단추를 선택 하 고, 목록에 새 항목이 표시 되는지 확인 한 다음, 웹 브라우저를 닫습니다.

     이 연습의 뒷부분에서는이 항목을 사용 하 여 업그레이드 배포 단계가이 목록의 콘텐츠를 덮어쓰지 않는지 확인 합니다.

#### <a name="to-test-the-upgrade-deployment-step"></a>업그레이드 배포 단계를 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서 **솔루션 탐색기**의 **EmployeesListDefinition** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

    속성 편집기/디자이너가 열립니다.

2. **SharePoint** 탭에서 **활성 배포 구성** 속성을 **업그레이드**로 설정 합니다.

    이 사용자 지정 배포 구성에는 새로운 업그레이드 배포 단계가 포함 되어 있습니다.

3. **Employees 목록** 프로젝트 항목에 대 한 바로 가기 메뉴를 열고 **속성** 또는 **열기**를 선택 합니다.

    속성 편집기/디자이너가 열립니다.

4. **보기** 탭에서 **전자 메일** 열을 선택 하 고 키를 선택 **<** 하 여 해당 열을 **선택한 열** 목록에서 **사용 가능한 열** 목록으로 이동 합니다.

    이 작업을 수행 하면 SharePoint 사이트에 있는 **Employees** 목록의 기본 보기에서 이러한 필드가 제거 됩니다.

5. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 하 여 디버깅을 시작 합니다.

6. 메서드의 이전에 설정한 중단점에서 Visual Studio의 다른 인스턴스의 코드가 중지 되는지 확인 `CanExecute` 합니다.

7. **F5** 키를 다시 선택 하거나 메뉴 모음에서 **디버그**  >  **계속**을 선택 합니다.

8. 메서드의 이전에 설정한 중단점에서 코드가 중지 되는지 확인 `Execute` 합니다.

9. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **계속** 을 마지막 시간으로 선택 합니다.

     웹 브라우저가 SharePoint 사이트를 엽니다.

10. 빠른 실행 영역의 **목록** 섹션에서 **직원** 목록을 선택 하 고 다음 세부 정보를 확인 합니다.

    - 이전에 수동으로 추가한 항목 (Andy, 시설 관리자)은 여전히 목록에 있습니다.

    - 이 목록 보기에는 **회사 전화** 및 **전자 메일 주소** 열이 표시 되지 않습니다.

      **업그레이드** 배포 구성은 SharePoint 사이트의 기존 **Employees** 목록 인스턴스를 수정 합니다. **업그레이드** 구성 대신 **기본** 배포 구성을 사용 하는 경우 배포 충돌이 발생할 수 있습니다. **직원** 목록을 바꿔서 Visual Studio에서 충돌을 해결 하 고, Andy에 대 한 항목 (시설 관리자)을 삭제 합니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 업그레이드 배포 단계의 테스트를 마친 후에는 SharePoint 사이트에서 목록 인스턴스 및 목록 정의를 제거 하 고 Visual Studio에서 배포 단계 확장을 제거 합니다.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>SharePoint 사이트에서 목록 인스턴스를 제거 하려면

1. 목록이 아직 열려 있지 않은 경우 SharePoint 사이트에서 **Employees** 목록을 엽니다.

2. SharePoint 사이트의 리본에서 **목록 도구** 탭을 선택 하 고 **목록** 탭을 선택 합니다.

3. **설정** 그룹에서 **목록 설정** 항목을 선택 합니다.

4. **사용 권한 및 관리**에서 **이 목록 삭제** 명령을 선택 하 고 **확인** 을 선택 하 여 휴지통으로 목록을 보낼지 확인 한 다음 웹 브라우저를 닫습니다.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>SharePoint 사이트에서 목록 정의를 제거 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **빌드**  >  **취소**를 선택 합니다.

     Visual Studio는 SharePoint 사이트에서 목록 정의를 취소 합니다.

#### <a name="to-uninstall-the-extension"></a>확장을 제거하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **도구**  >  **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **SharePoint 프로젝트의 배포 단계 업그레이드**를 선택 하 고 **제거** 명령을 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 를 선택 하 여 확장을 제거할 것인지 확인 하 고 **지금 다시 시작** 을 선택 하 여 제거를 완료 합니다.

4. Visual Studio의 두 인스턴스를 모두 닫습니다 (UpgradeDeploymentStep 솔루션이 열려 있는 Visual Studio의 인스턴스 및 실험적 인스턴스).

## <a name="see-also"></a>추가 정보
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
