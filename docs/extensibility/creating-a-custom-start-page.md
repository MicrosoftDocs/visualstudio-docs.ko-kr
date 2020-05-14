---
title: 사용자 지정 시작 페이지 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739635"
---
# <a name="creating-a-custom-start-page"></a>사용자 지정 시작 페이지 만들기

이 문서의 단계에 따라 사용자 지정 시작 페이지를 만들 수 있습니다.

## <a name="create-a-blank-start-page"></a>빈 시작 페이지 만들기

먼저 Visual Studio에서 인식할 태그 구조가 있는 *.xaml* 파일을 만들어 빈 시작 페이지를 만듭니다. 그런 다음 태그와 코드 뒤에 태그를 추가하여 원하는 모양과 기능을 생성합니다.

1. **유형 WPF 응용 프로그램의** 새 프로젝트를 만듭니다 **(시각적 C #** > **Windows 데스크톱).**

2. `Microsoft.VisualStudio.Shell.14.0`에 대한 참조를 추가합니다.

3. XML 편집기에서 XAML 파일을 열고 네임스페이스 선언을 제거하지 않고 최상위 \<Window> 요소를 \<UserControl> 요소로 변경합니다.

4. 최상위 `x:Class` 요소에서 선언을 제거합니다. 이렇게 하면 XAML 콘텐츠가 시작 페이지를 호스트하는 Visual Studio 도구 창과 호환됩니다.

5. 최상위 \<UserControl> 요소에 다음 네임스페이스 선언을 추가합니다.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     이러한 네임스페이스를 사용하면 Visual Studio 명령, 컨트롤 및 UI 설정에 액세스할 수 있습니다. 자세한 내용은 [시작 페이지에 Visual Studio 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)를 참조하십시오.

     다음 예제에서는 빈 시작 페이지에 대한 *.xaml* 파일의 태그를 보여 주습니다. 모든 사용자 지정 콘텐츠는 <xref:System.Windows.Controls.Grid> 내부 요소로 이동해야 합니다.

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

6. 빈 \<UserControl> 요소에 컨트롤을 추가하여 사용자 지정 시작 페이지를 채웁니다. Visual Studio와 관련된 기능을 추가하는 방법에 대한 자세한 내용은 [시작 페이지에 Visual Studio 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)를 참조하십시오.

## <a name="test-and-apply-the-custom-start-page"></a>사용자 지정 시작 페이지를 테스트하고 적용합니다.

Visual Studio가 크래시되지 않는지 확인할 때까지 사용자 지정 시작 페이지를 실행하도록 Visual Studio의 기본 인스턴스를 설정하지 마십시오. 대신 실험 인스턴스에서 테스트합니다.

### <a name="to-test-a-manually-created-custom-start-page"></a>수동으로 만든 사용자 지정 시작 페이지를 테스트하려면

1. XAML 파일 및 지원 텍스트 파일 또는 마크업 파일을 *%USERPROFILE%\My 문서\Visual Studio 2015\StartPages\\ * 폴더에 복사합니다.

2. 시작 페이지에서 Visual Studio에서 설치하지 않은 어셈블리의 컨트롤이나 형식을 참조하는 경우 어셈블리를 복사한 다음 *{Visual Studio 설치\\폴더}\Common7\IDE\PrivateAssemblies에*붙여넣습니다.

3. Visual Studio 명령 프롬프트에서 **devenv /rootsuffix Exp를** 입력하여 Visual Studio의 실험 인스턴스를 엽니다.

4. 실험적인 인스턴스에서 **도구** > **옵션** > **환경** > **시작** 페이지로 이동하여 사용자 **지정 시작 페이지** 드롭다운에서 XAML 파일을 선택합니다.

5. **보기** 메뉴에서 **시작 페이지**를 클릭합니다.

     사용자 지정 시작 페이지가 표시되어야 합니다. 파일을 변경하려면 실험 인스턴스를 닫고 변경한 파일을 복사하여 붙여넣은 다음 실험 인스턴스를 다시 열어 변경 내용을 확인해야 합니다.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Visual Studio의 기본 인스턴스에서 사용자 지정 시작 페이지를 적용하려면

- 시작 페이지를 테스트하고 안정적이라고 판단한 후 **옵션** 대화 상자에서 **시작 페이지 사용자 지정** 옵션을 사용하여 Visual Studio의 기본 인스턴스에서 시작 페이지로 선택합니다.

## <a name="see-also"></a>참조

- [연습: 시작 페이지에 사용자 지정 XAML 추가](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [시작 페이지에 사용자 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)
- [시작 페이지에 시각적 스튜디오 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [연습: 시작 페이지에 사용자 설정 저장](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [사용자 지정 시작 페이지 배포](../extensibility/deploying-custom-start-pages.md)
