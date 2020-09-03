---
title: '연습: Windows 스토어 앱용 단위 테스트 만들기 및 실행 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e62fe83d644b577d7d0a5f87312642f438c490
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851177"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>연습: Windows 스토어 앱용 단위 테스트 만들기 및 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에는 관리되는 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 응용 프로그램에 대한 단위 테스트 지원이 포함되어 있으며, Visual C#, Visual Basic 및 Visual C++에 대한 단위 테스트 라이브러리 템플릿이 포함되어 있습니다.

> [!TIP]
> [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱 개발에 대한 자세한 내용은 [Windows 스토어 앱 시작하기](https://msdn.microsoft.com/windows/apps/br211386.aspx)를 참조하세요.

 Visual Studio는 다음과 같은 유닛 테스트 기능을 제공합니다.

- [단위 테스트 프로젝트 만들기](#CreateAndRunUnitTestWin8Tailored_Create)

- [단위 테스트 프로젝트에 대한 매니페스트 편집](#CreateAndRunUnitTestWin8Tailored_Manifest)

- [단위 테스트 코딩](#CreateAndRunUnitTestWin8Tailored_Code)

- [단위 테스트 실행](#CreateAndRunUnitTestWin8Tailored_Run)

  다음 절차에서는 관리되는 Windows 8 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 응용 프로그램에 대한 단위 테스트를 작성, 실행 및 디버깅하는 단계를 설명합니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio

## <a name="create-unit-test-projects"></a><a name="CreateAndRunUnitTestWin8Tailored_Create"></a> 단위 테스트 프로젝트 만들기

#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Windows 스토어 응용 프로그램에 대한 단위 테스트 프로젝트를 만들려면

1. **파일** 메뉴에서 **새 프로젝트**를 선택합니다.

     새 프로젝트 대화 상자가 표시됩니다.

2. 템플릿에서 단위 테스트를 만들 프로그래밍 언어를 선택하고 연결된 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 단위 테스트 라이브러리를 선택합니다. 예를 들면 **Visual C#** 를 선택하고 **Windows 스토어**를 선택한 다음 **단위 테스트 라이브러리(Windows 스토어 응용 프로그램)** 를 선택합니다.

    > [!NOTE]
    > Visual Studio에는 Visual C#, Visual Basic 및 Visual C++에 대한 단위 테스트 라이브러리 템플릿이 포함되어 있습니다.

3. (선택 사항) **이름** 텍스트 상자에 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]단위 테스트 프로젝트에 사용할 이름을 입력합니다.

4. (선택 사항) **위치** 텍스트 상자에 입력하거나 **찾아보기** 단추를 선택하여 프로젝트를 만들 경로를 수정합니다.

5. (선택 사항) **솔루션** 이름 텍스트 상자에 솔루션에 사용할 이름을 입력합니다.

6. **솔루션용 디렉터리 만들기** 옵션을 선택한 상태에서 **확인** 단추를 선택합니다.

     ![맞춤형 단위 테스트 라이브러리](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")

     솔루션 탐색기는 새로운 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]단위 테스트 프로젝트로 채워지며 코드 편집기에는 UnitTest1이라는 제목의 기본 단위 테스트가 표시됩니다.

     ![새 맞춤형 단위 테스트 프로젝트](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="edit-the-manifest-for-the-unit-test-project"></a><a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> 단위 테스트 프로젝트에 대 한 매니페스트 편집
 단위 테스트 프로젝트가 필요한 기능을 제공하여 응용 프로그램을 실행하려면 매니페스트를 편집해야 할 수 있습니다.

#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>단위 테스트 프로젝트의 Windows 스토어 애플리케이션 매니페스트 파일을 편집하려면

1. 솔루션 탐색기의 새 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 단위 테스트 프로젝트에서 Package.appxmanifest 파일을 마우스 오른쪽 단추로 클릭하고 **열기**를 선택합니다.

     편집하기 위해 매니페스트 디자이너를 표시합니다.

2. 매니페스트 디자이너에서 **기능** 탭을 선택 합니다.

3. **기능**의 목록에서 단위 테스트와 테스트하는 코드에 필요한 기능을 선택합니다. 예를 들어, 단위 테스트에 필요하고 테스트하려는 코드에 인터넷 액세스 기능이 있어야 하는 경우 **인터넷** 확인란을 선택합니다.

    > [!NOTE]
    > 선택하는 기능에는 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 단위 테스트가 제대로 작동하는 데 필요한 기능만 포함되어야 합니다. 기능은 테스트되는 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 응용 프로그램의 일부가 아닌 기능을 포함할 필요가 전혀 없으며 일반적으로 테스트 중인 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]응용 프로그램에 대해 지정된 기능의 하위 집합이어야 합니다.

     매니페스트 디자이너에 대한 자세한 내용은 [매니페스트 디자이너를 사용하여 Windows 8.1 앱 패키지 구성](https://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d)을 참조하세요.

     ![단위 테스트 매니페스트](../test/media/unit-test-win8.png "Unit_Test_Win8_")

## <a name="code-the-unit-test"></a><a name="CreateAndRunUnitTestWin8Tailored_Code"></a> 단위 테스트 코딩

#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Windows 스토어 응용 프로그램에 대한 단위 테스트를 코딩하려면

1. 코드 편집기에서, 단위 테스트를 편집하고 테스트에 필요한 어설션과 논리를 추가합니다.

     자세한 내용은 MSDN 라이브러리에서 [어설션 클래스 사용](https://msdn.microsoft.com/library/ms182530.aspx) 을 참조하세요.

## <a name="run-unit-tests"></a><a name="CreateAndRunUnitTestWin8Tailored_Run"></a> 단위 테스트 실행

#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>솔루션을 빌드하고 테스트 탐색기를 사용하여 단위 테스트를 실행하려면

1. **테스트** 메뉴에서 **창**을 선택한 다음 **테스트 탐색기**를 선택합니다.

     테스트 탐색기가 테스트 목록 없이 표시됩니다.

2. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

     단위 테스트가 지금 나열됩니다.

    > [!NOTE]
    > 테스트 탐색기에서 단위 테스트 목록을 업데이트하는 솔루션을 빌드해야 합니다.

    > [!WARNING]
    > Visual Studio의 알려진 문제: 테스트 프로젝트를 빌드하기 전에 테스트 탐색기를 열어야 합니다.

3. 테스트 탐색기에서 만든 단위 테스트를 선택합니다.

    > [!TIP]
    > 테스트 탐색기는 **소스:** 옆의 소스 코드에 대한 링크를 제공합니다.

4. **모두 실행**을 선택합니다.

     ![단위 테스트 탐색기 &#45; 단위 테스트 실행](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")

    > [!TIP]
    > 탐색기에 나열된 하나 이상의 단위 테스트를 선택하고 마우스 오른쪽 단추를 클릭한 다음 **선택한 테스트 실행**을 선택합니다.
    >
    >  또한 **선택한 테스트 디버그**, **테스트 열기**를 선택하고 **속성** 옵션을 사용할 수 있습니다.
    >
    >  ![단위 테스트 탐색기 &#45; 단일 테스트 상황에 맞는 메뉴](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

     단위 테스트가 실행됩니다. 완료되면, 테스트 탐색기는 테스트 상태와 경과된 시간을 표시하고 소스에 대한 링크를 제공합니다.

     ![테스트 완료 &#45; 단위 테스트 탐색기](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")

## <a name="external-resources"></a>외부 리소스

### <a name="videos"></a>동영상
 [채널 9: XAML을 사용하여 빌드한 Windows 스토어 앱 유닛 테스트](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>포럼
 [Visual Studio 유닛 테스트](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="msdn-library"></a>MSDN 라이브러리
 [MSDN 라이브러리 – 기존 코드에 대한 단위 테스트 만들기 및 실행(Visual Studio 2010)](https://msdn.microsoft.com/library/hh270865(v=vs.110).aspx)

## <a name="see-also"></a>관련 항목
 [Visual Studio를 사용 하 여 스토어 앱 테스트](../test/testing-store-apps-with-visual-studio.md) [Team Foundation build를 사용 하 여 Windows 스토어 앱 빌드 및 테스트](https://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)
