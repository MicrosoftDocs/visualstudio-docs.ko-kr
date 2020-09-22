---
title: '연습: SharePoint 프로젝트 항목 형식 확장 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8186b1a1388745527fbb9f4dd37478942c36e62
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740008"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>연습: SharePoint 프로젝트 항목 형식 확장
  **비즈니스 데이터 연결 모델** 프로젝트 항목을 사용 하 여 SHAREPOINT의 BDC (비즈니스 데이터 연결) 서비스에 대 한 모델을 만들 수 있습니다. 기본적으로이 프로젝트 항목을 사용 하 여 모델을 만들 때 모델의 데이터는 사용자에 게 표시 되지 않습니다. 또한 사용자가 데이터를 볼 수 있도록 SharePoint에서 외부 목록을 만들어야 합니다.

 이 연습에서는 **비즈니스 데이터 연결 모델** 프로젝트 항목에 대 한 확장을 만듭니다. 개발자는 확장을 사용 하 여 BDC 모델의 데이터를 표시 하는 외부 목록을 프로젝트에 만들 수 있습니다. 이 연습에서는 다음 작업을 수행합니다.

- 두 가지 주요 작업을 수행 하는 Visual Studio 확장을 만듭니다.

  - BDC 모델의 데이터를 표시 하는 외부 목록을 생성 합니다. 확장 프로그램은 SharePoint 프로젝트 시스템의 개체 모델을 사용 하 여 목록을 정의 하는 *Elements.xml* 파일을 생성 합니다. 또한 BDC 모델과 함께 배포 되도록 프로젝트에 파일을 추가 합니다.

  - **솔루션 탐색기**의 **비즈니스 데이터 연결 모델** 프로젝트 항목에 바로 가기 메뉴 항목을 추가 합니다. 개발자는이 메뉴 항목을 클릭 하 여 BDC 모델의 외부 목록을 생성할 수 있습니다.

- VSIX (Visual Studio Extension) 패키지를 빌드하여 확장 어셈블리를 배포 합니다.

- 확장 테스트

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 완료 하려면 개발 컴퓨터에서 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Microsoft Windows, SharePoint 및 Visual Studio

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 프로젝트 항목을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

  다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- 의 BDC 서비스 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 입니다. 자세한 내용은 [BDC 아키텍처](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14))를 참조 하세요.

- BDC 모델에 대 한 XML 스키마입니다. 자세한 내용은 [BDC 모델 인프라](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14))를 참조 하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 다음과 같은 두 개의 프로젝트를 만들어야 합니다.

- Vsix 프로젝트를 만들어 프로젝트 항목 확장을 배포할 VSIX 패키지를 만듭니다.

- 프로젝트 항목 확장을 구현 하는 클래스 라이브러리 프로젝트입니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

    > [!NOTE]
    > **확장성** 노드는 VISUAL Studio SDK를 설치 하는 경우에만 사용할 수 있습니다. 자세한 내용은이 항목의 앞부분에 있는 전제 조건 섹션을 참조 하세요.

4. **새 프로젝트** 대화 상자의 맨 위에 있는 목록에서 **.NET Framework 4.5**을 선택 합니다.

     SharePoint 도구 확장에는이 버전의 .NET Framework 기능이 필요 합니다.

5. **VSIX 프로젝트** 템플릿을 선택 합니다.

6. **이름** 상자에 **GenerateExternalDataLists**를 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**솔루션 탐색기**에 **GenerateExternalDataLists** 프로젝트를 추가 합니다.

7. Source.extension.vsixmanifest 파일이 자동으로 열리지 않으면 GenerateExternalDataLists 프로젝트에서 바로 가기 메뉴를 연 다음 **열기** 를 선택 합니다.

8. Source.extension.vsixmanifest 파일에 Author 필드의 비어 있지 않은 항목 (Contoso 입력)이 있는지 확인 하 고 파일을 저장 한 다음 닫습니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에서 **GenerateExternalDataLists** 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트 추가** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **Windows** 노드를 선택 합니다.

3. 대화 상자 위쪽의 목록에서 **.NET Framework 4.5**을 선택 합니다.

4. 프로젝트 템플릿 목록에서 **클래스 라이브러리**를 선택 합니다.

5. **이름** 상자에 **BdcProjectItemExtension**를 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**BdcProjectItemExtension** 프로젝트를 솔루션에 추가 하 고 기본 Class1 코드 파일을 엽니다.

6. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트 구성
 프로젝트 항목 확장을 만드는 코드를 작성 하기 전에 확장 프로젝트에 코드 파일 및 어셈블리 참조를 추가 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. BdcProjectItemExtension 프로젝트에서 다음 이름의 두 코드 파일을 추가 합니다.

    - ProjectItemExtension

    - GenerateExternalDataLists

2. BdcProjectItemExtension 프로젝트를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **참조 추가**를 선택 합니다.

3. **어셈블리** 노드 아래에서 **프레임 워크** 노드를 선택 하 고 다음 어셈블리 각각의 확인란을 선택 합니다.

    - System.ComponentModel.Composition

    - WindowsBase

4. **어셈블리** 노드에서 **확장** 노드를 선택 하 고 다음 어셈블리에 대 한 확인란을 선택 합니다.

    - VisualStudio

5. **확인** 단추를 선택합니다.

## <a name="define-the-project-item-extension"></a>프로젝트 항목 확장 정의
 **비즈니스 데이터 연결 모델** 프로젝트 항목에 대 한 확장을 정의 하는 클래스를 만듭니다. 확장을 정의 하기 위해 클래스는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> . 기존 형식의 프로젝트 항목을 확장 하려는 경우 언제 든 지이 인터페이스를 구현 합니다.

#### <a name="to-define-the-project-item-extension"></a>프로젝트 항목 확장을 정의 하려면

1. 다음 코드를 ProjectItemExtension 코드 파일에 붙여 넣습니다.

    > [!NOTE]
    > 이 코드를 추가 하면 프로젝트에 컴파일 오류가 발생 합니다. 이러한 오류는 이후 단계에서 코드를 추가할 때 사라집니다.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>외부 데이터 목록 만들기
 `GenerateExternalDataListsExtension`BDC 모델의 각 엔터티에 대 한 외부 데이터 목록을 만드는 클래스의 부분 정의를 추가 합니다. 외부 데이터 목록을 만들기 위해이 코드는 먼저 BDC 모델 파일의 XML 데이터를 구문 분석 하 여 BDC 모델의 엔터티 데이터를 읽습니다. 그런 다음 BDC 모델을 기반으로 하는 목록 인스턴스를 만들고이 목록 인스턴스를 프로젝트에 추가 합니다.

#### <a name="to-create-the-external-data-lists"></a>외부 데이터 목록을 만들려면

1. 다음 코드를 GenerateExternalDataLists 코드 파일에 붙여 넣습니다.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>검사점
 연습의이 시점에서 프로젝트 항목 확장에 대 한 모든 코드가 이제 프로젝트에 있습니다. 솔루션을 빌드하여 프로젝트가 오류 없이 컴파일되는지 확인 합니다.

#### <a name="to-build-the-solution"></a>솔루션을 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>VSIX 패키지를 만들어 프로젝트 항목 확장 배포
 확장을 배포 하려면 솔루션의 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. 먼저 VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 빌드하여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 구성 하 고 만들려면

1. **솔루션 탐색기**에서 GenerateExternalDataLists 프로젝트의 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 **열기**를 선택 합니다.

     Visual Studio가 매니페스트 편집기에서 파일을 엽니다. Source.extension.vsixmanifest 파일은 모든 VSIX 패키지에 필요한 source.extension.vsixmanifest 파일의 기반이 됩니다. 이 파일에 대 한 자세한 내용은 [VSIX 확장 스키마 1.0 참조](/previous-versions/dd393700(v=vs.110))를 참조 하세요.

2. **제품 이름** 상자에 **외부 데이터 목록 생성기**를 입력 합니다.

3. **작성자** 상자에 **Contoso**를 입력 합니다.

4. **설명** 상자에 **외부 데이터 목록을 생성 하는 데 사용할 수 있는 비즈니스 데이터 연결 모델 프로젝트 항목의 확장명**을 입력 합니다.

5. 편집기의 **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

6. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값 `MefComponent` 은 source.extension.vsixmanifest 파일의 요소에 해당 합니다. 이 요소는 VSIX 패키지에 있는 확장 어셈블리의 이름을 지정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

7. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

8. **프로젝트** 목록에서 **BdcProjectItemExtension**를 선택한 다음 **확인** 단추를 선택 합니다.

9. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

10. 프로젝트가 오류 없이 컴파일되고 빌드 되었는지 확인 합니다.

11. 이제 GenerateExternalDataLists 프로젝트에 대 한 빌드 출력 폴더에 GenerateExternalDataLists 파일이 포함 되어 있는지 확인 합니다.

     기본적으로 빌드 출력 폴더는 .입니다. 프로젝트 파일을 포함 하는 폴더 아래의 \bin\Debug 폴더

## <a name="test-the-project-item-extension"></a>프로젝트 항목 확장 테스트
 이제 프로젝트 항목 확장을 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 확장 프로젝트 디버깅을 시작 합니다. 그런 다음 Visual Studio의 실험적 인스턴스에서 확장을 사용 하 여 BDC 모델의 외부 목록을 생성 합니다. 마지막으로 SharePoint 사이트에서 외부 목록을 열어 예상 대로 작동 하는지 확인 합니다.

#### <a name="to-start-debugging-the-extension"></a>확장 디버깅을 시작 하려면

1. 필요한 경우 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작한 다음 GenerateExternalDataLists 솔루션을 엽니다.

2. BdcProjectItemExtension 프로젝트에서 ProjectItemExtension 코드 파일을 연 다음 메서드의 코드 줄에 중단점을 추가 `Initialize` 합니다.

3. GenerateExternalDataLists 코드 파일을 연 다음 메서드의 첫 번째 코드 줄에 중단점을 추가 합니다 `GenerateExternalDataLists_Execute` .

4. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 하 여 디버깅을 시작 합니다.

     Visual Studio 는%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0에 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-extension"></a>확장을 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서, 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자에서 **템플릿** 노드를 확장 하 고 **Visual c #** 노드를 확장 한 다음 **SharePoint** 노드를 확장 하 고 **2010**을 선택 합니다.

3. 대화 상자 위쪽의 목록에서 **.NET Framework 3.5** 가 선택 되어 있는지 확인 합니다. 의 프로젝트에 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 는이 버전의 .NET Framework 필요 합니다.

4. 프로젝트 템플릿 목록에서 **SharePoint 2010 프로젝트**를 선택 합니다.

5. **이름** 상자에 **SharePointProjectTestBDC**를 입력 하 고 **확인** 단추를 선택 합니다.

6. SharePoint 사용자 지정 마법사에서 디버깅에 사용할 사이트의 URL을 입력 하 고 **팜 솔루션으로 배포**를 선택한 다음 **마침** 단추를 선택 합니다.

7. SharePointProjectTestBDC 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

8. **NewItem 추가-SharePointProjectTestBDC** 대화 상자에서 설치 된 언어 노드를 확장 하 고 **SharePoint** 노드를 확장 합니다.

9. **2010** 노드를 선택 하 고 **비즈니스 데이터 연결 모델 (팜 솔루션에만 해당)** 템플릿을 선택 합니다.

10. **이름** 상자에 **TestBDCModel**를 입력 한 다음 **추가** 단추를 선택 합니다.

11. ProjectItemExtension 코드 파일의 메서드에 설정 된 중단점에서 Visual Studio의 다른 인스턴스의 코드가 중지 되는지 확인 `Initialize` 합니다.

12. Visual Studio의 중지 된 인스턴스에서 **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **계속** 을 선택 하 여 프로젝트를 계속 디버깅 합니다.

13. Visual Studio의 실험적 인스턴스에서 **F5** 키를 선택 하거나, 메뉴 모음에서 **디버그**  >  **디버깅 시작** 을 선택 하 여 **TestBDCModel** 프로젝트를 빌드, 배포 및 실행 합니다.

     웹 브라우저가 디버깅을 위해 지정 된 SharePoint 사이트의 기본 페이지로 열립니다.

14. 빠른 실행 영역의 **목록** 섹션에 프로젝트의 기본 BDC 모델을 기반으로 하는 목록이 아직 포함 되어 있지 않은지 확인 합니다. 먼저 SharePoint 사용자 인터페이스를 사용 하거나 프로젝트 항목 확장을 사용 하 여 외부 데이터 목록을 만들어야 합니다.

15. 웹 브라우저를 닫습니다.

16. TestBDCModel 프로젝트가 열려 있는 Visual Studio 인스턴스에서 **솔루션 탐색기**의 **TestBDCModel** 노드에 대 한 바로 가기 메뉴를 열고 **외부 데이터 목록 생성**을 선택 합니다.

17. Visual Studio의 다른 인스턴스의 코드가 메서드에서 설정 하는 중단점에서 중지 되는지 확인 `GenerateExternalDataLists_Execute` 합니다. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **계속** 을 선택 하 여 프로젝트를 계속 디버깅 합니다.

18. Visual Studio의 실험적 인스턴스는 이름이 **Entity1DataList** 인 목록 인스턴스를 TestBDCModel 프로젝트에 추가 하 고, 인스턴스는 목록 인스턴스에 대해 이름이 **feature2>** 인 기능도 생성 합니다.

19. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작** 을 선택 하 여 TestBDCModel 프로젝트를 빌드, 배포 및 실행 합니다.

     웹 브라우저가 디버깅에 사용 되는 SharePoint 사이트의 기본 페이지를 엽니다.

20. 빠른 실행 영역의 **목록** 섹션에서 **Entity1DataList** 목록을 선택 합니다.

21. Identifier1 값이 0이 고 메시지 값이 Hello World 인 항목이 하나 뿐 아니라 이름이 Identifier1 및 Message 인 열이 목록에 포함 되어 있는지 확인 합니다.

     **비즈니스 데이터 연결 모델** 프로젝트 템플릿은이 모든 데이터를 제공 하는 기본 BDC 모델을 생성 합니다.

22. 웹 브라우저를 닫습니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 항목 확장 테스트를 마친 후에는 SharePoint 사이트에서 외부 목록과 BDC 모델을 제거 하 고 Visual Studio에서 프로젝트 항목 확장을 제거 합니다.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>SharePoint 사이트에서 외부 데이터 목록을 제거 하려면

1. SharePoint 사이트의 빠른 실행 영역에서 **Entity1DataList** 목록을 선택 합니다.

2. SharePoint 사이트의 리본에서 **목록** 탭을 선택 합니다.

3. **목록** 탭의 **설정** 그룹에서 **목록 설정**을 선택 합니다.

4. **사용 권한 및 관리**에서 **이 목록 삭제**를 선택 하 고 **확인** 을 선택 하 여 휴지통으로 목록을 보낼지 확인 합니다.

5. 웹 브라우저를 닫습니다.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>SharePoint 사이트에서 BDC 모델을 제거 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **빌드**  >  **취소**를 선택 합니다.

     Visual Studio는 SharePoint 사이트에서 BDC 모델을 제거 합니다.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Visual Studio에서 프로젝트 항목 확장을 제거 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **도구**  >  **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **외부 데이터 목록 생성기**를 선택한 다음 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 를 선택 하 여 확장을 제거할 것임을 확인 합니다.

4. **지금 다시 시작** 을 선택 하 여 제거를 완료 합니다.

5. Visual Studio의 두 인스턴스를 모두 닫습니다 (실험적 인스턴스와 GenerateExternalDataLists 솔루션이 열려 있는 인스턴스).

## <a name="see-also"></a>추가 정보
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)