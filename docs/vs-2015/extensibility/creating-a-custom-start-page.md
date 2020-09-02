---
title: 사용자 지정 시작 페이지 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acb7922658a5dd7db0839051a42a119733c8b1d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184199"
---
# <a name="creating-a-custom-start-page"></a>사용자 지정 시작 페이지 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[시작 페이지에서 설명한](../misc/creating-your-own-start-page.md)대로 시작 페이지 프로젝트 템플릿을 사용 하 여 사용자 지정 시작 페이지를 만들 수 없는 경우이 문서의 단계에 따라 수동으로 만들 수 있습니다.  
  
## <a name="creating-a-blank-start-page"></a>빈 시작 페이지 만들기  
 먼저 Visual Studio에서 인식 하는 태그 구조를 포함 하는 .xaml 파일을 만들어 빈 시작 페이지를 만듭니다. 그런 다음 태그와 코드 숨김으로 추가 하 여 원하는 모양과 기능을 만듭니다.  
  
#### <a name="to-create-a-blank-start-page"></a>빈 시작 페이지를 만들려면  
  
1. **WPF 응용 프로그램** (**Visual c #/Windows Desktop**) 형식의 새 프로젝트를 만듭니다.  
  
2. `Microsoft.VisualStudio.Shell.14.0`에 대한 참조를 추가합니다.  
  
3. XML 편집기에서 XAML 파일을 열고 \<Window> \<UserControl> 네임 스페이스 선언을 제거 하지 않고 최상위 요소를 요소로 변경 합니다.  
  
4. `x:Class`최상위 요소에서 선언을 제거 합니다. 이렇게 하면 XAML 콘텐츠가 시작 페이지를 호스트 하는 Visual Studio 도구 창과 호환 됩니다.  
  
5. 최상위 요소에 다음 네임 스페이스 선언을 추가 합니다 \<UserControl> .  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     이러한 네임 스페이스를 사용 하 여 Visual Studio 명령, 컨트롤 및 UI 설정에 액세스할 수 있습니다. 자세한 내용은 [시작 페이지에 Visual Studio 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)를 참조 하세요.  
  
     다음 예제에서는 빈 시작 페이지에 대 한 .xaml 파일의 태그를 보여 줍니다. 모든 사용자 지정 콘텐츠는 내부 요소로 이동 해야 합니다 <xref:System.Windows.Controls.Grid> .  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6. 빈 요소에 컨트롤을 추가 \<UserControl> 하 여 사용자 지정 시작 페이지를 채웁니다. Visual Studio와 관련 된 기능을 추가 하는 방법에 대 한 자세한 내용은 [시작 페이지에 Visual Studio 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)를 참조 하세요.  
  
## <a name="testing-and-applying-the-custom-start-page"></a>사용자 지정 시작 페이지 테스트 및 적용  
 Visual studio가 충돌 하지 않는지 확인할 때까지 사용자 지정 시작 페이지를 실행 하려면 Visual Studio의 기본 인스턴스를 설정 하지 마세요. 대신 실험적 인스턴스에서 테스트 합니다.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>수동으로 만든 사용자 지정 시작 페이지를 테스트 하려면  
  
1. XAML 파일, 지원 되는 텍스트 파일 또는 태그 파일을 **%USERPROFILE%\My Documents\Visual Studio 2015 \Startpages \\ ** 폴더에 복사 합니다.  
  
2. 시작 페이지에서 Visual Studio에서 설치 되지 않은 어셈블리의 컨트롤이 나 형식을 참조 하는 경우 어셈블리를 복사한 다음 _Visual studio 설치 폴더_**\Common7\IDE\PrivateAssemblies \\ **에 붙여넣습니다.  
  
3. Visual Studio 명령 프롬프트에서 **devenv/rootsuffix Exp** 를 입력 하 여 visual studio의 실험적 인스턴스를 엽니다.  
  
4. 실험적 인스턴스에서 **도구/옵션/환경/시작** 페이지로 이동 하 고 **사용자 지정 시작 페이지** 드롭다운에서 XAML 파일을 선택 합니다.  
  
5. **보기** 메뉴에서 **시작 페이지**를 클릭합니다.  
  
     사용자 지정 시작 페이지가 표시 됩니다. 모든 파일을 변경 하려면 실험적 인스턴스를 닫고 변경 내용을 적용 하 고 변경 된 파일을 복사 하 여 붙여넣은 다음 실험적 인스턴스를 다시 열어 변경 내용을 확인 해야 합니다.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Visual Studio의 기본 인스턴스에 사용자 지정 시작 페이지를 적용 하려면  
  
- 시작 페이지를 테스트 하 여 안정적인 것으로 확인 한 후에는 **옵션** 대화 상자에서 **시작 페이지 사용자 지정** 옵션을 사용 하 여 Visual Studio의 기본 인스턴스에서 시작 페이지로 선택할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [연습: 시작 페이지에 사용자 지정 XAML 추가](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [시작 페이지에 사용자 정의 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)   
 [시작 페이지에 Visual Studio 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [연습: 시작 페이지에 사용자 설정 저장](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [사용자 지정 시작 페이지 배포](../extensibility/deploying-custom-start-pages.md)
