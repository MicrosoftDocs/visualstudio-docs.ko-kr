---
title: '연습: 웹 파트를 표시 하는 서버 탐색기 확장 | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52dc3f418c3e86e126cbcf196fca2cf73fad35b2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583855"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>연습: 서버 탐색기 확장 하 여 웹 파트 표시
  Visual Studio에서는 **서버 탐색기** 의 **sharepoint 연결** 노드를 사용 하 여 sharepoint 사이트의 구성 요소를 볼 수 있습니다. 그러나 **서버 탐색기** 는 기본적으로 일부 구성 요소를 표시 하지 않습니다. 이 연습에서는 연결 된 각 SharePoint 사이트에 웹 파트 갤러리를 표시 하도록 **서버 탐색기** 를 확장 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 다음과 같은 방법으로 **서버 탐색기** 를 확장 하는 Visual Studio 확장을 만듭니다.

  - 확장은 **서버 탐색기**의 각 SharePoint 사이트 노드 아래에 **웹 파트 갤러리** 노드를 추가 합니다. 이 새 노드에는 사이트의 웹 파트 갤러리에 있는 각 웹 파트를 나타내는 자식 노드가 포함 되어 있습니다.

  - 확장은 웹 파트 인스턴스를 나타내는 노드의 새 형식을 정의 합니다. 이 새 노드 형식은 새 **웹 파트 갤러리** 노드 아래에 있는 자식 노드의 기반이 됩니다. 새 웹 파트 노드 형식은 속성이 나타내는 웹 파트에 대 한 정보를 **속성** 창에 표시 합니다. 노드 형식에는 웹 파트와 관련 된 다른 작업을 수행 하기 위한 시작 지점으로 사용할 수 있는 사용자 지정 바로 가기 메뉴 항목도 포함 되어 있습니다.

- 확장 어셈블리가 호출 하는 두 개의 사용자 지정 SharePoint 명령을 만듭니다. SharePoint 명령은 SharePoint 용 서버 개체 모델에서 Api를 사용 하기 위해 확장 어셈블리에서 호출할 수 있는 메서드입니다. 이 연습에서는 개발 컴퓨터의 로컬 SharePoint 사이트에서 웹 파트 정보를 검색 하는 명령을 만듭니다. 자세한 내용은 [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.

- 확장을 배포 하는 VSIX (Visual Studio Extension) 패키지를 빌드합니다.

- 확장을 디버깅 하 고 테스트 합니다.

> [!NOTE]
> 서버 개체 모델 대신 SharePoint 용 클라이언트 개체 모델을 사용 하는이 연습에 대 한 대체 버전은 [연습: 서버 탐색기 확장에서 sharepoint 클라이언트 개체 모델 호출](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)을 참조 하세요.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 완료 하려면 개발 컴퓨터에서 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Windows, SharePoint 및 Visual Studio

- Visual Studio SDK입니다. 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 프로젝트 항목을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

  다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- SharePoint 용 서버 개체 모델 사용 자세한 내용은 [SharePoint Foundation 서버 쪽 개체 모델 사용](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14))을 참조 하세요.

- SharePoint 솔루션의 웹 파트. 자세한 내용은 [웹 파트 개요](/previous-versions/office/ms432401(v=office.14))를 참조 하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 다음 세 개의 프로젝트를 만들어야 합니다.

- 확장을 배포할 VSIX 패키지를 만드는 VSIX 프로젝트입니다.

- 확장을 구현 하는 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 .NET Framework 4.5를 대상으로 해야 합니다.

- 사용자 지정 SharePoint 명령을 정의 하는 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 the.NET Framework 3.5를 대상으로 해야 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

    > [!NOTE]
    > **확장성** 노드는 VISUAL Studio SDK를 설치 하는 경우에만 사용할 수 있습니다. 자세한 내용은이 항목의 앞부분에 있는 전제 조건 섹션을 참조 하세요.

4. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택 합니다.

5. **VSIX 프로젝트** 템플릿을 선택 하 고 프로젝트 이름을 **webpartnode**로 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**솔루션 탐색기**에 **webpartnode** 프로젝트를 추가 합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 한 다음 **Windows** 노드를 선택 합니다.

3. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 4.5** 을 선택 합니다.

4. 프로젝트 템플릿 목록에서 **클래스 라이브러리**를 선택 하 고 프로젝트의 이름을 **webpartnodeextension**으로 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 솔루션에 **Webpartnodeextension** 프로젝트를 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint 명령 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 한 다음 **Windows** 노드를 선택 합니다.

3. 대화 상자의 맨 위에서 .NET Framework 버전 목록에서 **.NET Framework 3.5** 을 선택 합니다.

4. 프로젝트 템플릿 목록에서 **클래스 라이브러리**를 선택 하 고 프로젝트 이름을 **webpartcommands**로 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 솔루션에 **Webpartcommands** 프로젝트를 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-projects"></a>프로젝트 구성
 확장을 만드는 코드를 작성 하기 전에 코드 파일 및 어셈블리 참조를 추가 하 고 프로젝트 설정을 구성 해야 합니다.

#### <a name="to-configure-the-webpartnodeextension-project"></a>WebPartNodeExtension 프로젝트를 구성 하려면

1. WebPartNodeExtension 프로젝트에서 다음 이름을 가진 4 개의 코드 파일을 추가 합니다.

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. **Webpartnodeextension** 프로젝트에 대 한 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

3. **참조 관리자-WebPartNodeExtension** 대화 상자에서 **프레임 워크** 탭을 선택한 후 다음 각 어셈블리에 대 한 확인란을 선택 합니다.

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. **확장** 탭을 선택 하 고 VisualStudio 어셈블리에 대 한 확인란을 선택한 다음 **확인** 단추를 선택 합니다.

5. **솔루션 탐색기**에서 **webpartnodeextension** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

     **프로젝트 디자이너**가 열립니다.

6. **애플리케이션** 탭을 선택합니다.

7. **기본 네임 스페이스** 상자 (c #) 또는 **루트 네임 스페이스** 상자 ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] )에 **serverexplorer 노드**를 입력 합니다.

#### <a name="to-configure-the-webpartcommands-project"></a>Webpartcommands 프로젝트를 구성 하려면

1. WebPartCommands 프로젝트에서 WebPartCommands 라는 코드 파일을 추가 합니다.

2. **솔루션 탐색기**에서 **webpartcommands** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **기존 항목**을 선택 합니다.

3. **기존 항목 추가** 대화 상자에서 WebPartNodeExtension 프로젝트에 대 한 코드 파일이 포함 된 폴더를 찾은 다음, Webpartnodeextension 및 WebPartCommandIds 코드 파일을 선택 합니다.

4. **추가** 단추 옆의 화살표를 선택 하 고 표시 되는 메뉴에서 **링크로 추가** 를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 코드 파일을 WebPartCommands 프로젝트에 링크로 추가 합니다. 결과적으로 코드 파일은 WebPartNodeExtension 프로젝트에 있지만 파일의 코드도 WebPartCommands 프로젝트에서 컴파일됩니다.

5. **Webpartcommands** 프로젝트에 대 한 바로 가기 메뉴를 다시 열고 **참조 추가**를 선택 합니다.

6. **참조 관리자-WebPartCommands** 대화 상자에서 **확장** 탭을 선택 하 고 다음 각 어셈블리에 대 한 확인란을 선택한 다음 **확인** 단추를 선택 합니다.

    - Microsoft SharePoint

    - VisualStudio.

7. **솔루션 탐색기**에서 **webpartcommands** 프로젝트에 대 한 바로 가기 메뉴를 다시 열고 **속성**을 선택 합니다.

     **프로젝트 디자이너**가 열립니다.

8. **애플리케이션** 탭을 선택합니다.

9. **기본 네임 스페이스** 상자 (c #) 또는 **루트 네임 스페이스** 상자 ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] )에 **serverexplorer 노드**를 입력 합니다.

## <a name="create-icons-for-the-new-nodes"></a>새 노드에 대 한 아이콘 만들기
 **서버 탐색기** 확장에 대해 두 개의 아이콘을 만듭니다. 새 **웹 파트 갤러리** 노드의 아이콘 및 **웹 파트 갤러리** 노드 아래에 있는 각 자식 웹 파트 노드에 대 한 다른 아이콘을 만듭니다. 이 연습 뒷부분에서는 이러한 아이콘을 노드와 연결 하는 코드를 작성 합니다.

#### <a name="to-create-icons-for-the-nodes"></a>노드에 대 한 아이콘을 만들려면

1. **솔루션 탐색기**에서 **webpartnodeextension** 프로젝트에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

2. **프로젝트 디자이너**가 열립니다.

3. **리소스** 탭을 선택 하 고 **이 프로젝트에 기본 리소스 파일이 포함 되어 있지 않습니다 .를 선택 합니다. 링크를 하나 만들려면 여기를 클릭** 하십시오.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 리소스 파일을 만들어 디자이너에서 엽니다.

4. 디자이너 맨 위에서 **리소스 추가** 메뉴 명령 옆의 화살표를 선택한 다음 나타나는 메뉴에서 **새 아이콘 추가** 를 선택 합니다.

5. **새 리소스 추가** 대화 상자에서 새 아이콘의 이름을 **webpartsnode**로 지정한 다음 **추가** 단추를 선택 합니다.

     새 아이콘이 **이미지 편집기**에 열립니다.

6. 쉽게 인식할 수 있는 디자인이 포함 되도록 16x16 버전의 아이콘을 편집 합니다.

7. 32x32 버전의 아이콘에 대 한 바로 가기 메뉴를 열고 **이미지 형식 삭제**를 선택 합니다.

8. 5 ~ 8 단계를 반복 하 여 프로젝트 리소스에 두 번째 아이콘을 추가 하 고이 아이콘의 이름을 **WebPart**로 추가 합니다.

9. **솔루션 탐색기**에서 **webpartnodeextension** 프로젝트의 **Resources** 폴더 아래에 있는 **webpartnodeextension**에 대 한 바로 가기 메뉴를 엽니다.

10. **속성** 창에서 **빌드 작업**옆의 화살표를 선택 하 고 표시 되는 메뉴에서 **포함 리소스** 를 선택 합니다.

11. **웹 파트 .ico**에 대해 마지막 두 단계를 반복 합니다.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기에 웹 파트 갤러리 노드 추가
 각 SharePoint 사이트 노드에 새 **웹 파트 갤러리** 노드를 추가 하는 클래스를 만듭니다. 새 노드를 추가 하기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . 노드에 자식 노드를 추가 하는 등 **서버 탐색기**에서 기존 노드의 동작을 확장 하려는 경우 언제 든 지이 인터페이스를 구현 합니다.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기에 웹 파트 갤러리 노드를 추가 하려면

1. WebPartNodeExtension 프로젝트에서 SiteNodeExtension 코드 파일을 열고 다음 코드를 붙여 넣습니다.

    > [!NOTE]
    > 이 코드를 추가 하면 프로젝트에 컴파일 오류가 발생할 수 있지만 이후 단계에서 코드를 추가 하면 사라집니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>웹 파트를 나타내는 노드 형식 정의
 웹 파트를 나타내는 새 노드 형식을 정의 하는 클래스를 만듭니다. Visual Studio는이 새 노드 유형을 사용 하 여 **웹 파트 갤러리** 노드 아래에 자식 노드를 표시 합니다. 각 자식 노드는 SharePoint 사이트의 단일 웹 파트를 나타냅니다.

 새 노드 형식을 정의 하기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . **서버 탐색기**에서 새 노드 형식을 정의 하려는 경우 언제 든 지이 인터페이스를 구현 합니다.

#### <a name="to-define-the-web-part-node-type"></a>웹 파트 노드 형식을 정의 하려면

1. WebPartNodeExtension 프로젝트에서 WebPartNodeTypeProvder 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>웹 파트 데이터 클래스 정의
 SharePoint 사이트의 단일 웹 파트에 대 한 데이터를 포함 하는 클래스를 정의 합니다. 이 연습 뒷부분에서는 사이트의 각 웹 파트에 대 한 데이터를 검색 한 다음이 클래스의 인스턴스에 데이터를 할당 하는 사용자 지정 SharePoint 명령을 만듭니다.

#### <a name="to-define-the-web-part-data-class"></a>웹 파트 데이터 클래스를 정의 하려면

1. WebPartNodeExtension 프로젝트에서 Webpartnodeextension 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>SharePoint 명령에 대 한 Id 정의
 사용자 지정 SharePoint 명령을 식별 하는 여러 문자열을 정의 합니다. 이러한 명령은이 연습의 뒷부분에서 구현 합니다.

#### <a name="to-define-the-command-ids"></a>명령 Id를 정의 하려면

1. WebPartNodeExtension 프로젝트에서 WebPartCommandIds 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>사용자 지정 SharePoint 명령 만들기
 Sharepoint 용 서버 개체 모델을 호출 하 여 SharePoint 사이트의 웹 파트에 대 한 데이터를 검색 하는 사용자 지정 명령을 만듭니다. 각 명령은가 적용 된 메서드입니다 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> .

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint 명령을 정의 하려면

1. WebPartCommands 프로젝트에서 WebPartCommands 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>검사점
 연습의이 시점에서 **웹 파트 갤러리** 노드와 SharePoint 명령에 대 한 모든 코드는 이제 프로젝트에 있습니다. 솔루션을 빌드하여 두 프로젝트가 오류 없이 컴파일되도록 해야 합니다.

#### <a name="to-build-the-solution"></a>솔루션을 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

    > [!WARNING]
    > 이 시점에서 VSIX 매니페스트 파일에 Author의 값이 없기 때문에 WebPartNode 프로젝트에 빌드 오류가 있을 수 있습니다. 이후 단계에서 값을 추가 하면이 오류가 사라집니다.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>확장을 배포할 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션의 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. 먼저 VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 빌드하여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-the-vsix-package"></a>VSIX 패키지를 구성 하려면

1. **솔루션 탐색기**에서 webpartnode 프로젝트 아래의 매니페스트 편집기에서 **source.extension.vsixmanifest** 파일을 엽니다.

     Source.extension.vsixmanifest 파일은 모든 VSIX 패키지에 필요한 source.extension.vsixmanifest 파일의 기반이 됩니다. 이 파일에 대 한 자세한 내용은 [VSIX 확장 스키마 1.0 참조](/previous-versions/dd393700(v=vs.110))를 참조 하세요.

2. **제품 이름** 상자에 **서버 탐색기에 대 한 웹 파트 갤러리 노드**를 입력 합니다.

3. **작성자** 상자에 **Contoso**를 입력 합니다.

4. **설명** 상자에를 입력 하 고 **서버 탐색기의 SharePoint 연결 노드에 사용자 지정 웹 파트 갤러리 노드를 추가 합니다. 이 확장은 사용자 지정 SharePoint 명령을 사용 하 여 서버 개체 모델을 호출 합니다.**

5. 편집기의 **자산** 탭을 선택한 다음 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

6. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값 `MefComponent` 은 source.extension.vsixmanifest 파일의 요소에 해당 합니다. 이 요소는 VSIX 패키지에 있는 확장 어셈블리의 이름을 지정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

7. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

8. **프로젝트** 목록에서 **webpartnodeextension** 을 선택 하 고 **확인** 단추를 선택 합니다.

9. 매니페스트 편집기에서 **새로 만들기** 단추를 다시 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

10. **유형** 상자에 **SharePoint. Commands**를 입력 합니다.

    > [!NOTE]
    > 이 요소는 Visual Studio 확장에 포함 하려는 사용자 지정 확장 프로그램을 지정 합니다. 자세한 내용은 [Asset 요소 (VSX 스키마)](/previous-versions/dd393737(v=vs.110))를 참조 하세요.

11. **원본** 목록에서 현재 솔루션 목록 항목 **의 A 프로젝트** 를 선택 합니다.

12. **프로젝트** 목록에서 **webpartcommands**를 선택한 다음 **확인** 단추를 선택 합니다.

13. 메뉴 모음에서 빌드 **Build**  >  **솔루션**빌드를 선택한 다음 솔루션이 오류 없이 컴파일되는지 확인 합니다.

14. 이제 WebPartNode 프로젝트에 대 한 빌드 출력 폴더에 WebPartNode .vsix 파일이 포함 되어 있는지 확인 합니다.

     기본적으로 빌드 출력 폴더는 .입니다. 프로젝트 파일을 포함 하는 폴더 아래의 \bin\Debug 폴더

## <a name="test-the-extension"></a>확장 테스트
 이제 **서버 탐색기**에서 새 **웹 파트 갤러리** 노드를 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 확장 디버깅을 시작 합니다. 그런 다음 실험적 인스턴스의 새 **웹 파트** 노드를 사용 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.

#### <a name="to-start-debugging-the-extension"></a>확장 디버깅을 시작 하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]관리자 자격 증명을 다시 시작 하 고 WebPartNode 솔루션을 엽니다.

2. WebPartNodeExtension 프로젝트에서 SiteNodeExtension 코드 파일을 연 다음 및 메서드의 첫 번째 코드 줄에 중단점을 추가 `NodeChildrenRequested` `CreateWebPartNodes` 합니다.

3. **F5** 키를 선택 하 여 디버깅을 시작 합니다.

     Visual Studio는 서버 Explorer\1.0에 대 한%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part 갤러리 노드 확장에 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-extension"></a>확장을 테스트 하려면

1. 실험적 인스턴스의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 메뉴 모음에서 **보기**  >  **서버 탐색기**를 선택 합니다.

2. 테스트에 사용 하려는 SharePoint 사이트가 **서버 탐색기**의 **sharepoint 연결** 노드 아래에 표시 되지 않는 경우 다음 단계를 수행 합니다.

    1. **서버 탐색기**에서 **SharePoint 연결**에 대 한 바로 가기 메뉴를 열고 **연결 추가**를 선택 합니다.

    2. **Sharepoint 연결 추가** 대화 상자에서 연결 하려는 sharepoint 사이트의 URL을 입력 한 다음 **확인** 단추를 선택 합니다.

         개발 컴퓨터에서 SharePoint 사이트를 지정 하려면을 입력 **http://localhost** 합니다.

3. 사이트의 URL을 표시 하는 사이트 연결 노드를 확장 한 다음 자식 사이트 노드 (예: **팀 사이트**)를 확장 합니다.

4. 메서드의 이전에 설정한 중단점에서 다른 인스턴스의 코드가 중지 되는지 확인 한 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] `NodeChildrenRequested` 다음 **F5 키** 를 선택 하 여 프로젝트를 계속 디버깅 합니다.

5. Visual Studio의 실험적 인스턴스에서 **웹 파트 갤러리** 라는 새 노드가 최상위 사이트 노드 아래에 나타나는지 확인 한 다음 **웹 파트 갤러리** 노드를 확장 합니다.

6. Visual Studio의 다른 인스턴스의 코드가 메서드에서 이전에 설정한 중단점에서 중지 되는지 확인 한 `CreateWebPartNodes` 다음 **F5** 키를 선택 하 여 계속 해 서 프로젝트를 디버깅 합니다.

7. Visual Studio의 실험적 인스턴스에서 연결 된 사이트의 모든 웹 파트 **서버 탐색기**의 **웹 파트 갤러리** 노드 아래에 나타나는지 확인 합니다.

8. **서버 탐색기**에서 웹 파트 중 하나에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

9. 디버깅 하는 인스턴스에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 웹 파트에 대 한 세부 정보가 **속성** 창에 표시 되는지 확인 합니다.

## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio에서 확장 제거
 확장 테스트를 마친 후 Visual Studio에서 확장을 제거 합니다.

#### <a name="to-uninstall-the-extension"></a>확장을 제거하려면

1. 실험적 인스턴스의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 메뉴 모음에서 **도구**  >  **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **서버 탐색기에 대 한 웹 파트 갤러리 노드 확장**을 선택한 다음 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 단추를 선택 하 여 확장을 제거할 것인지 확인 하 고 **지금 다시 시작** 단추를 선택 하 여 제거를 완료 합니다.

4. Visual Studio의 두 인스턴스를 모두 닫습니다 (이 경우에는 WebPartNode 솔루션이 열려 있는 Visual Studio의 인스턴스 및 실험적 인스턴스).

## <a name="see-also"></a>참고 항목
- [서버 탐색기의 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [연습: 서버 탐색기 확장에서 SharePoint 클라이언트 개체 모델 호출](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [아이콘에 대 한 이미지 편집기](/cpp/windows/image-editor-for-icons)
- [아이콘 또는 다른 이미지 만들기 아이콘에 대 한 이미지 편집기 &#40;&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)