---
title: '연습: SharePoint 프로젝트 확장 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df10e2da9e6b4c31894dce0669e9aa0e580b92f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015082"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>연습: SharePoint 프로젝트 확장 만들기
  이 연습에서는 SharePoint 프로젝트용 확장을 만드는 방법을 보여 줍니다. 프로젝트 확장을 사용 하 여 프로젝트를 추가, 삭제 또는 이름을 바꿀 때와 같은 프로젝트 수준 이벤트에 응답할 수 있습니다. 또한 속성 값이 변경 될 때 사용자 지정 속성을 추가 하거나 응답할 수 있습니다. 프로젝트 항목 확장과 달리 프로젝트 확장은 특정 SharePoint 프로젝트 형식에 연결할 수 없습니다. 프로젝트 확장을 만들 때에서 모든 종류의 SharePoint 프로젝트를 열 때 확장이 로드 됩니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 이 연습에서는에서 만든 모든 SharePoint 프로젝트에 추가 되는 사용자 지정 부울 속성을 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . **True**로 설정 되 면 새 속성은 Images 리소스 폴더를 프로젝트에 추가 하거나 매핑합니다. **False**로 설정 하면 이미지 폴더가 있는 경우 제거 됩니다. 자세한 내용은 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)를 참조 하세요.

 이 연습에서는 다음 작업을 수행합니다.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]다음 작업을 수행 하는 SharePoint 프로젝트용 확장을 만듭니다.

  - 속성 창에 사용자 지정 프로젝트 속성을 추가 합니다. 속성은 모든 SharePoint 프로젝트에 적용 됩니다.

  - 는 SharePoint 프로젝트 개체 모델을 사용 하 여 매핑된 폴더를 프로젝트에 추가 합니다.

  - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]DTE (automation object model)를 사용 하 여 프로젝트에서 매핑된 폴더를 삭제 합니다.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]확장 (VSIX) 패키지를 빌드하여 프로젝트 속성의 확장 어셈블리를 배포 합니다.

- 프로젝트 속성 디버깅 및 테스트

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터에서 다음 구성 요소가 필요 합니다.

- [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint 및의 지원 되는 버전 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] 이 연습에서는의 **Vsix 프로젝트** 템플릿을 사용 하 여 [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] vsix 패키지를 만들어 프로젝트 속성 확장을 배포 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 다음과 같은 두 개의 프로젝트를 만들어야 합니다.

- Vsix 프로젝트를 만들어 프로젝트 확장을 배포할 VSIX 패키지를 만듭니다.

- 프로젝트 확장을 구현 하는 클래스 라이브러리 프로젝트입니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

    > [!NOTE]
    > 이 노드는 Visual Studio SDK를 설치한 경우에만 사용할 수 있습니다. 자세한 내용은이 항목의 앞부분에 있는 전제 조건 섹션을 참조 하세요.

4. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택한 다음 **VSIX 프로젝트** 템플릿을 선택 합니다.

5. **이름** 상자에 **projectextensionpackage**를 입력 한 후 **확인** 단추를 선택 합니다.

     **Projectextensionpackage** 프로젝트가 **솔루션 탐색기**에 나타납니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **Windows**를 선택 합니다.

3. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택한 다음 **클래스 라이브러리** 프로젝트 템플릿을 선택 합니다.

4. **이름** 상자에 **projectextension**을 입력 한 후 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Projectextension** 프로젝트를 솔루션에 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-project"></a>프로젝트 구성
 프로젝트 확장을 만드는 코드를 작성 하기 전에 확장 프로젝트에 코드 파일 및 어셈블리 참조를 추가 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. **Customproperty** 라는 코드 파일을 projectextension 프로젝트에 추가 합니다.

2. **Projectextension** 프로젝트에 대 한 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

3. **참조 관리자-CustomProperty** 대화 상자에서 **프레임 워크** 노드를 선택 하 고 system.componentmodel 및 system.object 어셈블리 옆의 확인란을 선택 합니다.

4. **확장** 노드를 선택 하 고 VisualStudio 및 EnvDTE 어셈블리 옆의 확인란을 선택한 다음 **확인** 단추를 선택 합니다.

5. **솔루션 탐색기**의 **projectextension** 프로젝트에 대 한 **References** 폴더 아래에서 **EnvDTE**를 선택 합니다.

6. **속성** 창에서 **Interop 형식 포함** 속성을 **False**로 변경 합니다.

## <a name="define-the-new-sharepoint-project-property"></a>새 SharePoint 프로젝트 속성 정의
 프로젝트 확장 및 새 프로젝트 속성의 동작을 정의 하는 클래스를 만듭니다. 새 프로젝트 확장을 정의 하기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . SharePoint 프로젝트에 대 한 확장을 정의 하려는 경우 언제 든 지이 인터페이스를 구현 합니다. 또한 클래스에를 추가 합니다 <xref:System.ComponentModel.Composition.ExportAttribute> . 이 특성 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 을 사용 하 여 구현을 검색 하 고 로드할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>형식을 특성의 생성자에 전달 합니다.

#### <a name="to-define-the-new-sharepoint-project-property"></a>새 SharePoint 프로젝트 속성을 정의 하려면

1. 다음 코드를 CustomProperty 코드 파일에 붙여 넣습니다.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>솔루션 빌드
 다음으로 솔루션을 빌드하여 오류 없이 컴파일되는지 확인 합니다.

#### <a name="to-build-the-solution"></a>솔루션을 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>VSIX 패키지를 만들어 프로젝트 속성 확장 배포
 프로젝트 확장을 배포 하려면 솔루션의 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. 먼저 VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 빌드하여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 구성 하 고 만들려면

1. **솔루션 탐색기**에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 연 다음 **열기** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 매니페스트 디자이너에서 파일을 엽니다. **메타 데이터** 탭에 표시 되는 정보는 **확장 및 업데이트**에도 표시 됩니다. 모든 VSIX 패키지에는 source.extension.vsixmanifest 파일이 필요 합니다. 이 파일에 대 한 자세한 내용은 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)를 참조 하세요.

2. **제품 이름** 상자에 **사용자 지정 프로젝트 속성**을 입력 합니다.

3. **작성자** 상자에 **Contoso**를 입력 합니다.

4. **설명** 상자에 **이미지 리소스 폴더의 매핑을 프로젝트로 전환 하는 사용자 지정 SharePoint 프로젝트 속성을**입력 합니다.

5. **자산** 탭을 선택한 다음 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

6. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값 `MEFComponent` 은 source.extension.vsixmanifest 파일의 요소에 해당 합니다. 이 요소는 VSIX 패키지에 있는 확장 어셈블리의 이름을 지정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

7. **원본** 목록에서 **현재 솔루션의 프로젝트** 옵션 단추를 선택 합니다.

8. **프로젝트** 목록에서 **projectextension**을 선택 합니다.

     이 값은 프로젝트에서 작성 하는 어셈블리의 이름을 식별 합니다.

9. **확인** 을 선택 하 여 **새 자산 추가** 대화 상자를 닫습니다.

10. 메뉴 모음에서 파일을 마치면 **파일**  >  **모두 저장** 을 선택한 다음 매니페스트 디자이너를 닫습니다.

11. 메뉴 모음에서 빌드 **Build**  >  **솔루션**빌드를 선택한 후 프로젝트가 오류 없이 컴파일되는지 확인 합니다.

12. **솔루션 탐색기**에서 **projectextensionpackage** 프로젝트에 대 한 바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기** 단추를 선택 합니다.

13. **파일 탐색기**에서 projectextensionpackage 프로젝트에 대 한 빌드 출력 폴더를 열고 폴더에 projectextensionpackage .vsix 라는 파일이 포함 되어 있는지 확인 합니다.

     기본적으로 빌드 출력 폴더는 .입니다. 프로젝트 파일을 포함 하는 폴더 아래의 \bin\Debug 폴더

## <a name="test-the-project-property"></a>프로젝트 속성 테스트
 이제 사용자 지정 프로젝트 속성을 테스트할 준비가 되었습니다. 의 실험적 인스턴스에서 새 프로젝트 속성 확장을 디버그 하 고 테스트 하는 것이 가장 쉽습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 이 인스턴스는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] VSIX 또는 기타 확장성 프로젝트를 실행할 때 생성 됩니다. 프로젝트를 디버깅 한 후에는 시스템에 확장을 설치한 다음의 일반 인스턴스에서 디버그 및 테스트를 계속할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Visual Studio의 실험적 인스턴스에서 확장을 디버그 하 고 테스트 하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]관리자 자격 증명으로 다시 시작 하 고 ProjectExtensionPackage 솔루션을 엽니다.

2. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 하 여 프로젝트의 디버그 빌드를 시작 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 프로젝트 Property\1.0에 확장을 설치 하 고의 실험적 인스턴스를 시작 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.

3. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 팜 솔루션에 대 한 SharePoint 프로젝트를 만들고 마법사의 다른 값에 대 한 기본값을 사용 합니다.

    1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

    2. **새 프로젝트** 대화 상자의 맨 위에 있는 .NET Framework 버전 목록에서 **.NET Framework 3.5** 를 선택 합니다.

         SharePoint 도구 확장에는이 버전의 기능이 필요 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] 합니다.

    3. **템플릿** 노드에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 하 고 **SharePoint** 노드를 선택한 다음 **2010** 노드를 선택 합니다.

    4. **SharePoint 2010 프로젝트** 템플릿을 선택 하 고 프로젝트 이름으로 **ModuleTest** 을 입력 합니다.

4. **솔루션 탐색기**에서 **ModuleTest** 프로젝트 노드를 선택 합니다.

     새 사용자 지정 속성 **맵 이미지 폴더가** **속성** 창에 표시 되며 기본값은 **False**입니다.

5. 해당 속성의 값을 **True**로 변경 합니다.

     이미지 리소스 폴더가 SharePoint 프로젝트에 추가 됩니다.

6. 해당 속성의 값을 다시 **False**로 변경 합니다.

     **이미지 폴더 삭제?** 대화 상자에서 **예** 단추를 선택 하면 이미지 리소스 폴더가 SharePoint 프로젝트에서 삭제 됩니다.

7. 실험적 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 인스턴스를 닫습니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 프로젝트 확장](../sharepoint/extending-sharepoint-projects.md)
- [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
