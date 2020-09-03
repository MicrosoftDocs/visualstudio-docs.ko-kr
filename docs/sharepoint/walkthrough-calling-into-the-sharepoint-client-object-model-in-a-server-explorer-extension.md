---
title: '서버 탐색기: SharePoint 연결 노드 확장'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ebd7d500767e896ce9576a3d007a4357b9c5281c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014632"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>연습: 서버 탐색기 확장에서 SharePoint 클라이언트 개체 모델 호출
  이 연습에서는 **서버 탐색기**의 **sharepoint 연결** 노드에 대 한 확장에서 sharepoint 클라이언트 개체 모델을 호출 하는 방법을 보여 줍니다. SharePoint 클라이언트 개체 모델을 사용 하는 방법에 대 한 자세한 내용은 [sharepoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.

 이 연습에서는 다음 작업을 수행합니다.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **서버 탐색기** 의 **SharePoint 연결** 노드를 확장 하는 확장을 만드는 방법은 다음과 같습니다.

  - 확장은 **서버 탐색기**의 각 SharePoint 사이트 노드 아래에 **웹 파트 갤러리** 노드를 추가 합니다. 이 새 노드에는 사이트의 웹 파트 갤러리에 있는 각 웹 파트를 나타내는 자식 노드가 포함 되어 있습니다.

  - 확장은 웹 파트 인스턴스를 나타내는 노드의 새 형식을 정의 합니다. 이 새 노드 형식은 새 **웹 파트 갤러리** 노드 아래에 있는 자식 노드의 기반이 됩니다. 새 웹 파트 노드 형식은 노드가 나타내는 웹 파트에 대 한 정보를 **속성** 창에 표시 합니다.

- 확장을 배포 하는 VSIX (Visual Studio Extension) 패키지를 빌드합니다.

- 확장을 디버깅 하 고 테스트 합니다.

> [!NOTE]
> 이 연습에서 만드는 확장 프로그램은 [연습: 서버 탐색기 확장 하 여 웹 파트를 표시 하](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)는 확장명과 비슷합니다. 이 연습에서는 SharePoint 서버 개체 모델을 사용 하지만이 연습에서는 클라이언트 개체 모델을 사용 하 여 동일한 작업을 수행 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터에서 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Windows, SharePoint 및 Visual Studio

- Visual Studio SDK입니다. 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 확장을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- SharePoint 클라이언트 개체 모델 사용 자세한 내용은 [관리 되는 클라이언트 개체 모델](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14))을 참조 하세요.

- SharePoint의 웹 파트 자세한 내용은 [웹 파트 개요](/previous-versions/office/ms432401(v=office.14))를 참조 하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 다음과 같은 두 개의 프로젝트를 만들어야 합니다.

- **서버 탐색기** 확장을 배포할 vsix 패키지를 만드는 vsix 프로젝트입니다.

- **서버 탐색기** 확장을 구현 하는 클래스 라이브러리 프로젝트입니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **확장성**을 선택 합니다.

    > [!NOTE]
    > **확장성** 노드는 VISUAL Studio SDK를 설치 하는 경우에만 사용할 수 있습니다. 자세한 내용은이 항목의 앞부분에 있는 전제 조건 섹션을 참조 하세요.

4. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택 합니다.

     SharePoint 도구 확장에는이 버전의 .NET Framework 기능이 필요 합니다.

5. **VSIX 프로젝트** 템플릿을 선택 합니다.

6. **이름** 상자에 **webpartnode**를 입력 한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**솔루션 탐색기**에 **webpartnode** 프로젝트를 추가 합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **Windows**를 선택 합니다.

3. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택 합니다.

4. 프로젝트 템플릿 목록에서 **클래스 라이브러리**를 선택 합니다.

5. **이름** 상자에 **webpartnodeextension**을 입력 한 후 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 솔루션에 **Webpartnodeextension** 프로젝트를 추가 하 고 기본 Class1 코드 파일을 엽니다.

6. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트 구성
 확장을 만드는 코드를 작성 하기 전에 프로젝트에 코드 파일과 어셈블리 참조를 추가 하 고 기본 네임 스페이스를 업데이트 해야 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. **Webpartnodeextension** 프로젝트에서 이름이 SiteNodeExtension 및 WebPartNodeTypeProvider 인 두 개의 코드 파일을 추가 합니다.

2. WebPartNodeExtension 프로젝트에 대 한 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

3. **참조 관리자-WebPartNodeExtension** 대화 상자에서 **프레임 워크** 노드를 선택 하 고 system.componentmodel 및 system.xml 어셈블리에 대 한 확인란을 선택 합니다.

4. **확장** 노드를 선택 하 고 다음 각 어셈블리에 대 한 확인란을 선택한 다음 **확인** 단추를 선택 합니다.

    - Microsoft. SharePoint. 클라이언트

    - Microsoft. SharePoint. Runtime

    - VisualStudio

5. **Webpartnodeextension** 프로젝트에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

     **프로젝트 디자이너**가 열립니다.

6. **애플리케이션** 탭을 선택합니다.

7. **기본 네임 스페이스** 상자 (c #) 또는 **루트 네임 스페이스** 상자 (Visual Basic)에서 **serverexplorer. SharePointConnections 노드**를 입력 합니다.

## <a name="create-icons-for-the-new-nodes"></a>새 노드에 대 한 아이콘 만들기
 **서버 탐색기** 확장에 대해 두 개의 아이콘을 만듭니다. 새 **웹 파트 갤러리** 노드의 아이콘 및 **웹 파트 갤러리** 노드 아래의 각 자식 웹 파트 노드에 대 한 다른 아이콘을 만듭니다. 이 연습 뒷부분에서는 이러한 아이콘을 노드와 연결 하는 코드를 작성 합니다.

#### <a name="to-create-icons-for-the-nodes"></a>노드에 대 한 아이콘을 만들려면

1. WebPartNodeExtension 프로젝트용 **프로젝트 디자이너** 에서 **리소스** 탭을 선택 합니다.

2. **이 프로젝트에 기본 리소스 파일이 포함 되지 않은 링크를 선택 합니다. 만들려면 여기를 클릭 하십시오.**

     Visual Studio에서 리소스 파일을 만들어 디자이너에서 엽니다.

3. 디자이너 맨 위에서 **리소스 추가** 메뉴 명령에 있는 화살표를 선택한 다음 **새 아이콘 추가**를 선택 합니다.

4. 새 아이콘 이름에 대해 **Webpartsnode** 를 입력 한 다음 **추가** 단추를 선택 합니다.

     새 아이콘이 **이미지 편집기**에 열립니다.

5. 쉽게 인식할 수 있는 디자인이 포함 되도록 16x16 버전의 아이콘을 편집 합니다.

6. 32x32 버전의 아이콘에 대 한 바로 가기 메뉴를 열고 **이미지 형식 삭제**를 선택 합니다.

7. 3 ~ 7 단계를 반복 하 여 프로젝트 리소스에 두 번째 아이콘을 추가 하 고이 아이콘의 이름을 **WebPart**로 추가 합니다.

8. **솔루션 탐색기**의 **webpartnodeextension** 프로젝트에 대 한 **리소스** 폴더에서 *webpartnodeextension*를 선택 합니다.

9. **속성** 창에서 **빌드 작업** 목록을 연 다음 **포함 리소스**를 선택 합니다.

10. *웹 파트 .ico*에 대해 마지막 두 단계를 반복 합니다.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기에 웹 파트 갤러리 노드 추가
 각 SharePoint 사이트 노드에 새 **웹 파트 갤러리** 노드를 추가 하는 클래스를 만듭니다. 새 노드를 추가 하기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . 노드에 새 자식 노드를 추가 하는 등 **서버 탐색기**에서 기존 노드의 동작을 확장 하려는 경우 언제 든 지이 인터페이스를 구현 합니다.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기에 웹 파트 갤러리 노드를 추가 하려면

1. 다음 코드를 **Webpartnodeextension** 프로젝트용 **SiteNodeExtension** 코드 파일에 붙여 넣습니다.

    > [!NOTE]
    > 이 코드를 추가 하면 프로젝트에 컴파일 오류가 발생 합니다. 이러한 오류는 이후 단계에서 코드를 추가할 때 사라집니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>웹 파트를 나타내는 노드 형식 정의
 웹 파트를 나타내는 새 노드 형식을 정의 하는 클래스를 만듭니다. Visual Studio는이 새 노드 유형을 사용 하 여 **웹 파트 갤러리** 노드 아래에 자식 노드를 표시 합니다. 이러한 각 자식 노드는 SharePoint 사이트의 단일 웹 파트를 나타냅니다.

 새 노드 형식을 정의 하기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . **서버 탐색기**에서 새 노드 형식을 정의 하려는 경우 언제 든 지이 인터페이스를 구현 합니다.

#### <a name="to-define-the-web-part-node-type"></a>웹 파트 노드 형식을 정의 하려면

1. **Webpartnodeextension** 프로젝트용 **Webpartnodetypeprovider** 코드 파일에 다음 코드를 붙여넣습니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>검사점
 연습의이 시점에서 **웹 파트 갤러리** 노드의 모든 코드는 이제 프로젝트에 있습니다. **Webpartnodeextension** 프로젝트를 빌드하여 오류 없이 컴파일되는지 확인 합니다.

#### <a name="to-build-the-project"></a>프로젝트를 빌드하려면

1. **솔루션 탐색기**에서 **webpartnodeextension** 프로젝트에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>확장을 배포할 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션의 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. 먼저 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 빌드하여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-the-vsix-package"></a>VSIX 패키지를 구성 하려면

1. **솔루션 탐색기**에서 **webpartnode** 프로젝트의 매니페스트 편집기에서 **source.extension.vsixmanifest** 파일을 엽니다.

     Source.extension.vsixmanifest 파일은 모든 VSIX 패키지에 필요한 source.extension.vsixmanifest 파일의 기반이 됩니다. 이 파일에 대 한 자세한 내용은 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)를 참조 하세요.

2. **제품 이름** 상자에 **서버 탐색기에 대 한 웹 파트 갤러리 노드**를 입력 합니다.

3. **작성자** 상자에 **Contoso**를 입력 합니다.

4. **설명** 상자에를 입력 하 고 **서버 탐색기의 SharePoint 연결 노드에 사용자 지정 웹 파트 갤러리 노드를 추가**합니다.

5. 편집기의 **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

6. **새 자산 추가** 대화 상자의 **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값 `MefComponent` 은 source.extension.vsixmanifest 파일의 요소에 해당 합니다. 이 요소는 VSIX 패키지에 있는 확장 어셈블리의 이름을 지정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

7. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

8. **프로젝트** 목록에서 **webpartnodeextension**을 선택 하 고 **확인** 단추를 선택 합니다.

9. 메뉴 모음에서 빌드 **Build**  >  **솔루션**빌드를 선택한 다음 솔루션이 오류 없이 컴파일되는지 확인 합니다.

10. 이제 WebPartNode 프로젝트에 대 한 빌드 출력 폴더에 WebPartNode .vsix 파일이 포함 되어 있는지 확인 합니다.

     기본적으로 빌드 출력 폴더는 .입니다. 프로젝트 파일을 포함 하는 폴더 아래의 \bin\Debug 폴더

## <a name="test-the-extension"></a>확장 테스트
 이제 **서버 탐색기**에서 새 **웹 파트 갤러리** 노드를 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 확장 프로젝트 디버깅을 시작 합니다. 그런 다음 Visual Studio의 실험적 인스턴스에서 새 **웹 파트** 노드를 사용 합니다.

#### <a name="to-start-debugging-the-extension"></a>확장 디버깅을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작한 다음 **Webpartnode** 솔루션을 엽니다.

2. WebPartNodeExtension 프로젝트에서 **SiteNodeExtension** 코드 파일을 연 다음 및 메서드의 첫 번째 코드 줄에 중단점을 추가 `NodeChildrenRequested` `CreateWebPartNodes` 합니다.

3. **F5** 키를 선택 하 여 디버깅을 시작 합니다.

     Visual Studio는 서버 Explorer\1.0에 대 한%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part 갤러리 노드 확장에 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-extension"></a>확장을 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 서버 탐색기 **보기**를 선택  >  **Server Explorer**합니다.

2. 테스트에 사용 하려는 SharePoint 사이트가 **서버 탐색기**의 **sharepoint 연결** 노드 아래에 나타나는지 확인 합니다. 나열 되지 않은 경우 다음 단계를 수행 합니다.

    1. **SharePoint 연결**에 대 한 바로 가기 메뉴를 열고 **연결 추가**를 선택 합니다.

    2. **Sharepoint 연결 추가** 대화 상자에서 연결 하려는 sharepoint 사이트의 URL을 입력 한 다음 **확인** 단추를 선택 합니다.

         개발 컴퓨터에서 SharePoint 사이트를 지정 하려면을 입력 **http://localhost** 합니다.

3. 사이트의 URL을 표시 하는 사이트 연결 노드를 확장 한 다음 자식 사이트 노드 (예: **팀 사이트**)를 확장 합니다.

4. Visual Studio의 다른 인스턴스의 코드가 메서드에서 이전에 설정한 중단점에서 중지 되는지 확인 한 `NodeChildrenRequested` 다음 **F5** 키를 선택 하 여 계속 해 서 프로젝트를 디버깅 합니다.

5. Visual Studio의 실험적 인스턴스에서 최상위 사이트 노드 아래에 표시 되는 **웹 파트 갤러리** 노드를 확장 합니다.

6. Visual Studio의 다른 인스턴스의 코드가 메서드에서 이전에 설정한 중단점에서 중지 되는지 확인 한 `CreateWebPartNodes` 다음 **F5** 키를 선택 하 여 계속 해 서 프로젝트를 디버깅 합니다.

7. Visual Studio의 실험적 인스턴스에서 연결 된 사이트의 모든 웹 파트 **서버 탐색기**의 **웹 파트 갤러리** 노드 아래에 표시 되는지 확인 합니다.

8. 웹 파트에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

9. **속성** 창에서 웹 파트에 대 한 세부 정보가 표시 되는지 확인 합니다.

10. **서버 탐색기**에서 동일한 웹 파트에 대 한 바로 가기 메뉴를 열고 **메시지 표시**를 선택 합니다.

     표시 되는 메시지 상자에서 **확인** 단추를 선택 합니다.

## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio에서 확장 제거
 확장 테스트를 마친 후 Visual Studio에서 제거 합니다.

#### <a name="to-uninstall-the-extension"></a>확장을 제거하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **도구**  >  **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **서버 탐색기에 대 한 웹 파트 갤러리 노드**를 선택 하 고 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 단추를 선택 합니다.

4. **지금 다시 시작** 단추를 선택 하 여 제거를 완료 합니다.

     프로젝트 항목도 제거 됩니다.

5. Visual Studio의 두 인스턴스를 모두 닫습니다 (이 경우에는 WebPartNode 솔루션이 열려 있는 Visual Studio의 인스턴스 및 실험적 인스턴스).

## <a name="see-also"></a>추가 정보
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [아이콘에 대 한 이미지 편집기](/cpp/windows/image-editor-for-icons)
- [아이콘 또는 다른 이미지 만들기 아이콘에 대 한 이미지 편집기 &#40;&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
