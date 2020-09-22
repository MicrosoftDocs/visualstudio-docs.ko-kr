---
title: 격리 셸 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841646"
---
# <a name="extending-the-isolated-shell"></a>격리 셸 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage, MEF (Managed Extensibility Framework) 구성 요소 부분 또는 일반 VSIX 프로젝트를 격리 된 셸 응용 프로그램에 추가 하 여 Visual Studio 격리 셸을 확장할 수 있습니다.  
  
> [!NOTE]
> 다음 단계를 수행 하면 Visual Studio Shell 격리 프로젝트 템플릿을 사용 하 여 기본 격리 셸 응용 프로그램을 만들 수 있습니다. 이 프로젝트 템플릿에 대 한 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 패키지 프로젝트 템플릿의 위치  
 Visual Studio 패키지 프로젝트 템플릿은 **새 프로젝트** 대화 상자의 세 가지 서로 다른 위치에 있습니다.  
  
1. **Visual Basic**에서 **확장성**. 프로젝트의 기본 언어는 Visual Basic입니다.  
  
2. **Visual c #** 아래에서 **확장성**. 프로젝트의 기본 언어는 C#입니다.  
  
3. **기타 프로젝트 형식**, **확장성**. 프로젝트의 기본 언어는 C++입니다.  
  
## <a name="adding-a-vspackage"></a>VSPackage 추가  
 격리 된 셸 응용 프로그램에 VSPackage를 추가할 수 있습니다. 다음 단계는 메뉴 명령을 추가 하는 방법을 보여 줍니다.  
  
#### <a name="to-add-a-new-vspackage"></a>새 VSPackage을 추가 하려면  
  
1. 이라는 Visual Studio 패키지 프로젝트를 추가 `MenuCommandsPackage` 합니다.  
  
2. 마법사의 **기본 VSPackage 정보** 페이지에서 **회사 이름** 을로 설정 하 `Fabrikam` 고 **VSPackage name** 을로 설정 `FabrikamMenuCommands` 합니다. **다음** 단추를 선택합니다.  
  
3. 다음 페이지에서 **메뉴 명령** 을 선택 하 고 **다음**을 선택 합니다.  
  
4. 다음 페이지에서 **명령 이름** 을로, 명령 ID를로 설정 하 `Fabrikam Command` **Command ID** `cmdidFabrikamCommand` 고 **다음**을 선택 합니다.  
  
5. **테스트 프로젝트 옵션 선택** 페이지에서 테스트 옵션을 선택 취소 한 후 **마침** 단추를 선택 합니다.  
  
6. ShellExtensionsVSIX 프로젝트에서 source.extension.vsixmanifest 파일을 엽니다.  
  
     **자산** 섹션에는 Vsshellstub 프로젝트에 대 한 항목이 포함 되어야 합니다.  
  
7. **새로 만들기** 단추를 선택 합니다.  
  
8. **새 자산 추가** 창의 **유형** 목록에서 **VisualStudio. VsPackage**를 선택 합니다.  
  
9. **원본** 목록에서 **현재 솔루션의 프로젝트가** 선택 되어 있는지 확인 합니다. **프로젝트** 목록 상자에서 **MenuCommandsPackage**를 선택 합니다.  
  
10. 파일을 저장하고 닫습니다.  
  
11. 솔루션을 다시 빌드하고 격리 된 셸 디버깅을 시작 합니다.  
  
12. 메뉴 모음에서 **도구** 메뉴, **Fabrikam 명령**을 차례로 선택 합니다.  
  
     메시지 상자가 표시 됩니다.  
  
13. 응용 프로그램 디버깅을 중지 합니다.  
  
## <a name="adding-a-mef-component-part"></a>MEF 구성 요소 파트 추가  
 다음 단계에서는 격리 된 셸 응용 프로그램에 MEF 구성 요소 파트를 추가 하는 방법을 보여 줍니다.  
  
#### <a name="to-add-a-mef-component"></a>MEF 구성 요소를 추가 하려면  
  
1. **새 프로젝트 추가** 대화 상자의 **Visual c #**, **확장성**에서 **편집기 여백** 템플릿을 사용 하 여 프로젝트를 추가 합니다. 이름을 `ShellEditorMargin`로 지정합니다.  
  
2. ShellExtensionsVSIX 프로젝트에서 코드 보기가 아닌 디자인 뷰 source.extension.vsixmanifest 파일을 엽니다.  
  
3. 섹션에서 `Asset` **콘텐츠 추가**를 선택 합니다.  
  
4. **새 자산 추가** 창의 **유형** 목록에서 **VisualStudio**을 선택 합니다.  
  
5. **원본** 목록에서 **현재 솔루션의 프로젝트가** 선택 되어 있는지 확인 합니다. **프로젝트** 목록 상자에서 **ShellEditorMargin**를 선택 합니다.  
  
6. 파일을 저장하고 닫습니다.  
  
7. 솔루션을 다시 빌드하고 격리 된 셸 디버깅을 시작 합니다.  
  
8. 텍스트 파일을 엽니다.  
  
     "Hello 세계!" 라는 단어를 포함 하는 녹색 여백 텍스트 파일 창의 아래쪽에 표시 됩니다.  
  
9. 응용 프로그램 디버깅을 중지 합니다.  
  
## <a name="adding-a-generic-vsix-project"></a>제네릭 VSIX 프로젝트 추가  
  
#### <a name="to-add-a-generic-vsix-project"></a>일반 VSIX 프로젝트를 추가 하려면  
  
1. **새 프로젝트 추가** 대화 상자의 **Visual c #**, **확장성**에서 **VSIXProject** 템플릿을 사용 하 여 프로젝트를 추가 합니다. 이름을 `EmptyVSIX`로 지정합니다.  
  
2. ShellExtensionsVSIX 프로젝트에서 코드 보기가 아닌 디자인 뷰 source.extension.vsixmanifest 파일을 엽니다.  
  
3. 섹션에서 `Assets` **새로 만들기**를 선택 합니다.  
  
4. **새 자산 추가** 창의 **유형** 목록에서 추가 하려는 콘텐츠의 종류를 선택 합니다.  
  
5. **소스**에서 **현재 솔루션의 프로젝트** 옵션이 선택 되어 있는지 확인 합니다. 목록 상자에서 VSIX 프로젝트의 이름을 선택 합니다.  
  
6. 파일을 저장하고 닫습니다.  
  
7. 이 프로젝트에 컴파일된 코드가 포함 된 경우 어셈블리가 출력에 포함 되도록 프로젝트를 편집 해야 합니다.  
  
    1. VSIX 프로젝트를 언로드하고 프로젝트 파일을 엽니다.  
  
    2. 첫 번째 `<PropertyGroup>` 블록에서 값을 `<CopyBuildOutputToOutputDirectory>` 로 변경 `true` 합니다.  
  
    3. 프로젝트를 저장 하 고 다시 로드 합니다.  
  
8. 솔루션을 빌드하고 실행합니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 기본 격리 셸 애플리케이션 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
