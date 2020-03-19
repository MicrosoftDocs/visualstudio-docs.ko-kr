---
title: VB 프로젝트 속성의 애플리케이션 페이지
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe303f86b282e7e803dacc1dd8f4d3c1d6b72121
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595815"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)

프로젝트 디자이너의 **애플리케이션** 페이지를 사용하여 프로젝트의 애플리케이션 설정과 속성을 지정할 수 있습니다.

**애플리케이션** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다. 그런 다음, 메뉴 모음에서 **프로젝트** > **속성**을 선택합니다. **프로젝트 디자이너**가 나타나면 **애플리케이션** 탭을 선택합니다.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>일반 애플리케이션 설정

다음 옵션을 사용하여 애플리케이션에 대한 일반 설정을 구성할 수 있습니다.

### <a name="assembly-name"></a>어셈블리 이름

어셈블리 매니페스트가 포함될 출력 파일의 이름을 지정합니다. 이 속성을 변경하면 **출력 이름** 속성도 변경됩니다.

[/out(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) 컴파일러 스위치를 사용하여 명령 프롬프트에서 출력 파일의 이름을 지정할 수도 있습니다.

프로그래밍 방식으로 이 속성에 액세스하는 방법에 대한 자세한 내용은 <xref:VSLangProj.ProjectProperties.AssemblyName%2A>를 참조하세요.

### <a name="root-namespace"></a>루트 네임스페이스

프로젝트의 모든 파일에 대한 기본 네임스페이스를 지정합니다. 예를 들어 **루트 네임스페이스**를 `Project1`로 설정하고 코드의 네임스페이스 외부에 `Class1`이 있는 경우 해당 네임스페이스는 `Project1.Class1`입니다. 코드의 `Class2` 네임스페이스에 `Order`가 있는 경우 해당 네임스페이스는 `Project1.Order.Class2`입니다.

**루트 네임스페이스**의 선택을 취소하는 경우 코드에서 프로젝트의 네임스페이스 구조를 지정할 수 있습니다.

> [!NOTE]
> `Global`네임스페이스 명령문[에서 ](/dotnet/visual-basic/language-reference/statements/namespace-statement) 키워드를 사용하는 경우 프로젝트의 루트 네임스페이스 외부에서 네임스페이스를 정의할 수 있습니다. **루트 네임스페이스**의 선택을 취소하면 `Global`이 최상위 네임스페이스가 되므로 `Global` 문에 `Namespace` 키워드가 필요하지 않습니다. 자세한 내용은 [Visual Basic의 네임스페이스](/dotnet/visual-basic/programming-guide/program-structure/namespaces)에서 "Namespace 문의 Global 키워드"를 참조하세요.

코드에서 네임스페이스를 만드는 방법에 대한 자세한 내용은 [Namespace 문](/dotnet/visual-basic/language-reference/statements/namespace-statement)을 참조하세요.

루트 네임스페이스 속성에 대한 자세한 내용은 [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)를 참조하세요.

프로그래밍 방식으로 이 속성에 액세스하는 방법에 대한 자세한 내용은 <xref:VSLangProj.ProjectProperties.RootNamespace%2A>를 참조하세요.

### <a name="target-framework-all-configurations"></a>대상 프레임워크(모든 구성)

애플리케이션의 대상 .NET 버전을 지정합니다. 이 옵션은 컴퓨터에 설치된 .NET 버전에 따라 다른 값을 가질 수 있습니다.

.NET Framework 프로젝트의 경우 기본값은 프로젝트를 만들 때 지정한 대상 프레임워크와 일치합니다.

> [!NOTE]
> 대화 상자를 처음 열면 [필수 조건 대화 상자](../../ide/reference/prerequisites-dialog-box.md)에 나열된 필수 조건 패키지가 자동으로 설정됩니다. 이후에 프로젝트의 대상 프레임워크를 변경하는 경우 새 대상 프레임워크에 맞도록 필수 조건을 수동으로 지정해야 합니다.

자세한 내용은 [Framework 대상 지정 개요](../../ide/visual-studio-multi-targeting-overview.md)를 참조하세요.

### <a name="application-type"></a>애플리케이션 종류

빌드할 애플리케이션 종류를 지정합니다. 값은 프로젝트 형식에 따라 달라집니다. 예를 들어 **Windows Forms 앱**의 경우 대부분 **Windows Forms 애플리케이션**, **클래스 라이브러리**, **콘솔 애플리케이션**, **Windows 서비스** 또는 **웹 컨트롤 라이브러리**를 지정할 수 있습니다.

웹 애플리케이션 프로젝트의 경우 **클래스 라이브러리**를 지정해야 합니다.

**애플리케이션 종류** 속성에 대한 자세한 내용은 [/target(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target)을 참조하세요. 프로그래밍 방식으로 해당 속성에 액세스하는 방법에 대한 자세한 내용은 <xref:VSLangProj.ProjectProperties.OutputType%2A>을 참조하세요.

### <a name="auto-generate-binding-redirects"></a>바인딩 리디렉션 자동 생성

앱 또는 해당 구성 요소가 동일한 어셈블리의 버전을 두 개 이상 참조하는 경우 프로젝트에 바인딩 리디렉션이 추가됩니다. 프로젝트 파일에서 바인딩 리디렉션을 수동으로 정의하려는 경우 **바인딩 리디렉션 자동 생성**의 선택을 취소합니다.

리디렉션에 대한 자세한 내용은 [어셈블리 버전 리디렉션](/dotnet/framework/configure-apps/redirect-assembly-versions)을 참조하세요.

### <a name="startup-form--startup-object--startup-uri"></a>시작 폼/시작 개체/시작 URI

애플리케이션의 시작 폼 또는 진입점을 지정합니다.

**애플리케이션 프레임워크 사용**이 선택된 경우(기본값), 이 목록에 **시작 폼**이라는 제목이 지정되고, 애플리케이션 프레임워크에서 개체가 아니라 시작 폼만 지원하기 때문에 폼만 표시됩니다.

프로젝트가 WPF 브라우저 애플리케이션인 경우 이 목록에 **시작 URI**라는 제목이 지정되고 기본값은 **Page1.xaml**입니다. **시작 URI** 목록을 사용하면 애플리케이션이 시작 시 표시하는 사용자 인터페이스 리소스(XAML 요소)를 지정할 수 있습니다. 자세한 내용은 <xref:System.Windows.Application.StartupUri%2A>을 참조하세요.

**애플리케이션 프레임워크 사용**의 선택이 취소된 경우 이 목록은 **시작 개체**가 되고 `Sub Main`을 포함하는 폼과 클래스 또는 모듈을 둘 다 표시합니다.

**시작 개체**는 애플리케이션 로드 시 호출할 진입점을 정의합니다. 일반적으로 애플리케이션의 기본 폼이나 애플리케이션 시작 시 실행되어야 하는 `Sub Main` 프로시저로 설정됩니다. 클래스 라이브러리에 진입점이 없기 때문에 이 속성의 유일한 옵션은 **(없음)** 입니다. 자세한 내용은 [/main](/dotnet/visual-basic/reference/command-line-compiler/main)을 참조하세요. 프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.StartupObject%2A>를 참조하세요.

### <a name="icon"></a>아이콘

프로그램 아이콘으로 사용할 .ico 파일을 설정합니다. **\<찾아보기...>** 를 선택하여 기존 그래픽을 찾습니다. 자세한 내용은 [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)(또는 [/win32icon(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option))을 참조하세요. 프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>를 참조하세요.

### <a name="assembly-information"></a>어셈블리 정보

이 단추를 클릭하면 [어셈블리 정보 대화 상자](../../ide/reference/assembly-information-dialog-box.md)가 표시됩니다.

### <a name="enable-application-framework"></a>애플리케이션 프레임워크 사용

프로젝트에서 애플리케이션 프레임워크를 사용할지 여부를 지정합니다. 이 옵션의 설정은 **시작 폼**/**시작 개체**에서 사용할 수 있는 옵션에 영향을 줍니다.

이 확인란이 선택된 경우 애플리케이션에서 표준 `Sub Main`을 사용합니다. 이 확인란을 선택하면 **Windows 애플리케이션 프레임워크 속성** 섹션의 기능을 사용할 수 있으며, 시작 폼도 선택해야 합니다.

이 확인란의 선택을 취소하면 애플리케이션이 `Sub Main`시작 폼**에서 지정된 사용자 지정** 을 사용합니다. 이 경우 시작 개체(메서드 또는 클래스의 사용자 지정 `Sub Main`) 또는 폼을 지정할 수 있습니다. 또한 **Windows 애플리케이션 프레임워크 속성** 섹션의 옵션을 사용할 수 없게 됩니다.

### <a name="view-windows-settings"></a>Windows 설정 보기

이 단추를 클릭하면 *app.manifest* 파일이 생성되고 열립니다. Visual Studio는 이 파일을 사용하여 애플리케이션에 대한 매니페스트 데이터를 생성합니다. 그런 다음, `<requestedExecutionLevel>`app.manifest*의*  태그를 다음과 같이 수정하여 UAC 요청된 실행 수준을 설정합니다.

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce는 `asInvoker` 수준이나 가상화된 모드(매니페스트 생성 안 함)로 작동합니다. 가상화된 모드를 지정하려면 app.manifest에서 전체 태그를 제거합니다.

매니페스트 생성에 대한 자세한 내용은 [Windows Vista의 ClickOnce 배포](../../deployment/clickonce-deployment-on-windows-vista.md)를 참조하세요.

## <a name="windows-application-framework-properties"></a>Windows 애플리케이션 프레임워크 속성

다음 설정은 **Windows 애플리케이션 프레임워크 속성** 섹션에서 사용할 수 있습니다. 이러한 옵션은 **애플리케이션 프레임워크 사용** 확인란이 선택된 경우에만 사용할 수 있습니다.

> [!TIP]
> 다음 섹션에서는 WPF(Windows Presentation Foundation) 앱에 특정된 **Windows 애플리케이션 프레임워크 속성** 설정을 설명합니다.

### <a name="enable-xp-visual-styles"></a>XP 비주얼 스타일 사용

*Windows XP 테마*라고도 하는 Windows XP 비주얼 스타일을 사용하거나 사용하지 않습니다. 예를 들어 Windows XP 비주얼 스타일은 둥근 모서리와 동적 색이 지정된 컨트롤을 사용할 수 있게 합니다. 기본값을 사용합니다.

### <a name="make-single-instance-application"></a>단일 인스턴스 애플리케이션 작성

사용자가 애플리케이션의 여러 인스턴스를 실행하지 못하도록 하려면 이 확인란을 선택합니다. 이 확인란은 기본적으로 *선택이 취소*되어 있으므로 애플리케이션의 여러 인스턴스를 실행할 수 있습니다. 자세한 내용은 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> 이벤트를 참조하세요.

### <a name="save-mysettings-on-shutdown"></a>종료할 때 My.Settings 저장

사용자가 컴퓨터를 종료할 때 애플리케이션의 `My.Settings` 설정이 저장되도록 지정하려면 이 확인란을 선택합니다. 기본 설정은 사용입니다. 이 옵션을 사용하지 않도록 설정할 경우 `My.Settings.Save`를 호출하여 애플리케이션 설정을 수동으로 저장할 수 있습니다.

### <a name="authentication-mode"></a>인증 모드

Windows 인증을 사용하여 현재 로그온한 사용자를 식별하도록 지정하려면 **Windows**(기본값)를 선택합니다. `My.User` 개체를 사용하여 런타임에 이 정보를 검색할 수 있습니다. 기본 Windows 인증 방법을 사용하는 대신 사용자를 인증할 사용자 고유의 코드를 제공하는 경우 **애플리케이션 정의**를 선택합니다.

### <a name="shutdown-mode"></a>종료 모드

다른 폼이 열려 있어도 시작 폼으로 설정된 폼을 닫을 때 애플리케이션이 종료되도록 지정하려면 **시작 폼을 닫을 때**(기본값)를 선택합니다. 마지막 폼을 닫을 때나 **또는** 문을 명시적으로 호출할 때 애플리케이션이 종료되도록 지정하려면 `My.Application.Exit`마지막 폼을 닫을 때`End`를 선택합니다.

**을 명시적으로 호출할 때 애플리케이션이 종료되도록 지정하려면** 명시적으로 종료할 때`Shutdown`를 선택합니다.

마지막 창을 닫을 때 또는 **을 명시적으로 호출할 때 애플리케이션이 종료되도록 지정하려면** 마지막 창을 닫을 때`Shutdown`를 선택합니다. 이 값은 기본 설정입니다.

주 창을 닫을 때 또는 **을 명시적으로 호출할 때 애플리케이션이 종료되도록 지정하려면** 주 창을 닫을 때`Shutdown`를 선택합니다.

### <a name="splash-screen"></a>시작 화면

시작 화면으로 사용할 폼을 선택합니다. 이전에 폼 또는 템플릿을 사용하여 시작 화면을 만든 상태여야 합니다. 기본값은 **(없음)** 입니다.

### <a name="view-application-events"></a>애플리케이션 이벤트 보기

애플리케이션 프레임워크 이벤트 `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` 및 `NetworkAvailabilityChanged`에 대한 이벤트를 작성할 수 있는 이벤트 코드 파일을 표시하려면 이 단추를 클릭합니다. 특정 애플리케이션 프레임워크 메서드를 재정의할 수도 있습니다. 예를 들어 `OnInitialize`를 재정의하여 시작 화면의 표시 동작을 변경할 수 있습니다.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>WPF(Windows Presentation Foundation) 앱에 대한 Windows 애플리케이션 프레임워크 속성

프로젝트가 WPF(Windows Presentation Foundation) 앱인 경우 **Windows 애플리케이션 프레임워크 속성** 섹션에서 다음 설정을 사용할 수 있습니다. 이러한 옵션은 **애플리케이션 프레임워크 사용** 확인란이 선택된 경우에만 사용할 수 있습니다. 이 표에 나열된 옵션은 WPF 또는 WPF 브라우저 애플리케이션에만 사용할 수 있습니다. WPF 사용자 정의 컨트롤 또는 사용자 지정 컨트롤 라이브러리에는 사용할 수 없습니다.

### <a name="shutdown-mode"></a>종료 모드

이 속성은 WPF(Windows Presentation Foundation) 애플리케이션에만 적용됩니다.

**을 명시적으로 호출할 때 애플리케이션이 종료되도록 지정하려면** 명시적으로 종료할 때<xref:System.Windows.Application.Shutdown%2A>를 선택합니다.

마지막 창을 닫을 때 또는 **을 명시적으로 호출할 때 애플리케이션이 종료되도록 지정하려면** 마지막 창을 닫을 때<xref:System.Windows.Application.Shutdown%2A>를 선택합니다. 이 값은 기본 설정입니다.

주 창을 닫을 때 또는 **을 명시적으로 호출할 때 애플리케이션이 종료되도록 지정하려면** 주 창을 닫을 때<xref:System.Windows.Application.Shutdown%2A>를 선택합니다.

이 설정을 사용하는 방법에 대한 자세한 내용은 <xref:System.Windows.Application.Shutdown%2A>을 참조하세요.

### <a name="edit-xaml"></a>XAML 편집

이 단추를 클릭하면 XAML 편집기에서 애플리케이션 정의 파일(Application.xaml)을 엽니다. 이 단추를 클릭하면 애플리케이션 정의 노드에서 *Application.xaml*이 열립니다. 리소스 정의 등의 특정 작업을 수행하려면 이 파일을 편집해야 할 수도 있습니다. 애플리케이션 정의 파일이 없는 경우 프로젝트 디자이너에서 새로 만듭니다.

### <a name="view-application-events"></a>애플리케이션 이벤트 보기

이 단추를 클릭하면 코드 편집기에서 `Application` 클래스 파일(*Application.xaml.vb*)을 엽니다. 파일이 없는 경우 프로젝트 디자이너에서 적절한 클래스 이름과 네임스페이스를 사용하여 새로 만듭니다.

<xref:System.Windows.Application> 개체는 특정 애플리케이션 상태가 변경될 때(예: 애플리케이션 시작 또는 종료 시) 이벤트를 발생시킵니다. 이 클래스가 노출하는 이벤트의 전체 목록은 <xref:System.Windows.Application>을 참조하세요. 이러한 이벤트는 `Application` partial 클래스의 사용자 코드 섹션에서 처리됩니다.
