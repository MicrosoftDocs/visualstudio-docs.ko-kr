---
title: '연습: 애플리케이션 빌드 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2d9b958dacfb35877abc9ad1e83a349e43a7af0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74296866"
---
# <a name="walkthrough-building-an-application"></a>연습: 애플리케이션 빌드

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습을 완료하면 Visual Studio로 애플리케이션을 빌드할 때 구성할 수 있는 여러 옵션에 더 익숙해집니다. 다른 작업 중에 샘플 애플리케이션에 대한 사용자 지정 빌드 구성을 만들고, 특정 경고 메시지를 숨기고, 빌드 출력 정보를 늘립니다.

이 항목에는 다음과 같은 섹션이 포함되어 있습니다.

[샘플 응용 프로그램 설치](../ide/walkthrough-building-an-application.md)

[사용자 지정 빌드 구성 만들기](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)

[응용 프로그램 빌드](../ide/walkthrough-building-an-application.md#BKMK_building)

[컴파일러 경고 숨기기](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)

[출력 창에 추가 빌드 세부 정보 표시](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)

[릴리스 빌드 만들기](../ide/walkthrough-building-an-application.md)

#### <a name="to-install-the-sample-application"></a>샘플 애플리케이션을 설치하려면

1. 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택합니다.

2. **온라인** 범주를 선택하고 나서 **샘플 갤러리** 범주를 선택합니다.

3. 검색 상자에서 `Introduction`을 지정하여 샘플을 찾습니다.

    ![확장 및 업데이트 대화 상자](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")

4. 결과 목록에서 **Introduction to Building WPF Applications (Visual C#)**(WPF 애플리케이션 빌드 소개(Visual C#)) 또는 **Introduction to Building WPF Applications (Visual Basic)**(WPF 애플리케이션 빌드 소개(Visual Basic))를 선택합니다.

5. **다운로드** 단추를 선택하고 나서 **닫기** 단추를 선택합니다.

   Introduction to Building WPF Applications(WPF 애플리케이션 빌드 소개) 샘플이 **새 프로젝트** 대화 상자에 나타납니다.

#### <a name="to-create-a-solution-for-the-sample-application"></a>샘플 애플리케이션에 대한 솔루션을 만들려면

1. **새 프로젝트** 대화 상자를 엽니다.

     ![메뉴 모음에서 [파일], [새로 만들기], [프로젝트]를 선택합니다.](../ide/media/exploreide-filenewproject.png "Exploreide-newprojectcsharp-FileNewProject")

2. **설치됨** 범주에서 **샘플** 범주를 선택하여 Introduction to Building WPF Applications(WPF 애플리케이션 빌드 소개) 샘플을 표시합니다.

3. Visual C#의 경우 솔루션 이름을 `IntroWPFcsharp`로 지정합니다.

     ![새 프로젝트 대화 상자, 설치된 샘플](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")

     또는

     Visual Basic의 경우 솔루션 이름을 `IntroWPFvb`로 지정합니다.

     ![새 프로젝트 대화 상자, Visual Basic 샘플](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")

4. **확인** 단추를 선택합니다.

## <a name="create-a-custom-build-configuration"></a><a name="BKMK_CreateBuildConfig"></a> 사용자 지정 빌드 구성 만들기

솔루션을 만들면 솔루션에 대한 디버그 및 릴리스 빌드 구성과 해당 기본 플랫폼 대상이 자동으로 정의됩니다. 나중에 이러한 구성을 사용자 지정하거나 고유한 구성을 만들 수 있습니다. 빌드 구성은 빌드 형식을 지정합니다. 빌드 플랫폼은 애플리케이션이 해당 구성에 대한 대상으로 지정하는 운영 체제를 지정합니다. 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md), [빌드 플랫폼 이해](../ide/understanding-build-platforms.md) 및 [디버그 및 릴리스 프로젝트 구성](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)을 참조하세요.

**구성 관리자** 대화 상자를 사용하여 구성 및 플랫폼 설정을 변경하거나 만들 수 있습니다. 이 절차에서는 테스트용 빌드 구성을 만듭니다.

#### <a name="to-create-a-build-configuration"></a>빌드 구성을 만들려면

1. **구성 관리자** 대화 상자를 엽니다.

    ![빌드 메뉴, 구성 관리자 명령](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")

2. **활성 솔루션 구성** 목록에서 **새로 만들기**를 선택 합니다.

3. **새 솔루션 구성** 대화 상자에서 새 구성의 이름을 `Test`로 지정하고, 기존 디버그 구성에서 설정을 복사하고, **확인** 단추를 선택합니다.

    ![새 솔루션 구성 대화 상자](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")

4. **활성 솔루션 플랫폼** 목록에서 **새로 만들기**를 선택 합니다.

5. **새 솔루션 플랫폼** 대화 상자에서 **x64**를 선택 하 고 x86 플랫폼에서 설정을 복사 하지 않습니다.

    ![새 솔루션 플랫폼 대화 상자](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")

6. **확인** 단추를 선택합니다.

   활성 솔루션 구성이 Test로 변경되고 활성 솔루션 플랫폼이 x64로 설정되었습니다.

   ![테스트 구성이 있는 구성 관리자](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")

   **표준** 도구 상자에서 **솔루션 구성** 목록을 사용하여 활성 솔루션 구성을 빠르게 확인하거나 변경할 수 있습니다.

   ![솔루션 구성 옵션 표준 도구 모음](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")

## <a name="build-the-application"></a><a name="BKMK_building"></a> 응용 프로그램 빌드

다음에는 사용자 지정 빌드 구성을 사용하여 솔루션을 빌드합니다.

#### <a name="to-build-the-solution"></a>솔루션을 빌드하려면

- 메뉴 모음에서 **빌드**, **솔루션 빌드**를 선택합니다.

  **출력** 창에는 빌드 결과가 표시됩니다. 빌드에 성공했지만 여러 경고 메시지가 생성되었습니다.

  그림 1: Visual Basic 경고

  ![출력 창(Visual Basic)](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

  그림 2: Visual C# 경고

  ![출력 창 Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

## <a name="hide-compiler-warnings"></a><a name="BKMK_hidewarning"></a> 컴파일러 경고 숨기기

빌드 출력을 어지럽히지 않도록 빌드하는 동안 특정 경고 메시지를 일시적으로 숨길 수 있습니다.

#### <a name="to-hide-a-specific-visual-c-warning"></a>특정 Visual C# 경고를 숨기려면

1. **솔루션 탐색기**에서 최상위 프로젝트 노드를 선택합니다.

2. 메뉴 모음에서 **보기**, **속성 페이지**를 선택합니다.

     **프로젝트 디자이너**가 열립니다.

3. **빌드** 페이지를 선택하고 **경고 표시 안 함** 상자에서 경고 번호 `1762`를 지정합니다.

     ![프로젝트 디자이너, 빌드 페이지](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")

     자세한 내용은 [프로젝트 디자이너, 빌드 페이지(C#)](../ide/reference/build-page-project-designer-csharp.md)를 참조하세요.

4. 솔루션을 빌드합니다.

     **출력** 창에는 빌드에 대한 요약 정보만 표시됩니다.

     ![출력 창, Visual C&#35; 빌드 경고](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")

#### <a name="to-suppress-all-visual-basic-build-warnings"></a>모든 Visual Basic 빌드 경고를 표시하지 않으려면

1. **솔루션 탐색기**에서 최상위 프로젝트 노드를 선택합니다.

2. 메뉴 모음에서 **보기**, **속성 페이지**를 선택합니다.

    **프로젝트 디자이너**가 열립니다.

3. **컴파일** 페이지에서 **모든 경고 사용 안 함** 확인란을 선택합니다.

    ![프로젝트 디자이너, 컴파일 페이지](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")

    자세한 내용은 [Visual Basic에서 경고 구성](../ide/configuring-warnings-in-visual-basic.md)을 참조하세요.

4. 솔루션을 빌드합니다.

   **출력** 창에는 빌드에 대한 요약 정보만 표시됩니다.

   ![출력 창, Visual Basic 빌드 경고](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")

   자세한 내용은 [방법: 컴파일러 경고 표시 안 함](../ide/how-to-suppress-compiler-warnings.md)을 참조 하세요.

## <a name="display-additional-build-details-in-the-output-window"></a><a name="BKMK_outputdetails"></a> 출력 창에 추가 빌드 세부 정보 표시

**출력** 창에 표시할 빌드 프로세스에 대한 정보의 양을 변경할 수 있습니다. 빌드 자세한 정도는 일반적으로 최소로 설정 됩니다. 즉, **출력** 창에는 우선 순위가 높은 경고 또는 오류와 함께 빌드 프로세스에 대 한 요약만 표시 됩니다. [옵션 대화 상자, 프로젝트 및 솔루션, 빌드 및 실행](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)을 사용 하 여 빌드에 대 한 자세한 정보를 표시할 수 있습니다.

> [!IMPORTANT]
> 추가 정보를 표시하면 빌드를 완료하는 데 더 오랜 시간이 걸립니다.

#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>[출력] 창에서 정보의 양을 변경하려면

1. **옵션** 대화 상자를 엽니다.

    ![도구 메뉴의 옵션 명령](../ide/media/exploreide-toolsoptionsmenu.png "Exploreide-newprojectcsharp-ToolsOptionsmenu")

2. **프로젝트 및 솔루션** 범주를 선택하고 나서 **빌드 및 실행** 페이지를 선택합니다.

3. **MSBuild 프로젝트 빌드 출력의 자세한 정도** 목록에서 **보통**을 선택하고 나서 **확인** 단추를 선택합니다.

4. 메뉴 모음에서 **빌드**, **솔루션 정리**를 선택합니다.

5. 솔루션을 빌드하고 **출력** 창에서 정보를 검토합니다.

    빌드 정보에는 빌드가 시작된 시간(시작 부분에 있음), 파일이 처리된 순서 및 프로세스를 완료하는 데 걸린 시간(끝 부분에 있음)이 포함됩니다. 이 정보에는 빌드하는 동안 Visual Studio에서 실행하는 실제 컴파일러 구문도 포함됩니다.

    예를 들어 Visual C# 빌드에서 [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) 옵션은 이 항목에서 이전에 지정한 경고 코드, 1762를 세 개의 다른 경고와 함께 나열합니다.

    Visual Basic 빌드에서 [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) 은 제외할 특정 경고를 포함 하지 않으므로 경고가 나타나지 않습니다.

   > [!TIP]
   > Ctrl + F 키를 선택 하 여 **찾기** 대화 상자를 표시 하면 **출력** 창의 내용을 검색할 수 있습니다.

   자세한 내용은 [방법: 빌드 로그 파일 보기, 저장 및 구성](../ide/how-to-view-save-and-configure-build-log-files.md)을 참조하세요.

## <a name="create-a-release-build"></a>릴리스 빌드 만들기

전달에 최적화된 샘플 애플리케이션 버전을 빌드할 수 있습니다. 릴리스 빌드의 경우 빌드가 시작되기 전에 실행 파일이 네트워크 공유에 복사되도록 지정합니다.

자세한 내용은 [방법: 빌드 출력 디렉터리 변경](../ide/how-to-change-the-build-output-directory.md) 및 [Visual Studio에서 프로젝트 및 솔루션 빌드 및 정리](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)를 참조하세요.

#### <a name="to-specify-a-release-build-for-visual-basic"></a>Visual Basic에 대한 릴리스 빌드를 지정하려면

1. **프로젝트 디자이너**를 엽니다.

     ![보기 메뉴, 속성 페이지 명령](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. **컴파일** 페이지를 선택합니다.

3. **구성** 목록에서 **릴리스**를 선택합니다.

4. **플랫폼** 목록에서 **x86**을 선택합니다.

5. **빌드 출력 경로** 상자에서 네트워크 경로를 지정합니다.

     예를 들어 \\\myserver\builds를 지정할 수 있습니다.

    > [!IMPORTANT]
    > 지정한 네트워크 공유가 신뢰할 수 있는 위치가 아님을 알리는 메시지 상자가 나타날 수 있습니다. 지정한 위치를 신뢰 하는 경우 메시지 상자에서 **확인** 단추를 선택 합니다.

6. 애플리케이션을 빌드합니다.

     ![빌드 메뉴의 솔루션 빌드 명령](../ide/media/exploreide-buildsolution.png "Exploreide-newprojectcsharp-BuildSolution")

#### <a name="to-specify-a-release-build-for-visual-c"></a>Visual C에 대 한 릴리스 빌드를 지정 하려면\#

1. **프로젝트 디자이너**를 엽니다.

    ![보기 메뉴, 속성 페이지 명령](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. **빌드** 페이지를 선택합니다.

3. **구성** 목록에서 **릴리스**를 선택합니다.

4. **플랫폼** 목록에서 **x86**을 선택합니다.

5. **출력 경로** 상자에서 네트워크 경로를 지정합니다.

    예를 들어 \\\myserver\builds를 지정할 수 있습니다.

   > [!IMPORTANT]
   > 지정한 네트워크 공유가 신뢰할 수 있는 위치가 아님을 알리는 메시지 상자가 나타날 수 있습니다. 지정한 위치를 신뢰 하는 경우 메시지 상자에서 **확인** 단추를 선택 합니다.

6. 애플리케이션을 빌드합니다.

    ![빌드 메뉴의 솔루션 빌드 명령](../ide/media/exploreide-buildsolution.png "Exploreide-newprojectcsharp-BuildSolution")

   실행 파일이 지정한 네트워크 경로에 복사됩니다. 해당 경로는 \\\myserver\builds\\*FileName*.exe입니다.

   축하합니다. 이 연습을 완료했습니다.

## <a name="see-also"></a>관련 항목

- [연습: 프로젝트 빌드(C++)](https://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)
- [ASP.NET 웹 애플리케이션 프로젝트 미리 컴파일 개요](https://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [연습: MSBuild 사용](../msbuild/walkthrough-using-msbuild.md)
